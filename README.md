# GrindBill PWA — GitHub Ready

Fast Quotes & Invoices. Zero Bloat.

## Files
- `index.html` — the whole app (splash + 6-step wizard + live preview)
- `manifest.webmanifest` (+ `manifest.json` alias) — correct PWA manifest, GrindBill
- `sw.js` — service worker, cache-first + offline fallback, version `grindbill-v2`
- `icons/` — `icon-192.png`, `icon-512.png`, `icon-512-maskable.png`, `apple-touch-icon.png`, `favicon.png`, `logo-transparent.png`

## Deploy on GitHub Pages
1. Create repo, upload ALL files (keep folder structure).
2. Settings → Pages → Deploy from branch → `main` / `/ (root)` → Save.
3. Open `https://<you>.github.io/<repo>/` — must be HTTPS (GitHub Pages is).
4. Install: Chrome/Edge → ⋮ → Install GrindBill / Add to Home Screen. iOS Safari → Share → Add to Home Screen.

## Local test (PWA needs localhost or HTTPS)
```bash
# Python
python3 -m http.server 8000
# then open http://localhost:8000
# Node
npx serve .
```
Check DevTools → Application → Manifest + Service Workers. No errors = good.

## Manifest check
- name: GrindBill, short_name: GrindBill, id: `/`, scope: `./`
- start_url: `./index.html`, display: standalone
- background/theme: `#0f172a`
- icons: 192 any, 512 any, 512 maskable

## Update the app
Bump `CACHE` in `sw.js` (e.g. `grindbill-v3`) + `?v=` if you change `start_url`, otherwise users may keep the old cached version.

## Notes
- Data saves in browser localStorage (`grindbill_*`) — business, presets, payment, draft.
- Export / Print PDF uses the browser print dialog (`window.print()`).
