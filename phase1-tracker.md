# Phase 1 Tracker (Weeks 1–2)

Use this sheet to record execution status for yohannescodes.com (portfolio) and yohanenswrites.com (blog). Update status daily.

## Status Legend
- ✅ Done
- 🚧 In progress
- ⏳ Blocked (needs decision/access)
- 📝 Not started

## Task Board
| Area | Task | Portfolio | Blog | Owner | PR / Artifact Link |
| --- | --- | --- | --- | --- | --- |
| Access & Baseline | Confirm DNS/CDN/admin access; verify Search Console properties (root + www) exist | 📝 | 📝 |  |  |
| Access & Baseline | Capture baseline Lighthouse (mobile) and WebPageTest; save JSON + summary link | 📝 | 📝 |  | `artifacts/*/lighthouse-baseline.json` |
| Access & Baseline | Export current sitemaps and robots.txt | 📝 | 📝 |  | `artifacts/*/sitemap-urls.txt` |
| Crawl & Audit | Run Screaming Frog crawl; export 404/5xx, redirect chains, duplicate titles/metas | 📝 | 📝 |  |  |
| Crawl & Audit | Prioritized blocker list agreed (5xx/404 > canonical/duplication) | 📝 | 📝 |  |  |
| HTTPS & Canonicalization | Enforce 301s: http→https and non-www→www (or chosen apex) | 📝 | 📝 |  | redirect map screenshot |
| HTTPS & Canonicalization | Add/verify canonical tags on templates (home, About, Services, blog posts, tags) | 📝 | 📝 |  |  |
| HTTPS & Canonicalization | Enable HSTS (`max-age=31536000; includeSubDomains; preload` after verification) | 📝 | 📝 |  |  |
| Performance & Delivery | Enable CDN (HTTP/2/3, Brotli), cache static assets, set Edge TTL | 📝 | 📝 |  |  |
| Performance & Delivery | Optimize hero images to WebP/AVIF; set `loading="lazy"` for below-the-fold media | 📝 | 📝 |  |  |
| Performance & Delivery | Inline critical CSS for hero/nav; defer non-critical JS | 📝 | 📝 |  |  |
| Performance & Delivery | Self-host fonts with `font-display: swap`; preload primary font | 📝 | 📝 |  |  |
| Structured Data | Add `Person` + `WebSite` (portfolio) with shared `@id`; validate via Rich Results Test | 📝 | — |  |  |
| Structured Data | Add `Article` schema on posts referencing shared `Person` `@id`; validate rendered HTML | — | 📝 |  |  |
| Robots, Sitemaps, Indexing | Publish robots.txt allowing public pages; disallow admin; reference sitemaps | 📝 | 📝 |  |  |
| Robots, Sitemaps, Indexing | Generate XML sitemaps and submit to Search Console | 📝 | 📝 |  |  |
| Accessibility & Semantics | Verify one H1 per page, alt text with name + context, labeled nav/CTA | 📝 | 📝 |  |  |
| Validation & Reporting | Re-run Lighthouse after fixes; document before/after deltas | 📝 | 📝 |  | `artifacts/*/lighthouse-after.json` |
| Validation & Reporting | Document redirect checks (http/non-www) and ensure no >1-hop chains | 📝 | 📝 |  | redirect map screenshot |
| Validation & Reporting | Produce one-page Phase 1 report (resolved blockers, remaining issues, next steps) | 📝 | 📝 |  |  |

## Notes
- Keep branches short-lived: one branch per change set (HTTPS redirects, structured data, performance). Merge with artifacts attached.
- Drop screenshots or CSV exports into `artifacts/portfolio/` and `artifacts/blog/` with clear filenames and PR references.
- When a task is done, replace the status and link to the PR/artifact for traceability.
