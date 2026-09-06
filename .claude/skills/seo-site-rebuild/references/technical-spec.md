# Technical Build Spec

The foundation the content sits on. Decide each of these explicitly in
`05-technical-spec.md` — a decision with a one-line reason, not an essay.

## Platform

Pick for who maintains it, not for what's fashionable.

| Situation | Recommendation |
|---|---|
| Client edits their own content, small brochure site | WordPress + a lightweight block theme, minimal plugins |
| You maintain it, speed is the differentiator | Static site (Astro/11ty/Next static export) on a CDN |
| Client already on Wix/Squarespace and won't move | Optimise in place; be honest about the ceiling |

Whatever the platform, the SEO essentials are the same and must be verified, not
assumed: editable title and meta description per page, editable H1, clean URLs,
XML sitemap, robots.txt, canonical control, redirect management, schema output,
image optimisation.

Plugin discipline on WordPress: one SEO plugin (Rank Math or Yoast), one caching
layer, one form plugin, one image optimiser. Every additional plugin is a
performance and security liability.

## Performance budget

Measured on mobile, 4G, mid-range device — not on your desktop.

| Metric | Budget |
|---|---|
| LCP | < 2.5s |
| CLS | < 0.1 |
| INP | < 200ms |
| Page weight | < 1.5MB, hero image < 200KB |
| Requests | < 50 |
| Fonts | ≤ 2 families, self-hosted, `font-display: swap`, preloaded |

Design decisions that break the budget get changed at design stage, not
"optimised" afterwards: no carousel heroes, no background video, no third-party
chat widget loaded on first paint, no icon font where SVG works.

## Indexation

- One canonical hostname; all variants (www/non-www, http/https) 301 to it.
- Trailing-slash convention chosen once and enforced.
- Self-referencing canonicals sitewide.
- XML sitemap at `/sitemap_index.xml` or `/sitemap.xml`, auto-updating,
  containing only indexable 200-status canonical URLs. Submitted in Search
  Console (Step 3).
- `robots.txt` allows crawling of CSS/JS, blocks nothing commercial, references
  the sitemap.
- Tag/author/date archives and internal search results: `noindex` unless they
  serve a real purpose.
- Staging site protected by HTTP auth — never `noindex` alone, and never let
  staging settings reach production.

## Structured data

Minimum set, output as JSON-LD, validated in Google's Rich Results Test:

| Page | Schema |
|---|---|
| Sitewide | `Organization` (or `LocalBusiness` where there's a service area), `WebSite` |
| Money / service pages | `Service` + `BreadcrumbList` |
| Pages with an FAQ section | `FAQPage` — only for questions actually on the page |
| Articles | `Article` with author and dates |
| Portfolio / case studies | `CreativeWork` |
| Contact page | `ContactPoint` |

`LocalBusiness` name, address and phone must match the Google Business Profile
character for character (Step 4).

## Analytics and consent

- GA4 with key events defined for the actions that matter: form submit, phone
  click, email click, quote-tool completion.
- Search Console verified, sitemap submitted, GA4 linked.
- UK/EU cookie consent banner that actually gates non-essential tags, and
  doesn't tank CLS or LCP.
- Call and form tracking that preserves NAP consistency — no swapped numbers in
  the markup that contradict the GBP listing.

## Accessibility (WCAG 2.2 AA baseline)

Contrast ≥4.5:1 for body text; visible focus states; keyboard-navigable nav and
forms; labelled form fields; semantic landmarks; alt text; no information
conveyed by colour alone. This overlaps with SEO more than people expect —
semantic structure is the same work.

## Forms and lead capture

Short forms, honeypot + rate limiting rather than a puzzle CAPTCHA, server-side
validation, an autoresponder, and enquiries delivered somewhere that isn't only
a shared inbox. Test the form on the live site after launch — a silently broken
contact form is the most expensive bug on any small-business website.

## Operational

- Staging environment, with a documented deploy path to production.
- Automated daily backups, restore tested once.
- SSL, security headers, automatic updates for the CMS and plugins.
- Uptime monitoring.
- A monthly Screaming Frog crawl scheduled (Step 17).
