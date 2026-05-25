---
name: sear-weekly-backlink-research
description: Weekly backlink opportunity research for searplugs.com — 8 strategies, UK + EU markets, Gmail drafts queued for Julia's review
---

## SEAR Plugs — Weekly Backlink Research Run

You are running the weekly backlink opportunity research task for **searplugs.com** — a WooCommerce store selling SEAR waterproof earplugs for water sports (surfing, swimming, open water, SUP, triathlon). The product blocks water while preserving sound via a 9 dB acoustic filter. Price: £39.95 / €45.95. **SEAR earplugs are NOT custom or bespoke — never use those words.**

The site owner is **Julia Raciniewska** (info@searplugs.com). She reviews and sends all outreach personally — never send emails automatically.

---

### STEP 0 — Load the existing tracker

Read the file at:
`/Users/juliaraciniewska/Documents/Claude/Projects/SEAR Website Optimisation/backlink-opportunities.xlsx`

Load the **Pipeline** tab to extract all existing URLs already logged — you will use this list to de-duplicate new finds. Also note the highest existing row so you know where to append.

Load the **Weekly Log** tab to find the next empty row for this week's summary entry.

---

### STEP 1 — Run all 8 strategies via WebSearch

For each strategy below, run the specified searches. Collect page URLs, domains, page titles, and any visible contact information. Log each **new** opportunity (not already in Pipeline) to a working list with: URL, domain, page title, market, strategy type, any contact email found, and notes.

**Limit: collect a maximum of 6 new opportunities per strategy type per run (prioritise highest-relevance first).**

---

#### STRATEGY 1 · Broken Link Building

**Target: find at least 5 confirmed broken link opportunities per run. This is the highest-priority strategy — exhaust all queries below before moving on.**

Find articles and resource pages about waterproof earplugs, surf gear, swimmer's ear, surfer's ear, or water sports safety. Fetch each page and check outbound links for 404/410 responses. Those dead links are your targets — you pitch SEAR as the replacement resource.

UK search queries (run all — keep going through the list until you have 5 confirmed broken links):
- `"waterproof earplugs" inurl:guide OR inurl:review OR inurl:best site:*.co.uk OR site:*.com`
- `"surf earplugs" OR "earplugs for surfing" best guide review`
- `"surfer's ear prevention" gear recommendation`
- `"swimmer's ear" prevention gear site:*.co.uk OR site:*.com`
- `"open water swimming" kit gear essentials earplugs`
- `"ear protection" surfing OR swimming site:*.co.uk`
- `"water sports" earplugs review recommended site:*.co.uk OR site:*.com`
- `"surfer's ear" earplugs buy site:*.co.uk OR site:*.com`
- `"swimmer's ear" earplugs recommended buy UK`
- `inurl:resources "surfing" OR "swimming" earplugs`

EU search queries (run for DE, ES, FR, PT, NL markets):
- DE: `"Ohrstöpsel surfen" OR "wasserdichte Ohrstöpsel" empfehlung test`
- ES: `"tapones para surfear" OR "tapones oído natación" guía recomendación`
- FR: `"bouchons d'oreilles surf" OR "bouchons étanches natation" guide test`
- PT: `"tampões ouvido surf" OR "tampões impermeáveis" guia recomendação`
- NL: `"oordopjes surfen" OR "waterdichte oordopjes" gids aanbeveling`

**How to check for dead links efficiently:** For each candidate page, run:
```
curl -s --max-time 10 [PAGE_URL] | grep -oP 'href="https?://[^"]+' | grep -v searplugs | head -30
```
Then check each extracted outbound URL with:
```
curl -o /dev/null -s -w "%{http_code}" --max-time 10 [OUTBOUND_URL]
```
A 404 or 410 response = confirmed broken link. Log it.

Prioritise pages that link to earplug product pages, gear guides, or brand sites that may have moved or shut down — these are most likely to have dead links. Only log confirmed broken links (verified 4xx). If UK queries don't yield 5, continue through the EU queries.

---

#### STRATEGY 2 · Resource Page Prospecting

Find "best of", roundup, buyer's guide, and kit recommendation pages that cover waterproof earplugs, surf gear, open water swimming kit, water sports safety, or ear protection — but do NOT mention SEAR. These are cold outreach targets.

