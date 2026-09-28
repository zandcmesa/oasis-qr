# Oasis QR

Branded, print-safe QR codes for Oasis Creative Studios clients. A single self-contained page — no build step, no backend.

**Live:** enable GitHub Pages (Settings → Pages → Deploy from a branch → `main` / root) and it serves at `https://zandcmesa.github.io/oasis-qr/`.

## What it does

- Encodes links, text, contact cards (vCard), Wi‑Fi, email, phone and SMS
- Styles: code and background colors, transparent background, square / rounded / dot modules, square / rounded / circle eyes, centered logo with knockout
- Frames: label above, label below, or border only, with color and corner radius
- Exports SVG (send this to printers) and PNG at web, social, and 2/4/8/16 in @ 300 dpi
- Scan check: flags low contrast, inverted colors, oversized logos, dense codes, and states a minimum print width
- Brand presets saved in the browser, with JSON export/import

## Per-client presets

Each client gets their own link: `https://zandcmesa.github.io/oasis-qr/?client=cornerstone`

That link loads `clients/cornerstone.json` — presets you manage in this repo — and shows them at the top of the Presets panel with the first one applied automatically. The client can still save their own local presets, kept separately per client slug in their browser.

To add a client:

1. In the app, style a code the way their brand should look and save it as a preset (repeat for each variant they need).
2. Click **Export presets**. The downloaded JSON is the `presets` array.
3. Create `clients/<slug>.json` shaped like `clients/example.json` — a `name` plus that `presets` array — and commit it.

Slugs are lowercase letters, digits and hyphens. Logos are embedded in the JSON as data URIs, so keep them small (an SVG or a ~200 px PNG).

## Dynamic codes (planned)

Codes are static for now. `buildPayload()` in `index.html` is the single seam: a short-link provider (own domain + redirect service or Cloudflare Worker) mints a short URL there, and everything downstream — styling, checks, exports — stays the same.

## Dependencies

Loaded from CDN at runtime: `qrcode-generator` 1.4.4 (cdnjs) and Google Fonts. Everything else is inline.
