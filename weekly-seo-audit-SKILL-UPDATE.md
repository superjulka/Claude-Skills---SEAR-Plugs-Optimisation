---
name: weekly-seo-audit
description: Weekly: pull GSC signals, analyse keyword gaps & CTR opportunities, upsert rule_hits, email Julia a prioritised report focused on driving organic traffic and sales
---

You are running the weekly SEO audit for searplugs.com. Today is Monday. Complete all steps below, then email Julia (info@searplugs.com) the full report.

**Primary goal: identify what will drive more organic traffic, improve rankings, and convert visitors into customers. Brand compliance and medical review checks are handled separately — do NOT include them in this report.**

---

## BigQuery credentials (required for Steps 3 & 4)

The GCP service account key file is at:
`/Users/juliaraciniewska/Documents/Claude/Projects/SEAR Website Optimisation/ga4-mcp-server-493809-2e91f23350e4.json`

In the Linux sandbox this maps to:
`/sessions/sharp-trusting-bohr/mnt/SEAR Website Optimisation/ga4-mcp-server-493809-2e91f23350e4.json`

Set `GOOGLE_APPLICATION_CREDENTIALS` to that path before running any BigQuery Python code.
Use `client = bigquery.Client(project="ga4-mcp-server-493809", location="EU")` — the dataset is in EU.

Install if needed: `pip install google-cloud-bigquery db-dtypes --break-system-packages -q`

**BigQuery logging is MANDATORY. Do not skip it.**

### ops_seo.rule_hits schema (use these exact column names):
- `url` STRING REQUIRED
- `rule_id` STRING REQUIRED
- `severity` STRING REQUIRED  (CRITICAL / HIGH / MEDIUM / LOW)
- `evidence` STRING NULLABLE  (evidence snippet + recommended fix in one field)
- `first_seen_ts` TIMESTAMP REQUIRED
- `last_seen_ts` TIMESTAMP REQUIRED
- `status` STRING REQUIRED  (open / resolved)
- `resolved_ts` TIMESTAMP NULLABLE
- `resolved_by` STRING NULLABLE

Dedup key: `(url, rule_id)`. Check for existing open hits, insert new rows via `insert_rows_json`, update `last_seen_ts` on re-raised rows via DML UPDATE.

### ops_seo.actions schema (use these exact column names):
- `action_ts` TIMESTAMP REQUIRED
- `action_type` STRING REQUIRED  (use "seo_audit")
- `url` STRING NULLABLE  (use "https://searplugs.com")
- `detail` JSON NULLABLE  (store audit summary as JSON string)

Log via `insert_rows_json` after all rule_hits are upserted. If credentials fail, stop and email Julia — do not continue with a skipped-logging audit.

---

## Step 1 — Pull GSC signals (run all in parallel)

- `mcp__gsc__quick_wins` (pos 4–25, min 30 impressions, CTR <= 8%) — striking-distance keywords
- `mcp__gsc__opportunity_finder` (last 28 days) — rising impressions, low clicks, emerging queries
- `mcp__gsc__content_decay` (page dimension, min 100 impressions) — pages losing visibility
- `mcp__gsc__cannibalization` — pages competing for the same queries
- `mcp__gsc__device_country_breakdown` (breakdown: "country") — for EU section
- `mcp__gsc__position_tracking` (weekly, last 90 days) for these 11 keywords:
  "surf earplugs", "swim earplugs", "earplugs for surfing", "earplugs for swimming",
  "waterproof earplugs for surfing", "waterproof earplugs for swimming",
  "earplugs for surfer's ear", "earplugs for swimmer's ear", "water sports earplugs",
  "surfer's ear prevention", "earplugs for kitesurfing"

---

## Step 2 — Identify SEO improvement opportunities

Focus exclusively on what drives rankings, traffic, and sales. For each issue, ask: "will fixing this bring more qualified visitors or convert more of the ones already landing?"

**Check for:**

**A. Keyword gaps** — core target keywords with zero or near-zero GSC impressions. These are content or authority gaps. Recommend: create new post, strengthen existing post, or build internal links.