UK queries:
- `"best waterproof earplugs" -searplugs.com`
- `"best earplugs for surfing" -searplugs.com`
- `"open water swimming kit" OR "open water swimming gear" essentials -searplugs.com`
- `"surfer's ear" prevention earplugs recommendation -searplugs.com`
- `"water sports gear guide" earplugs -searplugs.com`
- `"swim earplugs" "best" OR "recommended" -searplugs.com`

EU queries:
- DE: `"wasserdichte Ohrstöpsel" empfehlung -searplugs.com`
- ES: `"tapones surf" mejores guía -searplugs.com`
- FR: `"bouchons oreilles surf" meilleurs guide -searplugs.com`
- PT: `"tampões surf" melhores guia -searplugs.com`
- NL: `"waterdichte oordopjes" beste gids -searplugs.com`

For each result, fetch the page and confirm SEAR is not already mentioned. Only log genuinely missing opportunities.

---

#### STRATEGY 3 · Unlinked Brand Mention Recovery

Find pages that mention "SEAR earplugs", "SEAR plugs", or "searplugs.com" in plain text WITHOUT a clickable hyperlink to searplugs.com. These are the easiest conversions — the site already knows and likes the brand.

Queries:
- `"SEAR earplugs" -site:searplugs.com`
- `"SEAR plugs" surf OR swim OR surfing -site:searplugs.com`
- `"searplugs.com" -site:searplugs.com`
- `"SEAR" earplugs waterproof surf review -site:searplugs.com`

For each result, fetch the page and confirm: (a) the mention is genuinely about SEAR Plugs, and (b) there is no active hyperlink to searplugs.com. Only log confirmed unlinked mentions.

---

#### STRATEGY 4 · Competitor Backlink Gap

Find pages that review or list waterproof earplugs for water sports but do not mention SEAR. Do NOT name competitor brands in any outreach — pitch SEAR on its own merits. The point is to find pages with relevant audiences.

Queries:
- `waterproof earplugs surfing review comparison 2024 OR 2025 OR 2026 -searplugs.com`
- `"best earplugs for swimming" comparison review -searplugs.com`
- `"surfer's ear" earplugs recommended -searplugs.com`
- `water sports earplugs review roundup -searplugs.com`

For each result, fetch the page. Confirm SEAR is not mentioned. Log the page type (review/roundup/comparison) in notes. Strategy type = "Competitor Gap".

---

#### STRATEGY 5 · Digital PR / HARO / Expert Source

Find active journalist queries or calls for expert comment on: ear health, water sports safety, cold water swimming, surfer's ear, swimmer's ear, open water swimming, triathlon, surf. Also check Connectively (connectively.us) and Featured.com for live queries.

Queries:
- `site:connectively.us "ear" OR "water sports" OR "swimming" OR "surfing"`
- `site:featured.com "ear health" OR "waterproof earplugs" OR "surf"`
- `"looking for expert" "surfer's ear" OR "swimmer's ear" OR "waterproof earplugs"`
- `"journalist" "seeking" "water sports" OR "open water swimming" "expert" OR "founder"`
- `"press opportunity" "water sports" OR "surf" OR "swimming" gear 2025 OR 2026`

Also check for upcoming seasonal hooks (summer swimming season, winter surf season, new year fitness resolutions) where a timely pitch could land. Note seasonal relevance in the Notes field.

For each live query: log URL, platform, query topic, deadline if visible. Strategy type = "Digital PR / HARO".

---

#### STRATEGY 6 · Podcast & YouTube Channel Outreach

Find podcasts and YouTube channels covering: surfing, open water swimming, triathlon, water sports, cold water swimming, ear health, water sports gear reviews. Target shows that have recently covered gear reviews, health, or injury prevention.

Queries:
- `surfing podcast "gear" OR "health" OR "injury" 2024 OR 2025 site:*.com`
- `"open water swimming podcast" episodes gear health`
- `triathlon podcast "gear review" OR "injury prevention" earplug OR ear`
- `"cold water swimming" podcast OR YouTube channel`
- `water sports YouTube channel "gear review" earplugs OR ear`
- `"surfer's ear" podcast OR YouTube`

