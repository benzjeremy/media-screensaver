# 🌌 Media Screensaver

[![Go Reference](https://pkg.go.dev/badge/github.com/benzjeremy/media-screensaver.svg)](https://pkg.go.dev/github.com/benzjeremy/media-screensaver)
[![Go Report Card](https://goreportcard.com/badge/github.com/benzjeremy/media-screensaver.svg)](https://goreportcard.com/report/github.com/benzjeremy/media-screensaver)
[![CI](https://github.com/benzjeremy/media-screensaver/actions/workflows/ci_arch.yml/badge.svg)](https://github.com/benzjeremy/media-screensaver/actions)
[![Coverage](https://codecov.io/gh/benzjeremy/media-screensaver/branch/main/graph/badge.svg)](https://app.codecov.io/gh/benzjeremy/media-screensaver)
[![Awesome Go](https://awesome.re/mentioned-badge.svg)](https://github.com/avelino/awesome-go)
[![Release](https://img.shields.io/github/v/release/benzjeremy/media-screensaver)](https://github.com/benzjeremy/media-screensaver/releases)
[![Status: Pre-Release](https://img.shields.io/badge/Status-Pre--Release%20%2F%20WIP-orange.svg)](https://github.com/benzjeremy/media-screensaver)
[![License: GPL-3.0](https://img.shields.io/badge/License-GPL--3.0-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20Windows-lightgrey.svg)]()
[![Security: AES-256-GCM](https://img.shields.io/badge/Security-AES--256--GCM-success.svg)](https://en.wikipedia.org/wiki/Galois/Counter_Mode)

> 🌐 **Official Website:** [https://media-screensaver.benzjeremy.pp.ua/](https://media-screensaver.benzjeremy.pp.ua/)
> 📖 **Official Wiki & Documentation:** [https://media-screensaver.benzjeremy.pp.ua/wiki/](https://media-screensaver.benzjeremy.pp.ua/wiki/)

> [!IMPORTANT]
> ### 🚧 Pre-Release / Active Development Notice
> **This software is not yet finished and is under active development.**  
> All releases and binaries are **Pre-Releases** (Work in Progress), even if originally tagged or announced without a pre-release flag. Features, hardware tap APIs, and UI designs are actively developed and continually updated.

> An elegant, resource-friendly desktop screensaver with **Live OLED clock**, **Spotify song metadata**, **intelligent ad handling**, **focused clean design**, **hardware-coupled audio spectrum analysis (PulseAudio/PipeWire)**, **dynamic cover color palette**, **circular visualizer**, and an **inactivity daemon** for Linux (WebKitGTK) and Windows (App Mode). **100% Local-First & Zero Bloat.**

---

## ✨ Features & Highlights in v1.4

- 📢 **Intelligent Ad Detection & Handling (Spotify Free):**
  - Detects advertisements via MPRIS track IDs (`:ad:`), metadata, and API payloads.
  - Automatically switches to an embedded dark-themed ad placeholder (`ad-placeholder.svg`) with a subtle pulsating "ADVERTISEMENT" badge.
  - Clean fallback metadata ("Spotify Advertisement" / "Commercial Break") instead of frozen stale cover art or rendering glitches.
- 🎨 **Focused Clean Layout (Redundancy-Free Cover Presentation):**
  - Completely replaced the redundant vinyl/CD visual with a centered album art aesthetic featuring soft ambient glow and rounded geometry.
- 🎛️ **True Hardware Audio Spectrum Analysis (PulseAudio / PipeWire / WASAPI):**
  - Direct hardware tap of system audio via monitor sink.
  - 64-band FFT analysis (Cooley-Tukey Radix-2) with 60 FPS WebSocket streaming (`/api/audio-stream`).
  - Zero-latency visualization of real bass, mid, and treble frequencies rather than simulation.
- 🎨 **Dynamic Cover Palette (Adaptive Glow & Accents):**
  - Fast color space reduction and dominance extraction (K-Means / quantization) in Go.
  - Smooth 1.2s CSS/Canvas color transitions adapting screensaver glow and accents to the album's primary and secondary palette.
- 🌊 **Circular Visualizer Mode:**
  - 360° radial frequency spectrum around album art with glowing peak highlights.
- 💤 **Idle Detection Daemon (`--idle-timeout=N`):**
  - Monitors user inactivity via `xprintidle` / D-Bus / Win32 and activates the screensaver automatically.
- 🕒 **OLED Digital Clock & Date:**
  - High-contrast neon time display with configurable seconds toggle and 12h/24h format support.
- 🎨 **Color Accents & Themes (4 Styles):**
  - 🟢 **Spotify Classic:** Signature Spotify green with soft ambient neon.
  - 🔷 **Electric Cyan:** Futuristic ice-blue neon.
  - 🟣 **Neon Purple:** Cyberpunk violet / deep magenta.
  - 🟡 **Sunset Amber:** Warm gold / amber tone.
- 🌊 **Multi-Mode Canvas Audio Visualizer:**
  - **Bars:** 48 frequency bars with physical peak-hold drops and gradients.
  - **Wave:** Flowing oscilloscope wave with soft neon blur.
  - **Mirrored:** Mirrored dual columns radiating from the center.
  - Configurable sensitivity and responsiveness.
- 🎛️ **Interactive Playback Controls:**
  - **Progress Scrubber:** Click anywhere on the track bar to seek.
  - **Volume Slider:** Seamless volume adjustment via slider or keyboard shortcuts.
- 🎵 **Zero-Config Spotify MPRIS:**
  - Automatically detects Spotify Desktop and `spotify_player` on Linux over D-Bus without requiring API keys.
  - Smooth standby demo mode when Spotify is paused or closed.
- 🛡️ **Strict Security Architecture (Jeremy Benz Standards):**
  - **Cryptography:** AES-256-GCM token encryption derived via PBKDF2 (1,000,000 rounds, hardware fingerprint, unique salt stored in `~/.config/spotify-screensaver/salt.bin`).
  - **Network Isolation:** Local HTTP server binds strictly to `127.0.0.1:43210`.
  - **Anti-DNS-Rebinding & Anti-CSRF:** Strict validation of `Host` and `Origin` headers.
  - **Security Headers:** `X-Frame-Options: DENY`, `X-Content-Type-Options: nosniff`, `Referrer-Policy: no-referrer`, strict CSP.
- 💤 **Automatic Inactivity Fade:** Hides mouse cursor and HUD overlays after 4 seconds of idle time.

---

## ⌨️ Keyboard Shortcuts

| Key | Action |
|---|---|
| <kbd>Space</kbd> | Play / Pause |
| <kbd>→</kbd> | Next Track |
| <kbd>←</kbd> | Previous Track |
| <kbd>↑</kbd> / <kbd>↓</kbd> | Volume +5% / -5% |
| <kbd>F</kbd> or <kbd>F11</kbd> | Toggle Fullscreen Mode |
| <kbd>ESC</kbd> | Exit Screensaver / Close Settings Modal |

---

## 🚀 Installation & Usage

### 1. Download Precompiled Binaries (Recommended)

Download the matching binary from the [Releases page (Latest)](https://github.com/benzjeremy/media-screensaver/releases):

- **Linux (AMD64):** Download `media-screensaver-*-linux-amd64.tar.gz`, extract, and execute `./media-screensaver`.
- **Windows (AMD64):** Download `media-screensaver-*-windows-amd64.zip`, extract, and run `media-screensaver.exe`.

### 2. Build from Source (Linux with WebKitGTK)

```bash
git clone https://github.com/benzjeremy/media-screensaver.git
cd media-screensaver
go build -o media-screensaver .
./media-screensaver
```

### 3. Run in Fullscreen Screensaver Mode

```bash
./media-screensaver -fullscreen
```

### 4. Run in Default Browser Mode

```bash
./media-screensaver -browser
```

### 5. Cross-Compile for Windows

```bash
CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build -o bin/media-screensaver-windows-amd64.exe .
```

---

## 📚 Wiki & Documentation

Detailed documentation, shortcuts, and audio visualizer guides are available in our official web wiki:  
👉 **[Media Screensaver Wiki: https://media-screensaver.benzjeremy.pp.ua/wiki/](https://media-screensaver.benzjeremy.pp.ua/wiki/)**

- **MPRIS D-Bus Architecture**: [Zero-Config Setup](https://media-screensaver.benzjeremy.pp.ua/wiki/#mpris)
- **Audio Visualizer Modes**: [FFT Spectrum Analysis](https://media-screensaver.benzjeremy.pp.ua/wiki/#visualizer)
- **Installation & Daemon**: [Linux & Windows](https://media-screensaver.benzjeremy.pp.ua/wiki/#installation)
- **Keyboard Shortcuts**: [Quick Controls](https://media-screensaver.benzjeremy.pp.ua/wiki/#shortcuts)
- **Troubleshooting**: [WebKitGTK Performance & DMABUF](https://media-screensaver.benzjeremy.pp.ua/wiki/#security)

---

## ⚖️ License & Author

- **Developer:** Jeremy Benz ([@benzjeremy](https://github.com/benzjeremy))
- **License:** [GNU General Public License v3.0 (GPL-3.0)](LICENSE)

## Project rename

Spotify Screensaver is now **Media Screensaver**. This project remains in development (pre-release). Existing local data continues to use the legacy storage directory for compatibility.

## A personal note from Jeremy Benz

> I decided we needed to rename Spotify Screensaver to media-screensaver to avoid potential intellectual-property and trademark issues. The previous name directly referenced Spotify AB's brand. I wanted to make this change early, before it could lead to legal trouble. Same project, new name — thank you for sticking with it.
>
> — Jeremy Benz, project creator

Windows icon resource: regenerate `app_windows_amd64.syso` after icon changes with `x86_64-w64-mingw32-windres app.rc -O coff -o app_windows_amd64.syso`.
