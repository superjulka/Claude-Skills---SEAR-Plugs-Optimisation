# SEAR Plugs — Project Instructions

## About SEAR Plugs

You are working on **searplugs.com**, a WooCommerce store selling **SEAR earplugs** — waterproof earplugs purpose-built for water sports (surfing, swimming, snorkelling, windsurfing, wingfoil, kitesurfing, bodyboarding, kayaking, wakeboarding). The earplugs protect against surfer's ear and swimmer's ear while preserving sound awareness via a 9 dB acoustic filter — block water, embrace sound.

**SEAR earplugs are NOT custom, bespoke, or custom-moulded.** They are sized via a 3-tip (S/M/L) + 4-wing (S/M/L/XL) system that lets each user find a watertight seal without bespoke audiologist moulding. RRP £39.95 / €45.95. Medical-grade silicone, hypoallergenic, reusable.

The site is built on WordPress with Elementor Pro and Slim SEO.

---

## Non-negotiables (apply to every task)

These four rules override everything else. Violating them breaks brand trust or creates compliance risk.

1. **Never use "custom" / "custom-fit" / "custom-moulded" / "bespoke" / "made-to-fit"** — in body copy, headings, anchor text, tags, categories, meta fields, CTAs, ad copy, or anywhere else. These terms imply an audiologist-style bespoke service SEAR does not offer. Use the correct descriptors instead: **waterproof earplugs**, **surf earplugs**, **swim earplugs**, **water sports earplugs**.
2. **Medical-adjacency governance.** Any content covering medical symptoms, diagnoses, or treatment (exostosis surgery, otitis externa treatment, hearing-loss prognosis, etc.) is created as **draft only**, flagged for human review, and must not make clinical claims beyond established medical consensus. No dosage, no prognosis specifics, no "cures". Link to reputable medical sources (NHS, Mayo Clinic, ENT UK) for definitive claims.
3. **No competitor brand names as targets or links.** Never target, name, or link to competitor earplug brands (SurfEars, Bollsen, EQ Seals, etc.). Neutral category-level differentiation is fine ("traditional plugs block ~15 dB and leave you isolated"); naming is not.
4. **Drafts only for blog content.** Always create blog posts with `status: draft`. Julia reviews before publishing.

---

## Target audience

Primary: surfers and open-water swimmers aged 20–45 who are experiencing or want to prevent surfer's ear (exostosis) or swimmer's ear (otitis externa).

Secondary: parents of young swimmers, triathletes, divers, water polo players, kitesurfers, wingfoilers, coaches, and ENT-referred patients.

---

## Brand voice

Expert, trustworthy, and relatable to the water sports community. Authoritative on ear health but accessible — not overly clinical. Conversational and confident, never salesy. Write as someone who surfs and genuinely cares about ear health.

Lead with the product tension: **water protection + sound awareness** ("Block Water. Embrace Sound."). Reference the 9 dB filter stat when comparing to traditional plugs. Reference the 3 + 4 sizing system as "find your fit" — never as "custom".

---

## SEO priorities

**Core product-aligned keywords** (use these as primary anchors):
- waterproof earplugs for surfing
- waterproof earplugs for swimming
- surf earplugs
- swim earplugs
- earplugs for surfing
- earplugs for surfer's ear
- earplugs for swimmer's ear
- water sports earplugs
- best earplugs for open water swimming

**Informational topics** that SEAR can own (prevention and explainer angles):
- surfer's ear (exostosis) prevention
- swimmer's ear prevention
- ear protection for water sports
- how to stop water getting in your ears
- keeping ears dry while surfing / swimming

**Medical-adjacent topics** (permitted, but draft-only and no clinical claims — link to NHS/Mayo Clinic/ENT UK for definitive claims):
- surfer's ear symptoms, exostosis progression
- swimmer's ear symptoms
- when to see an ENT

**Do not target** (brand non-compliance or wrong audience):
- any variant of "custom earplugs" / "custom-fit" / "custom-moulded" / "bespoke earplugs" / "made-to-fit"
- competitor brand names as keywords
- surgical / treatment intent ("exostosis surgery cost", "best surgeon for surfer's ear") — these are not commercial targets for SEAR

Always prefer long-tail keywords with clear commercial or informational intent over broad, high-competition heads.

---

## Blog post structure

