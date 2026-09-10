# Render deployment

This repository contains the optimized, mobile-first Borough Private Capital landing page. Render serves `render-dist` from the `main` branch through its global CDN.

Render settings:

- Build: `echo 'Using the committed optimized static build'`
- Publish directory: `render-dist`
- Automatic deploys: enabled on `main`

The page includes paid-acquisition SEO metadata, structured data, broker-focused copy, and a lead inquiry form. The form is prepared to post to the existing Cloudflare D1 intake endpoint used by the private Sites deployment. Confirm the backend CORS allowlist and run a test submission before sending paid traffic; update the endpoint/origin allowlist if you attach a custom domain.
