# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio and resume site for Kristopher Gates, hosted on GitHub Pages at www.kdlgates.com (configured via CNAME).

## Architecture

This is a **zero-build static site** — no bundler, no framework, no package manager. The entire site is plain HTML + inline CSS.

- `index.html` — Main portfolio/landing page (hero, skills, experience, projects, education, contact)
- `resume.html` — Single-page resume with print-optimized `@media print` stylesheet and PDF download link
- `Kristopher_Gates_Resume.pdf` — Downloadable resume PDF
- `CNAME` — GitHub Pages custom domain config (`www.kdlgates.com`)

## Development

No build step. Open HTML files directly in a browser or use the local dev server on port 8080 (port 8000 is reserved for other local services):

```
npx serve -l tcp://0.0.0.0:8080
```

There are no tests, linters, or CI pipelines.

## Design System

Both pages share a consistent dark-theme design with CSS custom properties:

- **Fonts**: Inter (body), JetBrains Mono (labels/dates/monospace accents)
- **Colors**: `--accent: #7c5cfc` (purple), `--accent-secondary: #00d4aa` (teal), dark backgrounds (`#0a0a0f`, `#12121a`)
- **Gradient**: `linear-gradient(135deg, #7c5cfc, #00d4aa)` used for headings, logo, accents

`resume.html` includes a full `@media print` block that overrides to white background with dark text for clean PDF output. The `@page` rule is set to letter size with zero margins.

## Key Conventions

- All CSS is inline in `<style>` tags (no external stylesheets)
- No JavaScript — all animations use CSS (`@keyframes fadeUp`, `pulse`)
- Mobile responsiveness via `@media (max-width: 768px)` — nav links hide, grids collapse to single column
- Logo (`nav .logo`) links to `/` with a sparkle hover easter egg (`::after` pseudo-element)
