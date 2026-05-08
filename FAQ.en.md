# Frequently Asked Questions (FAQ)

> 📘 This document answers common questions about using novel-timeline. It is updated independently of the app.

If you're new to novel-timeline or hit something puzzling, check this page first. The more often a question is asked, the more likely it ends up here.

---

## License & Billing

### Q. How long is the free trial?

You get **90 days (3 months)** of full-feature use after installation. After day 90, the app switches to **Read-only mode**, but **all the data you've created is preserved** and you can still export it (JSON / NTZ / TXT).

### Q. How much does a subscription cost?

- **Monthly**: $10 / month
- **Annual**: $80 / year (about **33% cheaper** than monthly)

The annual plan is the best value. There is no perpetual license — the subscription model funds ongoing updates and license-validation infrastructure, and every new feature or patch is automatically included while your subscription is active.

### Q. What's the refund policy?

We offer **unconditional refunds within 14 days of purchase**, no questions asked (applies to both monthly and annual). Use the refund link in your purchase receipt email or the [Lemon Squeezy refund policy](https://www.lemonsqueezy.com/legal/refund-policy), or just email **askNovelTimeline@gmail.com** and we'll handle it.

### Q. Where do I get my license key after purchase?

A license key is automatically emailed to the address you used at checkout (subject: `Your novel-timeline license key`). If you don't see it, please check your **spam folder** as well.

Paste the key into **App → Settings → License** and it activates as soon as it validates. Even if your internet drops temporarily, the app keeps working during a **30-day offline grace period**.

---

## Troubleshooting

### Q. I got a "system clock anomaly detected" notice and the app went into Read-only mode.

This means your PC's system clock has rolled **backwards** compared to a previously recorded timestamp. Common causes:

- **Dead motherboard clock battery (CMOS)** — the clock resets to e.g. 2010 on every boot
- **NTP sync failure** — your time server briefly couldn't be reached
- **Time zone changes** — international travel, manual setting changes
- **Laptop wake-from-sleep** — clock drift while suspended

**How to fix it**:

1. Set your OS clock correctly.
   - **Windows**: Right-click the taskbar clock → "Adjust date/time" → turn ON "Set time automatically" → click "Sync now"
   - **macOS**: System Settings → General → Date & Time → turn ON "Set date and time automatically"
2. Open **App → Settings → License**.
3. Click **🕐 Fix clock-sync issue**. Read-only mode lifts immediately.

> This check exists to prevent trial-extension abuse. Genuine users can clear it instantly with the steps above. **Paid subscribers are not subject to this check** — server-side validation handles it for them.

### Q. External links (purchase / support / help) don't open in my browser.

**v1.0.0 (the official release)** opens external links correctly. If yours doesn't, you're probably on beta 0.0.13 or earlier — please update to v1.0.0 from the [Latest Release](https://github.com/seo1westn2020/novelTimeline_release/releases/latest) page. Earlier beta builds had a Windows WebView2 security issue that blocked external browser launches.

### Q. How do I know auto-save is working?

novel-timeline preserves every change automatically. If your project folder lives in a cloud-synced location (**OneDrive / Dropbox / iCloud**), the auto-save cadence is automatically tuned to reduce cloud sync traffic (5s → 10s idle, 60s force). Backup copies are rotated alongside every save, so **there's no risk of data loss**.

### Q. My project's .ntz file is gone!

novel-timeline keeps automatic backup copies inside your project folder:

- `*.bak.now.ntz` — most recent auto-save
- `*.bak.snapshot.ntz` — stable snapshot

Open one of these via **NTZ Import** in the app to restore the project to that point. If even those backups are missing, also check the OS **Recycle Bin / Trash** and the **cloud trash** (OneDrive and Dropbox keep deleted files for 30 days).

---

## Features

### Q. What do I need to use the AI features?

novel-timeline's AI features are **BYOK (Bring Your Own Key)**. You issue an API key from the provider of your choice, register it in the app, and your provider bills you directly based on usage.

Supported providers:

- **OpenAI** — GPT-4 family
- **Anthropic** — Claude family
- **Google** — Gemini family
- **Ollama** — **local execution, no API key needed, $0 cost** (speed depends on your hardware)

If you'd rather not pay anything, Ollama runs locally for free. A detailed screenshot setup guide is planned for a future update.

### Q. Can I access my data from other AI tools (ChatGPT, Gemini, etc.)?

Yes. All data is stored as **standard JSON**, and an **MCP server** lets Claude / Gemini / ChatGPT and other AI platforms connect directly. Open access is a core design principle — novel-timeline is deliberately not locked to any single AI vendor. A dedicated integration guide is planned.

### Q. Does it support all four languages (Korean / English / Japanese / Chinese)?

Yes. Switch any time via **Settings → Language**. UI labels and AI outputs (conflict-check results, draft text, etc.) both follow the language you pick.

---

## Contact

> Still stuck? Email **askNovelTimeline@gmail.com** or open a [GitHub Issue](https://github.com/seo1westn2020/novelTimeline_release/issues). We triage once a day, and new questions get folded into this FAQ.

---

**Last updated**: 2026-05-08
