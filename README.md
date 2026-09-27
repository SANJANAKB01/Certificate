# Sanjana Bhatia — Credential Registry

A single-page website showcasing certificates and competition results, built as one
self-contained HTML file (no build step, no dependencies to install).

## Files

- `certificates.html` — the whole site: markup, styles, and the certificate images
  (embedded directly as base64 so the page works as a single file).

## Viewing it locally

Just double-click `certificates.html`, or open it in a browser:

```
open certificates.html        # macOS
start certificates.html       # Windows
```

No server, build tools, or internet connection required — everything needed is inside
the one file (it does load two Google Fonts online; without internet it falls back to
system serif/mono fonts).

## Hosting it for free

Since it's a single static HTML file, any of these work in a few minutes:

- **GitHub Pages** — push the file to a repo, rename it to `index.html`, enable Pages
  in the repo settings.
- **Netlify / Vercel** — drag and drop the file (or a folder containing it) onto their
  dashboard.
- **Cloudflare Pages** — same drag-and-drop deploy flow.

## Updating content

Everything is in `certificates.html`:

- **Text** (titles, dates, descriptions) — edit directly inside the `<div class="entry">`
  blocks in the `<main>` section.
- **Adding a new certificate** — copy one whole `<div class="entry">...</div>` block,
  update the serial number, text, and swap the base64 image (see below), then bump the
  `CREDENTIALS` count in the header stats.
- **Certificate images** — each `<img src="data:image/jpeg;base64,...">` holds the
  certificate image inline. To swap one, convert your new image to base64
  (e.g. `base64 -w0 your-cert.jpg`) and replace the string between `base64,` and the
  closing quote.
- **Colors/fonts** — all defined as CSS variables at the top of the `<style>` block
  (`--bg`, `--ink`, `--brass`, etc.) and the Google Fonts `<link>` tags in `<head>`.

## Notes

- The page is responsive: certificate images stack below the text on narrow (mobile)
  screens and sit beside the text on wider (tablet/desktop) screens.
- Tapping any certificate thumbnail opens it full-size in a lightbox; tap outside the
  image or press Esc to close.
