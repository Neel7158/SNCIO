# SNCIO — sncio.in

Marketing site for **SNCIO** (Supply-Network-Centric Industrial Optimization) — MSME Lean Scheme approved consultants for Gujarat GIDC manufacturers.

**Live:** [www.sncio.in](https://www.sncio.in)

## Stack

Single-page static site. No build step.

- `index.html` — full page (HTML + inline CSS + vanilla JS)
- Fonts via Google Fonts (DM Sans, Bebas Neue, JetBrains Mono)
- Lead form posts to [Formspree](https://formspree.io) (`xbdqwldn`)
- Hosted on GitHub Pages with custom domain (`CNAME` → `www.sncio.in`)
- `.nojekyll` disables Jekyll so the page is served as raw HTML

## Files

| Path | Purpose |
|---|---|
| `index.html` | The site |
| `Logo.png` | Brand logo (nav + footer) |
| `Layout IMG.JPEG` | Hero blueprint image |
| `CNAME` | Custom domain config for GitHub Pages |
| `.nojekyll` | Tells GitHub Pages to skip Jekyll processing |

## Run locally

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

## Deploy

Push to the `website-0.0` branch. GitHub Pages builds from this branch automatically.

## Contact

Neel Shah · neels@sncio.in · +91 98257 22958
