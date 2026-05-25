# searplugs.com — Comprehensive SEO Audit Report

**Date:** April 15, 2026  
**Auditor:** Claude (AI SEO Consultant)  
**Scope:** Full site — product pages, blog posts, and key static pages  
**Tools used:** WordPress MCP, WooCommerce MCP, live page analysis, competitor benchmarking

---

## Executive Summary

searplugs.com has solid foundations: good product copy, a well-structured blog with 10 published posts, reasonable word counts, and a clean site design. The product's core differentiators (9 dB acoustic filter, medical-grade silicone, multi-size fit system) are communicated clearly on-page.

However, the site has a cluster of structural and technical SEO issues that are actively suppressing its performance in search. The most urgent problem is that the main product page is accessible at two different URLs — both returning HTTP 200 — which splits link equity and risks a duplicate content flag. The product is also filed under "Uncategorized," which shows up in breadcrumbs visible to every visitor from Google. Neither issue requires significant writing effort; both can be fixed in under an hour and will have an immediate impact.

At a content level, two blog posts are competing for identical search queries (keyword cannibalization), blog posts have zero cross-links to each other (a missed topical authority opportunity), and the product page is missing Product schema markup — meaning SEAR doesn't appear with star ratings, pricing, or availability in Google search results while competitors like SurfEars do.

**21 items were audited.** Issues breakdown: **5 Critical / 6 High / 6 Medium / 4 Low.**  
**7 Quick Wins** were identified — high-impact fixes that can be actioned in under 10 minutes each.

The top 3 actions to do first:
1. Fix the dual product URL (canonical + link standardisation)
2. Move product out of "Uncategorized" into a proper category
3. Add Product JSON-LD schema with price and availability

---

## Critical Issues

Issues that directly harm rankings, split link equity, or produce a poor SERP appearance. Fix these first.

---

### Critical Issue 1 — Dual Product Page URLs (Canonicalization Risk)

**Affects:** Product page (ID 99)  
**Quick Win:** Yes

**Current State:**  
The SEAR product page is accessible at two different URLs, both returning HTTP 200 OK with identical content:

- `https://searplugs.com/sear-swimming-surfing-ear-plugs/` ← WooCommerce canonical permalink
- `https://searplugs.com/product/sear-swimming-surfing-ear-plugs/` ← used in ALL internal links and nav

Neither URL carries a canonical tag pointing to the other. Google sees two pages with the same content and no instruction on which to prioritise. This splits the inbound link equity between two URLs, potentially halving the ranking power of each. It also creates a duplicate content signal.

Compounding this: different CTAs across the site use three different destination URLs for the same product:
- Navigation uses `/product/sear-swimming-surfing-ear-plugs/`
- Blog post CTAs use `/product/sear-swimming-surfing-ear-plugs/`
- The newest blog post (Exostosis, ID 2026) uses `/shop/` as the CTA destination
- Homepage CTA links to `searplugs.com` root

**Suggested Fix:**  
1. Add `<link rel="canonical" href="https://searplugs.com/sear-swimming-surfing-ear-plugs/" />` to the `/product/...` version. Ideally, implement a 301 redirect from `/product/sear-swimming-surfing-ear-plugs/` → `/sear-swimming-surfing-ear-plugs/` via `.htaccess` or a redirect plugin.
2. Update ALL internal links, navigation items, and blog CTAs to use the canonical permalink: `https://searplugs.com/sear-swimming-surfing-ear-plugs/`
3. Standardise the `/shop/` CTA in the Exostosis blog post to point to the product permalink too.

**Expected Impact:** Consolidates full link equity onto one URL. Eliminates duplicate content signal. Expected to improve product page rankings within 4–8 weeks of Google recrawl.

---

### Critical Issue 2 — Product Category Set to "Uncategorized"

**Affects:** Product page (ID 99)  
**Quick Win:** Yes

