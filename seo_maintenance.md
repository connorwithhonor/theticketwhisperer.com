# SEO Maintenance (Quick 60-Second Checklist)

Use this after major content/design changes.

## 1) Update sitemap date
- File: `sitemap.xml`
- Update each `<lastmod>` value to today's date in `YYYY-MM-DD` format.

Example:
```xml
<lastmod>2026-02-17</lastmod>
```

## 2) Confirm social preview image
- File: `index.html`
- Verify these tags point to the current share image:
  - `og:image`
  - `twitter:image`

## 3) Push and deploy
- Commit and push to `main`.
- Netlify will auto-deploy.

## 4) Force refresh social cache (optional but recommended)
- Facebook Sharing Debugger: https://developers.facebook.com/tools/debug/
- LinkedIn Post Inspector: https://www.linkedin.com/post-inspector/
- Twitter Card Validator: https://cards-dev.twitter.com/validator

## 5) Request reindex (optional)
- Google Search Console URL Inspection: request indexing for homepage.

---
Tip: If no meaningful content changed, you can leave `lastmod` untouched.
