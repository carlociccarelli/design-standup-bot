# Landing Page — Design Standup Bot

Static single-file landing for local Mac distribution.

## Files

- `index.html` — the landing page (vanilla HTML/CSS, no JS, no build step)
- `app-icon.png` — 1024×1024 app icon, used in nav + hero
- `screenshots/` — populate with the captures listed in `SCREENSHOTS.md`
- `DesignStandupBot.dmg` — drop the signed DMG here for the download button

## How to publish

Choose one:

### Option A — GitHub Pages (simplest)
1. Push this `landing/` folder to a GitHub repo as `docs/` (or set Pages to serve from `/landing/`)
2. Enable Pages in Settings → Pages
3. URL: `https://<your-user>.github.io/<repo>/`

### Option B — Netlify drop
1. Visit <https://app.netlify.com/drop>
2. Drag this `landing/` folder onto the page
3. Get a free `*.netlify.app` URL

### Option C — Local hosting + tunnel
For dev/sharing only:
```
cd landing
python3 -m http.server 8000
```
Pair with `ngrok http 8000` to share externally.

## Updating

- Icon change: re-run `Tools/generate-app-icon.sh` then copy the 1024 PNG here (`cp ../DesignStandupBot/.../icon_512x512@2x.png app-icon.png`)
- Copy / FAQ change: edit `index.html` directly
- New screenshot: capture per `SCREENSHOTS.md`, drop into `screenshots/`, reference in `index.html`
- New DMG release: replace `DesignStandupBot.dmg`, update `v1.0` references in `index.html`

## Customization checklist before going live

- [ ] Replace `https://github.com/carlociccarelli/design-standup-bot` URLs with the real repo
- [ ] Replace `mailto:carlociccarelli@gmail.com` if you want a different contact
- [ ] Confirm screenshots are captured and committed
- [ ] Confirm `DesignStandupBot.dmg` exists (or update the download button to a hosted location)
- [ ] Open `index.html` in a browser, click every link, scroll the FAQ
