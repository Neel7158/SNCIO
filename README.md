# SNCIO — sncio.in

Marketing site for **SNCIO** (Supply-Network-Centric Industrial Optimization) — MSME Lean Scheme approved consultants for Gujarat GIDC manufacturers.

**Live:** [www.sncio.in](https://www.sncio.in)

## Overview

This repository contains a lightweight, single-page marketing website served as static files.
There is no build pipeline, framework runtime, or package manager requirement.

## Stack

- `index.html` — complete page markup, styling, and interactions (inline HTML/CSS/JS)
- Google Fonts: DM Sans, Bebas Neue, JetBrains Mono
- Lead form integration via [Formspree](https://formspree.io) endpoint (`xbdqwldn`)
- Hosting via GitHub Pages + custom domain (`CNAME` → `www.sncio.in`)
- `.nojekyll` included to ensure GitHub Pages serves files directly

## Repository structure

| Path | Purpose |
|---|---|
| `index.html` | Primary page content, styles, and scripts |
| `Logo.png` / `Logo_fevicon.png` | Brand assets used in page and metadata |
| `Layout IMG.JPEG` / `Plant Layout.png` | Section imagery |
| `og-image.png` | Social sharing preview image |
| `CNAME` | Custom domain for GitHub Pages |
| `.nojekyll` | Disables Jekyll processing on GitHub Pages |
| `robots.txt` / `sitemap.xml` | Basic SEO crawl/index controls |

## Local development

Serve the directory with any static file server.

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

## Editing guide

- Content updates: edit text directly in `index.html`.
- Styling updates: adjust the inline `<style>` block in `index.html`.
- Interaction updates: adjust the inline `<script>` block in `index.html`.
- Asset updates: replace image files while preserving filenames (or update references in `index.html`).

## Form handling

The lead/contact form currently posts to Formspree form ID `xbdqwldn`.
If this changes, update the form `action` attribute in `index.html`.

## Deployment

Push commits to the `website-0.0` branch.
GitHub Pages is configured to publish from this branch.

## Contact

Neel Shah · neels@sncio.in · +91 98257 22958

## SEO baseline (India-first, scale-ready)

This site should treat `https://www.sncio.in/` as the primary canonical domain for India.
Keep `sncio.com` reserved for the future global site and avoid duplicate content between `.in` and `.com`.

### Immediate priorities

- Keep a single canonical URL for homepage (`https://www.sncio.in/`).
- Keep XML sitemap and robots.txt aligned with live URLs only.
- Add structured data (`ProfessionalService`) with consistent NAP (name, address/area, phone).
- Track conversion clicks for `tel:` and `mailto:` links in analytics.
- Create and verify Google Business Profile for local discoverability in Gujarat.

### Suggested page expansion (next phase)

When ready to move beyond a single-page landing site, add dedicated pages for:

1. Manufacturing Consultancy (`/manufacturing-consultancy/`)
2. Plant Design (`/plant-design/`)
3. Industrial Digitisation (`/industrial-digitisation/`)
4. Location pages for key Gujarat clusters and later pan-India pages

This structure is better for ranking than trying to target all intents from one URL.
