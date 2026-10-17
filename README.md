# tastecircle.org (2026-10 site)

The one-page marketing site for TasteCircle, the iPhone app. Static: no framework, no build step.
`index.html` + `assets/` + `/privacy/ /support/ /terms/` + `404.html` + the app's universal-link files.
Design decisions are in `DESIGN.md`. Every claim on the page comes from the app's code, the App Store
listing or `assets/plates/plates.json` (20 real posts).

## Preview
https://stationonemain-source.github.io/taste-circle-site/ (GitHub Pages, noindex). On Pages the site lives
under `/taste-circle-site/`, so `index.html` and the legal pages use relative paths. `404.html`, `addfriend.html`
and `post.html` use root paths because they only matter on the real domain.

## Deploy to Netlify (tastecircle.org)
1. Netlify → the site that serves tastecircle.org → Deploys → drag this folder in (or connect this repo,
   branch `main`, publish directory `/`, no build command).
2. `_redirects` maps `/post/*` and `/addfriend` to the fallback pages; `_headers` sets the AASA content type.
3. Verify with a different tool than the one that deployed: `curl -I` on `/`, `/privacy/`, `/support/`, `/terms/`,
   `/.well-known/apple-app-site-association` (must be `application/json`), `/addfriend`, `/post/x`.

## Remove on go-live
- `<meta name="robots" content="noindex">` in `index.html`, `privacy/`, `support/`, `terms/` (keep it on
  `404.html`, `addfriend.html`, `post.html`).
- The "Preview" section above.

## Do not touch
- `.well-known/apple-app-site-association`: byte-for-byte copy of the live file. Reformatting it can break
  universal links.
- The legal text inside `<article>` on the three legal pages.
- The logo mark PNGs (extracted from the App Store icon). Never redraw.