**Current State:**  
The sole product is assigned to WooCommerce's default "Uncategorized" category. This surfaces in three harmful ways:
- Breadcrumb on the product page reads: `Home > Uncategorized > SEAR Ear Plugs`  
- The shop archive page (`/shop/`) has no meaningful category structure
- Internal category links route through `/product-category/uncategorized/` — a zero-value SEO URL

Any visitor landing from a Google search sees "Uncategorized" in the page breadcrumb, which damages trust and signals a lack of site organisation to Google's crawlers.

**Suggested Fix:**  
Create a new WooCommerce product category: **"Earplugs for Water Sports"** (slug: `earplugs-water-sports`). Assign product ID 99 to it. The breadcrumb will then read `Home > Earplugs for Water Sports > SEAR Ear Plugs`, which is both credible and keyword-rich.

| | Before | After |
|--|--|--|
| Breadcrumb | Home > Uncategorized > SEAR Ear Plugs | Home > Earplugs for Water Sports > SEAR Ear Plugs |
| Category URL | /product-category/uncategorized/ | /product-category/earplugs-water-sports/ |

**Expected Impact:** Immediate improvement to on-page professionalism and SERP snippet quality. Category page gains SEO value for "earplugs for water sports" queries.

---

### Critical Issue 3 — Homepage and /shop/ Share Identical H1 and Meta Title

**Affects:** Homepage (`/`) and Shop page (`/shop/`)  
**Quick Win:** Yes

**Current State:**  
Both pages return the same meta title and H1:
- Meta title: *"Premium Surfing & Swimming Earplugs | SEAR Plugs"*
- H1: *"Premium Water Earplugs for Surfing & Swimming"*

Google must choose between two identical pages targeting the same query. It typically chooses one to rank and demotes the other — or, worse, rotates between them unpredictably. Since SEAR has one product, the shop page (`/shop/`) is effectively the same content as the homepage. Without differentiation, both pages compete against each other.

**Suggested Fix:**  
Give `/shop/` its own unique Slim SEO meta title and description that differentiates it from the homepage.

| | Before | After |
|--|--|--|
| /shop/ meta title | "Premium Surfing & Swimming Earplugs \| SEAR Plugs" | "Shop Earplugs for Surfing & Swimming \| SEAR Plugs" |
| /shop/ meta description | (same as homepage) | "Waterproof earplugs for surfers and swimmers — block water, not sound. Choose your size, order today. Free UK shipping on all orders." |
| /shop/ H1 | "Premium Water Earplugs for Surfing & Swimming" | "SEAR Earplugs — Shop Water Sports Ear Protection" |

**Expected Impact:** Eliminates duplicate meta signals between the two most important pages on the site. Allows Google to confidently surface the correct page for different queries.

---

### Critical Issue 4 — No Product Schema Markup (Rich Snippets Missing)

**Affects:** Product page (ID 99)  
**Quick Win:** No

**Current State:**  
The product page's JSON-LD schema includes: WebSite, BreadcrumbList, WebPage, Organization, and ImageObject — but **no Product schema**. This means Google cannot display:
- ⭐ Star ratings in search results
- 💷 Pricing (£39.95)
- ✅ Availability (In Stock)
- 🔖 Review count

The main competitor, SurfEars, shows 4.8 stars from 700+ reviews in search results. SEAR shows a plain blue link with no enrichment. The CTR gap between a result with rich snippets and one without can be 20–30%.

