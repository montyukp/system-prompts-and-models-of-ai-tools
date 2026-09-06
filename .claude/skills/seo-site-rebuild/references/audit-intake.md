# Audit Intake

What to ask for, and what to do with each format.

## Ask for, in priority order

1. The domain.
2. Any existing audit — any format.
3. Search Console access, or an export of Performance → Queries and → Pages
   (last 3–6 months). This is the highest-value input and the one most often
   forgotten.
4. GA4 access or an organic landing-page export.
5. The commercial answer: which single service should organic search sell for
   the next 3–6 months?
6. Real proof assets: portfolio, reviews, pricing, client permission to name them.

## Format handling

| Format | Extract |
|---|---|
| Screaming Frog export | Internal_all tab: status codes, titles, H1s, indexability, word count, depth. Then response codes and redirect chains. |
| Lighthouse / PageSpeed JSON | Core Web Vitals, opportunities. Ignore the composite score; it isn't a ranking factor. |
| Search Console export | Queries at positions 11–30 with impressions = the improve-first list (Step 16). Pages with impressions and no clicks = title/intent problem. |
| Ahrefs / Semrush / OpenSEO report | Ranked keywords, competitor overlap. Treat their "health score" as noise. |
| Agency PDF | Separate genuine findings from upsell. Anything without an affected URL is a claim, not a finding. |
| Screenshot or prose | Take it as the symptom list; verify against the live site. |
| Nothing | Crawl it yourself (`mcp__Openseo__run_site_audit`) or fetch the key pages and audit manually. Say which. |

## Verify against the live site

Tool exports go stale and lie. Before writing findings, check by hand: the
homepage, the main service page, the contact page, and one article — on mobile.
