# SEO Audit — Oficina AG3 (oficinaag3.com.br)

**Date:** 2026-07-02
**Business type:** Brick-and-mortar Local Service — Automotive Repair (Dodge/Ram/Chrysler/Jeep specialist), São Paulo, SP
**Site platform:** Zyro / Hostinger Website Builder (Astro-rendered SPA)
**Pages discovered:** 3 (Home `/`, Contato `/contatooficina-ag3`, Projetos `/projetos`)
**Method:** Rendered each page with Playwright (`render_page.py`), parsed DOM/meta/schema (`parse_html.py`), scored content (`content_quality.py`), linted GBP surfaces (`gbp_deprecation_lint.py`), checked robots.txt/sitemap.xml/llms.txt directly, verified resource status codes and www/non-www/HTTP-HTTPS canonicalization via curl.

---

## Overall SEO Health Score: 25 / 100 (Critical)

| Category | Weight | Score | Weighted |
|---|---|---|---|
| Technical SEO | 22% | 15/100 | 3.3 |
| Content Quality | 23% | 35/100 | 8.1 |
| On-Page SEO | 20% | 30/100 | 6.0 |
| Schema / Structured Data | 10% | 0/100 | 0.0 |
| Performance | 10% | 50/100 | 5.0 |
| AI Search Readiness | 10% | 15/100 | 1.5 |
| Images | 5% | 25/100 | 1.25 |
| **Total** | 100% | | **25.1 ≈ 25/100** |

The dominant driver of the low score is that **all three pages carry `<meta name="robots" content="noindex">`**, which means the site is currently invisible to Google regardless of any other optimization. Everything else compounds on top of that: zero structured data, an empty sitemap, no dedicated service pages, and thin content.

---

## 1. Technical SEO — 15/100

**Critical**
- **`<meta name="robots" content="noindex">` is present on all 3 pages** (home, contato, projetos), confirmed in raw rendered HTML. This is very likely a leftover from the Hostinger/Zyro builder's staging/preview mode that was never removed at go-live. As long as this tag is present, Google (and Bing) will not index any page on the domain — every other SEO effort is moot until this is fixed.
- **`sitemap.xml` exists but is empty.** `robots.txt` correctly references `https://www.oficinaag3.com.br/sitemap.xml`, and the file returns HTTP 200, but its `<urlset>` contains zero `<url>` entries. This gives crawlers no page inventory to work from.

**High**
- **www / non-www duplicate serving.** `https://oficinaag3.com.br/` (no www) returns HTTP 200 with the exact same content as `https://www.oficinaag3.com.br/` — no 301 redirect exists between the two hosts. This is partially mitigated because the canonical tag on both versions correctly points to `https://www.oficinaag3.com.br/`, but a proper 301 redirect at the host level is the industry-standard fix and removes any residual duplicate-content risk.
- **Unidentified 404 console error on every page.** Every rendered page logs one `Failed to load resource: 404` in the browser console. All resources referenced in the static HTML (`href`/`src` attributes, ~30 unique URLs) were checked individually and all returned 200/301/302 — none 404. The failing resource is therefore loaded dynamically via JavaScript (likely a third-party tracking/analytics pixel injected by the Zyro/Hostinger runtime) and wasn't identifiable from static markup. Low SEO impact but worth a quick DevTools Network-tab check by whoever manages the Hostinger account, since a 404 firing on every pageview can affect Core Web Vitals CLS/latency and pollutes analytics.

**Not a problem (correcting an initial hypothesis)**
- The `Content-Security-Policy: frame-ancestors zyro.com *.zyro.com *.builder-preview.com *.hostinger.* ...` header only restricts who can **embed this site in an iframe** (anti-clickjacking). It does not block Googlebot, other crawlers, or normal browser navigation — this is standard, safe Hostinger builder behavior, not an SEO or accessibility issue.

**Working correctly**
- HTTPS enforced with HSTS (`max-age=63072000; includeSubDomains; preload`).
- `robots.txt` is minimal and permissive (`Disallow:` empty — allows all crawlers, including AI bots like GPTBot/ClaudeBot by default).
- Mobile viewport meta tag present and correct on all pages.
- Canonical tags present and self-referencing correctly on all 3 pages.
- HTTP → HTTPS redirects correctly (301).

