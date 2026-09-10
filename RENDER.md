# Render deployment

This repository contains the optimized, self-contained Borough Private Capital site build. Render serves `render-dist` from the `main` branch through its global CDN.

Render settings:

- Build: `echo 'Using the committed optimized static build'`
- Publish directory: `render-dist`
- Automatic deploys: enabled on `main`

The page is SEO- and mobile-ready for broker and investor acquisition campaigns. The Render form posts to the existing Cloudflare D1-backed intake endpoint used by the private Sites deployment. Keep the Render service URL as `https://borough-private-capital.onrender.com` (or update the allowlist in `app/api/inquiries/route.ts` if you choose a custom Render domain) before sending paid traffic.
