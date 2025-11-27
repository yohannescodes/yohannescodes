# Phase 4 Execution Playbook: Entity & Reputation Management (Weeks 2–ongoing)

Use this playbook to strengthen "Yohannes Haile" entity signals, disambiguate from Yohannes Haile-Selassie, and build trust across all surfaces. Applies to **yohannescodes.com**, **yohanenswrites.com**, and external profiles.

## Workflow & Branching
- **Branching**: one branch per change set (e.g., `seo/p4-wikidata`, `seo/p4-about-disambiguation`, `seo/p4-kp-sameas`).
- **Artifacts per PR**: before/after screenshots of About page disambiguation block, JSON-LD snippets, list of `sameAs` URLs, Wikidata diff link, and Search Console entity screenshot if available.
- **Storage**: save under `/artifacts/portfolio/` or `/artifacts/blog/` with filenames like `phase4-disambiguation-block.png`, `phase4-person-schema.json`, `phase4-wikidata-proof.md`.
- **Tracker**: log status/owners/PRs/artifacts in `phase4-tracker.md`.

## Core Tasks
- **Consistent identity**: update headers/footers, author bios, and schema to use the exact string "Yohannes Haile — iOS Software Engineer (Ethiopia)".
- **Disambiguation**: add a short note on About pages clarifying you are not Yohannes Haile-Selassie; include in schema `description`.
- **Structured data hardening**: unify `Person` `@id` across portfolio/blog; add `sameAs` to LinkedIn, GitHub, App Store, YouTube, Twitter, Medium, Wikidata (once created).
- **Wikidata/Knowledge Panel**: create or update Wikidata item with occupation, country, portfolio/blog links, and social handles; link to both domains via `sameAs`. If possible, add a profile photo with proper licensing.
- **Review acquisition**: collect testimonials on LinkedIn/Clutch/Upwork; embed `Review` schema on portfolio services/case studies pages with rating or recommendation text.
- **Profile alignment**: standardize bios and headline across LinkedIn, GitHub, App Store developer page, Twitter, and Stack Overflow. Ensure all link back to portfolio/blog.
- **Monitoring**: set Google Alerts for your name; log notable mentions/backlinks monthly.

## Implementation Details
- **Person schema**: use a canonical `@id` such as `https://www.yohannescodes.com/#yohannes-haile`. Reference this in `Article`, `FAQPage`, and `ProfessionalService` schemas.
- **Organization schema**: if using `ProfessionalService`, set `founder` to the `Person` `@id`, include NAP details, and Ethiopia as `areaServed`.
- **Disambiguation copy example**: "This site belongs to Yohannes Haile, an iOS software engineer based in Ethiopia (not related to the paleoanthropologist)." Place near bio and in FAQ.
- **Imagery**: reuse the same headshot across sites; include `image` and `thumbnailUrl` fields in schema with the canonical URL.

## Validation Checklist
- [ ] `Person` schema identical on portfolio/blog with matching `@id` and `sameAs` URLs.
- [ ] Disambiguation note present on About pages and reflected in schema `description`.
- [ ] Wikidata item created/updated with correct links and occupation.
- [ ] Reviews/testimonials embedded and marked up where available.
- [ ] Profiles (LinkedIn, GitHub, App Store, Twitter, Stack Overflow) share the same headline and links.
- [ ] Artifacts stored and tracker updated.

## Reporting
- Monthly: note new backlinks/mentions related to your name and whether Google SERPs surface the correct entity panel. Log changes in `phase4-tracker.md`.
