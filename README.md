# The Liberal Manifesto — site

Static, no build step, no framework. Four pages:

- `index.html` — auto-redirects to `/he/`, `/ar/` or `/en/` based on the visitor's browser language (falls back to a manual chooser if JS is off).
- `en/index.html` — English version.
- `he/index.html` — Hebrew version, RTL.
- `ar/index.html` — Arabic version, RTL (Amiri for the text and Noto Kufi Arabic Light for the lead-ins, since Bellefair/Frank Ruhl Libre have no Arabic).
- `assets/style.css` — shared styling.

## Font note

The Hebrew source doc uses **FrankRuehl**. FrankRuehl itself isn't licensed for web embedding, so both pages use **Frank Ruhl Libre** — Google's free, open-source revival of the same typeface, with full Hebrew *and* Latin support. Loaded from Google Fonts, zero cost, and it means both language versions share one typographic identity instead of two mismatched fonts.

## Background

Recreated as a layered CSS gradient + subtle grain texture (no image file), so there's no extra asset to host or load — matches the aged-parchment tone of the reference you showed, at effectively zero weight/cost.

## Deploying for ~free (Cloudflare Pages)

1. Push this folder to a GitHub repo (or drag-and-drop the folder directly in the Cloudflare dashboard — no git required).
2. Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** → connect the repo (or direct upload). Framework preset: **None**. Build command: none. Output directory: `/` (the repo root).
3. Deploy — you get a free `*.pages.dev` URL immediately to preview.
4. **Domain:** register `theliberalmanifesto.co.il` through an ISOC-IL accredited registrar (e.g. domainthenet, Bezeq International, or similar — roughly ₪70–100/year, the only real cost in this whole setup). When choosing a registrar, confirm it lets you point nameservers elsewhere ("NS delegation") — not all Israeli registrars allow this by default.
5. In Cloudflare, add `theliberalmanifesto.co.il` as a zone (Cloudflare's free plan covers DNS + SSL), then point the registrar's nameservers at Cloudflare.
6. In the Pages project → **Custom domains**, add `theliberalmanifesto.co.il`. Root will auto-redirect to `/he/` or `/en/`; both are already real paths so `theliberalmanifesto.co.il/he` and `.../en` work directly too.

Total ongoing cost: just the annual `.co.il` registration. Hosting, SSL, and CDN are free on Cloudflare Pages' free tier.
