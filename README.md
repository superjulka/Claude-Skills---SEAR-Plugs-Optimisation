# SEAR Plugs — Automated SEO & Website Optimisation System

> An end-to-end SEO automation stack built for **[searplugs.com](https://searplugs.com)** — a WooCommerce store selling waterproof earplugs for water sports. The system is designed to be adapted and personalised for any e-commerce or content-driven brand.

---

## What This Is

This repository contains the **project instructions, skills, and workflow definitions** that power an AI-driven SEO and content operation for SEAR Plugs. It covers everything from keyword research and blog writing to product page optimisation, site auditing, and Meta Ads management — all governed by brand rules and connected to live data sources.

The stack runs inside **Claude Cowork** (Anthropic's desktop AI tool), with skills acting as reusable, specialised agents that can be triggered by natural language or automated schedules.

---

## The SEAR Plugs Context

SEAR earplugs are waterproof earplugs purpose-built for water sports — surfing, swimming, snorkelling, windsurfing, kitesurfing, and more. They protect against surfer's ear (exostosis) and swimmer's ear (otitis externa) while preserving sound awareness through a 9 dB acoustic filter.

The site is built on **WordPress + WooCommerce**, using **Elementor Pro** for page building and **Slim SEO** for on-page SEO fields.

---

## What's in This Repository

```
/
├── project-instructions.md     # Brand rules, SEO priorities, voice guidelines,
│                               # WordPress setup, and data model
├── skills/
│   ├── keyword-researcher/     # Discovers keyword opportunities from GSC + seed topics
│   ├── content-calendar-planner/ # Maps keywords to publish dates (monthly/quarterly)
│   ├── seo-blog-writer/        # Full blog post workflow: research → draft → WP publish
│   ├── seo-site-auditor/       # 28-rule site audit with GSC signals + BigQuery
│   ├── product-seo-optimizer/  # Rewrites WooCommerce product copy + Slim SEO meta
│   ├── meta-ads-monthly-review/ # Monthly Meta Ads optimisation workflow
│   ├── sear-meta-ads-brand-rules/ # Brand compliance rules for ad copy
│   └── ...                     # Additional utility skills
└── README.md
```

---

## How It Works

The system is built around five core skills that cover the SEO workflow end-to-end:

### 1. `keyword-researcher`
Pulls from Google Search Console to find queries where the site already has impressions, then surfaces gap opportunities and long-tail targets. Outputs a ranked spreadsheet consumed by the next step.

### 2. `content-calendar-planner`
Takes the keyword list and maps topics to publish dates across a month or quarter. Saves a live `content-calendar-active.xlsx` as the handoff artefact.

### 3. `seo-blog-writer`
Writes the full post — checking GSC for cannibalisation risks and quick-win internal link targets, applying brand voice rules, flagging medical-adjacent content for human review, and creating the WordPress draft with Slim SEO meta fields pre-filled.

### 4. `seo-site-auditor`
Audits the site against 28 checks covering brand compliance, meta completeness, thin content, cannibalisation, indexing coverage, and content decay. Writes findings to BigQuery (`ops_seo.rule_hits`) and routes fixes to the product optimizer or blog writer.

### 5. `product-seo-optimizer`
Rewrites WooCommerce product titles, short/long descriptions, and Slim SEO meta. Closes resolved rule hits and logs all changes to `ops_seo.actions`.

---

## Data Layer

Ground truth for all SEO decisions lives in **BigQuery** (GCP):

| Dataset | What's in it |
|---|---|
| `analytics_*` | GA4 raw event data (daily export) |
| `searchconsole` | GSC bulk export — URL and site impression data |
| `marts_seo` | `dim_url` + `fact_url_perf` — URL-centric performance marts |
| `ops_seo.rule_hits` | Open audit findings |
| `ops_seo.actions` | Change log of all SEO mutations |

Connected tools: Google Search Console MCP, GA4 MCP, BigQuery MCP, WordPress MCP (authenticated), Adspirer (Meta/Google Ads).

---

## Brand Rules (Non-Negotiables)

These four rules are hardcoded into every skill and the project instructions. They exist to protect brand trust and compliance:

1. **Never use "custom", "custom-fit", "custom-moulded", "bespoke", or "made-to-fit"** — SEAR earplugs use a 3-tip + 4-wing sizing system, not audiologist moulding. Use: waterproof earplugs, surf earplugs, swim earplugs, water sports earplugs.
2. **Medical-adjacency governance** — content covering symptoms, diagnoses, or treatment is created as draft only, flagged with `<!-- MEDICAL REVIEW NEEDED -->`, and links to NHS/Mayo Clinic/ENT UK for clinical claims.
3. **No competitor brand names** — no targeting, naming, or linking to competitor earplug brands.
4. **Drafts only for blog content** — all posts are created as WordPress drafts for human review before publishing.

---

## Adapting This for Your Brand

This system was built for SEAR Plugs but is designed to be repurposed. Here's what to change:

### 1. Project Instructions (`project-instructions.md`)
Update the following sections for your brand:
- **About** — your product, what it does, who it's for
- **Non-negotiables** — your brand's compliance rules, restricted terminology, and content governance policies
- **Target audience** — primary and secondary personas
- **Brand voice** — tone, style, what to avoid
- **SEO priorities** — your core keywords, informational topics, and terms to avoid
- **Blog post structure** — adjust word counts, required sections, and CTA anchors
- **WordPress setup** — your site URL and theme/SEO plugin
- **Data model** — your BigQuery project ID and dataset names (or swap for another analytics stack)

### 2. Skills
Each skill reads the project instructions for brand context, so most of the adaptation happens there. You may also want to:
- Update the **meta-ads brand rules skill** with your own ad copy guidelines
- Adjust the **SEO audit rule checks** in `seo-site-auditor` to match your site's structure
- Swap the **Slim SEO** meta field mappings in `seo-blog-writer` and `product-seo-optimizer` if you use a different SEO plugin (Yoast, RankMath, etc.)

### 3. Data Connections
Replace or reconfigure:
- GSC property URL (your domain)
- BigQuery project ID and dataset names
- GA4 property ID
- WordPress site URL and authentication
- Ad account IDs (Meta, Google)

### 4. Cadence & Scheduling
The default cadence is:
- **Weekly** — review new rule hits, process quick wins, publish scheduled drafts
- **Monthly** — keyword research refresh, content calendar planning, content decay review
- **Quarterly** — deep position/cannibalisation review, strategy refresh

Adjust these to match your publishing frequency and team capacity.

---

## Tech Stack

| Layer | Tool |
|---|---|
| CMS | WordPress + WooCommerce |
| Page builder | Elementor Pro |
| SEO plugin | Slim SEO |
| Analytics | GA4 (via BigQuery export) |
| Search data | Google Search Console (bulk export + MCP) |
| Data warehouse | BigQuery (GCP) |
| Ads | Meta Ads + Google Ads (via Adspirer MCP) |
| AI layer | Claude Cowork (Anthropic) |
| Consent stack | Complianz + WP Consent API + Google Consent Mode v2 |

---

## Getting Started

1. Clone this repository
2. Open the project folder in Claude Cowork and select it as your workspace
3. Update `project-instructions.md` with your brand details
4. Connect your data sources (GSC, GA4, BigQuery, WordPress MCP, Adspirer)
5. Run `/keyword-researcher` to generate your first keyword list
6. Run `/content-calendar-planner` to map out your first month of content
7. Run `/seo-site-auditor` to baseline your current site health

---

## Licence

MIT — free to use, adapt, and build on.
