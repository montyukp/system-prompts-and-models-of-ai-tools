---
name: seo-site-rebuild
description: Turn a website audit into a full SEO-led redesign and build plan. Use when someone supplies a site audit (Screaming Frog/Lighthouse/PageSpeed/Search Console export, a crawl, a URL, or hand-written notes) and wants the site restructured, rebuilt or redesigned so it ranks and converts — producing a keyword map, URL disposition plan, page blueprints, technical build spec and a phased rollout. Triggers include "audit this site and redesign it", "rebuild my website for SEO", "here's my site audit", "what should the new site look like", "SEO site architecture", "keyword map", "money page".
---

# SEO Site Rebuild

Take an audit of an existing site (or a blank slate) and produce a **redesign that
satisfies the MTU 20-step SEO method** plus a **build plan** someone can execute.

The method is in `references/method.md`. Read it before planning. Every
recommendation you make must trace back to one of its 20 steps — if it doesn't,
cut it.

## Non-negotiables

- **One commercial offer drives the site.** If the brief tries to rank for
  websites + SEO + AI + apps + marketing at once, say so and force a choice
  (Step 1). A new site spread across five offers ranks for none.
- **Never invent evidence.** No fabricated reviews, testimonials, case studies,
  client names, results or search volumes. Where proof is missing, specify a
  clearly-labelled demonstrator/sample project instead (Step 11) and mark it
  `[NEEDS CLIENT INPUT]`.
- **Never invent numbers.** If you have no keyword volume, difficulty or traffic
  data, write `no data` — do not estimate a figure that looks authoritative.
- **Conversion beats word count.** Every page blueprint carries a primary CTA.
  A page that ranks and doesn't convert is a failure (Step 10).
- **One keyword cluster per page.** Splitting `web design leeds` and
  `web designer leeds` across two pages is a defect, not a strategy (Step 8).

## Workflow

Work through these phases in order. Do not skip ahead to page copy — the map
comes first.

### Phase 0 — Intake

Establish these before analysing anything. Ask the user only for what you
genuinely cannot determine; make defensible assumptions for the rest and label
them **Assumption:** in the output.

| Input | Needed for | If missing |
|---|---|---|
| Domain / URL | everything | ask — blocking |
| The audit itself | Phase 1 | ask — blocking, unless it's a greenfield build |
| Primary commercial offer | Steps 1, 9 | propose one from the site, confirm in output |
| Target customer + location | Steps 2, 5 | infer from the site, flag as assumption |
| Current platform + who maintains it | Phase 6 | assume WordPress, flag |
| Search Console / GA access | Steps 3, 16 | proceed without; note the gap |
| Real proof assets (portfolio, reviews, pricing) | Step 11 | mark `[NEEDS CLIENT INPUT]` |

Format-by-format handling is in `references/audit-intake.md`. Accept the audit
in whatever form it arrives: Screaming Frog CSV/XLSX export,
Lighthouse or PageSpeed JSON, a Search Console export, an Ahrefs/Semrush/OpenSEO
report, an agency PDF, a screenshot, or a paragraph of complaints. Parse it.

Optional accelerators when they're available in the session — use them, don't
depend on them: `WebFetch` to read the live pages, the DataforSEO or OpenSEO MCP
tools for real volume/difficulty/SERP data, `mcp__Openseo__run_site_audit` to
generate a crawl when the user has no audit to give. If none are available, run
the whole method on judgement and say plainly which figures are unverified.

### Phase 1 — Normalise the audit

Convert the raw audit into two tables. Nothing else from the audit survives into
later phases.

1. **Findings** — one row per real problem:
   `severity (blocker/major/minor) | issue | affected URLs | which step it breaks | fix`.
   Severity is by business impact, not by what the tool coloured red. A crawler
   warning on a page nobody should keep is a `minor`. Ignore warnings that affect
   nothing (Step 17) and say you're ignoring them.
   Use `assets/findings-template.csv`.
2. **URL inventory** — every existing URL with (`assets/url-disposition-template.csv`):
   `URL | topic | current title/H1 | indexable? | traffic/impressions if known | disposition`.

   Disposition is exactly one of:
   - `KEEP` — on-message, ranks or could; light optimisation only
   - `REWRITE` — right topic, wrong execution
   - `MERGE → <target>` — cannibalising another page (Step 8)
   - `NEW` — no current page serves this intent
   - `RETIRE + 301 → <target>` — off-message or thin
   - `RETIRE + 410` — never redirect junk into a money page just to preserve a URL

Blockers to always look for: noindex/robots blocks on commercial pages, missing
or duplicate titles and H1s, broken internal links, redirect chains, thin or
duplicated service pages, no XML sitemap, mobile failures, slow LCP, missing
alt text, no NAP/local signals, no schema, no visible CTA.

### Phase 2 — Lock the commercial focus (Steps 1–2)

Write, in the output: the one offer organic search must sell for the next 3–6
months, the secondary upsell, the deferred offers, and the narrow customer
profile (location, business size, customer type, problem, desired result).
Everything downstream is judged against this. If the existing site contradicts
it, that contradiction is a Phase 1 finding.

### Phase 3 — Keywords (Steps 5–8)

1. Seed list of **30–50** candidates: service terms × modifiers (location,
   customer type, price/affordability, platform, "freelance", "near me"). Not
   thousands.
