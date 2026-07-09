# Action Plan — Oficina AG3 SEO Remediation

Prioritized by impact. Do the Critical section first — nothing else matters for organic visibility until it's done.

---

## CRITICAL (do this week)

### 1. Remove `noindex` from all pages
- **Issue:** Home, Contato, and Projetos all serve `<meta name="robots" content="noindex">`. The site cannot appear in Google/Bing search at all right now.
- **Fix:** In the Hostinger/Zyro website builder, find the site-wide or per-page SEO/indexing setting (often under Site Settings → SEO, or a per-page "Hide from search engines" toggle) and disable it. This is very likely a leftover from initial setup/staging that was never turned off at launch.
- **Effort:** 15 minutes.
- **Verify:** Re-render each page and confirm `<meta name="robots">` is gone or set to `index, follow`. Then submit the homepage for indexing via Google Search Console once access exists.

### 2. Populate `sitemap.xml`
- **Issue:** `sitemap.xml` is served (200 OK) but contains zero URL entries.
- **Fix:** Regenerate via the builder's sitemap setting (usually automatic once pages are unhidden from search), or manually list the 3 current URLs plus any new service pages created in Phase 2 below.
- **Effort:** 15–30 minutes (may auto-resolve once #1 is fixed, since builder sitemaps are often tied to the same indexing toggle).

### 3. Add `AutoRepair` schema (JSON-LD) to every page
- **Issue:** Zero structured data anywhere on the site.
- **Fix:** Add a single `AutoRepair` JSON-LD block (template already drafted in `FULL-AUDIT-REPORT.md` Section 4) to the site's global `<head>` (or footer, via the builder's custom code/embed feature). Requires the owner to confirm: exact opening hours, and whether the Facebook/TikTok handles found in the footer are the current official accounts (for `sameAs`).
- **Effort:** 1–2 hours, mostly gathering the missing facts (hours) from the owner.

---

## HIGH (do this month)

### 4. Build dedicated service pages
- **Issue:** No individual URLs for services (oil change, Jeep/Ram/Chrysler diagnostics, suspension work, etc.) — per Whitespark's local ranking studies, this is the single highest-leverage on-page local SEO factor, and it's currently entirely missing.
- **Fix:** Create 4–8 service pages (e.g. `/manutencao-jeep-sao-paulo`, `/revisao-dodge-ram`, `/diagnostico-eletronico-chrysler`), each with 300+ words targeting a specific service + brand + city combination, its own title/meta description, and a `Service` schema block nested under the `AutoRepair` entity.
- **Effort:** 4–6 hours per page including content writing (or delegate content drafting).

### 5. Add visible phone number + `tel:` click-to-call link
- **Issue:** No plain-text phone number or `tel:` link anywhere; the number only exists inside WhatsApp URL parameters (and inconsistently formatted — one instance has a stray hyphen: `551194278-2852` vs the correct `5511942782852`).
- **Fix:** Add a visible `+55 11 94278-2852` with `<a href="tel:+5511942782852">` in the header/footer and Contato page. Normalize the WhatsApp link to use the clean digits-only number everywhere.
- **Effort:** 30 minutes.

### 6. Add opening hours to the site + schema
- **Issue:** Opening hours are published nowhere — not visible to users, not in schema.
- **Fix:** Get exact hours from the owner (input needed — NEW DATA-style question), display on Contato page, add to `openingHoursSpecification` in the schema from item #3.
- **Effort:** 30 minutes once hours are provided.

### 7. Rewrite title tags and meta descriptions
- **Issue:** All 3 titles (71–86 chars) and meta descriptions (173–245 chars) exceed Google's display limits and will be truncated; the brand name is redundantly repeated in the home title.
- **Fix:** Tighten to ≤60 char titles / ≤155 char descriptions, lead with the most distinctive keyword (e.g. "Oficina Jeep, Dodge, Ram e Chrysler em SP | Oficina AG3").
- **Effort:** 1 hour.

### 8. Fix www / non-www duplicate serving
- **Issue:** `oficinaag3.com.br` (no www) returns 200 with identical content instead of 301-redirecting to `www.oficinaag3.com.br`. Canonical tags currently paper over this, but a proper redirect is the standard fix.
- **Fix:** Configure a host-level 301 redirect in Hostinger DNS/domain settings from apex to www (or vice versa, whichever is the intended canonical host — currently www, per the existing canonical tags).
- **Effort:** 30 minutes (DNS/hosting panel config).

