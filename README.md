# framestackai.com

Marketing site for [Framestack AI Builder](https://github.com/ysz7/framestack-ai-builder) — an
open-source visual builder for Python AI apps where the code stays the source of truth.

This repository holds the website only. The builder itself lives in
[ysz7/framestack-ai-builder](https://github.com/ysz7/framestack-ai-builder).

## What's here

A static site — no build step, no dependencies, no framework. Two hand-written HTML
pages with their CSS and a few lines of JavaScript inlined.

```
index.html      landing page
product.html    product page (canvas, node kinds, quick start)
robots.txt      crawler rules
sitemap.xml     URL list for search engines
favicon.ico     favicon (16 / 32 / 48 px in one file)
favicon.svg     scalable favicon for modern browsers
apple-touch-icon.png
assets/img/     screenshots, social preview images, logo
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

Every image reference and its expected size is documented in
[`assets/img/README.txt`](assets/img/README.txt). Two things worth knowing before you
swap one out:

- The `<img>` tags carry explicit `width` and `height` attributes. They set the aspect
  ratio the browser reserves while loading, which is what keeps the page from jumping.
  Replace a screenshot with a different aspect ratio and you must update those numbers.
- The screenshots have a wireframe fallback: if a file is missing, an `onerror` handler
  hides the image and reveals a CSS-drawn placeholder instead of a broken-image icon.

## Editing

Both pages are self-contained: the design tokens, the stylesheet and the scripts sit
inside each file. The two pages share the same token block near the top of `<head>` — if
you change a color or a font there, change it in both.

## Deploying

Copy the repository contents to any static host. The site expects to be served from the
root of a domain; if you host it under a subpath, switch the three root-relative icon
links in both pages to relative paths.

`sitemap.xml` and the `canonical` / `og:url` tags hardcode `https://framestackai.com` —
update them if the domain changes.

## License

MIT — see [LICENSE](LICENSE).
