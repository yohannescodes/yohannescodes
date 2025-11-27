# Phase 7 Execution Playbook: Analytics, Tracking, and Tooling (Weeks 1–ongoing)

Operational guidance for measuring SEO progress across **yohannescodes.com** and **yohanenswrites.com**.

## Workflow & Branching
- **Branching**: one branch per instrumentation set (e.g., `seo/p7-ga4-plausible`, `seo/p7-search-console-sitemaps`, `seo/p7-rank-tracker-setup`).
- **Artifacts per PR**: screenshots of GA4/Plausible goal configs, Search Console property verifications, sitemap submissions, tag manager snippets, and rank-tracker exports.
- **Storage**: place under `/artifacts/portfolio/` or `/artifacts/blog/` as `phase7-ga4-goals.png`, `phase7-sitemaps.txt`, `phase7-rank-tracker.csv`.
- **Tracker**: update `phase7-tracker.md` after each instrumentation change.

## Core Tasks
- **Search Console**: verify root + www for both domains; submit sitemaps; monitor coverage and Core Web Vitals.
- **Analytics**: configure GA4 or Plausible with goals for contact submissions, outbound App Store/GitHub clicks, email clicks, and newsletter signups (if present).
- **Event tracking**: add lightweight events (contact button clicks, code sample copy, CTA scroll depth) via tag manager or inline script.
- **Heatmaps/UX**: enable Hotjar/Clarity on portfolio; exclude logged-in admin sessions if applicable.
- **Rank tracking**: track keywords (name, name + iOS, iOS developer Ethiopia, Swift package terms); export weekly CSVs.
- **Dashboards & reporting**: create a monthly report template with KPIs, goals, and top landing pages; store in artifacts.

## Implementation Details
- Prefer **server-side-friendly** analytics where possible (Plausible) to avoid performance hits; defer scripts to avoid LCP impact.
- **Consent**: ensure cookie/consent banners if using GA4 where required by local regulation; keep copy short and unobtrusive.
- **Sitemaps**: separate XML sitemaps for portfolio and blog; auto-regenerate on deploy.
- **Tagging**: name events consistently (`cta_contact_click`, `case_study_download`, `code_copy`, `gbp_click`).

## Validation Checklist
- [ ] Search Console properties verified; sitemaps submitted and success confirmed.
- [ ] GA4/Plausible goals fire correctly (test via preview/debug mode).
- [ ] Key events tracked (contact clicks, outbound App Store/GitHub, newsletter signups).
- [ ] Heatmaps running on portfolio without harming Core Web Vitals.
- [ ] Rank-tracking export saved with weekly timestamp.
- [ ] Tracker updated with links to dashboards/reports.

## Reporting
- Monthly: export KPI snapshot (impressions, clicks, avg position, conversions) and attach to `phase7-tracker.md`. Note progress on name/location queries specifically.
