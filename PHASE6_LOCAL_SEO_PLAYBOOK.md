# Phase 6 Execution Playbook: Local SEO (Weeks 3–6)

Apply this playbook to rank for location-intent searches like "iOS developer in Ethiopia" and related city terms.

## Workflow & Branching
- **Branching**: one branch per local asset (e.g., `seo/p6-location-landing`, `seo/p6-gbp-setup`, `seo/p6-citations-batch1`).
- **Artifacts per PR**: Google Business Profile screenshots, NAP sheet, citation submission list, LocalBusiness schema JSON-LD, Lighthouse for location page, and map embed screenshots.
- **Storage**: use `/artifacts/portfolio/` for location landing and GBP assets; `/artifacts/blog/` for any supporting content.
- **Tracker**: maintain `phase6-tracker.md` with NAP, citations, and validation results.

## Core Tasks
- **Location landing**: create `iOS App Development in Ethiopia` page with services, service area, testimonials, CTA, and `ProfessionalService` or `LocalBusiness` schema referencing the canonical `Person` `@id`.
- **Google Business Profile**: set service area (Ethiopia), link to portfolio, add booking/contact links, and post updates (app launches, tutorials).
- **NAP consistency**: define a single Name/City/Email/Phone set; apply across portfolio, blog author bios, directory listings, and structured data.
- **Citations**: submit to local directories, alumni pages, and tech communities; capture URLs and submission dates.
- **Reviews**: encourage LinkedIn/Clutch/Upwork reviews; mirror key quotes on location page with `Review` schema.
- **Map & directions**: embed a map (if applicable) and ensure schema includes `areaServed` and `serviceType`.

## Implementation Details
- **Schema**: Prefer `ProfessionalService` with `serviceType` = "iOS app development"; include `founder` pointing to `Person` `@id`, `areaServed` = Ethiopia, and `sameAs` pointing to GBP URL once live.
- **Meta**: title/description must include name + "iOS developer in Ethiopia"; H1 mirrors title.
- **Internal links**: from homepage, services, and relevant tutorials to the location landing.
- **UTM tracking**: use UTM tags on GBP links to monitor conversions.

## Validation Checklist
- [ ] Location landing live with schema validation (Rich Results Test) and Lighthouse mobile ≥90.
- [ ] GBP verified, filled, and linked; posts published.
- [ ] NAP consistent across portfolio, blog bios, and citations.
- [ ] Citation list captured with URLs and submission dates.
- [ ] Reviews surfaced on landing page with schema.
- [ ] Tracker updated with artifacts and verification steps.

## Reporting
- Weekly (during rollout): track GBP impressions/actions, Search Console location-query metrics, and citation approvals. Update `phase6-tracker.md`.