---

## MEDIUM (do this quarter)

### 9. Add H2 structure and fix heading hierarchy
- **Issue:** No H2s exist anywhere on the site; content jumps H1 → H3. Several H3s are semantically empty (bare "®" symbols, footer copyright text tagged as headings).
- **Fix:** Restructure each page so major sections (Sobre Nós, Serviços, Projetos, Contato) use H2, with H3 reserved for genuine subsections. Remove heading tags from decorative "®" marks and footer copyright text.
- **Effort:** 2–3 hours across all pages.

### 10. Expand thin content
- **Issue:** Home 257 words, Contato 112, Projetos 98 — thin for a competitive local vertical.
- **Fix:** Expand "Sobre Nós" to properly leverage the "since 1991" trust signal (certifications, technician experience, brand-specialization detail); expand Projetos into real before/after case studies with specifics (make/model, problem, work performed, outcome); add an FAQ section (also serves AI Search Readiness).
- **Effort:** 3–5 hours content writing.

### 11. Add customer testimonials with attribution
- **Issue:** Only one unattributed quote exists.
- **Fix:** Gather 3–5 real customer testimonials with name, vehicle model, and (ideally) a link to/mention of the Google review it came from; mark up with `Review`/`aggregateRating` schema once enough exist (don't fabricate a rating — pull real numbers from GBP once available).
- **Effort:** Ongoing — dependent on owner outreach to past customers.

### 12. Add `llms.txt`
- **Issue:** Doesn't exist (404).
- **Fix:** Create a simple `llms.txt` at the root summarizing the business, services, and linking to key pages, once the service pages from item #4 exist (no point doing this before there's real content to point to).
- **Effort:** 1 hour, after item #4.

### 13. Add alt text to all images
- **Issue:** ~16 of 18 homepage images have empty/missing alt text (brand logos, hero images, project photos).
- **Fix:** Write descriptive alt text for every image (e.g. "Jeep Wrangler na Oficina AG3 durante revisão" instead of blank).
- **Effort:** 1–2 hours.

---

## LOW (opportunistic / nice-to-have)

### 14. Investigate the recurring 404 console error
- **Issue:** Every page fires one unidentified `Failed to load resource: 404` — likely a JS-injected tracking pixel, not a page/asset in the static HTML (all 30 static resource URLs checked returned 200/301/302).
- **Fix:** Open Chrome DevTools → Network tab on the live site, filter to failed (red) requests, identify the exact URL, and either fix or remove it.
- **Effort:** 30 minutes.

### 15. Verify and standardize social profile handles
- **Issue:** Facebook handle (`chrysleragtres.ltda`) and TikTok handle (`oficina.aglll`) don't match the "AG3"/"AGIII" branding used elsewhere on-site — worth confirming these are current, owned, active accounts before wiring them into schema `sameAs`.
- **Effort:** 15 minutes to check, longer if accounts need to be updated/rebranded.

### 16. Get a real Lighthouse/PageSpeed run once API access is available
- **Issue:** `pagespeed_check.py` was rate-limited in this environment; only rough Playwright render-time proxies (6.4–8.8s, not a true load-time metric) are available.
- **Fix:** Re-run `pagespeed_check.py` with a dedicated Google API key, or run Lighthouse directly in Chrome DevTools, to get real LCP/INP/CLS numbers and confirm whether performance is actually a problem.
- **Effort:** 15 minutes once a key/quota is available.

---

## Suggested Sequencing

1. **Week 1:** Items 1–3 (Critical) — unblocks indexing entirely.
2. **Weeks 2–4:** Items 4–8 (High) — service pages, click-to-call, hours, titles/descriptions, www redirect.
3. **Month 2–3:** Items 9–13 (Medium) — content depth, headings, testimonials, alt text, llms.txt.
4. **Ongoing:** Items 14–16 (Low) as time allows.

Once Google Search Console access is set up, re-check indexation status weekly during the first month to confirm the noindex fix actually took effect and pages are being crawled/indexed.
