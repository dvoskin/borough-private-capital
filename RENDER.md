# Render deployment

## Two sites

- `render-dist/` is Borough Private Capital (private lending and broker partners): Render static site `borough-private-capital`, https://borough-private-capital.onrender.com
- `management-dist/` is Borough Property Management: Render static site `borough-property-management`, https://borough-property-management.onrender.com
- The sites do not link to each other. `render-dist/property-management/` only forwards old links to the management site's Services page.
- Both folders use the same design system; keep `assets/site.css` identical in both.

This repository contains the optimized, mobile-first Borough Private Capital landing page. Render serves `render-dist` from the `main` branch through its global CDN.

Render settings:

- Build: `echo 'Using the committed optimized static build'`
- Publish directory: `render-dist`
- Automatic deploys: enabled on `main`

The page includes paid-acquisition SEO metadata, structured data, broker-focused copy, and a lead inquiry form. The form is prepared to post to the existing Cloudflare D1 intake endpoint used by the private Sites deployment. Confirm the backend CORS allowlist and run a test submission before sending paid traffic; update the endpoint/origin allowlist if you attach a custom domain.

## Design system

- All styling lives in `render-dist/assets/site.css`. Tokens at the top define color, the type scale, spacing, and radius. Pages link that one file; do not add page-level `<style>` blocks. (Measured 09-14: linking it instead of inlining changes Lighthouse mobile by 0 points.)
- Type: system UI sans for body copy, labels, and controls; Georgia for `h1`/`h2` only. Font sizes come only from the scale tokens: display, title, heading, lede, body, small, label.
- Components: `.nav` (full-width sticky header; `.menu` sheet below 1024px), `.hero` + `.media`, `.facts`, `.paths`, `.card` + `.num`, `.checks`, `.accordion`, `.note`, `.callout`, `.cta`, `.form` / `.fields` / `.field`, `.footer`, and `.mobile-cta` (hidden while an element marked `data-cta-end` is on screen).
- Hero images keep `fetchpriority="high"` and must not use `loading="lazy"` or `decoding="async"`. With `decoding="async"`, Chromium left the hero image unpainted inside `.media` until something forced a repaint.

## Deal ticker

- The ticker on the homepage, Private Lending, and Broker Partners pages lists loan types Borough finances by property type and market (`data-status="profiles"`), with no heading and no dollar amounts.
- When real funded deals are available, replace the items in both `.ticker-list` lists (the second copy keeps the loop seamless and is hidden from screen readers), add amounts, add a visible "Recently Funded" label, and set `data-status="live"`. Never show invented deals or amounts as funded.
