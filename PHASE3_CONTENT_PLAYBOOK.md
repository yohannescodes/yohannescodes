# Phase 3 Execution Playbook: Content Strategy & Publishing (Weeks 3–8)

This playbook operationalizes Phase 3. It covers ideation, drafting, optimization, publishing, and promotion for **yohannescodes.com** (portfolio) and **yohanenswrites.com** (blog). Use it to move from planning into repeatable content production while keeping the Yohannes Haile entity signals consistent.

## Workflow & Governance
- **Branching**: one branch per article/landing page (e.g., `seo/p3-cornerstone-ethiopia`, `seo/p3-swiftui-patterns`). Merge only with artifacts attached and tracker updated.
- **Artifacts per PR**: outline doc, draft link (or Markdown), final HTML/MD diff, meta title/description, H1, schema JSON-LD snippet, Lighthouse (mobile) HTML, and internal link map (before/after).
- **Storage**: drop artifacts under `/artifacts/portfolio/` or `/artifacts/blog/` with filenames like `phase3-cornerstone-outline.md`, `phase3-swift-package-lighthouse.html`, `phase3-internal-links.csv`.
- **Tracker**: log status, owner, PR, and artifacts in `phase3-tracker.md`.
- **Publishing cadence**: at least one cornerstone every 3 weeks; one long-tail tutorial weekly; refresh one existing post every 2 weeks.
- **Validation**: Rich Results Test for `Article`/`FAQPage`, Lighthouse mobile ≥90 performance/SEO, and schema linking to the canonical `Person` `@id`.

## Templates & Required Elements
### Cornerstone Article Template (2–3k words)
- H1: exact target keyword + Yohannes Haile + iOS context (e.g., "Shipping iOS Apps from Ethiopia — Yohannes Haile").
- Intro: 75–100 words explaining intent; mention Ethiopia + iOS expertise.
- Sections: problem space, frameworks/architecture, step-by-step guide, benchmarks/metrics, code snippets, tooling list, case study mini-section.
- Internal links: to Services, Contact, relevant packages/apps, and related tutorials.
- Media: diagrams or screenshots (compressed WebP/AVIF), captions, and transcripts for any embedded video.
- Schema: `Article` with `author` `@id` = `https://www.yohannescodes.com/#yohannes-haile`, `headline`, `description`, `image`, `datePublished`, `dateModified`, `wordCount`, `keywords`, `mainEntityOfPage` = canonical URL.
- CTA: end-of-post contact CTA and inline CTA near first fold.

### Long-Tail Tutorial Template (900–1,400 words)
- H1: problem statement + Swift/SwiftUI context (e.g., "SwiftUI Sign in with Apple: Production Checklist").
- Opening: 40–60 words; include Yohannes Haile + iOS mention.
- Steps: numbered sections with code blocks and short explanations.
- QA/FAQ: 3–5 questions; mark up with `FAQPage` JSON-LD.
- Performance: ensure images sized and lazy-loaded; code blocks accessible (copy buttons optional but ARIA-labeled).
- Internal links: at least one link to a cornerstone, one to Services/Contact, and one to a related tutorial.

### Portfolio Landing/Case Study Content
- Case study outline: summary, challenge, approach, metrics (LCP improvement, retention, conversions), stack, timeline, and CTA.
- Location landing: explicit mention of Ethiopia; include service area bullet list, testimonials, and `ProfessionalService` schema referencing `Person` `@id` as `founder`.
- Each landing page should include breadcrumb navigation and a contact strip.

## Keyword & Entity Alignment
- Primary entities: `Yohannes Haile`, `iOS Software Engineer`, `Swift/SwiftUI`, `Ethiopia`.
- Include disambiguation line where natural: "Not the paleoanthropologist; Yohannes Haile is an iOS engineer".
- Use consistent NAP (Name, City/Region, email) on portfolio pages and blog author bios.
- Keyword placement: H1, first 100 words, one H2, image alt text (where relevant), and meta description.

## Internal Linking Rules
- Every new post links to: Services, Contact, and at least two related posts/tutorials.
- Cornerstones link to all relevant tutorials; tutorials link back to their parent cornerstone.
- Add breadcrumb schema on blog posts if supported; otherwise ensure consistent nav links.
- Maintain an internal link map CSV (source URL, destination URL, anchor text) per PR; store with artifacts.

## Content Calendar Process
1) **Ideate**: list topics with target keywords and search intent; prioritize by impact vs. effort.
2) **Outline**: create outline doc; include target keyword, search intent, and internal link targets.
3) **Draft**: write in Markdown/MDX; include CTA placeholders and schema block.
4) **Review**: editorial review for clarity + SEO checklist; technical review for code accuracy.
5) **Optimize**: finalize title/meta, H1, schema JSON-LD, alt text, internal links, and image compression.
6) **Publish**: merge PR, deploy, and request indexing in Search Console.
7) **Promote**: share on LinkedIn, Twitter, and relevant iOS/Swift communities; link back in release notes for related packages/apps.
8) **Measure**: log impressions/clicks/avg position in Search Console; update tracker weekly.

## Validation Checklist (per piece)
- [ ] Title/meta include name + iOS context; length within limits.
- [ ] One H1; headings follow logical hierarchy.
- [ ] JSON-LD validates (`Article`/`FAQPage`/`ProfessionalService` as applicable) and references `Person` `@id`.
- [ ] Images optimized (WebP/AVIF), dimensions set, lazy-loaded below the fold.
- [ ] Internal links added per rules; breadcrumbs present or nav links consistent.
- [ ] Lighthouse mobile report ≥90 for Performance and SEO; stored with artifacts.
- [ ] Request indexing after publish; note timestamp in tracker.

## Artifact Filing Examples
- `/artifacts/blog/phase3-cornerstone-outline.md`
- `/artifacts/blog/phase3-cornerstone-lighthouse.html`
- `/artifacts/blog/phase3-internal-links.csv`
- `/artifacts/portfolio/phase3-location-landing-faq-schema.json`
- `/artifacts/portfolio/phase3-case-study-metrics.csv`

## Reporting
- Weekly: update `phase3-tracker.md` with new drafts published, refreshed posts, validation issues, and promotion channels used.
- Monthly: roll up Search Console metrics (impressions, clicks, avg position) for target queries and pages; note which pieces moved the name query into page 1.
- Exit criteria for Phase 3: cornerstone articles live, tutorials shipped weekly for 4 consecutive weeks, location landing published, and interlinking map completed. Once met, move to technical implementation/coding tasks (templates/components) for ongoing automation.