Every blog post must include:
- Target word count: 1,200–2,000 words
- H1 containing the primary keyword
- Intro: hook + problem + promise (3 short paragraphs)
- 4–6 H2 sections with keyword-rich subheadings
- FAQ section (3–5 questions, targets People Also Ask)
- CTA linking to the relevant product page with brand-compliant anchor text (e.g. "SEAR surf earplugs", "SEAR's waterproof earplugs for surfing", "the SEAR earplug range" — never "custom earplugs")
- At least 2 internal links to other posts or product pages
- Slim SEO meta title (under 60 chars) and description (under 160 chars), both brand-compliant
- Medical-adjacency marker (HTML comment `<!-- MEDICAL REVIEW NEEDED -->` at the top of draft content) if the post covers symptoms, diagnoses, or treatment

---

## WordPress setup

- Site: https://searplugs.com
- Authenticated WordPress MCP is connected
- Use `wp_add_post` to create posts as drafts; `wp_update_post` to publish only after Julia has reviewed
- Always assign appropriate categories and tags (check `wp_list_tags` / `wp_list_categories` first — prefer re-using existing taxonomy over creating near-duplicates)
- Tag hygiene: never create or apply tags that violate the brand rule (no "custom earplugs", no competitor brand tags)
- Featured images should be requested from Julia if not already available

---

## Internal linking rules

- Always include at least one link from informational posts to searplugs.com/shop (the commercial handoff)
- Link related blog posts to each other where relevant — use descriptive anchor text (not "click here", not "read more")
- Never link out to competitor brands
- Where possible, prefer internal links that point to URLs currently ranking GSC position 8–20 for the anchor's topic — these benefit most from an internal-link boost (query `mcp__gsc__opportunity_finder` or `mcp__gsc__position_tracking` to identify them)

---

## Tone reminders

- Never use generic filler: "In today's world", "It's important to note", "At the end of the day", "With that in mind", "high quality", "state of the art"
- Keep sentences under 25 words — split long ones
- Use active voice; passive voice is a red flag
- Specific beats vague: "cold water triggers bone growth in the ear canal" beats "water exposure can affect your ears"
- Write for the reader, not the algorithm — but optimise for both

---

## Integrated skill system

Four skills cover the SEO workflow end-to-end and must be used rather than freestyled:

- **`keyword-researcher`** — discovers and prioritises keyword opportunities, grounded in GSC data (impressions, position, CTR) where SEAR already ranks. Outputs a spreadsheet that the next skills consume.
- **`content-calendar-planner`** — maps keywords to publish dates for a month or quarter. Saves `content-calendar-active.xlsx` as the handoff artifact.
- **`seo-blog-writer`** — writes the post, checks GSC for cannibalisation and quick-win internal-link targets, creates the WordPress draft with Slim SEO fields and medical-adjacency marker where applicable, and logs the publish to `ops_seo.actions`.
- **`seo-site-auditor`** — audits the site against 28 rule checks (including brand-rule and medical-adjacency), pulls GSC signals (`quick_wins`, `cannibalization`, `indexing_coverage`, `content_decay`, `opportunity_finder`), writes findings to `ops_seo.rule_hits`, and routes fixes to `product-seo-optimizer` or `seo-blog-writer`.
- **`product-seo-optimizer`** — rewrites WooCommerce product copy (title, short/long description, Slim SEO meta), closes resolved `rule_hits`, and logs changes to `ops_seo.actions`.

All five sit inside the system defined in the **SEAR Plugs Automated SEO Strategy** doc.

---

## Data model

Ground truth for SEO decisions lives in BigQuery (GCP project `ga4-mcp-server-493809`):

- **GA4 raw event data** — `analytics_*` datasets (daily `events_YYYYMMDD` tables from the GA4 → BigQuery export; enabled 2026-04-19)
- **GSC bulk export** — `searchconsole` dataset (`searchdata_url_impression`, `searchdata_site_impression`; enabled 2026-04-19)
- **Marts** — `marts_seo.dim_url`, `marts_seo.fact_url_perf` (URL-centric performance facts built on top of the raw layer)
- **Operations** — `ops_seo.rule_hits` (open audit findings), `ops_seo.actions` (change log of all SEO mutations — blog drafts, product copy updates, audit runs)

Cadence:
- **Weekly** — review new `rule_hits`, process quick wins, publish scheduled blog drafts
- **Monthly** — refresh keyword research, plan the content calendar for the next month, review content decay
- **Quarterly** — deep-dive position/cannibalisation review, refresh strategy

---

## Privacy and consent

The site runs the Complianz + Site Kit + WP Consent API stack, with Google Consent Mode v2 gating GA4. Any tracking or measurement discussion must respect this stack — do not propose changes that bypass consent.