**B. CTR underperformance** — pages/queries where position is good (top 15) but CTR is below expected (~3% at pos 10, ~5% at pos 7, ~8% at pos 5). Recommend: rewrite meta title or description with the specific text to use.

**C. Ranking inconsistency** — keywords oscillating widely week-to-week (e.g. pos 15 one week, pos 50 the next). Likely thin content or poor internal linking. Recommend: content depth, internal links from related posts.

**D. Content decay** — pages that ranked well historically but are declining. Recommend: refresh with new content, update stats, add FAQ section.

**E. Cannibalization** — two SEAR URLs fighting for the same query, splitting signals. Recommend: consolidate or redirect.

**F. Internal linking gaps** — check whether key commercial posts link to /shop or the product page. Every blog post should have at least one product CTA.

**G. Thin/missing meta** — pages without a Slim SEO title or description. Pull individual post meta via `wp_get_post` (context=edit) to check `meta_data.slim_seo`. These are direct CTR losses.

**H. Schema / rich results** — product page should have Product schema with price and availability. Check if it's present.

Do NOT flag: competitor name mentions, "custom" language in blog body copy, missing medical review markers, or any brand compliance issue. These are managed separately.

---

## Step 3 — Dedupe against open rule_hits

Query `ops_seo.rule_hits` for existing open SEO findings. Mark each finding as new or re-raised. Step is REQUIRED.

---

## Step 4 — Write findings to BigQuery (MANDATORY)

Upsert all SEO findings into `ops_seo.rule_hits`. Log the audit run in `ops_seo.actions`. Confirm counts in the email.

---

## Step 5 — Email Julia

Send one email to info@searplugs.com. Subject: `SEAR SEO Weekly — [date]`

Plain text only. Use ASCII dividers (---). No HTML, no styled cards, no badges.

---

### KEYWORD POSITION TRENDS

Last 4 weeks for each tracked keyword (weekly granularity). Use "—" if no data. Add trend arrow (up / down / stable).

| Keyword | 4 wks ago | 3 wks ago | 2 wks ago | Last week | Trend |
|---|---|---|---|---|---|

Below: 2–3 bullets on what the trends mean and what specific action to take this week.

---

### KEYWORD GAPS

List the core target keywords with zero or <5 GSC impressions in the past 28 days. For each:
- State: not yet indexing / thin content / no internal links
- Recommend: specific post to create or strengthen

---

### CTR OPPORTUNITIES

Queries/pages with good position but underperforming CTR. For each, write the exact replacement meta title or description to test.

---

### QUICK WINS THIS WEEK

Top 3 highest-impact, lowest-effort SEO fixes. Be concrete — write the actual copy, not just the instruction.

---

### CONTENT & RANKING ISSUES

All SEO findings by severity. For each: URL, issue, specific fix. Focus on what moves rankings or traffic.

Severity: CRITICAL = indexing blocked; HIGH = direct ranking/traffic loss; MEDIUM = missed opportunity; LOW = marginal gain.

---

### EU MARKETS (mandatory every week)

EU is a top strategic priority. Always include, even when data is sparse.

EU Traffic (last 28 days):
| Country | Clicks | Impressions | CTR | Avg Position |

Non-brand EU impressions: [number]

Country anomalies: Any EU country with good position but very low CTR — include hypothesis and specific fix.

Top EU action this week: One concrete recommendation (e.g. add EUR price to DE meta description, create ES landing page).

EU content gap: Highest-priority European language gap with example target keywords.

---

### HANDOFFS

- Fixes for product page: [list] → product-seo-optimizer
- New content needed: [list] → seo-blog-writer
- Requires Julia's input: [list]
- BigQuery logging: [completed — N new, N re-raised / FAILED — reason]

---

## Non-negotiables

- Every finding must cite a specific URL and evidence — no generic advice
- Write exact replacement copy for every meta title/description recommendation
- Keyword gap section is mandatory — if all 11 core keywords show impressions, say so explicitly
- EU section is mandatory every week
- BigQuery logging is mandatory — do not skip
- Do NOT include brand compliance, competitor mentions, or medical review findings
