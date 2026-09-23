# nitesharma.github.io

Portfolio site. Static HTML and CSS — served by GitHub Pages straight from
`main`. No build step, no JavaScript, no third-party requests.

## Files

- `index.html` — the page
- `styles.css` — all styling; design tokens live in `:root`
- `fonts.css` — `@font-face` declarations for the two self-hosted families
- `fonts/` — Darker Grotesque and JetBrains Mono, woff2, latin + latin-ext
- `favicon.svg` — NS mark

## Design

Direction: **brutalism**, built on OpenDesign's `design-systems/brutalism`
package — primary `#DD614C`, text `#111827`, Darker Grotesque for display,
JetBrains Mono for labels, 3px rules, numbered sections, sharp corners.

Typefaces are self-hosted on purpose. The page makes no request to
`fonts.googleapis.com` or `fonts.gstatic.com`, so no visitor's IP is handed to
a third party just to render two typefaces. The latin/latin-ext `unicode-range`
declarations are preserved so the browser picks the right subset per glyph.

## Editing

The page is authored as a variation and generated, so the two stay in sync:

```sh
python3 scripts/build_site.py       # variations/d-brutalist.html -> site/
python3 scripts/fetch_fonts.py site # re-download the self-hosted woff2 files
```

One-off tweaks are fine to make directly in `styles.css`; a change that belongs
in the design itself should go into the variation and be rebuilt.

## History

This replaced a compiled Flutter web build from December 2021 that had no
source in the repo. That build is intact at `7347881` and can be restored with:

```bash
git checkout 7347881 -- .
```