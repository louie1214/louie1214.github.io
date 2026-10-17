# louie1214.github.io

Personal professional profile, portfolio, and résumé for **Louis Mancone IV** — network engineer
(IP/MPLS, Metro Ethernet, enterprise services, network automation).

Live at **https://louie1214.github.io/**

## Stack

Deliberately none. Hand-written static HTML and CSS, one small vanilla-JS file, no build step and
no dependencies — GitHub Pages serves the repo root as-is. Editing a file and pushing is the
entire deploy pipeline.

```
index.html                          profile / portfolio (single page)
resume.html                         full résumé, print- and PDF-friendly
404.html                            not-found page
.nojekyll                           serve files verbatim, skip Jekyll processing
assets/
  css/site.css                      design tokens, layout, components, print styles
  js/site.js                        theme toggle, sticky header, scroll reveal, nav highlighting
  Louis-Mancone-IV-Resume.docx      source résumé, linked as a download
```

## Local preview

Any static server works:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

## Publishing to GitHub Pages

The remote is already set to `https://github.com/louie1214/louie1214.github.io.git` — a **user
site**, so the repo name must stay exactly that.

```bash
git push -u origin main
```

Then in the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
branch `main`, folder `/ (root)`. First publish takes a minute or two.

## Conventions

- **Theme** — light and dark are both first-class. Every color is a token on `:root`; dark values
  are redefined under both `@media (prefers-color-scheme: dark)` and `[data-theme="dark"]` so the
  toggle wins in either direction. The choice persists in `localStorage` and is applied in a tiny
  inline script before first paint to avoid a flash.
- **Print** — `resume.html` is designed to print. The `@media print` block at the bottom of
  `site.css` flattens colors, drops chrome, and sets `break-inside: avoid` on cards and entries.
  Print to PDF from the browser rather than maintaining a separate PDF artifact.
- **Content lives in the HTML.** There is no CMS and no data file; edit the markup directly. The
  résumé exists in two places on purpose — `index.html` is the narrative version, `resume.html` is
  the literal one. Update both when a role or date changes.

## TODO

- [ ] Swap the `LM` monogram favicon for a real one if you want something less generic
- [ ] Add a photo to the hero (optional — `assets/img/` exists for it)
- [ ] Ansible Flex is the featured project — refresh its capability list as the app grows
- [ ] Phone number is intentionally **not** on the site — add it to `resume.html` if you want it public
