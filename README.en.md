<p align="center">
  <img src="./assets/logo.png" alt="novel-timeline" width="160" />
</p>

# novel-timeline

> 🌐 **Language**: [한국어](./README.md) · English (this file)

A **timeline-based story management tool** for novelists.
Organize complex characters, events, foreshadowings, and relationships
at a glance — with a built-in writing editor and AI integration for
long-form manuscript work.

> This repository is the official **open-beta distribution channel**.
> The source code is maintained in a separate private repository.

---

## Download

The latest build is available on the **[Latest Release](https://github.com/seo1westn2020/novelTimeline_release/releases/latest)** page. For the full release history, see the [Releases](https://github.com/seo1westn2020/novelTimeline_release/releases) page.

| OS | File | Notes |
|---|---|---|
| **Windows 10 / 11** | [novel-timeline_1.0.0_x64-setup.exe](https://github.com/seo1westn2020/novelTimeline_release/releases/download/v1.0.0/novel-timeline_1.0.0_x64-setup.exe) | NSIS installer |
| **macOS 12+ (Apple Silicon)** | [novel-timeline_1.0.0_aarch64.dmg](https://github.com/seo1westn2020/novelTimeline_release/releases/download/v1.0.0/novel-timeline_1.0.0_aarch64.dmg) | Disk image (Apple Silicon only) |

> 📋 What's new in v1.0.0: [RELEASE_NOTES_v1.0.0.en.md](./RELEASE_NOTES_v1.0.0.en.md)

> These builds are **not yet code-signed.** Your OS may flag the app as "from an unidentified developer," but the app runs fine.

### If Windows blocks the installer

When the `Windows Defender SmartScreen` warning appears:

1. Click the small **"More info"** link to reveal the **Run** button.
2. Click **"Run"** to proceed with the installation.

### If macOS blocks the app

When you see `"App is damaged and can't be opened"` or `"unidentified developer"` on first launch:

1. In the Applications folder, **right-click the novel-timeline icon** and choose **"Open"**.
   *(If your mouse doesn't support right-click — e.g. Apple Magic Mouse — hold **`Control`** while clicking instead.)*
2. If the security dialog appears again, click **"Open"** once more.
3. After approving once, normal double-click works.

> On macOS Sequoia (15) or later, if right-click is also blocked, go to **System Settings → Privacy & Security** and click **"Open Anyway"** at the bottom.

> If none of the above works, open Terminal and remove the quarantine attribute:
> ```bash
> xattr -d com.apple.quarantine "/Applications/novel-timeline.app"
> ```

---

## Features

- **Timeline** — Organize events on a time axis, group concurrent events, drag to reorder
- **Relationship Graph** — Visualize character relationships, per-page character selection, filter by alive status / category
- **Character Management** — Personality, speech style, faction membership, status timeline
- **Faction Management** — Track each character's faction join/leave timeline, detect dual membership
- **Foreshadowing Tracking** — Link setups and payoffs (planted and paid-off events)
- **Writing Editor** — A4 paginated layout, footnote system, preview/print
- **AI conflict checking / draft generation (BYOK)** — OpenAI / Anthropic / Google / Ollama with your own key
- **Auto-save** — every change is preserved automatically; no data loss on exit
- **New version alert badge** — auto badge in header when a new release lands (checked once a day)
- **Collections** — Store reference images, text, and links
- **Export** — TXT (per chapter / full), JSON (full / selected / per relationship-graph page)
- **i18n** — Korean / English / Japanese / Chinese
- **Themes** — Dark / Light

---

## Pricing

| Tier | Price | Notes |
|---|---|---|
| **Free Trial** | Free | **90 days (3 months)** of full-feature use after installation. No usage limits |
| **Monthly** | $10 / month | Full features, auto-renews monthly |
| **Annual** | $80 / year | Full features, yearly billing (~33% discount vs. monthly) |

> No perpetual license is offered.

> All SKUs (monthly/annual) are eligible for an unconditional refund within 14 days of purchase ([Refund Policy](./legal/refund.en.md)).

### Read-only mode after trial or subscription expiry

If the 3-month trial expires without an active paid subscription, or an active subscription expires or is cancelled, the app enters **Read-only mode**.

| Action | Allowed | Blocked |
|---|---|---|
| View existing projects | ✅ | |
| Export JSON · NTZ · TXT | ✅ | |
| Enter license key · change settings | ✅ | |
| Edit events/characters/foreshadowings/relationships, etc. | | ❌ |
| Import external files · create new projects | | ❌ |

**User data files are never damaged or destroyed**, and can always be exported for external backup.

Payment and license-key issuance/validation are handled by [Lemon Squeezy](https://lemonsqueezy.com).

---

## Using your license key

1. Upon purchase, a **license key** will be sent to your email.
2. Launch novel-timeline → **Settings → License Key** and paste the key.
3. Once validated, paid features will be activated automatically.

Even if your internet connection is unstable, the app will continue
to function normally during a **30-day offline grace period**.

---

## Bug reports / feedback

- Email: **askNovelTimeline@gmail.com**
- When reporting a bug, please include:
  - OS and version (Windows 11 / macOS 14, etc.)
  - novel-timeline version
  - Steps to reproduce
  - Screenshots

---

## Supporters

novel-timeline is a solo indie project. Heartfelt thanks to **everyone helping shape the tool — through monetary support, translation fixes, feature suggestions, bug reports, and ideas**.

> _No supporters yet. Be the first!_

### ☕ Monetary support

| | |
|---|---|
| ☕ **Ko-fi** | [ko-fi.com/novelTimeline](https://ko-fi.com/novelTimeline) |
| 💳 **PayPal** | [paypal.me/novelTimeline](https://paypal.me/novelTimeline) |

If novel-timeline helps you during the trial, a coffee goes a long way.

### 🌍 Translation, feature ideas, bug reports

Non-monetary contributions are equally welcome. Reach out via email **askNovelTimeline@gmail.com** or GitHub Issues. Accepted contributions are listed below (with consent).

### Format

| Name | Date | Contribution | Message |
|---|---|---|---|
| _First slot_ | — | — | — |

---

## License

The Software is distributed under an **End User License Agreement (EULA)**.
Please review the [LICENSE.en](./LICENSE.en) file before installation.
For the Korean original, see [LICENSE](./LICENSE); in case of any
inconsistency, the Korean version prevails.

Copyright © 2026 Seo Il-seon (novel-timeline). All rights reserved.

---

## Legal Documents

Terms of Service, Refund Policy, and Privacy Policy that apply when you
purchase or use novel-timeline. English texts are legally binding;
Korean versions are reference translations.

| Document | 한국어 | English |
|---|---|---|
| Terms of Service | [legal/terms.md](./legal/terms.md) | [legal/terms.en.md](./legal/terms.en.md) |
| Refund Policy (14-day, all SKUs) | [legal/refund.md](./legal/refund.md) | [legal/refund.en.md](./legal/refund.en.md) |
| Privacy Policy | [legal/privacy.md](./legal/privacy.md) | [legal/privacy.en.md](./legal/privacy.en.md) |
| Index | [legal/README.md](./legal/README.md) | — |
