# Functional Strength + Neck/Shoulder Routine — PWA

A mobile-first workout reference app. Displays your full routine with animated exercise images from the free-exercise-db.

## Deploy to GitHub Pages (quickest path)

```bash
# 1. Create a new repo (or use an existing one)
gh repo create workout-routine --public --clone
cd workout-routine

# 2. Copy these files into the repo root
#    index.html, manifest.json, sw.js,
#    icon-192.png, icon-512.png, apple-touch-icon.png

# 3. Push
git add .
git commit -m "workout PWA"
git push origin main

# 4. Enable GitHub Pages
#    Go to repo Settings → Pages → Source: "Deploy from a branch"
#    Branch: main, folder: / (root)
#    Save — your site will be live at https://<username>.github.io/workout-routine/
```

## Install on iPhone

1. Open your GitHub Pages URL in **Safari**
2. Tap the **Share** button (square with arrow)
3. Tap **"Add to Home Screen"**
4. Name it whatever you want, tap **Add**

It will appear as a full-screen app with its own icon. The service worker caches everything on first load, so it works offline at the gym.

## How it works

- Fetches exercise data from [free-exercise-db](https://github.com/yuhonas/free-exercise-db) (public domain)
- Alternates between start/end position images to simulate movement animation
- Service worker caches all assets and images for offline use after first load
- Rehab/mobility exercises (chin tucks, wall slides, face pulls, etc.) show form cue cards instead of images

## Files

```
index.html          — the entire app (single file, no build step)
manifest.json       — PWA manifest for home screen install
sw.js               — service worker for offline caching
icon-192.png        — PWA icon
icon-512.png        — PWA icon (large)
apple-touch-icon.png — iOS home screen icon
```

## Alternative: Cloudflare Pages

```bash
# Drag and drop the folder at https://dash.cloudflare.com
# → Workers & Pages → Create → Pages → Upload assets
```

## Alternative: Netlify

```bash
# Drag and drop at https://app.netlify.com/drop
```
