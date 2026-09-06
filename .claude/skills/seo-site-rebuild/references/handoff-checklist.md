# Client Hand-Off Gate

Run before a site built for a client goes live or leaves your hands. Anything in
**Gate 1** is a stop — it doesn't ship until it's cleared, regardless of deadline.

## Gate 1 — Truthfulness (stop-ship)

Placeholder content that was fine in a design system becomes a
misrepresentation the moment it sits on a real, named, registered business.

- [ ] **No invented reviews, ratings or review counts.** "4.9/5 from 200+
      reviews" is a factual claim about a real trading business. If the reviews
      don't exist, the section comes out. Replace with a "be our first review"
      prompt and a link to the Google Business Profile.
- [ ] **No invented testimonials or client names.** Including "realistic"
      placeholder quotes attributed to plausible-sounding people.
- [ ] **No invented case studies, job counts, "years in business", or
      "X customers served"** unless the owner has confirmed the number.
- [ ] **No stock photography presented as the client's own work.** Pexels/Unsplash
      images in a "our recent jobs" gallery are a claim, not a placeholder.
      Either get real photos or reframe the section so it doesn't claim authorship.
- [ ] **No accreditation logos the business doesn't hold** (Gas Safe, Which?
      Trusted Trader, TrustMark, CIPHE, manufacturer-approved installer badges).
      Each one is verifiable by a customer in about ten seconds.
- [ ] **No brand/manufacturer logos** without confirmation the business actually
      works with them.
- [ ] **Service areas are confirmed, not guessed.** Naming towns the business
      doesn't cover generates wasted enquiries and looks like spam.

In UK terms, invented reviews and unheld accreditations on a live commercial
site engage the Consumer Protection from Unfair Trading Regulations and, for
fake reviews specifically, the Digital Markets, Competition and Consumers Act
2024. Practically: it's the client who carries that risk, from a site you built.
Don't hand it over.

## Gate 2 — Legal and regulatory identity

- [ ] Registered company name and number shown (footer is conventional) and
      matching Companies House exactly.
- [ ] Registered office address correct and current.
- [ ] VAT number if VAT-registered.
- [ ] **Trade registration numbers displayed and correct** — for gas work, the
      Gas Safe Register number, which customers can and do check against the
      register. "Gas Safe registered" as bare text with no number is weaker than
      the number itself.
- [ ] Privacy policy, and a cookie banner that genuinely gates non-essential tags.
- [ ] Contact form privacy notice / lawful basis for the data collected.
- [ ] Terms of service or terms of business if the site takes bookings or payment.

## Gate 3 — NAP consistency

One canonical set of name, address, phone. Identical, character for character,
across: the site body, the footer, `LocalBusiness` schema, the Google Business
Profile, and every directory listing.

- [ ] One address only — no contradiction between contact text, embedded map and
      schema.
- [ ] Phone numbers correct, formatted consistently, and `tel:` linked.
- [ ] Email correct and `mailto:` linked (watch for malformed addresses like
      `info@www.domain.co.uk`).
- [ ] Opening hours match the Google Business Profile.
- [ ] Address re-confirmed with the owner within a week of launch if they've
      flagged a possible move.

## Gate 4 — Placeholder and template-leftover sweep

Grep the build for these before every hand-off:

```
lorem|ipsum|placeholder|example\.com|TODO|FIXME|Your Company|Lorem
href="#"|href=""|localhost|127\.0\.0\.1|staging\.|\.test/
pexels|unsplash|shutterstock|istockphoto
```

- [ ] No dead `href="#"` nav items.
- [ ] No links pointing at a different client's site or the template's demo
      content.
- [ ] No leftover theme/agency credit unless the client agreed to it.
- [ ] Favicon, OG image and page titles are the client's, not the template's.

## Gate 5 — It actually works

- [ ] **Submit the contact form on the live site and confirm the email arrives.**
      Then check the spam folder. This is the single most common silent failure.
- [ ] Autoresponder fires and reads correctly.
- [ ] Every phone and email link opens correctly on a real phone.
- [ ] Every internal link resolves — no 404s, no redirect chains.
- [ ] Custom 404 page exists and links back into the site.
- [ ] Test on a real mobile device, not just a resized browser window.

## Gate 6 — SEO foundation

- [ ] Unique title and meta description per page (or per section on a one-pager).
- [ ] Exactly one H1; logical heading order.
- [ ] Indexable: no stray `noindex`, robots.txt not blocking, staging auth removed.
- [ ] Self-referencing canonical.
- [ ] XML sitemap present and submitted to Search Console.
- [ ] `LocalBusiness` schema present, valid in the Rich Results Test, and
      containing **no `aggregateRating` unless real reviews exist**.
- [ ] Images compressed, descriptive filenames, alt text.
- [ ] Old site's URLs 301-mapped to the new ones, one hop, tested.
- [ ] Core Web Vitals within budget on mobile.

## Gate 7 — Agency credit

Standard on every build: a single credit line in the footer. It is one of the
few free lead sources an agency has — someone likes a site, scrolls down, finds
out who made it. Four conditions, all of them non-optional.

- [ ] **Agreed in writing before the build starts.** Put it in the proposal or
      contract, not sprung on the client at hand-over. Suggested wording:

      > MTU Projects retains a small credit link in the website footer, reading
      > "Website by MTU Projects". It can be removed at any time on request.

      Some agencies discount the build for keeping it, or charge a one-off fee
      to remove it. Either turns it into an explicit trade rather than an
      assumption. Decide the policy once and apply it consistently.

- [ ] **Brand anchor text only.** The link text is the agency name — nothing
      else:

      ```html
      <p class="site-credit">
        Website by <a href="https://mtuprojects.co.uk/" rel="noopener">MTU Projects</a>
      </p>
      ```

      Never keyword anchors such as "web design Leeds" or "website designer
      Leeds". The same keyword-anchored link repeated in the footer of every
      client site is a textbook link-scheme pattern: Google devalues it at best
      and counts it against the agency at worst. The temptation is strongest
      when those are exactly the phrases the agency is trying to rank for —
      resist it. A brand-anchored credit is legitimate attribution and holds up.

- [ ] **Visually modest.** One line of small text beside the copyright, in the
      muted footer colour. No logo, no styling that competes with the client's
      own branding. It is a credit, not an advertisement.

- [ ] **Removed on request, immediately and without argument.** It is the
      client's website.

Also check the reverse: **remove the previous agency's credit** if you have
rebuilt their site. Leftover "Website designed by <old agency>" lines are common
in rebuilds and pass link equity to a competitor from a site you now maintain.

## Gate 8 — Hand-over pack

The client owns their business's infrastructure. Hand it over in writing:

- [ ] Domain registrar access, in the client's name, with the client as registrant.
- [ ] Hosting and CMS logins, client as administrator.
- [ ] Google Search Console and GA4, owned by the client's Google account with
      you added as a user — not the reverse.
- [ ] Google Business Profile ownership confirmed as the client's.
- [ ] Backups configured, and one restore tested.
- [ ] A short "how to edit your site" doc or screen recording.
- [ ] What's outstanding, in writing: every `[NEEDS CLIENT INPUT]` item still
      unresolved, and what happens if it's never supplied.
