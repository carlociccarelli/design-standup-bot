# Screenshot Guide — Landing Page Assets

Reproducible recipes for the screenshots that go on the landing page.
Take each one at **2× retina resolution** so it stays crisp on HiDPI displays
(macOS Screenshot command saves at the display's native scale automatically).

Recommended file format: **PNG**. Save into `landing/screenshots/` so the
landing page's relative paths resolve.

---

## Setup once

1. Open System Settings → Appearance → set to **Dark mode** for the primary set
   (looks better against the landing page's dark hero), then re-shoot in Light
   for the gallery contrast.
2. Quit and relaunch the app so the popover starts in a known state.
3. Make sure the menu bar background behind the popover is clean (no other
   apps' icons visible) — use a plain desktop wallpaper.

---

## Shot 1 — Hero (digest with items)

**File:** `screenshots/01-hero-digest.png`

**Setup**:
- All four services connected with real credentials (Figma, Jira, GitHub, Trello)
  — or as many as you have real accounts for; at minimum two distinct sources
  so the tab strip is visible
- Items visible across multiple sources (≥ 4 rows showing)
- One unread item visible (so the `N unread · Mark all as read` bar is in shot)
- Active tab: **All** (showing the grouped list)

**Capture**:
- Click the menu bar icon → popover opens
- `Cmd-Shift-4`, then Space, then click the popover window
- Result: 400×640 popover with rounded corners + drop shadow, transparent
  background captured

**Notes**: the hero shot is the first thing visitors see. Pick items with
short-ish titles so nothing truncates awkwardly. Having all four sources
visible reinforces the "aggregated digest" pitch.

---

## Shot 2 — Settings (services connected)

**File:** `screenshots/02-settings-connected.png`

**Setup**:
- Settings panel open
- All four service cards filled in (Figma, Jira, GitHub, Trello). Tokens can
  stay obscured (`••••`) — looks cleaner and keeps real credentials out of the
  shot
- The `+ Add service` button at top right is hidden because every service is
  connected — that's intentional and shows the catalog is complete
- Preferences section visible: refresh interval + per-source notification toggles

**Capture**: same popover capture technique.

**Notes**: this shot may need to be slightly scrolled (the popover content is
taller than 640px once all four service cards are visible). Capture from the
top of the form so the back-arrow + "Settings" title are in frame.

---

## Shot 3 — Onboarding (first launch)

**File:** `screenshots/03-onboarding.png`

**Setup**:
- Disconnect everything via Settings, then close popover
- Reopen popover → onboarding screen appears with 4 service tiles
- All four tiles (Figma, Jira, GitHub, Trello) appear as connectable — there
  are no "Coming soon" pills anymore (every catalog entry is a real integration)

**Capture**: same.

---

## Shot 4 — Light mode

**File:** `screenshots/04-light-mode-digest.png`

**Setup**: System Settings → Appearance → Light. Same as Shot 1 but in light mode.

Demonstrates the app adapts properly (a key claim in the privacy/quality story).

> **Note**: the old `screenshots/04-coming-soon.png` is obsolete — the app no
> longer has any "Coming soon" placeholder cards because every catalogued
> service ships as a real integration. The file can be deleted; the landing
> no longer references it. Renaming the light-mode shot from `05` to `04`
> keeps the inventory contiguous and lets future shots grow naturally.

---

## Optional: animated demo

If you want a short GIF on the landing:

**File:** `screenshots/demo.gif` (target: < 2 MB)

**Recipe** (using macOS built-in screen recording):
1. `Cmd-Shift-5` → Record Selected Portion → frame the popover
2. Run a flow: open popover → switch tabs → mark all as read → open settings
3. Stop recording, save .mov
4. Convert with `ffmpeg` (if installed) or upload to ezgif.com:
   `ffmpeg -i demo.mov -vf "fps=15,scale=600:-1" -loop 0 demo.gif`
5. Optimize size: keep ≤ 6 seconds, ≤ 15fps, ≤ 600px width

---

## After capturing

Drop the files into `landing/screenshots/`. The landing page `index.html`
references them via relative paths — names matter.

If you change a file name, update the corresponding `<img src="">` in
`landing/index.html`.