**Suggested Fix:**  
Add a Product JSON-LD block to the product page template. Minimum viable schema:

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "SEAR Earplugs — Waterproof Earplugs for Surfing & Swimming",
  "description": "Waterproof earplugs for surfers and swimmers. 9 dB acoustic filter blocks water and wind while keeping ambient sound clear.",
  "brand": { "@type": "Brand", "name": "SEAR" },
  "sku": "SEARV2",
  "offers": {
    "@type": "Offer",
    "price": "39.95",
    "priceCurrency": "GBP",
    "availability": "https://schema.org/InStock",
    "url": "https://searplugs.com/sear-swimming-surfing-ear-plugs/"
  }
}
```

Once WooCommerce reviews are enabled and collected (see High Issue 3), add `aggregateRating` to unlock star snippets.

**Expected Impact:** Price and availability shown in search results immediately. Star ratings unlock once reviews are collected. Expected CTR increase of 15–25% vs current plain listing. A schema plugin (e.g. Schema Pro or Slim SEO Schema) can implement this without custom development.

---

### Critical Issue 5 — Inconsistent Internal Linking to Product Page

**Affects:** All 10 blog posts + navigation  
**Quick Win:** No

**Current State:**  
Across the site, three different URLs are used as CTAs to the product page:
1. `/product/sear-swimming-surfing-ear-plugs/` (navigation + most blog posts)
2. `/shop/` (Exostosis post, ID 2026)
3. `searplugs.com/` root (some homepage CTAs)

This dilutes the link equity that flows to the product page. Each URL gets only a fraction of the internal link signals that should all point to one canonical URL.

**Suggested Fix:**  
Conduct a find-and-replace across all blog posts and pages. Replace every instance of:
- `/product/sear-swimming-surfing-ear-plugs/` → `/sear-swimming-surfing-ear-plugs/`
- CTAs pointing to `/shop/` for product purchases → `/sear-swimming-surfing-ear-plugs/`
- CTAs pointing to site root for the product → `/sear-swimming-surfing-ear-plugs/`

Update the navigation menu item "Surfer Plugs" to point to the canonical product permalink.

**Expected Impact:** Full consolidation of internal link equity to the product page. Expected incremental ranking improvement for the product page's target keywords within 4–6 weeks.

---

## High Issues

Issues with meaningful ranking impact — fix after Critical items are resolved.

---

### High Issue 1 — Keyword Cannibalization: Two Posts Targeting the Same Query

**Affects:** Post ID 1685 ("Swimming Ear Plugs for Adults") and Post ID 1691 ("Best Earplugs for Swimming Adults")  
**Quick Win:** No

**Current State:**  
Two published blog posts target near-identical commercial queries:
- ID 1685: *"Swimming Ear Plugs for Adults: Protect Your Ears During Water Sports"* — 4,461 words, comprehensive guide with reviews and comparison
- ID 1691: *"Best Earplugs for Swimming Adults (2026): Top Picks Tested & Ranked"* — ~1,500 words, buyer's guide format

Google must decide which page best answers "best swimming ear plugs for adults" — but with two competing pages, neither ranks as strongly as one consolidated authority piece would.

**Suggested Fix:**  
Post 1685 (4,461 words) is the stronger asset. Make it the definitive pillar post for this keyword cluster. Options for post 1691:
- **Option A (preferred):** 301-redirect ID 1691 to ID 1685, consolidating all link equity and traffic.
- **Option B:** Differentiate ID 1691 to target a distinct query — e.g. *"Best Earplugs for Open-Water Swimming (2026)"* — rewriting it to focus specifically on outdoor/ocean swimmers rather than pool swimmers.

**Expected Impact:** Consolidating to one strong page can lift rankings from position 8–15 to position 3–8 for the target keywords. Two cannibalized pages both ranking at 12 is worse than one page ranking at 4.

---

### High Issue 2 — Zero Cross-Linking Between Blog Posts

**Affects:** All 10 blog posts  
**Quick Win:** No

**Current State:**  
Every blog post links out to product pages and utility pages (How It Works, About Us, Contact) but **none link to each other**. This means Google cannot follow topical pathways across the blog, topical authority clusters cannot form, and lower-authority posts get no PageRank boost from stronger posts.

Key missed linking opportunities:
- "Surfing 101" → "Surfer's Ear Exostosis" (massively relevant, currently no link)
- "Surfer's Ear vs Swimmer's Ear" → "Surfer's Ear Exostosis" (same topic cluster)
- "Swimming Earplugs Explained" → "Swimming Ear Plugs for Adults" (natural next step)
- "Swimming 101" → "Swimming Earplugs Explained" (natural progression)

**Suggested Fix:**  
Add 2–3 in-content cross-links to each blog post. Priority links to add first:

| Source Post | Add Link To | Suggested Anchor Text |
|--|--|--|
| Surfing 101 (ID 1698) | Surfer's Ear Exostosis (ID 2026) | "how surfer's ear develops" |
| Swimming 101 (ID 1709) | Swimming Earplugs Explained (ID 1681) | "which swimming earplugs to choose" |
| Surfer's Ear vs Swimmer's Ear (ID 1677) | Surfer's Ear Exostosis (ID 2026) | "how exostosis progresses" |
| Swimming Ear Plugs for Adults (ID 1685) | Swimming Earplugs Explained (ID 1681) | "types of swimming earplugs" |
| Kitesurfing 101 (ID 1702) | Surfer's Ear Exostosis (ID 2026) | "cold water ear damage" |

**Expected Impact:** Strengthens topical authority for the surfer's ear/swimmer's ear cluster. Helps newer posts (like ID 2026, published April 2026) inherit PageRank from established posts. Expected improvement in crawl frequency and rankings for ear-health posts within 6–10 weeks.

---

### High Issue 3 — No Verified WooCommerce Reviews

**Affects:** Product page (ID 99)  
**Quick Win:** No

**Current State:**  
WooCommerce shows 0 reviews (average_rating: 0.00, rating_count: 0). Three customer testimonials appear on the page from Erin S., Lila T., and Lucas M. — but these are manually displayed, not verified WooCommerce reviews. Without verified reviews, no aggregateRating can be added to the Product schema, meaning no star ratings appear in Google search results.

SurfEars currently shows **4.8/5 from 700+ reviews** in search results. This is a significant conversion and CTR advantage.

**Suggested Fix:**  
1. Import the three existing testimonials manually as WooCommerce reviews to immediately have a rating baseline.
2. Set up a post-purchase email (WooCommerce or Klaviyo) sent 7 days after delivery, asking for a product review.
3. Target 10 verified reviews within 60 days — at that point, add aggregateRating to Product schema.

**Expected Impact:** Even 5 reviews at 4.8★ can generate star-rating rich snippets. Research shows star ratings improve CTR by an average of 17%. At current traffic levels, this translates directly to more product page visits without any ranking change.

---

### High Issue 4 — 101 Series Posts Have No Tags

**Affects:** 5 posts (IDs 1695, 1698, 1702, 1705, 1709)  
**Quick Win:** Yes

**Current State:**  
The five "101 beginner guide" posts — Surfing, Swimming, Wing Foiling, Kitesurfing, Windsurfing — have **zero tags assigned**. Only the most recent post (ID 2026, Surfer's Ear Exostosis) has tags. Without tags, WordPress cannot build topical taxonomy links, tag archive pages have no content, and Google gets weaker topical signals.

**Suggested Fix:**  
Add relevant tags to each post (2–5 tags per post). Suggested tags:

| Post | Suggested Tags |
|--|--|
| Surfing 101 (ID 1698) | surfing 101, beginner surfing guide, surfer's ear, ear protection surfing |
| Swimming 101 (ID 1709) | swimming 101, beginner swimming guide, swimmer's ear, ear protection swimming |
| Kitesurfing 101 (ID 1702) | kitesurfing 101, water sports ear protection, kitesurfer's ear |
| Wing Foiling 101 (ID 1705) | wing foiling 101, wing foil beginner guide, water sports earplugs |
| Windsurfing 101 (ID 1695) | windsurfing 101, windsurf beginner guide, ear protection water sports |

Also ensure posts IDs 1677, 1681, 1685, 1691 receive relevant tags (most currently have none).

**Expected Impact:** Builds tag archive pages that can rank for niche long-tail queries. Strengthens internal taxonomy. 10-minute fix with no writing required.

---

### High Issue 5 — Long URL Slug on Exostosis Post

**Affects:** Post ID 2026  
**Quick Win:** No

**Current State:**  
The newest post has a slug of 86 characters:  
`/surfers-ear-exostosis-what-it-is-how-it-progresses-and-how-to-prevent-it/`  

Recommended maximum is 60 characters. Overly long slugs are truncated in SERPs, harder to share and cite, and carry slightly less SEO weight per character than clean, concise slugs.

**Suggested Fix:**  
Shorten to `/surfers-ear-exostosis/` (24 chars). Implement a 301 redirect from the current URL to the new slug. Update all internal links that reference the old URL (currently found in the blog and nav).

| | Before | After |
|--|--|--|
| Slug | /surfers-ear-exostosis-what-it-is-how-it-progresses-and-how-to-prevent-it/ | /surfers-ear-exostosis/ |
| Character count | 86 | 24 |

**Expected Impact:** Cleaner URL improves shareability and SERP display. Marginal ranking signal improvement. Important to implement before this page builds significant backlinks to the long URL.

---

### High Issue 6 — FAQ Page H1 Has No Keywords + Missing FAQ Schema

**Affects:** FAQ Page (ID 1205)  
**Quick Win:** Yes

**Current State:**  
- H1 is simply: *"Frequently Asked Questions"* — no keyword signal whatsoever
- The page contains 14 valuable Q&As covering fit, sound, water protection, care, and returns
- None of these Q&As use FAQ JSON-LD schema markup
- Without schema, the page has no chance of appearing in Google's "People Also Ask" boxes

**Suggested Fix:**  

*H1 update:*  
Before: `Frequently Asked Questions`  
After: `SEAR Earplugs FAQ — Fit, Sound, Surfer's Ear & Care Explained`

