# Phase 2 Execution Playbook: On-Page Optimization (Weeks 2–3)

This playbook turns the Phase 2 objectives into concrete tasks for **yohannescodes.com** (portfolio) and **yohanenswrites.com** (blog). Focus on high-intent pages and canonical content that differentiate Yohannes Haile (iOS) from Yohannes Haile-Selassie.

## Workflow & Artifacts
- Branching: use short-lived branches per page/cluster (e.g., `seo/p2-homepage-copy`, `seo/p2-services`).
- PR attachments: updated HTML/meta diffs, rendered structured data validation screenshot (Rich Results), Lighthouse (mobile) HTML report for the page, and before/after copy snippets.
- Storage: keep PR artifacts in `/artifacts/portfolio/` or `/artifacts/blog/` with filenames like `phase2-homepage-lighthouse.html`, `phase2-services-copy.txt`.
- Tracker: update `phase2-tracker.md` with status/owner/PR links.

## Portfolio Site (yohannescodes.com)
### Global Requirements
- Title format: `Page Name | Yohannes Haile — iOS Software Engineer in Ethiopia` (≤60 chars where possible).
- Meta description: 150–160 chars mentioning Yohannes Haile, iOS apps, Swift/SwiftUI, Ethiopia.
- H1: include name + iOS developer; one per page.
- Canonical: absolute URL per page; ensure no trailing-slash drift.
- Internal links: cross-link to Contact and Services from every key page; link to blog for deeper content.
- CTAs: primary "Hire Yohannes" (contact) + secondary "View apps" (portfolio) where relevant.
- Schema: embed `Person` JSON-LD on Home/About; `FAQPage` where FAQs exist; `BreadcrumbList` on case studies.

### Home Page Checklist
- H1 example: `Yohannes Haile — iOS Software Engineer in Ethiopia`.
- Above the fold: value prop + CTA + social proof badges (App Store/LinkedIn/GitHub links).
- Sections: featured apps (with metrics), Swift packages, testimonials, services summary, blog highlights, contact strip.
- Keywords to weave naturally: "iOS developer", "Swift", "SwiftUI", "Ethiopia", "Swift packages".
- Image alt text includes name + app context.
- Artifact: Lighthouse mobile report after changes.

### About Page Checklist
- Long-form bio that differentiates from Yohannes Haile-Selassie; include location and iOS focus.
- Mention shipped apps, Swift packages, and notable collaborations.
- Add disambiguation note ("Not the paleoanthropologist; iOS engineer focused on consumer apps").
- Structured data: `Person` JSON-LD with same `@id` as Phase 1 and `knowsAbout` topics.
- Link to Contact and Services.

### Services Page Checklist
- Target queries: "iOS app developer for hire", "Swift package consulting", "SwiftUI freelance".
- Describe offers: new app builds, package development, performance optimization, release/ASO support.
- Pricing signals: engagement models (fixed, retainer, hourly range); add CTA to request quote.
- Add FAQ section (3–5 questions) with `FAQPage` JSON-LD.

### Case Studies (≥3)
- Template per case study: summary, problem, solution, metrics (LCP improvements, conversion lift, ratings), stack.
- Include CTAs and links back to Services/Contact.
- Add `BreadcrumbList` schema pointing to `/case-studies/` parent.
- Provide unique meta titles/descriptions with industry keywords (e.g., fintech, health, productivity).

### Contact Page
- NAP block (Name, City/Region, Email; phone optional). Keep consistent with other properties.
- Short form with spam protection; include reassurance copy (response time, availability).
- Add FAQ for hiring/logistics; embed `FAQPage` JSON-LD.

### Location Landing Page
- Target: "iOS app development in Ethiopia". Include map embed, service area, industries served, and CTA.
- Schema: `ProfessionalService` or `LocalBusiness` referencing the `Person` `@id` as `founder` or `employee`.

## Blog (yohanenswrites.com)
### Global Requirements
- Title format: `Article Title | Yohannes Haile, iOS Developer`.
- Meta description: 150–160 chars summarizing value + iOS angle.
- Canonical: permalink; ensure tags/categories canonicalize to themselves.
- Internal links: surface portfolio contact/services from top/within posts; link between related posts.
- Schema: `Article` JSON-LD with `author` `@id` from portfolio, `headline`, `image`, `datePublished`, `dateModified`, `wordCount`.

### Blog Taxonomy
- Categories: SwiftUI, Combine, App Store launch, localization, monetization, Swift packages.
- Add intro copy per category; link to cornerstone articles once published.
- Generate tag/category sitemaps if supported.

### Post Template Checklist
- H1 = post title; first 100 words mention Yohannes Haile + iOS/Swift context naturally.
- Include table of contents, code snippets with captions, and optimized images with descriptive alt text.
- Add FAQ section where applicable and mark up with `FAQPage` JSON-LD.
- Add CTA at end (hire/contact or view portfolio) and inline link to relevant package/app.

### Cornerstone Articles (brief outlines)
1) **Complete Guide to Shipping iOS Apps from Ethiopia**
   - Sections: payments/compliance, telecom constraints, testing/distribution from Ethiopia, App Store territories, case study snippet.
   - Target keywords: "iOS apps from Ethiopia", "App Store Ethiopia", "ship iOS apps Africa".
2) **SwiftUI Production Patterns for Consumer Apps**
   - Sections: architecture, performance, accessibility, analytics, release automation; include benchmarks.
   - Target keywords: "SwiftUI production", "SwiftUI performance", "consumer iOS apps".
3) **How to Build and Distribute Swift Packages**
   - Sections: package structure, semantic versioning, doc generation, CI/testing, distribution via Swift Package Index; feature ClarioKit.
   - Target keywords: "Swift package distribution", "Swift package CI", "Swift package index".

## Measurement & Validation
- For each page change, record: before/after Lighthouse mobile scores, meta title/description, H1, and primary keyword target in `phase2-tracker.md`.
- Validate structured data via Rich Results Test (screenshots stored with PR artifacts).
- After deployment, request indexing for updated pages and watch Search Console for coverage.

## Acceptance Criteria per Page/Cluster
- Unique title/meta with name + profession; one H1 with name/iOS context.
- JSON-LD valid and linked to the canonical `Person` `@id`.
- Internal links to Contact/Services and at least one blog link where relevant.
- Images optimized (dimensions specified, lazy for below-the-fold).
- Accessibility: heading hierarchy clean; alt text descriptive; CTA aria-labels set if icon-only.

## Reporting
- Weekly status update: completed pages, pending PRs, validation issues, and upcoming content.
- At end of Phase 2: one-page summary of optimized pages, before/after scores, and prioritized follow-ups for Phase 3 content.
