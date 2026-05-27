# Third-Party Service Compliance — Design Standup Bot

**Last reviewed:** 25 May 2026

This document tracks how Design Standup Bot complies with the Developer Terms
of each external service it integrates with. Update when you change how the app
uses those services or when their terms change materially.

---

## Figma — Developer Policy

**Reference:**
- Developer Terms: <https://www.figma.com/developers/terms>
- API Docs: <https://www.figma.com/developers/api>

| Requirement | Our compliance |
|-------------|---------------|
| Use Personal Access Tokens responsibly (don't share, store securely) | ✅ Token stored in macOS Keychain (`kSecAttrAccessibleAfterFirstUnlock`). Never logged. Never transmitted anywhere except `api.figma.com` |
| Respect rate limits (~ requests per minute per token) | ✅ Sequential file fetching with 1-second delay between requests (`FigmaService.Constant.rateLimitDelayBetweenFilesNanos`). Per-file failures are caught + logged but don't retry-spam |
| Do not bulk-export or resell Figma data | ✅ Only fetches **comments where the current user is mentioned**, only displays them locally, never persists beyond a 30-day local cache, never transmits to any third party |
| Respect file permissions | ✅ Uses the user's own PAT; only sees files that PAT can access. 403 responses are caught + surfaced as "missing scope" without retrying |
| Display Figma branding correctly | ✅ Uses official "Figma" name and the SF Symbol `paintbrush.pointed` in service cards. No misuse of Figma logos |
| Do not impersonate Figma | ✅ App is clearly named "Design Standup Bot" — no Figma branding in the app name, icon, or marketing |
| Honor user consent and revocation | ✅ User-initiated Disconnect deletes credentials immediately (Keychain + UserDefaults) |

**Open question:** when GitHub/Gmail are implemented, similar review needs to
run against their terms.

---

## Atlassian (Jira Cloud) — API Terms

**Reference:**
- Developer Terms: <https://developer.atlassian.com/platform/marketplace/atlassian-developer-terms/>
- REST API Docs: <https://developer.atlassian.com/cloud/jira/platform/rest/v3/>

| Requirement | Our compliance |
|-------------|---------------|
| Use API tokens responsibly | ✅ Token stored in macOS Keychain. Basic auth header sent only to the user-configured `{tenant}.atlassian.net` |
| Do not exceed rate limits | ✅ Single JQL request per refresh (no per-issue fanout). Default `maxResults: 50` cap. Scheduler runs at minimum 15-minute interval |
| Read-only access only (no writes) | ✅ App makes only `GET /rest/api/3/myself` and `GET /rest/api/3/search/jql`. No mutations (no comment posts, no transitions, no edits) |
| Honor Jira permissions model | ✅ Uses the user's PAT; only sees issues the user can already access. 403 responses surface as `missingPermissions` error |
| Do not bulk-export | ✅ Fetches only assigned + recently-watched issues for current user. Local 30-day cache only |
| Do not impersonate Atlassian | ✅ App is clearly named "Design Standup Bot". Uses generic SF Symbol `checkmark.square` for the service card icon |
| JQL queries are user-scoped | ✅ JQL always begins with `assignee = currentUser() OR (watcher = currentUser() AND updated >= -7d)` — never queries unrelated users' data |

---

## Other compliance notes

### macOS App Store guidelines (if/when submitting)

If the app is ever submitted to the Mac App Store, additional checks needed:

- Privacy Nutrition Labels declaration:
  - Data Linked to You: None (tokens stay on-device)
  - Data Not Linked to You: None
  - Data Used to Track You: None
- App Sandbox: ✅ enabled
- Hardened Runtime: required for notarization
- Code signing: requires Apple Developer account (currently deferred — local
  distribution only)

### Data residency

All data processing happens on the user's Mac. No cloud component owned by the
app. Figma data stays in Figma's regions; Atlassian data stays in Atlassian's
regions. Neither is replicated to any third party by this app.

---

## When to re-review this document

- A new third-party integration is added (GitHub, Gmail, etc.) → add a section
- Figma or Atlassian change their developer terms materially
- App behavior changes regarding data retention, sharing, or transmission
- Before submitting to Mac App Store