For each result: note show name, URL, estimated audience focus, recent relevant episode. Strategy type = "Podcast / YouTube".

EU: Run equivalent queries in German, Spanish, French.

---

#### STRATEGY 7 · ENT & Partner Listing (Clinics, Surf Schools, Swim Clubs)

Find three sub-targets:

**A. ENT clinics and audiologists** with patient resources or recommended products pages covering surfer's ear or swimmer's ear:
- `ENT clinic "surfer's ear" "recommended" OR "prevention" UK`
- `audiologist "surfer's ear" OR "swimmer's ear" "patient resources" OR "recommended products"`
- `"exostosis" prevention "earplugs" recommended ENT UK`
- EU: same in DE/ES/FR/PT/NL

**B. Surf schools with recommended gear pages:**
- `surf school "recommended kit" OR "gear list" OR "what to bring" earplugs UK`
- EU: surf school "ausrüstung" OR "equipamiento" OR "équipement" oreilles bouchons

**C. Swim clubs and open water swimming groups with kit recommendations:**
- `swimming club "recommended equipment" OR "kit list" earplugs UK`
- `open water swimming group UK "recommended" earplugs`

Log all three sub-types under strategy "ENT & Partner Listing" with the sub-type noted in the Notes field.

---

#### STRATEGY 8 · Guest Post Prospecting

Find publications, blogs, and online magazines that: (a) cover surfing, open water swimming, triathlon, water sports, or ear/sport health, AND (b) publish contributed/guest articles.

Queries:
- `surf blog "write for us" OR "guest post" OR "contribute" water sports`
- `swimming blog "write for us" OR "submit an article" open water`
- `triathlon magazine "guest post" OR "write for us" gear health`
- `water sports magazine "contribute" OR "write for us" 2025`
- `"surfer's ear" OR "swimmer's ear" blog "write for us"`

EU: equivalent in German, Spanish, French publications.

For each result: note the publication, their contributor guidelines URL if visible, apparent audience size/relevance. Prioritise sites with clear editorial quality. Strategy type = "Guest Post".

---

### STEP 2 — Score and prioritise all new finds

For all new opportunities collected across all 8 strategies, assign a rough priority score (1–3):

- **3 (High):** Unlinked mention (already knows SEAR), active HARO query with deadline, confirmed broken link on high-traffic page
- **2 (Medium):** Resource page or competitor gap on relevant domain, podcast with clear audience fit, ENT/clinic with patient resources page
- **1 (Lower):** Guest post opportunity, general EU prospect without confirmed fit

Sort the full list highest-priority first.

---

### STEP 3 — Update the tracker

Append all new opportunities to the **Pipeline** tab of:
`/Users/juliaraciniewska/Documents/Claude/Projects/SEAR Website Optimisation/backlink-opportunities.xlsx`