*Meta title (set via Slim SEO — already partially set but improve):*  
Before: `SEAR Plugs FAQ | Earplugs for Swimming, Surfing & Water Sports`  
After: `SEAR Earplugs FAQ: Sound, Fit, Surfer's Ear & Care` (50 chars)

*Add FAQ schema* covering the top 5 questions:
1. Will I still hear my environment while wearing SEAR?
2. Can SEAR Plugs prevent Surfer's Ear and Swimmer's Ear?
3. How do I find my correct SEAR fit?
4. How long do SEAR Plugs last?
5. Are SEAR Plugs waterproof?

**Expected Impact:** FAQ schema can generate People Also Ask appearances for ear-health and product queries — high-visibility SERP real estate at zero additional ranking effort. Updated H1 provides a keyword signal Google currently receives nothing from this page.

---

## Medium Issues

Incremental gains — address these in the week or two following Critical and High fixes.

---

### Medium Issue 1 — Duplicate Terms & Conditions Pages

**Affects:** Pages ID 1747 (`/terms-and-conditions/`) and ID 1954 (`/terms/`)  
**Quick Win:** Yes

**Current State:**  
Two separate Terms and Conditions pages are published simultaneously. ID 1747 contains the full legal document (15,554 chars); ID 1954 appears to be a shorter duplicate (1,650 chars). Both are indexed. Footer links point to `/terms-and-conditions/` — the shorter page at `/terms/` is an orphaned duplicate.

