[README.md](https://github.com/user-attachments/files/31749846/README.md)
# 🌌 Orion Music

<div align="center">

![Orion Music Icon](icons/orion128.png)

**A modern, minimalist, always-on-top floating YouTube Music desktop player with Apple Dynamic Island notifications, Smart DJ Crossfade, and Real-Time Audio Normalization.**

[![Version](https://img.shields.io/badge/version-1.1.0-cyan.svg)](https://github.com/mattheusamaral/orion-music)
[![Electron](https://img.shields.io/badge/Electron-28.3.3-47848F.svg?logo=electron&logoColor=white)](https://electronjs.org)
[![Platform](https://img.shields.io/badge/platform-Windows-0078D6.svg?logo=windows&logoColor=white)](https://microsoft.com/windows)
[![Discord](https://img.shields.io/badge/Discord%20RPC-Enabled-5865F2.svg?logo=discord&logoColor=white)](https://discord.com)
[![AdBlock](https://img.shields.io/badge/AdBlock-Integrated-00F2FE.svg)](#)

</div>

---

## ✨ Features

### 🏝️ Top-Screen "Dynamic Island" Notifications
- **Authentic Apple Dynamic Island Physics:** An ultra-sleek OLED black pill springs from the top-center of your screen upon track changes.
- **Rich Track Metadata:** Displays circular high-resolution album art, song title, artist, and animated cyan sound wave bars.
- **3-Second Display Duration:** Displays for exactly 3.0 seconds before smoothly contracting.
- **Click-Through & Non-Intrusive:** Never steals typing focus and does not block clicks in games or work applications.
- **Strict Album Art Sync:** Guaranteed to match the song that just started, completely eliminating stale previous-track artwork.

### ⚡ Smart DJ Crossfade
- **Zero Silent Gaps:** Detects the last 3 seconds of any song, smoothly fades out volume, and skips YouTube Music’s silent tail directly into the next track.
- **Smooth Fade-In:** Ramps the incoming track volume from 15% to 100% over 2 seconds.
- **Interactive Control:** Toggleable via the cyan neon `⚡` button in the player or the system tray menu.

### 🔊 Real-Time Audio Normalizer (Anti-Volume Spike)
- **Acoustic Dynamics Compressor:** Uses the Web Audio API directly on the audio stream.
- **Fast 3ms Attack:** Immediately compresses jarring volume spikes on modern loud tracks.
- **Clean +2.0 dB Make-Up Gain:** Boosts quieter classical or acoustic tracks to create a uniform, comfortable listening experience.

### 🌌 3 Versatile Player Modes
1. **Normal Mode (400 × 125 px):** High-res album cover, track details, draggable progress bar with seek, volume slider, opacity control, and instant search panel.
2. **Compact Bar (400 × 34 px):** Ultra-slim horizontal ticker with marquee title and essential transport buttons.
3. **Orion Badge Mode (36 × 36 px):** Ultra-compact floating neon badge with pulsing glow.
   - **Pointer-Capture Dragging:** Fluid movement with grab/grabbing cursor.
   - **Auto-Collapse on Blur:** Click to peek and change tracks; clicking away outside the player automatically shrinks it back to the Orion Badge!
   - **Edge Docking Drawer:** Push the badge against your screen edge to hide it into an interactive neon tab that slides out on hover.

### 🛡️ Built-in Ad-Blocker & Ad-Skipper
- Intercepts and blocks ad domains at the network layer.
- Automatically mutes and fast-forwards through video commercials and dismisses YouTube Music upgrade banners.

### 🎮 Discord Rich Presence
- Shows live playback status, current song, artist, and elapsed/total time in your Discord profile.

### 🔒 Continuous Volume Lock
- Prevents YouTube Music from resetting or oscillating volume across track changes.

---

## 🚀 Getting Started

### Prerequisites
- [Node.js](https://nodejs.org) (v18 or newer recommended)
- npm (included with Node.js)

### Installation

1. **Clone this repository:**
   ```bash
   git clone https://github.com/mattheusamaral/orion-music.git
   cd orion-music
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the application:**
   ```bash
   npm start
   ```

---

## 📦 Building & Packaging

### 1. Build Standalone Portable Executable
To package the app into a standalone Windows binary (`dist/Orion Music-win32-x64`):
```bash
node build.js
```
*(or `npm run package`)*

### 2. Compile Windows Setup Installer
If you have [Inno Setup 6](https://jrsoftware.org/isinfo.php) installed:
```bash
iscc installer.iss
```
This compiles `dist/installer/OrionMusic-Setup-v1.1.0.exe` with LZMA2 multithreaded compression.

---

## 🔒 Security & Privacy

- **No Remote Telemetry:** Orion Music does not collect, track, or transmit your personal data.
- **Direct & Secure:** Streams directly from YouTube Music using Electron's secure isolated contexts (`contextIsolation: true`).
- **Clean Repository:** Sensitive paths, personal configurations, and heavy binary artifacts are fully excluded via `.gitignore`.

---

## 📜 License & Credits

- **Author:** Matheus Amaral (`mattheus.amaaral@gmail.com`)
- **Copyright:** Copyright (C) 2026 mattheus.amaaral@gmail.com. All rights reserved.
- **License:** Proprietary / All Rights Reserved (see [LICENSE](LICENSE)).