For each row set:
- Column A: today's date (YYYY-MM-DD)
- Column B: full URL
- Column C: domain (extracted from URL)
- Column D: page title
- Column E: market (UK / DE / ES / FR / PT / NL)
- Column F: strategy type (exact values: Broken Link | Resource Page | Unlinked Mention | Competitor Gap | Digital PR / HARO | Podcast / YouTube | ENT & Partner Listing | Guest Post)
- Column G: contact name (if found)
- Column H: contact email (if found)
- Column I: Status = "New"
- Columns J–M: leave blank
- Column N: domain authority estimate if discoverable (leave blank if not)
- Column O: notes (sub-type, seasonal hook, specific page detail, why it's a good fit)

Do NOT overwrite or modify any existing rows. Only append.

Save the updated file back to the same path.

---

### STEP 4 — Draft outreach emails for the top 5 opportunities

For the 5 highest-priority new opportunities, create Gmail draft emails using the Gmail MCP tool (`create_draft`).

For each draft:
- **To:** use the contact email if found. If no contact email is found, use `info@searplugs.com` as a placeholder — the Gmail MCP requires at least one recipient and will error if left blank. Add a clear action note at the very top of the email body: `[ACTION: Find & replace recipient — check [site]/contact before sending]`
- **Subject:** use the matching template subject line from the Templates tab (personalised for the specific target)
- **Body:** use the matching template email body, replacing all [bracketed] placeholders with specific details from the actual page (actual page title, specific thing you noticed on the page, their name if found, etc.)
- Add a note at the top of each draft: `[REVIEW BEFORE SENDING — auto-drafted by weekly backlink task]`

Update the tracker for those 5 rows: set Status = "Drafted", Date Drafted = today.

---

### STEP 5 — Update the Weekly Log tab

In the **Weekly Log** tab, find the next empty row and log:
- Column A: Monday's date for this week (YYYY-MM-DD)
- Columns B–I: count of new opportunities found per strategy type (Broken Link, Resource Page, Unlinked Mention, Competitor Gap, Digital PR/HARO, Podcast/YouTube, ENT & Partner, Guest Post)
- Column J: total found (formula =SUM(B:I) already in place — do NOT overwrite this cell)
- Column K: number of emails drafted (= 5 or fewer)
- Column L: 0 (emails sent — Julia fills this in herself)
- Column M: 0 (links won — Julia fills this in herself)
- Column N: brief summary note (e.g. "3 broken links found on UK surf blogs; 1 active HARO query re: cold water swimming; 2 ENT clinics in ES")

Save the updated file.

---

### STEP 6 — Broken link monitor check (existing Won Links)

Open the **Won Links** tab. For any rows where Last Checked is more than 21 days ago OR Link Status = "Pending Check":
- Use WebFetch or curl to check if the linking URL still exists and the link to searplugs.com is still present
- Update Last Checked to today's date
- Update Link Status to "Live", "Broken", or "Removed" accordingly
- If any link has gone "Broken" or "Removed", add a note so Julia can follow up

Save the updated file.

---

### STEP 7 — Send a plain-text summary email to Julia

Create one final Gmail draft to `info@searplugs.com` with subject:
`Weekly backlink run — [N] new opportunities, [N] drafts ready (w/c [Monday date])`

The body must be **plain text only** — no HTML, no styled cards, no badges. Use ASCII dividers (━━━━━━━━━━), emoji bullets, and indented action items. Use the `body` parameter (not `htmlBody`) when calling `create_draft`. Follow this structure exactly:

```
Hi Julia,

Your weekly backlink research run is complete. Here's the full summary.

━━━━━━━━━━━━━━━━━━━━━━━━
RESULTS AT A GLANCE
━━━━━━━━━━━━━━━━━━━━━━━━
New opportunities found:   [N]
Gmail drafts queued:        [N]
Won Links checked:          [N] ([status])
Broken links confirmed:     [N]

Updated tracker:
/Users/juliaraciniewska/Documents/Claude/Projects/SEAR Website Optimisation/backlink-opportunities.xlsx


━━━━━━━━━━━━━━━━━━━━━━━━
TOP PRIORITIES BY CATEGORY
━━━━━━━━━━━━━━━━━━━━━━━━

[For each strategy type that produced results, list the top 1–2 opportunities:]
🔴/🟡/🟢 [STRATEGY TYPE] (Priority: HIGH/MEDIUM/LOWER)
→ [Site name] — [URL]
   [One sentence on why it's a good fit / what was found]
   Draft ready / No draft yet — [action instruction]
   ⚠️  [Medical flag if applicable]

━━━━━━━━━━━━━━━━━━━━━━━━
YOUR ACTION LIST THIS WEEK
━━━━━━━━━━━━━━━━━━━━━━━━

READY TO SEND (just review and hit send):
1. ✅ [Site] — [strategy], draft in Gmail, To: [email]
2. ✅ [Site] — [strategy], draft in Gmail, To: [email or placeholder note]

NEEDS CONTACT EMAIL BEFORE SENDING:
3. [Site] — draft waiting · find contact at [URL]
...

WRITE & SEND WHEN READY (templates waiting in tracker):
[N+1]. [Site] — [template to use]
...

LOG YOUR SENDS: When you send any email, update Column L (Emails Sent) in the Weekly Log tab and set the Date Sent in the Pipeline tab. When a link is won, update the Won Links tab — it'll be monitored automatically from next week.


━━━━━━━━━━━━━━━━━━━━━━━━
NOTES
━━━━━━━━━━━━━━━━━━━━━━━━
• [Any urgent items — HARO deadlines, removed won links, seasonal hooks]
• [Any items flagged for medical review]
• [Anything else Julia should know]

Best,
Claude (weekly backlink automation)
```

---

### OUTREACH HOOKS BY AUDIENCE TYPE

Every outreach email must follow the structure and tone derived from Julia's real sent emails. Use the appropriate hook for the audience type:

#### Publications, magazines, blogs, and review sites
Use the **affiliate partnership** hook. Template structure (adapt each element to the specific target):
1. Personal greeting — use their name if known, otherwise "Hi [Site Name] Team"
2. Intro: "I'm Julia Raciniewska, Co-Founder of [SEAR Plugs](https://searplugs.com/)"
3. Reference their EXACT article with a hyperlink: e.g. "I came across your article [Best Earplugs for Surfing](https://example.com/article)"
4. SEAR's differentiator: "the only earplug designed to block water and cold air while offering minimal 9dB sound attenuation for maximum situational awareness"
5. The gap SEAR fills for their specific audience — personalise this
6. Offer: "unique reader discount code" + "affiliate reward of 10% from the sale price"
7. Close: "Please let me know if this is something you'd be interested in to discuss further"
8. Sign off: "Julia Raciniewska, Co-Founder of SEAR Plugs"

#### ENT clinics, audiologists, hearing professionals
Professional recommendation angle. Mention "several ENT practices and audiology clinics already stock SEAR as a recommendation option." Highlight the 9 dB acoustic filter and waterproof protection. Reference their specific patient resource or recommended products page with a hyperlink.

#### Surf schools and swim clubs
Partner/kit recommendation angle. Position SEAR as the earplug they should recommend to their students or members for preventing surfer's ear or swimmer's ear. Reference their specific gear page or surfer's ear article with a hyperlink.

#### Broken link pages
Flag the specific dead link found on their page and pitch SEAR as the replacement resource. Name the exact dead URL that was found. Reference their specific article with a hyperlink.

#### Wholesale / retailers (UK/EU only)
Trade price £19.23/unit, RRP £39.95, min 5 units, sample offer available. Sign as "Julia Raciniewska, Co-Founder & COO, SEAR."

---

### CONSTRAINTS & BRAND RULES

- **Never** use the words "custom", "custom-fit", "custom-moulded", "bespoke", or "made-to-fit" in any drafted email or note. Use: waterproof earplugs, surf earplugs, swim earplugs, water sports earplugs.
- **Never** name competitor brands (SurfEars, Bollsen, EQ Seals, etc.) in any drafted outreach. Differentiate on SEAR's own merits only.
- **Never** send any email — only create Gmail drafts. Julia sends everything herself.
- **Never** create WordPress posts or update any site content as part of this task.
- **Always** include the EU markets (DE, ES, FR, PT, NL) in strategies 1, 2, 3, 4, and 7 — EU is a top commercial priority.
- **Geographic filter — UK and EU only:** Never target US-based publications, magazines, or blogs. SEAR cannot ship to the US. Also never target retailers that primarily stock US-branded water sports products (e.g. US surf shops). Before logging or drafting for any opportunity, verify the target is UK or EU-based.
- **Never offer to "send a pair"** in editorial outreach to publications, magazines, or review sites. Use the affiliate partnership hook instead. (A product sample for testing/review is acceptable if the publisher asks, but do not initiate with "send a pair" language.)
- **Always hyperlink to the exact article or page** being referenced in every outreach email. Never mention a page without linking to it. The link must point to the specific article URL, not just the homepage.
- If any opportunity involves a medical claim or references surfer's ear treatment/surgery, note "Medical — Julia to review carefully" in the Notes field.

---

### SUCCESS CRITERIA

This run is complete when:
- New opportunities have been appended to the Pipeline tab
- 5 Gmail drafts are queued for Julia's review
- The Weekly Log has been updated with this week's counts
- The Won Links tab has been checked for any broken/removed links
- The tracker file has been saved to the workspace folder
- A plain-text summary email draft has been created to info@searplugs.com