---

## 2. Content Quality — 35/100

- **Thin content across the board:** Home = 257 words, Contato = 112 words, Projetos = 98 words. For a local service business competing on "Dodge/Ram/Chrysler/Jeep especializada São Paulo," this is far below what's needed to rank for even moderately competitive queries.
- **E-E-A-T signal found but under-leveraged:** the About section states the shop has been "trabalhando com as marcas mais conhecidas do mercado desde 1991" (operating since 1991) — a strong 30+ year experience/trust signal — but it's a single buried sentence, not reinforced with certifications, technician bios, brand-authorized-dealer language, before/after case studies with detail, or review counts.
- **Only one testimonial**, unattributed (no customer name, no vehicle model, no date, no photo) — weak social proof for an E-E-A-T-sensitive vertical like auto repair.
- **"Projetos" page is a portfolio, not proof-driven case studies** — 98 words total across what should be a showcase page; no before/after narrative, no technical detail on what was done, no customer outcomes.
- `content_quality.py` (filler/AI-pattern/repetition heuristic) scored the homepage 92/100 on writing hygiene (no filler, no AI-slop phrasing, low repetition) — the writing itself is clean, the problem is sheer volume and depth, not quality of the sentences that exist.
- No FAQ content anywhere on the site — a missed opportunity for both traditional SEO (featured snippets) and AI answer-engine citability.

---

## 3. On-Page SEO — 30/100

- **No dedicated service pages.** All services are listed as a short section on the homepage with no individual URLs for "troca de óleo," "revisão Jeep," "diagnóstico eletrônico," "suspensão Ram," etc. Per Whitespark's local ranking factor studies, dedicated service pages are consistently the #1 on-page factor for local organic map-pack and organic rankings. This is the single highest-leverage on-page gap on the site.
- **Title tags too long and redundantly branded:**
  - Home: 71 chars — *"Oficina AG3: Especializada em Dodge, Ram, Chrysler e Jeep | Oficina AG3"* (brand name appears twice)
  - Contato: 77 chars
  - Projetos: 86 chars
  All exceed Google's ~580px / ~60-char practical display limit and will be truncated in SERPs.
- **Meta descriptions too long:** Home 173 chars, Contato 223 chars, Projetos 245 chars — all well past the ~155-160 char display limit, guaranteeing truncation.
- **No H2 headings anywhere on the site.** Heading hierarchy jumps straight from H1 to H3, and several H3s are semantically meaningless (bare "®" symbols repeated 4x on the homepage, footer copyright text tagged as H3 twice per page). This flattens the page's topical structure for both classic SEO crawlers and AI content parsers.
- **H1 is generic:** "Oficina AGiii" (home) / "PRONTOS PARA TRABALHAR JUNTOS" (contato) / "EXPLORE ALGUNS DOS NOSSO PROJETOS" (projetos, with a grammar typo — "NOSSO" should be "NOSSOS") — none target actual search intent keywords like city + brand + service.
- **No in-body internal linking** — `parse_html.py` found zero internal links inside page content on any of the 3 pages; the only internal navigation is the header/footer nav (Home/Contato/Projetos), so there's no contextual link equity flow even between the 3 existing pages.
- **No visible, crawlable phone number as text** — the phone number only appears embedded inside `wa.me`/WhatsApp deep-link URLs (`5511942782852`), never as plain text or a `tel:` link (see Local SEO section).

---

## 4. Schema / Structured Data — 0/100

- **Zero JSON-LD or microdata found on any page** (`schema: []` across home, contato, projetos).
- No `LocalBusiness`/`AutoRepair` schema, no `aggregateRating`/`Review`, no `openingHoursSpecification`, no `geo` coordinates, no `PostalAddress`.
- Per schema.org, the correct type for this business is **`AutoRepair`** (a subtype of `LocalBusiness` → `AutomotiveBusiness` → `AutoRepair`), not generic `LocalBusiness`. Using the specific subtype gives Google stronger vertical-specific signal and unlocks richer local pack/knowledge panel treatment.
- Open Graph and Twitter Card tags ARE present and reasonably well-formed on all 3 pages (title, description, image, og:type) — good for social sharing, but this does not substitute for Schema.org markup.

