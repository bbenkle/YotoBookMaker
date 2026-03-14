# YotoBookMaker

A native macOS app that splits audiobook files into individual chapter tracks and uploads them directly to your [Yoto](https://yotoplay.com) player.

> **Independent tool — not affiliated with or endorsed by Yoto Limited.**

![Platform](https://img.shields.io/badge/macOS-14%2B-blue) ![License](https://img.shields.io/badge/license-MIT-green)

---

## Download

Grab the latest release from the [Releases](../../releases) page, open the `.dmg`, and drag **YotoBookMaker** to your Applications folder.

---

## What it does

Yoto cards support custom audio content, but loading a full audiobook requires splitting it into individual chapter files and uploading each one. YotoBookMaker handles the entire process in five guided steps.

---

## How to use it

### 1 — Select your audiobook

Drop an audiobook file onto the window or click **Browse Files**. The book title and author are read automatically from the file.

**Supported formats:** M4B · M4A · MP3 · MP4 · WAV · AAC

---

### 2 — Configure

Choose how chapters should be detected and pick your export settings.

**Chapter detection methods:**

| Method | When to use |
|---|---|
| **Embedded Metadata** | Best choice — works with most M4B files from Audible, iTunes, Libro.fm, etc. Instant and accurate. |
| **Silence Detection** | For files with no chapter markers. Finds chapter breaks by analyzing gaps in the audio. |
| **JSON Timestamps** | Provide a JSON file with exact start times if you need full manual control. |

**Export options:** M4A or M4B · 64–192 kbps · Mono (recommended for Yoto)

#### JSON Timestamps format

If you choose **JSON Timestamps**, browse to a `.json` file containing your chapter list. Each entry needs a title and a start/end time:

```json
[
  { "title": "Opening Credits", "start": "0:00:00", "end": "0:05:42" },
  { "title": "Chapter 1",       "start": "0:05:42", "end": "0:38:17" },
  { "title": "Chapter 2",       "start": "0:38:17", "end": "1:11:04" }
]
```

Times use `H:MM:SS` or `M:SS` format. Milliseconds are also supported (`start_ms` / `end_ms`). An example file is included in the [repository](example-chapters.json).

---

### 3 — Split

Click **Start Splitting**. A live log shows what's happening as each chapter is detected and exported. The chapter list stays on screen after splitting so you can review results, and you can re-run with different settings at any time.

---

### 4 — Icons

Each chapter gets a color-coded pixel art icon, generated entirely on your Mac — no internet needed.

- **Generate All** — auto-generate icons for every chapter
- **Randomize All** — give every chapter a unique random color scheme
- **Per-chapter customization** — hover any chapter card to generate, redo, upload your own image, or customize the colors and pattern
- **Bulk import** — choose a folder of images and they'll be matched to chapters by number in the filename (e.g. `ch-01.png`, `Chapter 22.jpeg`)

---

### 5 — Upload

Sign in to your Yoto account — no password is entered into the app; you approve access in your browser. Then click **Upload to Yoto** and the app handles the rest: uploading audio, icons, and creating a ready-to-play playlist on your card.

Your sign-in is saved securely in the macOS Keychain so you only need to do it once.

---

## Privacy

| | |
|---|---|
| Audio splitting | Stays entirely on your Mac |
| Icon generation | Stays entirely on your Mac |
| Speech recognition (used during silence detection) | On-device. Only falls back to Apple's servers if the on-device model is unavailable — this is logged if it happens |
| Upload | Sent to Yoto's servers — only when you click Upload |

No analytics. No telemetry. No third-party services.

---

## Requirements

- macOS 14 Sonoma or later
- A [Yoto account](https://my.yotoplay.com) (only needed for the upload step)

---

## Disclaimer

YotoBookMaker is an independent, community-built tool. It is **not affiliated with, endorsed by, or supported by Yoto Limited**. Yoto, the Yoto logo, and Yoto Player are trademarks of Yoto Limited.

Only upload audio content you own or have the legal right to use — such as DRM-free audiobook purchases or public domain recordings. Do not upload commercially licensed content without the rights holder's authorization.

---

## License

MIT — see [LICENSE](LICENSE) for details.
