# CLAUDE.md

## Deploy

Push to `main` → GitHub Pages auto-deploys. No build step, no CI. Just static files.

```
git add -A && git commit -m "message" && git push origin main
```

Live at https://www.kdlgates.com. Allow 1-2 min for Pages cache.

## Files

- `index.html` — portfolio/landing page (single file, no deps)
- `resume.html` — resume page (matches site theme, print-friendly)
- `Kristopher_Gates_Resume.pdf` — generated via Chrome headless from resume.html
- `CNAME` — custom domain config (www.kdlgates.com)

## PDF Regen

```
chrome --headless --print-to-pdf="Kristopher_Gates_Resume.pdf" --no-margins --print-to-pdf-no-header "file:///path/to/resume.html?v=cachebust"
```

## DNS

A records → GitHub Pages IPs (185.199.108-111.153). CNAME www → KDLGates.github.io. MX/SPF for Google Workspace — don't touch.