**Suggested Fix:**  
Add `<meta name="robots" content="noindex">` to ID 1954 (`/terms/`), or implement a 301 redirect from `/terms/` → `/terms-and-conditions/`. Verify footer links all point to `/terms-and-conditions/` only.

**Expected Impact:** Eliminates a minor duplicate content signal. Frees up crawl budget. Low ranking impact but important for site hygiene.

---

### Medium Issue 2 — "How SEAR Works" Page H1 Has No Keyword

**Affects:** Page ID 346 (`/how-sear-works/`)  
**Quick Win:** No

**Current State:**  
- H1: *"How SEAR Works"* — brand-only, no keyword
- Meta title: *"How SEAR Plugs Work: Water Protection Without Blocking Sound"* — this is decent but the H1/meta don't align, creating a mixed signal
- This page could rank for "how do surfing earplugs work" or "acoustic filter earplugs explained" but currently signals nothing useful

**Suggested Fix:**  

| | Before | After |
|--|--|--|
| H1 | "How SEAR Works" | "How SEAR Earplugs Work: 9 dB Acoustic Filter Explained" |
| Meta title | "How SEAR Plugs Work: Water Protection Without Blocking Sound" | "How SEAR Earplugs Work: Block Water, Hear Everything" (52 chars) |
| Meta desc | "Learn how SEAR Plugs work to block water and wind while preserving natural sound. Designed for real conditions in water sports." | "SEAR uses a hydrophobic acoustic mesh to block cold water and wind while keeping ambient sound clear. See how 9 dB of protection keeps you aware in the water." (157 chars) |

