# On-Page Checklist (Step 12)

Run against every page brief before it's called done, and every page before it
ships. Fail = fix, not note.

## Content
- [ ] **Title** — target subject + a reason to click. ≤60 chars. Unique sitewide.
- [ ] **H1** — exactly one, matches the page's promise, not identical to the title.
- [ ] **H2/H3** — logical hierarchy, no skipped levels, no headings used for styling.
- [ ] **URL** — short, descriptive, lowercase, hyphenated, no dates or IDs, no stop words.
- [ ] **Meta description** — ≤155 chars, a clear reason to visit. Not keyword soup.
- [ ] **Opening** — states who the page is for and the problem, within two sentences.
- [ ] **One intent per page** — no second keyword cluster smuggled in.
- [ ] **Natural relevance** over keyword density. Read it aloud; if it sounds
      optimised, it is.

## Media
- [ ] Images compressed, WebP where supported, correctly sized (no 3000px hero
      scaled to 800px).
- [ ] Descriptive filenames: `leeds-web-design-portfolio.webp`, not `IMG_4471.jpg`.
- [ ] Alt text describing the image's purpose. Decorative images get `alt=""`.
- [ ] Explicit width/height or aspect-ratio to prevent layout shift.

## Links
- [ ] Internal links to relevant pages, with descriptive anchors (not "click here").
- [ ] Cluster articles link up to the money page.
- [ ] No orphan pages — every page reachable from nav or a linked page.
- [ ] No broken links, no redirect chains, no links to retired URLs.

## Conversion
- [ ] Obvious primary CTA, repeated, consistent wording.
- [ ] Contact route visible without scrolling to the footer.

## Technical
- [ ] Indexable — no stray `noindex`, not blocked in robots.txt.
- [ ] Self-referencing canonical.
- [ ] In the XML sitemap.
- [ ] Relevant schema present and valid (see `technical-spec.md`).
- [ ] Mobile: no horizontal scroll, tap targets ≥44px, text ≥16px.
- [ ] Core Web Vitals within budget on mobile.

## After publishing (Step 13)
- [ ] Search Console → URL Inspection → live test passes.
- [ ] Request indexing where appropriate.