2. **Intent test** each promising phrase (Step 6): what page type dominates page
   one — service pages, blogs, directories, comparisons, map pack? Then: can this
   business realistically produce that? If not, park it and say why.
3. **Score** 1–5 on Demand, Commercial fit, Intent, Difficulty. Weight commercial
   fit and intent above raw volume (Step 7). Ten serious local enquiries beat
   5,000 students.
4. Select **10–15 priority keywords** and **map each to exactly one page**
   (Step 8). Group near-duplicate phrasings onto the same page. Split only where
   intent genuinely differs.

Deliver as `keyword-map.csv` using `assets/keyword-map-template.csv`.

### Phase 4 — Architecture

Design the new IA from the keyword map, not from the old menu.

- Flat URLs, one topic each, short and descriptive: `/web-design-leeds/`,
  `/small-business-websites/`, `/website-cost-uk/`.
- Money pages at root level. Supporting articles under `/guides/` or `/blog/`.
- Every cluster article links up to its money page; siblings link to each other
  where useful (Step 14).
- Nav carries the money pages and the primary CTA only. Don't put the blog index
  before the offer.
- Produce a **redirect map** from the Phase 1 dispositions — old URL → new URL,
  301, one hop, no chains.

Deliver the architecture as a tree plus an internal-linking table
(`from page | to page | anchor | why`).

### Phase 5 — Page blueprints

For the money page, follow `references/money-page.md` in full: competitor
teardown of ~5 ranking pages first (headings, offer, pricing visibility, proof,
FAQs, CTA, length, weaknesses), then the H1/H2 skeleton, then the
differentiators competitors cannot copy (Steps 9–11).

For every other page in the map, write a brief using
`assets/page-brief-template.md`: target keyword,
intent, URL, title tag (≤60 chars, with a reason to click), meta description
(≤155 chars), H1, H2 outline, word-count range, internal links in and out,
primary CTA, schema type, and any `[NEEDS CLIENT INPUT]` assets.

Run every blueprint against `references/on-page-checklist.md` (Step 12) before
calling it done.

### Phase 6 — Technical build spec

This is the "solid foundation" half of the ask. Cover, at the level of decisions
rather than essays: platform and theme/stack choice with a reason, hosting and
CDN, performance budget (LCP < 2.5s, CLS < 0.1, INP < 200ms) and how the design
stays inside it, image pipeline (WebP, compressed, descriptive filenames, alt
text), URL and trailing-slash convention, canonical strategy, XML sitemap and
robots.txt, structured data, analytics and consent, accessibility baseline
(WCAG 2.2 AA), forms and lead capture with spam protection, and backup/staging.

Details and the schema templates are in `references/technical-spec.md`.

### Phase 7 — Build plan

A phased plan, each item with owner, effort estimate and dependency:

- **Week 0 — foundations:** Search Console + property verification, Google
  Business Profile, analytics, staging environment (Steps 3–4).
- **Weeks 1–2 — the money page ships first.** Not the homepage. Not the blog.
- **Weeks 3–4 — supporting pages, redirect map, launch, URL inspection**
  (Step 13).
- **Days 30–90 — one strong article per week** (Step 15), the first linkable
  asset (Step 18), lightweight outreach (Step 19).
- **Ongoing monthly:** Screaming Frog crawl (Step 17), Search Console
  queries/pages review with improve-before-you-publish bias (Step 16), AI
  visibility check (Step 20).

Include a **launch checklist** and the ongoing cadence as a table.

### Phase 7b — Hand-off gate

Before a build you produced goes live or leaves your hands, run
`references/handoff-checklist.md`. Gate 1 (truthfulness) is a stop-ship: design
placeholders that were harmless in a mockup — invented reviews and ratings,
plausible-sounding testimonials, stock photos in a "our work" gallery,
accreditation badges the business doesn't hold — become misrepresentation the
moment they sit on a real trading business's domain. Strip them or replace them
with something true, and never soften this to "flag for later".

### Phase 8 — Write the deliverables

Write files to `seo-rebuild/<domain>/`:

| File | Contents |
|---|---|
| `00-summary.md` | Focus decision, top findings, what changes and why, assumptions |
| `01-audit-findings.md` | Findings + URL inventory tables |
| `02-keyword-map.csv` | Scored keywords → pages |
| `03-architecture.md` | Sitemap tree, internal linking, redirect map |
| `04-page-briefs.md` | Money page blueprint + every other page brief |
| `05-technical-spec.md` | Build spec and schema |
| `06-build-plan.md` | Phased plan, launch checklist, ongoing cadence |

Then offer — once, in one line — to publish `00-summary.md` as an artifact for
sharing with the client, and to draft the money page copy as the next step.

## Judgement calls

- **Audit says 300 problems.** Fix what affects crawling, indexing, usability or
  a priority page. List the rest as "accepted" (Step 17).
- **The site is fine, the offer is wrong.** Say it. Restructuring around a
  confused proposition is wasted work.
- **Client wants a rebuild but has traffic.** Preserve it: keep URLs where you
  can, redirect one-to-one where you can't, and never launch without the redirect
  map tested.
- **No proof assets at all.** Ship the money page with a labelled demonstrator
  portfolio and transparent pricing — pricing visibility is itself a
  differentiator most competitors dodge (Step 11).
- **Greenfield, no existing site.** Skip Phase 1's URL inventory, keep every
  other phase.
