# Privacy Policy — Design Standup Bot

**Last updated:** 25 May 2026 (revised same day for GitHub integration)  
**Author:** Carlo Ciccarelli

This document describes what data Design Standup Bot handles, where it lives,
and what we never do with it. It applies to all distributions of the macOS app.

---

## Plain-English summary

- Everything stays on your Mac. No analytics, no telemetry, no crash reports.
- We only talk to the APIs you explicitly connect: Figma, Jira, GitHub, and Trello.
- Your tokens live in the macOS Keychain. Your IDs live in your local UserDefaults.
- Cached items live in your app's Application Support folder, pruned after 30 days.
- No data is ever sent to us. There is no "us" server.

---

## What data is collected

The app handles only data you provide it directly:

| Data | Why | Stored where | Retention |
|------|-----|--------------|-----------|
| Figma Personal Access Token | Auth header on Figma API requests | macOS Keychain | Until you Disconnect or remove the app |
| Figma Team ID | URL path for Figma API | UserDefaults | Same |
| Figma File Keys (optional) | URL path for Figma API | UserDefaults | Same |
| Jira API Token | Basic Auth header on Jira API requests | macOS Keychain | Same |
| Jira Base URL | Host for Jira API requests | UserDefaults | Same |
| Jira User Email | Basic Auth Identity | UserDefaults | Same |
| GitHub Personal Access Token | Bearer auth header on GitHub API requests | macOS Keychain | Same |
| GitHub Enterprise URL (optional) | Host for GitHub API requests (when not using github.com) | UserDefaults | Same |
| GitHub Repo Allow-list (optional) | Filter for the GitHub Search API query | UserDefaults | Same |
| Trello API Key | Query string `?key=…` on Trello API requests | macOS Keychain | Same |
| Trello User Token | Query string `?token=…` on Trello API requests | macOS Keychain | Same |
| Cached digest items | Offline display + new-item detection | `~/Library/Application Support/cache/items.json` | Items older than 30 days are pruned on every save |
| Notification preferences | Per-source enable flags | UserDefaults | Same |
| Snooze + read state | Local UX state | Cached items JSON | Snooze resets at midnight; read state preserved |

No background collection occurs. The app does not request location, contacts,
calendar, microphone, camera, or any other system data.

---

## What data is sent off-device

Network requests are made **only** to:

- `api.figma.com` — only when you have Figma credentials configured and a refresh occurs
- `your-tenant.atlassian.net` — the host you configured, only when Jira credentials are configured
- `api.github.com` (or your GitHub Enterprise host) — only when GitHub credentials are configured
- `api.trello.com` — only when you have Trello credentials configured and a refresh occurs

These requests carry your credentials in standard auth artifacts: `X-Figma-Token`,
`Authorization: Basic ...` (Jira), `Authorization: Bearer ...` (GitHub), and
`?key=…&token=…` query parameters (Trello, per their API convention).
Figma, Atlassian, GitHub, and Trello's privacy policies govern how they handle
those requests on their end.

No requests are made to any other host. No requests are made to a server owned
by the app author or any third party.

---

## What we do not do

- No analytics (no Mixpanel, Segment, Amplitude, Firebase, anything)
- No crash reporting (no Sentry, Crashlytics, anything)
- No advertising SDKs
- No third-party SDKs of any kind
- No "phone home" requests to check for updates from us
- No data resale or sharing
- No background data export beyond user-configured Figma/Jira/GitHub/Trello fetches

---

## Third-party services

When you connect Figma, Jira, GitHub, or Trello, you are interacting with
their services subject to their own terms:

- **Figma**: <https://www.figma.com/legal/privacy/>
- **Atlassian (Jira)**: <https://www.atlassian.com/legal/privacy-policy>
- **GitHub**: <https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement>
- **Trello (Atlassian)**: <https://www.atlassian.com/legal/privacy-policy>

Design Standup Bot does not have its own user account, server, or backend.
There is no third-party processor.

---

## macOS Permissions

The app requests permission for:

- **Notifications** (`UNUserNotificationCenter`) — only to surface new mentions
  on your menu bar. You can revoke this in System Settings → Notifications at any time.
- **Network client** (sandbox entitlement) — required for any API calls.

The app does **not** request:

- Full Disk Access
- Accessibility
- Screen Recording
- Camera, Microphone, Contacts, Calendar, Photos, Location

---

## Your rights and control

- **Disconnect a service** — Settings → tap "Disconnect" on the service card.
  This deletes the token from Keychain and the IDs/URLs from UserDefaults.
- **Stop notifications** — Settings → toggle "Enable notifications" off, or
  revoke at the system level.
- **Delete all local data** — quit the app and delete:
  - `~/Library/Application Support/cache/items.json` (cached items)
  - The app's UserDefaults plist (preferences + IDs)
  - The relevant Keychain entries (`com.designstandupbot.figma.token`,
    `com.designstandupbot.jira.token`, `com.designstandupbot.github.token`,
    `com.designstandupbot.trello.apiKey`, `com.designstandupbot.trello.token`)
  Or simply uninstall the app and clear those locations.

---

## Children

Design Standup Bot is a professional tool. It is not directed at children under 13
and does not knowingly collect data from them.

---

## Changes to this policy

This file is versioned with the app source. The "Last updated" date at the top
reflects the most recent change. If a future release materially changes data
handling, the bundled policy will be updated and the change noted in release notes.

---

## Contact

Carlo Ciccarelli — `carlociccarelli@gmail.com`
