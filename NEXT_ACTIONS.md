# Next Actions: Make the SEO rollout real

Use this as the short list of actions to perform now that the planning docs and first templates are in place. Update the trackers as you complete each item.

## 1) Deploy and enforce the preferred host variant
- [ ] Deploy the current static assets for `yohannescodes.com` and `yohanenswrites.com` to your host/CDN.
- [ ] Force HTTPS and your chosen apex/www variant; confirm `301` chains are clean (no double hops).
- [ ] Re-run the curl spot checks from Phase 1: `curl -I http://<domain> | grep -i location` and `curl -I https://<domain>/sitemap.xml`.

## 2) Validate structured data from rendered pages
- [ ] Run Google Rich Results Test on the homepage and one blog page to ensure `Person`, `WebSite`, and `Article` schema are detected.
- [ ] Capture screenshots/exports and drop them under `artifacts/portfolio/` or `artifacts/blog/`.

## 3) Submit sitemaps and verify properties
- [ ] Add root + `www` properties for both domains in Google Search Console.
- [ ] Submit `https://<domain>/sitemap.xml` for each property and confirm status = Success.

## 4) Capture performance baselines
- [ ] Run mobile Lighthouse against the homepage and blog index; save JSON outputs in `artifacts/portfolio/` and `artifacts/blog/`.
- [ ] If available, run a WebPageTest using a mobile profile and log the public link in the trackers.

## 5) Instrument analytics and goals
- [ ] Set up GA4 or Plausible. Create goals for contact form submits, outbound App Store/GitHub clicks, and newsletter signups.
- [ ] Validate events in preview/debug mode; store screenshots/config exports in `phase7-tracker.md` links.

## 6) Start rank tracking
- [ ] Track weekly for these queries: "Yohannes Haile", "Yohannes Haile iOS", "iOS developer Ethiopia", "Swift packages Ethiopia", "ClarioKit".
- [ ] Export CSVs weekly and attach them to the Phase 7 tracker.

## 7) Keep the trackers updated
- [ ] Mark each relevant row in `phase1-tracker.md`–`phase7-tracker.md` with links to artifacts, PRs, or external reports as you complete the above.
- [ ] Note any blockers or follow-ups directly in the tracker comments.
