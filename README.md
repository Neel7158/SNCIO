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