**Recommended schema shape** (values sourced from the rendered pages):
```json
{
  "@context": "https://schema.org",
  "@type": "AutoRepair",
  "name": "Oficina AG3 (Chrysler AGIII Oficina Especializada)",
  "image": "https://assets.zyrosite.com/.../imagem_2024-07-31_162816846.png",
  "telephone": "+5511942782852",
  "email": "andrea@oficinaag3.com.br",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Av. Casa Verde, nº 3064",
    "addressLocality": "São Paulo",
    "addressRegion": "SP",
    "postalCode": "02520-300",
    "addressCountry": "BR"
  },
  "url": "https://www.oficinaag3.com.br/",
  "priceRange": "$$",
  "openingHoursSpecification": [ /* NEEDS TO BE SOURCED — not published anywhere on site, see Local SEO */ ]
}
```
`schema_generate.py` was available in the plugin toolkit; it was not run against a template because the required inputs (confirmed opening hours, confirmed sameAs social profile URLs) needed owner confirmation first — see Action Plan.

---

## 5. Local SEO — NAP & Local Signals

- **Address confirmed and consistent (single source, no conflicting variants found):** "AV. CASA VERDE, Nº 3064 - CASA VERDE, CEP: 02520-300 - SÃO PAULO - SP" — appears once, only on the Contato page, embedded inside a text block (not marked up semantically, no `address` HTML tag, no schema).
- **Phone number inconsistency found:** the WhatsApp click-to-chat button uses `phone=551194278-2852` (with a stray hyphen inside the number) while the `wa.me` deep link and presumably the real number is `5511942782852` (11 942 782 852). The hyphen version still functions because WhatsApp strips non-digits, but it's sloppy and should be normalized — and critically, **the phone number never appears as visible, selectable plain text or a `tel:` link anywhere on the site.** Visitors and crawlers only see it inside WhatsApp URL parameters.
- **No click-to-call `tel:` link exists anywhere on the site** — a basic, high-value local-conversion element that's completely missing. For a repair shop where many customers still prefer calling for urgent issues, this is a conversion (not just SEO) gap.
- **Google Maps embed present** on the Contato page (`<iframe class="grid-map__frame" src="https://maps.google.com/maps?q=AV.%20CASA%20VERDE...">`) — good, but it's a generic maps-query embed, not a proper Google Business Profile "place" embed tied to a verified GBP listing ID, so it doesn't reinforce GBP entity signals.
- **No opening hours published anywhere on the site** — not on the Contato page, not in schema (there's no schema at all), not near the map. This is a meaningful gap for both users and for `openingHoursSpecification` schema.
- **No GBP profile reference/link found on-site** (no "View on Google" link, no embedded GBP reviews widget).
- **Email found and consistent:** `ANDREA@OFICINAAG3.COM.BR`, appears identically on all 3 pages (as a `mailto:` link).
- **Social profiles found in footer:** Facebook (`facebook.com/chrysleragtres.ltda`), Instagram (`instagram.com/oficina_ag3`), TikTok (`tiktok.com/@oficina.aglll`), YouTube channel. These are good `sameAs` candidates for schema once confirmed as still active/owned by the business — note the Facebook handle ("chrysleragtres") and TikTok handle ("oficina.aglll") don't match the "AG3"/"AGIII" branding used elsewhere, worth verifying these are the current official accounts.

---

## 6. Performance

- **Google PageSpeed Insights / CrUX data: unavailable.** `pagespeed_check.py` was run twice (with a wait in between) and both times returned `"PSI rate limit exceeded (240 QPM / 25,000 QPD)"` — this is a shared/rate-limited API key baked into the plugin, not something fixable from this environment. See "Not Run / Missing Access" section below for what this would have provided.
- **Rough proxy signal — Playwright render time:** Home 6.4s, Contato 8.8s, Projetos 6.7s. These numbers include full headless-Chromium cold-start overhead (browser launch, not just page load) and are **not equivalent to a Lighthouse/CrUX load-time metric** — treat as a weak directional signal only. They are on the slower side for a 3-page static-content builder site and worth validating with a real Lighthouse run once API access is available.
- Images are served through Hostinger/Zyro's `assets.zyrosite.com/cdn-cgi/image/...` transformation CDN with explicit `format=auto`, width/height, and `fit=crop` params — this is a good sign for responsive image delivery and likely mitigates a lot of raw file-size risk even without confirmed Lighthouse numbers.
- `content-encoding: br` (Brotli) is enabled at the CDN edge — good compression practice.

---

## 7. Images

- **Alt text coverage is poor.** Of the 18 `<img>` elements found on the homepage, only 2 have meaningful alt text ("Oficina AG3 logo" — duplicated for the same image used twice). The remaining ~16 images (Dodge/Chrysler/SRT brand logos, hero background, project photos) have either `alt=""` (empty) or `alt=null` (attribute missing entirely). This is a missed opportunity for image search visibility and an accessibility gap.
- **No oversized images detected** — all images are served pre-sized through the CDN transformation layer with explicit width/height attributes on most (reduces CLS risk).
- Two hero/background images use `loading="lazy"` appropriately; the above-the-fold logo image correctly has no lazy-loading (`lazy_method: "none"`), which is correct practice for LCP-critical images.

---

## 8. AI Search Readiness — 15/100

- **`llms.txt` does not exist** (returns Hostinger's generic 404 page, not a custom 404, meaning it was never created).
- **`robots.txt` has no explicit rules for AI crawlers** (GPTBot, ClaudeBot, PerplexityBot, Google-Extended, etc.) — but since the blanket rule is `Disallow:` (empty, i.e., allow-all), these crawlers are technically permitted to fetch the site by default. The practical blocker is not robots.txt, it's the **`noindex` meta tag**, which many AI crawlers and answer engines also respect as a "do not use this content" signal, and the near-total absence of citable structured content.
- **Structural citability is weak:** no H2s, no FAQ format, no direct-answer-style paragraphs, no schema for entity grounding (no `AutoRepair`/`LocalBusiness` schema for AI systems to anchor facts like address/phone/hours to). AI answer engines strongly favor pages with clear question-style headings and self-contained factual paragraphs — this site has neither.
- Fixing `noindex` + adding `AutoRepair` schema + adding a real FAQ section per service would move this from near-zero to a reasonably competitive baseline with minimal extra work beyond what's already needed for traditional SEO.

---

## Checks NOT Run — Missing Paid/Authenticated Access

The following were explicitly out of scope for this environment (no credentials configured) and were skipped rather than guessed at:

| Data source | What it would add |
|---|---|
| **Google Search Console** | Actual indexation status per page (confirms/quantifies the noindex impact), search query performance, manual actions, mobile usability errors, existing click/impression data to prioritize which fixes matter most. |
| **Google Analytics 4** | Real traffic volume, current organic vs. direct vs. referral mix, conversion events (WhatsApp clicks, form submits) to baseline before/after this remediation. |
| **Chrome UX Report (CrUX) / PageSpeed Insights** | Field-measured Core Web Vitals (LCP/INP/CLS) from real Chrome users — attempted via `pagespeed_check.py` but blocked by a shared API key rate limit (240 QPM / 25,000 QPD exceeded), not a credentials gap per se but effectively unavailable in this run. Worth re-running standalone with a dedicated API key. |
| **DataForSEO** | Keyword rankings, search volume for "oficina Dodge/Jeep/Ram São Paulo"-type queries, competitor keyword gap analysis, SERP feature presence, backlink profile size/quality. |
| **Moz / Bing Webmaster backlink APIs** | Domain authority, referring domain count/quality, anchor text distribution — needed to know whether the domain has any off-page equity worth preserving/building on, and to benchmark against local competitor auto shops. |

Without GSC in particular, it's not possible to confirm *how long* the site has carried the noindex tag or how much historical ranking/traffic may have been lost — this should be the very first thing checked once GSC access is available.
