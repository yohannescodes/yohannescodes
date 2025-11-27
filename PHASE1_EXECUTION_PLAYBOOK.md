# Phase 1 Execution Playbook: Technical Foundation (Weeks 1–2)

This playbook turns the Phase 1 goals into concrete tasks for **yohannescodes.com** (portfolio) and **yohanenswrites.com** (blog). Prioritize fixes that unblock crawling and indexation before polish.

## Workflow notes (do first)
- Create a short-lived branch per change set (e.g., `seo/phase1-https`, `seo/phase1-structured-data`) and open PRs with before/after artifacts.
- For every PR, attach: Lighthouse (mobile) JSON, WebPageTest summary link, updated sitemap URL, and redirect mapping screenshot.
- Track tasks in `phase1-tracker.md` (one line per task with status/owner/link to PR). Store artifacts in `artifacts/portfolio/` or `artifacts/blog/` per site.

## 0) Access & Baseline
- Ensure access to hosting/CDN, DNS, Search Console, analytics, and error logs for both domains.
- Capture benchmarks before changes: PageSpeed/Lighthouse (mobile), WebPageTest, and server response headers for home, About, and a sample blog post.
- Export current sitemaps and robots.txt to compare after updates.

**Per-site task board**
| Site | Owner | Key artifact | Where to store |
| --- | --- | --- | --- |
| yohannescodes.com | | Lighthouse JSON (mobile), redirect map (http/non-www), updated sitemap URL | `/artifacts/portfolio/` |
| yohanenswrites.com | | Lighthouse JSON (mobile), redirect map, updated sitemap URL | `/artifacts/blog/` |

Quick commands to capture baselines:
- `curl -I https://www.yohannescodes.com` (TTFB + headers)
- `curl -I http://yohannescodes.com` (should 301 to HTTPS + www)
- `lighthouse https://www.yohannescodes.com --preset=mobile --output=json --output-path=./artifacts/portfolio/lighthouse-baseline.json`

## 1) Crawl & Audit
- Run Screaming Frog/Serpstat crawl for each domain; export 404/5xx, redirect chains, duplicate titles/metas, missing canonicals, blocked pages.
- Manually test `http`, `https`, `www`, and non-`www` variants to verify redirect behavior. Expected: 301 to `https://www.<domain>/` (or chosen apex) consistently.
- Deliverables: CSV of issues, prioritized list of blockers (5xx/404 > duplicate content > missing canonicals > thin pages).

## 2) HTTPS, Canonicalization, and Security
- Enforce HTTPS with HSTS (at least `max-age=31536000; includeSubDomains; preload` once stable).
- Force a single host variant via 301s (Cloudflare Page Rules/Redirect Rules or web server):
  - `http -> https` (permanent)
  - `non-www -> www` (or inverse, choose one standard)
- Remove mixed content by upgrading asset URLs to `https`. Confirm `Content-Security-Policy` allows required domains.
- Add canonical tags on every template:
  - Portfolio pages: canonical = live URL (avoid trailing slash drift).
  - Blog posts: canonical = permalink; tag/category pages canonicalize to themselves to avoid duplicates.
- Verification commands:
  - `curl -I http://yohannescodes.com | grep -i location` (should return `https://www.yohannescodes.com/`)
  - `curl -I https://yohannescodes.com | grep -i location` (should return `https://www.yohannescodes.com/`)
  - `curl -I https://www.yohannescodes.com/robots.txt` (200)

## 3) Performance & Delivery
- CDN: Enable Cloudflare CDN, HTTP/2 + HTTP/3, Brotli compression, and "Cache Everything" for static assets with sensible TTLs.
- Images: Convert hero/portfolio images to WebP/AVIF; set `<img loading="lazy">` for below-the-fold media; include width/height to prevent CLS.
- CSS/JS: Inline critical CSS for hero + nav; defer non-critical JS; tree-shake vendor bundles. If using Next.js/Astro, enable image optimization and route-level code splitting.
- Fonts: Self-host and use `font-display: swap` to avoid FOIT; preload primary font files if <25kb.
- Targets: LCP < 1.5s (mobile), TTFB < 100ms with CDN edge caching; monitor with Lighthouse CI or WebPageTest.

