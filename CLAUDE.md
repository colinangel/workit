# CLAUDE.md

## Branching

- Always create a new branch for new work unless explicitly updating code on an existing branch.
- Branch names should be descriptive of the change.

## Repository

GitHub: https://github.com/colinangel/workit

## About

Functional Strength + Neck/Shoulder workout tracker PWA. Mobile-first, offline-capable, single-file app with no build step or external dependencies.

### Features
- Exercise tracking with per-set rep counts and done/undone toggles
- Weight progression system (auto-suggests increases after N sessions)
- Dynamic add/remove sets per exercise (persisted across sessions)
- Rep defaults persist — if you increase reps today, tomorrow starts there
- Day-by-day and week navigation to view/log any date
- Progress tab with period filters (week, month, 3mo, 6mo, year, all time)
- Animated SVG exercise demonstrations
- Form cue cards for mobility/rehab exercises

### localStorage keys
- `wk_log` — daily workout logs keyed by date (e.g. `{"2025-03-24": {...}}`)
- `wk_prog` — weight progression state (current weight, sessions completed, increment)
- `wk_defaults` — per-exercise customizations (set count, default reps)

## Architecture

Single-file PWA — all HTML, CSS, and JS live in `index.html`. No framework, no build tool.

```
index.html            — entire app (HTML + CSS + JS, ~1300 lines)
sw.js                 — service worker for offline caching (cache-first strategy)
manifest.json         — PWA manifest for home screen install
icon-192.png          — PWA icon
icon-512.png          — PWA icon (large)
apple-touch-icon.png  — iOS home screen icon
```

### Service worker

`sw.js` uses a cache-first strategy. The cache name (e.g. `workout-v5`) must be bumped on every deploy so the old cache is purged and users pick up changes. Update `const CACHE_NAME` in `sw.js` whenever `index.html` changes.

## Build & Deploy

No build step. Deploy the files as-is to any static host.

### GitHub Pages (primary)
1. Push to `main`
2. Settings > Pages > Source: "Deploy from a branch", branch: `main`, folder: `/`
3. Site is live at `https://colinangel.github.io/workit/`

### Alternatives
- **Cloudflare Pages**: Upload folder at dash.cloudflare.com > Workers & Pages > Create > Pages
- **Netlify**: Drag and drop at app.netlify.com/drop

### Install as app
- **iOS Safari**: Share > "Add to Home Screen"
- **Android Chrome**: Menu > "Add to Home Screen"

Close and reopen twice after a deploy to activate the new service worker.