**Expected Impact:** Better alignment between H1, meta title, and page content. Improved relevance for "how do surfing earplugs work" and related informational queries.

---

### Medium Issue 3 — "The SEAR Story" About Page Has No Custom Meta

**Affects:** Page ID 406 (`/about-sear-plugs/`)  
**Quick Win:** No

**Current State:**  
The About page has no custom Slim SEO meta title or description. Slim SEO will auto-generate the title from the page name, resulting in a generic "The SEAR Story" snippet in search results — missing the opportunity to capture "SEAR earplugs" brand searches and reinforce credibility.

**Suggested Fix:**  

| | Before | After |
|--|--|--|
| Meta title | (auto-generated: "The SEAR Story") | "About SEAR Plugs: Ear Protection Built by Water Athletes" (56 chars) |
| Meta description | (auto-generated) | "SEAR was created by surfers and swimmers who refused to choose between ear protection and ocean awareness. Meet the team behind the plugs." (137 chars) |

**Expected Impact:** Better brand SERP appearance. Increases click-through for branded searches. Small but meaningful signal for E-E-A-T (Experience, Expertise, Authoritativeness, Trustworthiness).

---

### Medium Issue 4 — Keyword Cannibalization Risk: "Swimming Earplugs Explained"

**Affects:** Post ID 1681 (`/swimming-earplugs-guide/`) and Post ID 1685 (`/swimming-ear-plugs-adults/`)  
**Quick Win:** No

**Current State:**  
Post 1681 targets "swimming earplugs" generically; post 1685 targets "swimming ear plugs for adults." These overlap significantly. Combined with the existing cannibalization between posts 1685 and 1691 (High Issue 1), there are now three posts in the same keyword territory — all competing.

**Suggested Fix:**  
After resolving the 1685/1691 cannibalization (High Issue 1), differentiate post 1681 more clearly. Update its focus to "types of swimming earplugs" (vented vs flanged vs moldable) rather than overlapping with the adult buyer guides. Update slug from `/swimming-earplugs-guide/` to `/types-of-swimming-earplugs/` (301-redirect the old slug).

**Expected Impact:** Creates clear topical separation between posts, allowing each to rank for its distinct query without cannibalising the others.

---

### Medium Issue 5 — 101 Series Posts Have Shallow Ear-Health Sections

**Affects:** Posts IDs 1695, 1698, 1702, 1705, 1709  
**Quick Win:** No

**Current State:**  
Each 101 beginner guide includes a brief "ear protection" section (50–100 words). These sections are too short to establish any topical authority for ear health and miss the chance to contextualise why a beginner needs ear protection specifically. The Surfing 101 guide mentions "Ear protection (seriously underrated)" as a heading but the copy under it is minimal.

**Suggested Fix:**  
Expand the ear-protection section in each 101 guide to 200–300 words. Include: what the specific condition is (surfer's ear / swimmer's ear), the timeline of damage (how long it takes to develop), and an internal link to the relevant deep-dive post. Example for Surfing 101:

*"Protecting your ears ranks alongside a good leash and a quality wetsuit — non-negotiable in cold water. Cold water and wind cause exostosis, a bony growth in the ear canal known as surfer's ear. It develops slowly over years of exposure. By the time symptoms show, you may already need surgery. [Learn how surfer's ear develops and how to stop it →]. SEAR earplugs block the water and wind that trigger exostosis without reducing your situational awareness in the lineup."*

