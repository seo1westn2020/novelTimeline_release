# novel-timeline v1.0.0 — First Public Release

**Release date**: 2026-04-26

The first public build of a **timeline-based story management tool** for novelists. Characters, events, foreshadowings, relationship graphs, the writing editor, reference collections, and AI assistance — every tool you need for long-form manuscript work, all in one screen.

---

## New features

### Character reference photos
- Each character can hold **up to 5 reference photos** drawn from your collection.
- Upload an image once in the Collections tab, then pick it from the character editor — no need to upload the same file twice.
- Click a thumbnail in the writing editor's right sidebar to pop up a **near-full-screen view (90% of window)**, so you can quickly check appearance, costume, and props while writing.

### Complementary outline on character nodes
- Solves the long-standing issue of character colors blending into the dark-mode background.
- Every character color now gets an **automatic complementary outline**, so any color stays clearly visible on the relationship graph and character cards.

### Hamburger menu Help (FAQ) expanded to 11 entries
- The hamburger menu (≡) → "Help" surfaces frequently asked questions directly in the app.
- Topics include: trial policy (3 months + Read-only mode), how to enter a license key, registering character photos, using aliases, NTZ vs. JSON, support channels, bug reporting, and AI usage (with BYOK cost guidance) — 11 items in total.

### Multilingual UI — Korean / English / 日本語 / 中文
- Switch between four languages from the hamburger menu (≡) → "Language".
- Not just UI labels — **AI output (settings validation results, drafts) responds in the selected language** as well, via branched system prompts.
- Japanese and Chinese translations have gone through a first-pass automatic translation plus domain-term verification for writing tools. If anything reads off, please let us know at askNovelTimeline@gmail.com or via GitHub Issues — we'll fold it into the next patch.

### New-version alert badge
- A blue **"v{new version} update available ↗"** badge appears in the header automatically when a new release is published.
- Clicking it opens the GitHub Releases page in a new tab, taking you straight to the download.
- It only **checks once per day**, so it's gentle on battery and bandwidth — no per-launch GitHub round-trip.

---

## Improvements

### Clean empty state on first launch
- Previously, first launch automatically opened a sample project. Based on the feedback "I'd rather build a sample myself when I need one," the app now starts with an **empty project**.
- Existing projects load just like before — nothing changes for current users.

### "+ Add Item" button respects the current filter
- In Collections, pressing "+ Add Item" while the **photo filter** is active now defaults the new item type to **photo** (previously it always started as a memo).
- This eliminates the "I clicked Add to attach a photo, but a memo form came up" confusion.

### Windows builds unified to a single EXE
- The previous beta shipped both `.msi` and `.exe` installers, but "the difference between MSI and EXE isn't obvious to non-technical users" — so we've unified to a **single NSIS .exe**.
- Cleaner download page, simpler install instructions.

### Supporters consolidated into a single GitHub source of truth
- The in-app supporters modal has been replaced by a link to the GitHub "Supporters" section.
- Monetary support, translation fixes, feature suggestions, bug reports, and ideas — all listed in one place that's always up to date.

### Stabilized Chapter-based ordering and movement
- When events accumulate and concurrent groups are made and unmade repeatedly, empty chapters used to linger awkwardly or text could go missing. We've redesigned the internal model so that **chapters are managed as permanent units**.
- Chapters with content show a **small green dot** next to their sidebar header — at a glance you can see which chapters have manuscript text.
- Empty chapters that contain no events still appear in the sidebar with a **dotted outline**, so you can click in and start writing immediately (previously empty chapters were invisible, making them hard to enter).
- Truly empty chapters — no text, no events — are auto-cleaned, keeping the list tidy.

### Concurrent-event split button — ↓ intuitive icon
- The button that pulls an event out of a concurrent group into the next chapter has been changed from → to **↓**.
- "Move this event down (to the next chapter)" now reads visually clearer.

### Bottom timeline scrubber ↔ Writing tab sync
- Dragging the bottom scrubber left/right now **also moves the displayed chapter in the Writing tab**.
- The previous asymmetry where only the Events tab followed the scrubber, and the Writing tab stayed put, is fixed.

