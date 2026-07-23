# theticketwhisperer.com

## Deploy — MANUAL Netlify CLI (git push does NOT deploy)
- **Netlify site ID:** `d5d1dfc9-65d8-41ef-b81f-5cd15228ff3f`
- This repo has **no** `.github/workflows/deploy.yml` and **no** root `netlify.toml`, so there is
  no git-connected build. Pushing to GitHub saves the source and changes nothing on the live site.
- **Deploy = full-site atomic replace.** A partial or stale folder WIPES what is live. Always
  deploy the COMPLETE tree.

```
netlify deploy --prod --site d5d1dfc9-65d8-41ef-b81f-5cd15228ff3f --dir <complete-folder>
```

Stage first, excluding repo-only files:

```
robocopy . <stage> /E /XD .git .github .netlify node_modules /XF CLAUDE.md README.md seo_maintenance.md
```

- **Ignore `.netlify/netlify.toml`.** It is CLI-generated local state with a stale
  `command = "npm run build --prod"` and a `dist/` publish path. There is no `package.json`
  and no `dist/`. It is not the build config, do not act on it.

## PHASE 0 before any deploy
Count what is live and confirm this repo contains all of it. The site is a single-page
`index.html` plus `/blog/`. Verified 2026-07-23: repo is a complete mirror of live.

## Blog
- Pattern: `blog/<slug>/index.html` + `og.png` in the same folder, self-contained styles using
  the site tokens (`--primary:#002366`, `--accent:#FFD700`, Inter + Oswald).
- Add a post: create the folder, insert one `<a class="bm-card">` into `#bm-post-grid` in
  `blog/index.html` (newest first), add the `<url>` to `sitemap.xml`.
- Build to `connor-palace/standards/CONTENT-BUILD-STANDARD.md`. Gate: zero em dashes,
  valid JSON-LD, one H1, OG card present, CalDRE disclosure in the footer.

## Content rules specific to this site
- **California citations only.** Say so on every page.
- **Not legal advice.** Connor is a retired LAPD motor officer, not an attorney. Every post
  carries the not-legal-advice, California-only, and results-not-guaranteed disclaimers.
- Do not promise that officers fail to respond. That is not a strategy and we do not sell it.

## History
- **2026-07-23:** `blog.theticketwhisperer.com` no longer resolves. Removed it from
  `sitemap.xml`, from the footer "The Blog" link on both pages, and from the homepage
  `sameAs` array. The blog lives at `/blog/`.