**Expected Impact:** Increases topical depth on ear health within beginner guides. Creates natural internal links to the ear-health post cluster. Marginal SEO gain but meaningful for E-E-A-T and reader engagement.

---

### Medium Issue 6 — Product Page Lacks FAQ Schema

**Affects:** Product page (ID 99)  
**Quick Win:** No

**Current State:**  
The product page contains FAQ-style content (Q&As about the acoustic filter, fit sizes, and ear health) but no FAQ JSON-LD schema. Without schema, this content has no chance of appearing in Google's People Also Ask results for product-related queries.

**Suggested Fix:**  
Add FAQ JSON-LD schema to the product page with these questions:
1. Do SEAR earplugs block all sound?
2. What sizes are included with SEAR earplugs?
3. Can I use SEAR earplugs in a pool and the ocean?
4. How long do SEAR earplugs last?
5. Do SEAR earplugs prevent surfer's ear?

**Expected Impact:** PAA appearances for product queries. Competitors with FAQ schema on product pages frequently claim 1–3 PAA boxes for branded and category queries — a high-visibility SERP feature with no additional ranking effort required.

---

## Low Issues

Nice-to-have improvements — address once higher-priority items are complete.

---

### Low Issue 1 — Product Image Alt Text Could Be More Specific

**Affects:** Product images (IDs 1506, 1472, and others)  
**Quick Win:** No

**Current State:**  
Product image alt texts are descriptive but don't include the brand name or primary keyword:
- Image 1506: *"Pair of reusable water-sports earplugs displayed on a white surface."*
- Image 1472: *"Man inserting blue water-sports earplugs while standing by the ocean."*

These are functional but miss the keyword reinforcement that alt text can provide.

**Suggested Fix:**  

| Image ID | Before | After |
|--|--|--|
| 1506 | "Pair of reusable water-sports earplugs displayed on a white surface." | "SEAR waterproof earplugs for surfing and swimming — pair on white surface." |
| 1472 | "Man inserting blue water-sports earplugs while standing by the ocean." | "Man wearing SEAR earplugs by the ocean — preventing surfer's ear." |
| 1469 | "SEAR earplug kit layout showing earplugs, sizes, leash, and carrying case." | "SEAR earplug kit — 3 tip sizes, 4 wing sizes, waterproof case, and floatable leash." |

**Expected Impact:** Marginal. Strengthens keyword-in-image signals for Google Image Search and adds minor on-page keyword context. Low effort improvement.

---

### Low Issue 2 — Navigation Anchor Text Is Not Keyword-Rich

**Affects:** Site-wide navigation  
**Quick Win:** No

**Current State:**  
The main navigation uses "Surfer Plugs" as the label for the product link. This is the highest-frequency anchor text on the entire site (appearing on every page), yet it targets a phrase that almost nobody searches for. "Surfer Plugs" has minimal search volume compared to "earplugs for surfing" or "surfing earplugs."

**Suggested Fix:**  
Update the navigation label from *"Surfer Plugs"* to *"Earplugs for Surfing & Swimming"*. This is the most-seen internal anchor text on the site — every page passes this signal to the product page.

**Expected Impact:** Minor but consistent keyword signal improvement. Given the site-wide frequency of this anchor text, the cumulative signal is non-trivial. Does not require any content changes — just a nav menu update.

---

### Low Issue 3 — Blog Post on "Surfer's Ear vs Swimmer's Ear" Has Brand Name in H1

**Affects:** Post ID 1677 (`/surfers-ear-vs-swimmers-ear-prevention/`)  
**Quick Win:** No

**Current State:**  
H1: *"Surfer's Ear vs. Swimmer's Ear: Understanding the Risks & How SEAR Plugs Keep You Protected"*

Including the brand name ("SEAR Plugs") in the H1 reduces keyword density for the actual search query. The H1 is 93 characters — far longer than the ideal 55–70 characters. The meta title is already well-crafted: *"Surfer's Ear vs Swimmer's Ear: Key Differences & Prevention"* — but the H1 undercuts it.

