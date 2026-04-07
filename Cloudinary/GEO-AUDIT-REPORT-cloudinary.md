# GEO Audit Report: Cloudinary
GEO Analyzer - dawid.ai | Built by Dawid Jozwiak

**Audit Date:** 2026-04-07
**Target:** https://cloudinary.com/
**Business Type:** SaaS (Image/Video API Platform)
**Pages Analyzed:** 10

---

## Executive Summary

**Composite GEO Score: 67/100 — Good (51-75)**

Cloudinary is a well-established SaaS brand with strong entity signals (Wikipedia, Wikidata **Q27150151**, Forbes Cloud 100 six years running, $2B Blackstone valuation) and a best-in-class llms.txt implementation (121KB, spec-compliant). But it suffers a **critical schema gap**: no Organization sameAs, no SoftwareApplication/Product/Offer, no FAQPage JSON-LD. The 25/100 schema score undermines an otherwise strong technical and authority foundation.

**Top leverage points:**
1. Add Organization + Product JSON-LD (biggest entity-linking win)
2. Move homepage stats into SSR prose (citability currently 35/100 on homepage)
3. Publish proprietary benchmark data (Perplexity moat)
4. Counter Trustpilot's 2.9/5 narrative (visible negative signal in LLM responses)

### Score Breakdown

| Dimension | Score | Weight | Contribution | Tier |
|---|---|---|---|---|
| AI Citability | 58 | 25% | 14.5 | Good |
| Brand Authority | 84 | 20% | 16.8 | Excellent |
| Content E-E-A-T | 71 | 20% | 14.2 | Good |
| Technical GEO | 78 | 15% | 11.7 | Excellent |
| Schema / Structured Data | 25 | 10% | 2.5 | Critical |
| Platform Optimization | 74 | 10% | 7.4 | Good |
| **Composite** | **67** | | | **Good** |

### Platform Readiness

| Platform | Score | Citation Likelihood |
|---|---|---|
| ChatGPT Web Search | 82 | High (strongest fit) |
| Google Gemini | 76 | High |
| Bing Copilot | 73 | High |
| Google AI Overviews | 72 | High |
| Perplexity AI | 68 | Moderate (weakest fit) |

---

## Critical Issues

1. **No Organization schema with sameAs links anywhere on site.** The largest single GEO loss for a Wikipedia-listed SaaS brand. AI cannot structurally tie cloudinary.com to its entity graph. **Fix:** Add global Organization JSON-LD with sameAs → Wikipedia (Q27150151), LinkedIn, YouTube, Crunchbase, X, GitHub.

2. **No SoftwareApplication/Product/Offer schema on Programmable Media or /pricing.** Major SaaS rich-result and AI comparison miss — AIO/ChatGPT cannot extract structured pricing or feature data. **Fix:** Add SoftwareApplication + Offer JSON-LD with tiers, currency, feature list, aggregateRating.

3. **No proprietary benchmark or research data on product pages.** Perplexity and AIO favor primary-source data; marketing prose alone limits citation likelihood. **Fix:** Publish p50/p95 latency, format negotiation savings, compression % benchmarks.

## High-Severity Issues

