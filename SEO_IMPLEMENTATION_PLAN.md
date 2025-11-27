# SEO Implementation Plan for Yohannes Haile

## Objectives
- Rank the portfolio (yohannescodes.com) and blog (yohanenswrites.com) on the first page for searches on "Yohannes Haile", "Yohannes Haile iOS developer", and location queries like "iOS developer in Ethiopia".
- Establish clear entity signals that distinguish you from Yohannes Haile-Selassie.
- Build durable organic traffic from developer-focused and consumer app content while protecting reputation.

## Guiding Principles
- Prioritize technical hygiene (fast, crawlable, secure) before link acquisition.
- Make entity alignment explicit across all properties (consistent name, bio, and social links).
- Publish intent-focused content and keep it fresh with a predictable cadence.
- Measure everything: impressions, clicks, position, conversions (contact form, package installs, newsletter signups).

## Immediate Next Steps
If you want to move right now, follow the checklist in `NEXT_ACTIONS.md` (deploy the current static pages, enforce the preferred host/HTTPS variant, validate schema, submit sitemaps, capture Lighthouse baselines, and turn on analytics/rank tracking). Keep artifacts linked from the phase trackers as you go.

## Phase 1: Technical Foundation (Weeks 1–2)
See `PHASE1_EXECUTION_PLAYBOOK.md` for the step-by-step execution checklist for this phase. Track live progress in `phase1-tracker.md` and keep artifacts under `artifacts/portfolio/` or `artifacts/blog/`.
- Branching/PR workflow: open one short-lived branch per change set (HTTPS redirects, structured data, performance). Attach before/after Lighthouse JSON, WebPageTest link, and updated sitemap URLs to the PR.
- **Crawl & audit**: Run Screaming Frog/Serpstat crawl; export 404/5xx, redirect chains, duplicate titles/metas. Fix blockers first.
- **HTTPS & canonicalization**: Ensure HTTPS-only, HSTS, canonical tags on all pages; remove duplicate http/non-www variants.
- **Performance**: Target <1.5s LCP, <100ms TTFB. Use Cloudflare CDN + Brotli, enable HTTP/2/3. Optimize images (WebP/AVIF), lazy-load non-critical assets, inline critical CSS for above-the-fold hero.
- **Structured data**: Add `Person` schema to About page and homepage with exact name, headline ("iOS Software Engineer"), links to GitHub, LinkedIn, App Store, blog, and `sameAs` pointing to both domains. Add `Organization`/`WebSite` schema with `searchAction` for site search. On blog posts, use `Article` schema with author pointing to `Person` entity.
- **Robots/Indexing**: Ensure `robots.txt` allows key sections; submit XML sitemaps (separate for portfolio and blog) to Google Search Console. Add hreflang if localized pages are added later.
- **Accessibility & semantics**: Use proper headings, descriptive alt text (including name + iOS context where relevant), ARIA labels for nav and CTAs.

## Phase 2: On-Page Optimization (Weeks 2–3)
See `PHASE2_ONPAGE_PLAYBOOK.md` for the actionable checklist and content outlines. Track execution in `phase2-tracker.md` with PR and artifact links.
- **Homepage (portfolio)**: H1 "Yohannes Haile — iOS Software Engineer in Ethiopia". Meta title/description include name + iOS keywords. Add CTA to contact. Include featured apps, Swift packages, testimonials, press/mentions.
- **About page**: Long-form bio differentiating from Yohannes Haile-Selassie; mention Ethiopia location, iOS focus, Swift packages, shipped apps. Embed structured data (`Person`).
- **Services page**: Target "iOS app developer for hire", "Swift package consulting"; include pricing models and industries.
- **Case studies**: Create at least 3 detailed case studies (problem, solution, metrics, stack). Optimize for "SwiftUI app case study", "health/fintech iOS app" terms.
- **Contact page**: Short form with spam protection; include NAP (Name, Address, Phone) consistent across properties; add FAQ schema for common queries.
- **Blog taxonomy**: Add category/tag pages for SwiftUI, Combine, App Store launch, localization, and monetization to cluster topical authority.

## Phase 3: Content Strategy (Weeks 3–8)
See `PHASE3_CONTENT_PLAYBOOK.md` for page/article templates, validation, and artifact workflow. Track status in `phase3-tracker.md`.
- **Cornerstone articles** (2–3k words each):
  - "Complete Guide to Shipping iOS Apps from Ethiopia" (include compliance, payments, telecom constraints).
  - "SwiftUI Production Patterns for Consumer Apps" (with code snippets and performance benchmarks).
  - "How to Build and Distribute Swift Packages" (show ClarioKit as example).