**Suggested Fix:**  

| | Before | After |
|--|--|--|
| H1 | "Surfer's Ear vs. Swimmer's Ear: Understanding the Risks & How SEAR Plugs Keep You Protected" | "Surfer's Ear vs Swimmer's Ear: Key Differences, Risks & Prevention" |

The brand mention can live naturally in the body copy and the CTA — it doesn't need to compete for H1 space with the target keyword.

**Expected Impact:** Minor ranking signal improvement. Cleaner H1/meta title alignment. The meta title is already good; aligning the H1 to it reinforces the signal.

---

### Low Issue 4 — Buyer's Guide Posts Need Annual Refresh Signals

**Affects:** Posts IDs 1685, 1691, 1681  
**Quick Win:** No

**Current State:**  
Three buyer's guide posts were published in January 2026 with year signals in their titles or descriptions (e.g. "2026"). These posts will need annual refreshing to maintain relevance. Currently, there is no visible "last reviewed" date, and no structured process for updating them.

**Suggested Fix:**  
1. Add a visible "Last reviewed: January 2026" line at the top of each buyer's guide.
2. Add a reminder (e.g. Google Calendar event or scheduled task) to update these posts each January — refresh the year references, check that competitor comparisons are still accurate, and update the WordPress "modified" date.
3. For post 1691 (which already uses "2026" in the title), ensure the title is updated to "2027" at the start of next year.

**Expected Impact:** Content freshness is a moderate ranking factor for competitive "best [product] 2026" queries. Stale year signals (e.g. "2026" in a 2027 search) cause click-through rate drops as users skip over apparently outdated results.

---

## Competitor Benchmark Summary

**SurfEars (surfears.com)** was assessed as the primary competitor. Key gaps to close:

| Factor | SurfEars | SEAR | Gap |
|--|--|--|--|
| Verified reviews | 700+ (4.8★) | 0 | Critical |
| Star ratings in SERPs | Yes | No (no schema) | Critical |
| Press mentions | Stab, Inertia, Surf Bunker | None visible | Medium |
| Price | €54.95 | £39.95 | SEAR advantage |
| Sustainability angle | 5% to ocean restoration | Not mentioned | Medium |
| Product category | Clear | "Uncategorized" | Critical |
| Trust signal in SERPs | "4.8★ from 700+ reviews" | Plain link | Critical |

SEAR's price advantage over SurfEars is significant and not currently surfaced in the product meta description. Once Product schema is in place with pricing, this advantage will be visible in search results automatically.

---

## Implementation Roadmap

### Week 1 (Critical — do these immediately)
1. Fix dual product URLs — add canonical + standardise all internal links to `/sear-swimming-surfing-ear-plugs/`
2. Create "Earplugs for Water Sports" WooCommerce category and assign product
3. Update `/shop/` meta title and H1 to be unique from homepage
4. Set up post-purchase review email sequence

### Week 2 (High — quick wins + structural)
5. Add tags to all 10 blog posts
6. Shorten Exostosis post slug to `/surfers-ear-exostosis/` with 301 redirect
7. Update FAQ page H1 and add FAQ JSON-LD schema
8. Begin cross-linking blog posts (priority: Surfing 101 → Exostosis; Surfer's Ear vs Swimmer's Ear → Exostosis)

### Week 3 (Critical + High — technical)
9. Implement Product JSON-LD schema (price, availability)
10. Decide on 1685/1691 cannibalization strategy (redirect or differentiate)

### Week 4+ (Medium + Low)
11. Update "How SEAR Works" and "The SEAR Story" meta fields
12. Expand ear-protection sections in 101 guides
13. Update navigation anchor text
14. Fix duplicate Terms & Conditions page
15. Update product image alt text
16. Add FAQ schema to product page

---

*Full issue log and quick wins tab available in the accompanying XLSX file: `seo-audit-all-2026-04-15.xlsx`*