4. Homepage stats (3M+ devs, 11K+ brands, 50M req/sec) embedded in JS/CSS — citability = 35/100. Move to SSR prose.
5. FAQ page uses microdata (itemscope) not JSON-LD FAQPage. Convert to JSON-LD.
6. Zero author bylines or Person schema across all content. Add named bylines + Person schema + LinkedIn sameAs.
7. robots.txt disallows /documentation/sdks/* and /blog/20*. Reopen via explicit Allow.
8. Security headers missing (HSTS, Referrer-Policy, Permissions-Policy); X-Content-Type-Options sent empty.
9. Trustpilot 2.9/5 across only 5 reviews (80% one-star, pricing complaints). Review push + transparent pricing page.
10. No visible "Last updated" dates. Add dateModified surfacing.

## Medium / Low Issues

11. Generic marketing phrasing dominates core product pages ("streamline", "unleash").
12. No Person schema on /team.
13. Organization sameAs (if it existed) would be missing YouTube, GitHub, Wikidata, Crunchbase, G2.
14. IndexNow not implemented.
15. Homepage entity-sparse (only 1 distinct entity detected in 390 words).
16. `/llms-full.txt` returns 404 (llms.txt itself is best-in-class).
17. Legacy jQuery + Bootstrap 4.3.1 + heavy 3rd-party stack; INP risk medium-high.
18. All content uses generic WebPage instead of Article/BlogPosting.
19. 56% fan-out coverage (11/25 subqueries uncovered).
20. URL uses underscore: `/products/programmable_media`.

---

## 3. AI Citability Deep Dive

**Homepage citability:** 35/100 (D grade — Low Citability) — single answer block detected; stats buried in JS components.
**Best content page citability (/products/programmable_media):** 30.7/100 — heavy feature copy, low self-contained answer density.
**RAG Retrieval Simulation:** 38 chunks analyzed for "best image and video optimization API" — top passage scored **0.5519** (cosine similarity). Moderate retrieval signal.

**Most Citable Pages:**
- `/faq` — 16+ self-contained Q&A answers (bandwidth definitions, video usage limits)
- `/customers` — Quantified case studies (Adidas 50M req/sec, Puma, Fiverr, Neiman Marcus)
- `/solutions/ecommerce` — Strong quantified claims (Manscaped 50% conv lift, Puma 71% load gain)
- `/about` — Company stats block + dated modification
- `/products/programmable_media` — Deep technical feature coverage

**Least Citable Pages:**
- `/` — Homepage with JS-embedded stats
- `/team` — Thin content, no Person schema
- `/pricing` — No Product/Offer schema
- `/solutions/why_cloudinary` — Generic marketing copy
- `/developers` — Interactive UI, few scannable answer blocks

---

## 4. Entity & Knowledge Graph Analysis

| Entity | Type | Status | Wikidata QID | Note |
|---|---|---|---|---|
| Cloudinary | ORG | ✓ Linked | Q27150151 | "American data storage company" |

**Density metrics (homepage):**
- Entities per 100 words: 0.51
- Unique entity ratio: 0.5
- Wikidata coverage: 100% (of detected entities)
- Entity health score: **70/100**
- Total triples: 20

**Note:** Homepage is entity-sparse — only 1 distinct entity found with 2+ occurrences across 390 words. This reflects marketing-fragment density rather than referential content.

---

## 5. RAG Retrieval Simulation

**Query:** "best image and video optimization API"
**Method:** Cosine Similarity (TF-IDF)
**Total chunks:** 38
**Top passage score:** 0.5519 — moderate
**Top passage preview:** From `/products/programmable_media`, top chunk centers on AI-powered image and video transformation at scale.

**Implication:** Content contains relevant vocabulary but lacks tightly-matched answer blocks. Adding a definitional opening ("Cloudinary is an image and video optimization API that...") and question-phrased H2s would materially lift RAG retrieval scores.

---

## 6. Query Fan-Out Coverage

**Primary query:** "best image and video optimization API"
**Coverage:** 14/25 subqueries covered (**56%**)
**Gaps:** 11 subqueries uncovered (confidence < 0.15)

### Top Content Gaps

| Rank | Subquery | Confidence | Closest Page |
|---|---|---|---|
| 1 | how to transcode videos in cloud | 0.052 | /products/programmable_media |
| 2 | image compression service | 0.076 | /products/programmable_media |
| 3 | DAM for ecommerce | 0.077 | /solutions/ecommerce |
| 4 | how to deliver responsive images | 0.085 | /products/programmable_media |
| 5 | how to optimize images for web | 0.102 | /products/programmable_media |
| 6 | video streaming for websites | <0.15 | /products/programmable_media |
| 7 | video transcoding API | <0.15 | /products/programmable_media |
| 8 | Cloudinary free tier | <0.15 | /pricing |
| 9 | image background removal API | <0.15 | /products/programmable_media |
| 10 | what is a DAM system | <0.15 | /about |

See **GEO-TO-WRITE-cloudinary.md** for full content creation specs per gap.

---

## 7. Brand Authority

**Brand score: 84/100 — Excellent**

| Platform | Status | Detail |
|---|---|---|
| Wikipedia | Present | Full article, 26 refs, founders named, $2B valuation |
| Wikidata | Present | **Q27150151** — "American data storage company" |
| Knowledge Graph | High confidence | JPEG XL collaboration with Google |
| LinkedIn | Active | 68,843 followers, 201-500 employees |
| YouTube | Active | Official @Cloudinary channel, DevJams podcast |
| G2 | Strong | 4.5/5 across 118 reviews (72% five-star) |
| Capterra | Listed | Cross-referenced with G2 |
| Trustpilot | **Weak** | 2.9/5 across only **5 reviews** (80% one-star) |
| Reddit | Active | 33 direct threads across r/webdev, r/nextjs, r/node, r/django, r/SaaS, r/devops — positive sentiment with pricing complaint subcurrent |
| Forbes Cloud 100 | 6 consecutive years | Strong industry authority |

**Competitive position:** Default-cited brand in nearly every "best image CDN" comparison. Wins on breadth (DAM, video, AI) vs imgix (speed), Cloudflare Images (price), Bunny.net (cost), Akamai (enterprise).

**Weakest signal:** Trustpilot's 5-review × 2.9/5 combination is retrievable by LLMs asking about Cloudinary downsides. Even 20 positive reviews would flip this.

---

## 8. Technical GEO

**Technical Score: 78/100 — Good**

- **Rendering:** Full SSR via WordPress (cld-2021 theme), fronted by Cloudflare with HTTP/3. **AI crawlers see everything.** (98/100)
- **Crawlability:** robots.txt permissive for AI crawlers, 5 sitemaps declared, lastmod current. (85/100)
- **Indexability:** Unique titles/descriptions, self-canonical, complete OG, no hreflang (English-only). (88/100)
- **Security headers:** HTTPS + HTTP/3 present, CSP extensive, but **HSTS missing**, **X-Content-Type-Options sent empty**, **Referrer-Policy missing**, **Permissions-Policy missing**. (55/100)
- **Core Web Vitals risk:** Medium. LCP moderate (render-blocking CSS), INP medium-high (heavy 3rd-party stack: GTM, Marketo, Drift, 6sense, Cookiebot, OneTrust, Crazyegg, Convert, ZoomInfo, AdRoll, StackAdapt, G2, LinkedIn, Facebook, Clarity). (62/100)
- **Mobile:** Viewport set, layout responsive. `maximum-scale=5.0` limits accessibility. (85/100)
- **URL structure:** Clean, shallow, lowercase. Single nit: underscore in `programmable_media`. (88/100)

### llms.txt Status (from Python validation)

- `/llms.txt` — **Present** (121KB, spec-compliant H1 + blockquote + H2 sections, per-link descriptions)
- `/llms-full.txt` — **Not found (404)**

### AI Crawler Access Map

| Crawler | Access |
|---|---|
| GPTBot, OAI-SearchBot, ChatGPT-User | Allow |
| ClaudeBot, PerplexityBot | Allow |
| Google-Extended, GoogleBot | Allow |
| Amazonbot, Bytespider, CCBot | Allow |
| Applebot-Extended, FacebookBot, Cohere-ai, BingBot | Allow |

**Concerning disallow paths:** `/documentation/sdks/*`, `/demos/*`, `/blog/20*` — hide high-value developer content from generic crawlers (partially mitigated by llms.txt for compliant agents).

### Framework / Source Analysis

- Framework: WordPress (cld-2021 theme) + jQuery 3.4.1 + Bootstrap 4.3.1 (EOL)
- Inline CSS: 131,823 bytes
- Inline JS: 16,116 bytes
- External scripts: 13
- Render-blocking scripts: 4 (jQuery, Bootstrap, DebugBear, ConvertExperiments)

---

## 9. Schema & Structured Data — **CRITICAL DIMENSION (25/100)**

**What's working:**
- BreadcrumbList (valid, all pages)
- WebSite + SearchAction (valid)
- All JSON-LD server-rendered (no JS injection risk)
- Yoast-style `@graph` pattern is clean and valid

**Critical gaps:**
1. **No Organization schema anywhere** — largest entity-linking loss
2. **Zero sameAs links** — AI cannot structurally tie domain to cross-platform identity
3. **No SoftwareApplication / Product / Offer** — major SaaS rich-result miss
4. **No Person schema** on /team or for content authors
5. **No FAQPage JSON-LD** despite /faq having 51 Question microdata items
6. **All content uses generic WebPage** instead of Article/BlogPosting
7. **No speakable property** anywhere

---

## 10. Platform Readiness (per-platform)

| Platform | Score | Citation Likelihood | Primary Barrier |
|---|---|---|---|
| ChatGPT | 82 | High | Homepage stats buried in JS components |
| Gemini | 76 | High | Missing Wikidata sameAs in Organization schema |
| Bing Copilot | 73 | High | IndexNow not implemented; no HSTS |
| Google AI Overviews | 72 | High | No Product/SoftwareApplication schema; no dateModified surfacing |
| Perplexity | 68 | Moderate | Marketing prose instead of primary-source benchmarks |

**Strongest platform fit:** ChatGPT — Wikipedia entity, full SSR, GPTBot allowed, best-in-class llms.txt, active developer content.
**Weakest platform fit:** Perplexity — lacks dated, benchmark-style content Perplexity heavily weights.

---

## 11. Competitor Benchmark

Cloudinary's authority and entity signals materially exceed direct competitors (imgix, Bunny.net, Cloudflare Images, Akamai Image Manager) on Wikipedia presence, Forbes Cloud 100, and G2 breadth. The gap is smaller on **proprietary benchmarks** — where imgix and Cloudflare publish technical performance data more aggressively.

---

## 12. Quick Wins & 30-Day Action Plan

### Quick Wins (<4h each) — projected +8-15 points

1. Fix X-Content-Type-Options empty header (add nosniff) — <1h
2. Add HSTS, Referrer-Policy, Permissions-Policy at Cloudflare edge — 1h
3. Convert /faq microdata to JSON-LD FAQPage — 2h
4. Add global Organization JSON-LD with sameAs (Wikipedia Q27150151, LinkedIn, YouTube, GitHub, Crunchbase, X) — 2h
5. Publish `/llms-full.txt` consolidated file — 2h
6. Add visible "Last updated" dates + dateModified across marketing pages — 3h
7. Move homepage hero stats into SSR HTML prose — 3h
8. Implement IndexNow protocol — 2h

### Medium-Term (1-5 days each) — projected +8-15 points

1. Add SoftwareApplication + Offer JSON-LD to /products/programmable_media and /pricing
2. Reopen /documentation/sdks/* in robots.txt (use canonical/noindex for dup-content)
3. Add Person schema across /team with LinkedIn sameAs
4. Replicate /solutions/ecommerce case-study density across all /solutions pages
5. Publish 11 fan-out gap guides (see GEO-TO-WRITE reference)
6. Audit GTM tags; lazy-load non-critical pixels to lift INP
7. Trustpilot review push campaign
8. Publish transparent pricing/overage policy page

### Strategic (ongoing) — projected +8-15 points

1. Publish proprietary benchmark data (p50/p95 latency, compression %) — quarterly
2. Establish named-author editorial program with Person schema
3. Plan migration off Bootstrap 4.3.1/jQuery — 1-2 months
4. Convert blog to BlogPosting schema with author/publisher/speakable
5. Quarterly dateModified refresh across marketing pages

**Projected score after all tiers: 97/100 (Excellent)**

---

## Appendix: Pages Analyzed

1. https://cloudinary.com/
2. https://cloudinary.com/products/programmable_media
3. https://cloudinary.com/pricing
4. https://cloudinary.com/about
5. https://cloudinary.com/solutions/ecommerce
6. https://cloudinary.com/solutions/why_cloudinary
7. https://cloudinary.com/developers
8. https://cloudinary.com/customers
9. https://cloudinary.com/faq
10. https://cloudinary.com/team

---

*GEO Analyzer - dawid.ai | Built by Dawid Jozwiak*
