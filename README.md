# framestackai.com

Marketing site for **Framestack AI Builder** — a macOS desktop app that is a visual editor
over an ordinary Python project. The canvas is read from the project's folders and imports,
and a node turns green only when the project's own tests run through that code and pass.

This repository holds the website only.

## What's here

A static site — no build step, no dependencies, no framework. One hand-written HTML page
with its CSS and a few lines of JavaScript inlined.

```
index.html          landing page
robots.txt          crawler rules
sitemap.xml         URL list for search engines
favicon.ico         favicon (16 / 32 / 48 px in one file)
favicon.svg         scalable favicon
apple-touch-icon.png
assets/img/         logo and screenshots used by the page
assets/             brand source files (logo and icon variants)
assets/app-screenshots/  original, full-resolution app screenshots
```

## Running it locally

There is nothing to install or compile. Serve the folder over HTTP:

```
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

Opening `index.html` straight from the filesystem mostly works, but the favicon and
apple-touch-icon are referenced with root-relative paths (`/favicon.ico`), so they only
resolve when the site is served from the root of a domain.

## Images

The page uses four files from `assets/img/`:

| File | Size | Used for |
| --- | --- | --- |
| `framestack-logo.svg` | vector | header, hero and footer wordmark |
| `app-window.png` | 2000 × 1300 | hero screenshot, also the Open Graph image |
| `node-detail.png` | 2000 × 1167 | node-colour section |
| `canvas-graph.png` | 2000 × 1029 | how-it-works section |

The `<img>` tags carry explicit `width` and `height` attributes. They set the aspect ratio
the browser reserves while loading, which is what keeps the page from jumping. Replace a
screenshot with a different aspect ratio and you must update those numbers.

The favicon, the apple-touch-icon and `assets/img/framestack-logo.svg` are derived from the
brand files in `assets/` — `framestackai-icon.png` / `.svg` for the icons and
`framestackai-logo-transparent.svg` for the wordmark.

## Editing

The page is self-contained: the design tokens, the stylesheet and the scripts sit inside
`index.html`.

## Deploying

Copy the repository contents to any static host. The site expects to be served from the
root of a domain; if you host it under a subpath, switch the three root-relative icon links
to relative paths.

`sitemap.xml` and the `canonical` / `og:url` tags hardcode `https://framestackai.com` —
update them if the domain changes.

## License

MIT — see [LICENSE](LICENSE). This covers the website source in this repository.
