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

The DMG is **ad-hoc signed** (no Apple Developer Program). On first launch,
right-click the app → **Open** to bypass Gatekeeper one time. Subsequent
launches are silent.

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