- **Long-tail tutorials** (weekly): Focus on specific problems (e.g., "Implementing Sign in with Apple in SwiftUI", "Offline-first Core Data"). Include code gists, Lighthouse-friendly images, and FAQs with FAQ schema.
- **Thought leadership**: Monthly posts on scaling teams, release automation, and App Store optimization.
- **Content refresh**: Quarterly update of top 10 posts; add current iOS version references and new screenshots.
- **Multimedia**: Short Loom videos embedded with transcripts; publish on YouTube with consistent titles/links.

## Phase 4: Entity & Reputation Management (Weeks 2–ongoing)
See `PHASE4_ENTITY_REPUTATION_PLAYBOOK.md` for execution details and `phase4-tracker.md` for progress logging.
- **Consistent identity**: Standardize the signature "Yohannes Haile — iOS Software Engineer (Ethiopia)" across GitHub, LinkedIn, App Store, Stack Overflow, Twitter, Medium.
- **Wikidata/knowledge panels**: Create/update Wikidata item with portfolio/blog links, occupation, location. Pursue Google Knowledge Panel by ensuring `sameAs` coverage and authoritative mentions.
- **Disambiguation content**: Add a short note on About page clarifying not related to Yohannes Haile-Selassie; use structured data `description` to reinforce context.
- **Review acquisition**: Collect testimonials on LinkedIn and Clutch/Upwork (if applicable); embed via schema `Review`.

## Phase 5: Link Building & Digital PR (Weeks 4–12)
See `PHASE5_LINKBUILDING_PLAYBOOK.md` for outreach workflow and `phase5-tracker.md` for targets/placements.
- **Developer backlinks**: Guest posts on iOS/Swift newsletters (iOS Dev Weekly), contribute to open-source projects with links in AUTHORS/README, publish Swift package documentation with links to portfolio.
- **Startup/tech directories**: Submit to Indie Hackers, Product Hunt maker profile, BetaList; ensure consistent NAP and bio.
- **Local signals**: Get listed in Ethiopian tech directories, university alumni pages, and local dev communities. Sponsor/mentor at local meetups; publish recap posts with backlinks.
- **Press**: Pitch case studies to mobile dev podcasts/blogs; issue a press release when releasing a notable package or app.

## Phase 6: Local SEO (Weeks 3–6)
See `PHASE6_LOCAL_SEO_PLAYBOOK.md` for local workflow and `phase6-tracker.md` for execution status.
- **Location pages**: Add a "iOS App Development in Ethiopia" landing page (and city-specific if relevant) with schema `LocalBusiness` or `ProfessionalService`. Include map embed, NAP, service area.
- **Google Business Profile**: Create/optimize with service area, website, and booking/contact links. Post updates with app launches and tutorials.
- **Citations**: Ensure consistent NAP on local directories; monitor with a citation tracker.

## Phase 7: Analytics, Tracking, and Tooling (Weeks 1–ongoing)
See `PHASE7_ANALYTICS_TOOLING_PLAYBOOK.md` for instrumentation steps and `phase7-tracker.md` for verification.
- **Search Console**: Verify both domains (root + www) and submit sitemaps. Monitor coverage, core web vitals, and manual actions.
- **Analytics**: Set up Plausible/GA4 with goals for contact form submissions, email signups, and outbound clicks to App Store/GitHub.
- **Heatmaps & UX**: Use Hotjar/Clarity on portfolio to improve CTA placement.
- **Rank tracking**: Track keywords: ["Yohannes Haile", "Yohannes Haile iOS", "iOS developer Ethiopia", "Swift packages Ethiopia", "ClarioKit"].
- **Reporting cadence**: Monthly SEO report with impressions, clicks, avg position, CTR by page, backlink growth, and content velocity.

## Implementation Checklist (condensed)
- [ ] Enforce HTTPS + canonical tags on both domains
- [ ] Add `Person`, `Organization`, `WebSite`, `Article`, and `FAQ` schema where appropriate
- [ ] Create/optimize key pages: Home, About, Services, Case Studies, Contact, Location landing
- [ ] Publish cornerstone articles + weekly long-tail tutorials
- [ ] Set up Search Console, sitemaps, analytics, and rank tracking
- [ ] Launch backlink campaign (developer sites, local directories, press)
- [ ] Standardize identity across all platforms and add disambiguation note

## Integration Notes
- Prefer static-site generators (Next.js/astro) with MDX for blog; ensure sitemap generation and structured data components.
- Use canonical URLs on blog tags/categories to prevent duplication.
- Automate image optimization and RSS feed submission to Apple News/other aggregators.
- Keep a `content-calendar.md` with publish dates, keywords, and owners; review quarterly based on Search Console data.
