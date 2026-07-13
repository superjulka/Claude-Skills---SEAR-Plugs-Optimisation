# Inbox-as-CRM — Outreach Tracker Rebuild Task

> Generic, parameterised version of the scheduled task that rebuilds SEAR's B2B tracker from Gmail. Full story: [The Inbox Is the CRM](https://julia-site-seven.vercel.app/workflows/inbox-as-crm). Real thread IDs, segment heuristics and file paths removed.

## Principle

Gmail is the single source of truth. The tracker is **rebuilt from scratch on every run** by parsing the sent folder and inbox — nothing can drift out of sync, because the inbox *is* the state. Accepted trade-off: classification is heuristic, so a human sanity-checks the dashboard.

## Task specification

1. **Search Gmail:**
   - Sent: `in:sent subject:"[YOUR CAMPAIGN TAG]"` (max 500)
   - Inbox: `in:inbox [YOUR BRAND]` (max 200)
   - Note: depending on your Gmail tool surface, results may need a double JSON parse (`outer[0]['text']` → parse again → `messages[].headers`).
2. **Dedupe** sent messages by `threadId` → unique outreach threads.
3. **Filter noise** from the inbox: automated notifications (payments, CMS, mailing tools), self-sent mail, unrelated senders.
4. **Classify each genuine reply** into six statuses: `Confirmed Order` / `Sample Requested` / `Positive — follow up` / `Acknowledged` / `Replied — Mixed` / `Auto-Reply` (default: `No Reply Yet`). Consider adding an `Unclassified` bucket — forcing every reply into fixed statuses hides the interesting mixed cases.
5. **Categorise every contact** into your segments using a domain + subject-keyword map: `[DEFINE YOUR SEGMENT → KEYWORD MAP]`.
6. **Build the workbook** (openpyxl): Sheet 1 — tracker (9 columns, colour-coded status, freeze panes, alternate row shading); Sheet 2 — dashboard (response overview %, by-category table, hot-prospects list).
7. **Verification gate:** run a spreadsheet recalculation check; the file is not done until it returns zero formula errors. **Also verify derived fields** — company names derived from email domains were wrong on our first build; a review pass before shipping is part of the spec.
8. **Draft a summary email** (to yourself) with totals, hot prospects and the tracker location. Draft, not send.

## Operational notes learned in production

- Write the task prompt to run **cold**: exact queries, parse patterns, full column spec, colour map, success criteria. No reliance on conversation memory.
- **Pre-run the task manually once** ("run now") to pre-approve tool permissions, so the scheduled run doesn't stall on a permission prompt.
- If you want this weekly, actually create the recurring schedule — our "weekly update" email template outlived the one-time cron behind it, and refreshes quietly became manual.