## 4) Structured Data (JSON-LD)
Add JSON-LD to the portfolio homepage and About page, and ensure blog posts embed `Article` schema referencing the same `Person` entity. Use the **same** `@id` for the `Person` object on both domains. Example (customize URLs and IDs):

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Person",
  "@id": "https://www.yohannescodes.com/#yohannes-haile",
  "name": "Yohannes Haile",
  "jobTitle": "iOS Software Engineer",
  "url": "https://www.yohannescodes.com/",
  "image": "https://www.yohannescodes.com/static/yohannes.jpg",
  "sameAs": [
    "https://www.linkedin.com/in/yohannes-haile/",
    "https://github.com/yohannescodes",
    "https://apps.apple.com/developer/yohannes-haile",
    "https://www.yohannescodes.com/",
    "https://www.yohanenswrites.com/"
  ],
  "knowsAbout": ["iOS development", "Swift packages", "SwiftUI", "App Store shipping", "Ethiopia"]
}
</script>
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "url": "https://www.yohannescodes.com/",
  "name": "Yohannes Haile Portfolio",
  "alternateName": "Yohannes Haile iOS Developer",
  "potentialAction": {
    "@type": "SearchAction",
    "target": "https://www.yohannescodes.com/search?q={search_term_string}",
    "query-input": "required name=search_term_string"
  }
}
</script>
```

`Article` schema snippet for blog posts (reference the same `Person` ID):

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "mainEntityOfPage": "https://www.yohanenswrites.com/posts/<slug>/",
  "headline": "<Post Title>",
  "image": ["https://www.yohanenswrites.com/posts/<slug>/cover.jpg"],
  "datePublished": "2024-01-15",
  "dateModified": "2024-01-16",
  "author": {
    "@id": "https://www.yohannescodes.com/#yohannes-haile"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Yohannes Codes",
    "url": "https://www.yohanenswrites.com/",
    "logo": {
      "@type": "ImageObject",
      "url": "https://www.yohanenswrites.com/static/logo.png"
    }
  }
}
</script>
```

Validation steps:
- Run [Rich Results Test](https://search.google.com/test/rich-results) for both domains after deployment.
- For SSR/static sites, validate the rendered HTML (not just the source template) to ensure JSON-LD is not stripped by hydration.

- On blog posts, add `Article` schema with `author` referencing the `Person` `@id`, `datePublished`, `dateModified`, `headline`, `image`, `wordCount`, and canonical URL.
- Validate structured data via Rich Results Test and Schema.org validator after deployment.

## 5) Robots, Sitemaps, and Indexing
- Robots: Allow key paths; disallow admin/cms if present. Example for both domains:
  - `User-agent: *`
  - `Disallow: /admin` (adjust if no admin)
  - `Allow: /`
  - `Sitemap: https://www.yohannescodes.com/sitemap.xml`
  - `Sitemap: https://www.yohanenswrites.com/sitemap.xml`
- Sitemaps: Generate separate XML sitemaps per site; ensure they include canonical URLs only and stay <50k URLs / <50MB. Regenerate on publish.
- Submit sitemaps to Google Search Console (both root and www properties) and request indexing for key pages after technical fixes.
- Quick checks: `curl -I https://www.yohannescodes.com/sitemap.xml` (200 + `Content-Type: application/xml`); same for blog. Verify Search Console shows `Success` for sitemap fetch.

## 6) Accessibility & Semantics
- Ensure one H1 per page with name + profession/location where relevant.
- Add descriptive alt text for headshots/app screenshots (include "Yohannes Haile" + app context when natural).
- Label nav, main, and footer landmarks; provide `aria-label` for CTAs like "Hire Yohannes" or "View portfolio".
- Verify color contrast meets WCAG AA; ensure focus states are visible.

## 7) Validation & Reporting
- After fixes, rerun Lighthouse (mobile) and capture before/after scores for performance, accessibility, SEO, and best practices.
- Document redirects (http→https, non-www→www) and verify no redirect chains >1 hop.
- Create a one-page report summarizing resolved blockers, remaining issues, and next steps for Phase 2.

## Quick Checklist
- [ ] HTTPS-only with HSTS and consistent host redirects
- [ ] Canonical tags on all templates; no duplicate variants
- [ ] WebPageTest/Lighthouse scores recorded pre/post
- [ ] JSON-LD for Person, WebSite, Organization; Article on blog posts
- [ ] Robots.txt + XML sitemaps live and submitted to Search Console
- [ ] Lazy-loaded optimized images; critical CSS + deferred JS
- [ ] Alt text, heading structure, and ARIA labels verified
- [ ] One-page validation report delivered
