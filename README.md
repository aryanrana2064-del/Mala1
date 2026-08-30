# 🙏 MalaVerse

A premium, installable **digital prayer bead (mala/japa) counter** — built as a single-file, dependency-free Progressive Web App (PWA) with a glassmorphism design, smooth animations, and offline support.

![Theme](https://img.shields.io/badge/theme-dark%20glassmorphism-1a1a2e) ![PWA](https://img.shields.io/badge/PWA-ready-ffd966) ![Dependencies](https://img.shields.io/badge/dependencies-none-3fae6a)

---

## ✨ Features

- **Simple, focused counting** — a single "Volume Up" button increments your count, "Reset" clears it back to zero.
- **Mala round tracking** — automatically shows how many full malas (108 beads) you've completed.
- **Premium glassmorphism UI** — frosted glass card, dark radial gradient background (`#1a1a2e` → `#0f0f1a`), and a warm golden counter (`#ffd966`).
- **Satisfying animations** — the counter "pops" (scale 1 → 1.12 → 1) on every increment, and buttons depress with a tactile `translateY` press effect.
- **Haptic feedback** — vibrates on supported mobile devices when you count or reset.
- **Keyboard shortcuts** — count and reset without touching the screen (see below).
- **Persistent count** — your count is saved locally, so it survives page reloads and app restarts.
- **Installable PWA** — add it to your home screen and use it like a native app, fully offline.
- **Mobile-first & responsive** — large (48px+) touch targets, works beautifully on any screen size.
- **Zero dependencies** — pure HTML, CSS, and JavaScript. No frameworks, no build step.

---

## 📱 How to Use

1. Open `index.html` in any modern browser (or visit the deployed URL).
2. Tap **🔊 Volume Up** each time you complete a repetition (bead/mantra).
3. Watch the golden counter pop with every tap, and see your mala round count update automatically every 108 counts.
4. Tap **⟳ Reset** to start a fresh count (e.g., for a new mala session).
5. For the best experience, **install it to your home screen**:
   - **Android (Chrome):** Tap the menu (⋮) → "Add to Home screen" / "Install app".
   - **iOS (Safari):** Tap the Share icon → "Add to Home Screen".
   - **Desktop (Chrome/Edge):** Click the install icon in the address bar.

Once installed, the app works fully **offline** thanks to the built-in service worker.

---

## ⌨️ Keyboard Shortcuts

| Key             | Action        |
|-----------------|---------------|
| `Space` or `+`  | Increment count |
| `R`             | Reset count   |

---

## 📦 Project Structure

```
malaverse/
├── index.html                        # Full app: HTML + CSS + JS (single file)
├── manifest.json                     # PWA manifest (icons, theme, display mode)
├── sw.js                             # Service worker — offline caching
├── icon-192.png                      # App icon, 192×192 (placeholder — see note below)
├── icon-512.png                      # App icon, 512×512 (placeholder — see note below)
├── .github/
│   └── workflows/
│       └── build-apk.yml             # GitHub Actions: auto-builds an Android APK
└── README.md                         # This file
```

> ⚠️ **Icon placeholders:** `icon-192.png` and `icon-512.png` are referenced by `manifest.json` and `sw.js` but are **not included** in this generation — you'll need to add your own square PNG icons at those exact filenames (192×192 and 512×512 pixels). For best results on Android, design them with a maskable-safe zone (keep key content within the center ~80% of the canvas), since the manifest declares both `"purpose": "any"` and `"purpose": "maskable"`.

---

## 🤖 Automatic APK Builds (GitHub Actions)

This repo includes a GitHub Actions workflow at `.github/workflows/build-apk.yml` that automatically packages the PWA into an **Android APK** using [PWABuilder](https://www.pwabuilder.com/).

**How it works:**
- **Trigger:** Runs automatically on every push to the `main` branch (or manually via "Run workflow").
- **Steps:** Checks out the code → sets up Node.js 20 → installs the `@pwabuilder/pwabuilder` CLI → serves the PWA locally → builds the Android package (`com.mala.verse`) → uploads the resulting `.apk`/`.aab` as a downloadable build artifact.

**To download your APK:**
1. Go to your repository's **Actions** tab on GitHub.
2. Select the latest **"Build Android APK"** workflow run.
3. Scroll to the **Artifacts** section and download `malaverse-apk`.
4. Unzip it to find your installable `.apk` file.

> Package ID: `com.mala.verse` · App name: **MalaVerse**

---

## 🎨 Design Specs

| Element        | Value |
|----------------|-------|
| Background     | `radial-gradient(#2d2d44, #0f0f1a)` |
| Card           | `rgba(255,255,255,0.06)` with `backdrop-filter: blur(20px)` |
| Counter color  | `#ffd966` |
| Primary text   | `#f0e6d0` |
| Muted text     | `#b8ad9a` |
| Increment button | Green gradient (`#3fae6a` → `#267a4a`) |
| Reset button   | Red gradient (`#e8556b` → `#b23048`) |
| Pop animation  | `scale(1) → scale(1.12) → scale(1)` over `0.12s` |
| Button press   | `translateY(6px)` |

---

## 🛠️ Tech Notes

- No external libraries, fonts, or CDNs — everything is self-contained in `index.html`.
- Uses the system font stack (Segoe UI and native fallbacks) for fast loading and a native feel.
- Count is persisted with `localStorage`.
- Fully keyboard-accessible and screen-reader-friendly (`aria-live` region on the counter).

---

Ram Ram 🙏

