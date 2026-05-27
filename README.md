# Design Standup Bot

Your daily design standup, in the macOS menu bar.

A native macOS menu bar app that aggregates **Figma mentions**, **Jira issues**,
**GitHub PRs**, and **Trello cards** into one glanceable popover. Built for UX
leads who don't want to start the day with seven browser tabs.

→ **[Landing page & download](https://carlociccarelli.github.io/design-standup-bot/)**
→ **[Privacy Policy](PRIVACY.md)** · **[Third-party compliance](THIRD-PARTY-COMPLIANCE.md)**

![App icon](docs/app-icon.png)

---

## This repo

This repository is the **public face** of Design Standup Bot:

- 📥 **Hosts the landing page** at <https://carlociccarelli.github.io/design-standup-bot/>
  via GitHub Pages (served from `docs/`)
- 🐛 **Receives bug reports** and 💡 **feature requests** through
  [Issues](https://github.com/carlociccarelli/design-standup-bot/issues)
- 📄 **Carries the privacy + third-party compliance docs** that the app links to

**The source code is private** (this is a single-developer project). If you'd
like a feature, see something broken, or have a security concern — open an
issue. I read every one.

---

## Download

Always download from the landing page:

→ **<https://carlociccarelli.github.io/design-standup-bot/>**

The DMG is **ad-hoc signed** (no Apple Developer Program), so macOS will
warn you the first time you open it. The bypass takes ~10 seconds and
only needs to happen once:

**Method A — Right-click (try this first)**

1. Right-click (or Control-click) `DesignStandupBot.app` in `/Applications`
2. Choose **Open** from the menu
3. Click **Open** in the confirmation dialog

**Method B — System Settings (macOS Sonoma / Sequoia)**

If the warning dialog only offers *"Move to Trash" / "Done"* with no
*Open Anyway* button, use this path instead:

1. Click **Done** on the warning (NOT *Move to Trash*)
2. Open **System Settings → Privacy & Security**
3. Scroll down — you'll see *"DesignStandupBot was blocked from use…"*
4. Click **Open Anyway**, confirm with Touch ID / password

After either method, macOS whitelists the app — every subsequent launch
is silent.

> **Note:** there is no `Releases` tab on this repo. The DMG is distributed
> only via the landing so download attribution stays on a single channel.

---

## Privacy

**Everything stays on your Mac.**

- Zero analytics, zero telemetry, zero crash reports, zero third-party SDKs
  in the app itself
- Tokens live in the macOS Keychain; preferences in UserDefaults
- Network requests **only** to the services you connect (Figma, Jira, GitHub,
  Trello). Nothing else.

Full details: [PRIVACY.md](PRIVACY.md).

---

## Feedback

In the app: **Settings → Send feedback** (mailto) or **Request feature**
(opens a GitHub issue). Direct:

- Email: `info@carlociccarelli.com`
- Issues: <https://github.com/carlociccarelli/design-standup-bot/issues>

---

## License

The app binary is distributed under [MIT](LICENSE) © 2026 Carlo Ciccarelli.
The source code is not currently public — that's a distribution choice, not
a licensing one. If you have a use case that would benefit from the source
being available, open an issue and let's talk.