---

## Bug fixes

### Conflict checking now includes characters mentioned only in body text (BUG-012)
- **Before**: If you mentioned character X only in the manuscript body without tagging them in the event's "Characters" field, the AI conflict checker missed them — taboo violations, voice contradictions, and relationship inconsistencies slipped through as a **silent failure** (the UI showed "no conflicts").
- **This fix**: Names and aliases that appear in the body are auto-detected and added to the validation set. Persona information now reaches the AI prompt even without manually tagging each character.

### Images disappearing right after NTZ import (BUG-014, Windows .exe only)
- **Before**: On Windows builds (.exe), importing an NTZ file would show the collection item names but **fail to load the image files themselves**.
- **This fix**: Reordered Tauri backend asset save/load commands — Windows builds now display imported NTZ images correctly.

### NTZ import blocked from an empty project (BUG-015)
- **Before**: A regression where pressing "Import NTZ" right after first launch (in the **empty-project state**) raised "Save failed — project title is empty," blocking the import.
- **This fix**: The empty-state path now skips the pre-save and proceeds to import directly.

### License renewal safety net (BUG-011)
- For scenarios where you go offline (travel, outings) right after payment, even if some auto-renewal webhooks are missed, we've added a **3-day buffer** to the expiry timestamp so the app **does not falsely flip into Read-only mode**.
- A normal renewal signal still overwrites the buffer, so the actual expiry time isn't inflated.

---

## Known limitations

- **Code-signing certificates are not yet applied.** For Windows SmartScreen and macOS Gatekeeper bypass instructions, see [README — Download](./README.en.md#download).
- **AI features use BYOK (Bring Your Own Key)**. You'll need an API key from OpenAI, Anthropic, or Google (configured in Settings → AI) to use them. Per-validation cost is roughly **$0.005–0.01**.
- **The trial lasts 90 days from install**. After that, the app enters **Read-only mode** — your data itself is never damaged, and you can always export it for external backup.

---

## Installation

### Windows 10 / 11

1. From the [Latest Release](https://github.com/seo1westn2020/novelTimeline_release/releases/latest) page, download `novel-timeline_<version>_x64-setup.exe`.
2. Double-click the downloaded file.
3. If SmartScreen warns, click the small **"More info"** link, then **"Run"**.
4. Follow the installer to finish — Start menu and desktop shortcuts will be created.

### macOS 12+ (Apple Silicon)

> v1.0.0 ships an **Apple Silicon (M1 / M2 / M3 / M4)** build only. An Intel Mac build requires a separate compile, so it's been deferred — if you'd like one, please email **askNovelTimeline@gmail.com** and we'll add it.

1. From the [Latest Release](https://github.com/seo1westn2020/novelTimeline_release/releases/latest) page, download `novel-timeline_<version>_aarch64.dmg`.
2. Double-click the .dmg to mount it, then drag the novel-timeline icon into the **Applications** folder.
3. On first launch, **right-click the icon in the Applications folder → "Open"** (a plain double-click may be blocked).
   *(If your mouse doesn't support right-click — e.g. Apple Magic Mouse — hold **`Control`** while clicking instead.)*
4. Click **"Open"** once more in the security dialog, and the app launches normally.

> On macOS Sequoia (15) or later, if the above is also blocked, go to **System Settings → Privacy & Security** and click **"Open Anyway"** at the bottom.

> If none of the above works, open Terminal and remove the quarantine attribute:
> ```bash
> xattr -d com.apple.quarantine "/Applications/novel-timeline.app"
> ```

---

## Bug reports / feedback

- Email: **askNovelTimeline@gmail.com**
- Including the following details helps us respond faster:
  - OS and version (e.g., Windows 11 23H2, macOS 14.5)
  - novel-timeline version (hamburger menu → "About")
  - Steps to reproduce
  - Screenshots

---

We hope this tool is, in some small way, useful to your craft.
