# 🌌 Orion Music

<div align="center">

![Orion Music Icon](icons/orion128.png)

**A modern, minimalist, always-on-top floating YouTube Music desktop controller for Windows with Apple Dynamic Island notifications, Desktop Dynamic Notch, Smart DJ Crossfade, and Real-Time Audio Stream Optimization.**

[![Version](https://img.shields.io/badge/version-1.2.0-cyan.svg)](https://github.com/mattheusamaral/orion-music)
[![Electron](https://img.shields.io/badge/Electron-28.3.3-47848F.svg?logo=electron&logoColor=white)](https://electronjs.org)
[![Platform](https://img.shields.io/badge/platform-Windows-0078D6.svg?logo=windows&logoColor=white)](https://microsoft.com/windows)
[![Discord](https://img.shields.io/badge/Discord%20RPC-Enabled-5865F2.svg?logo=discord&logoColor=white)](https://discord.com)
[![Playback](https://img.shields.io/badge/Playback-Uninterrupted-00F2FE.svg)](#)

</div>

---

## ✨ Key Features

### 🌟 Dynamic Ambilight & Adaptive Ambient Glow
- **Real-Time Palette Extraction:** An intelligent chromatic algorithm samples the album artwork and projects an adaptive neon aura glow around both the floating player widget and the top-screen Dynamic Island.
- **Vibrant & Complementary Tones:** Seamlessly shifts ambient colors based on the genre and cover art mood.
- **One-Click Toggle:** Enable or disable Dynamic Ambilight instantly via the sun icon in the top header.

### 📜 Quick Queue Drawer ("Up Next" Panel)
- **Glassmorphic Slide-Out Drawer:** Expands the widget into a dual-column layout revealing upcoming queued songs with artwork thumbnails and track durations.
- **Direct Track Hopping:** Click any item in the queue to skip directly to that song without ever opening the heavy YouTube Music tab.
- **Live Queue Synchronization:** Constantly mirrors your active YouTube Music queue in real-time.
- **Zero-Blink Architecture:** Built on a pre-allocated canvas that eliminates Windows DWM flickering during drawer expansion.

### 🏝️ Top-Screen "Dynamic Island" Notifications
- **Authentic Dynamic Island Physics:** An ultra-sleek OLED black pill springs from the top-center of your screen upon track changes.
- **Rich Track Metadata & Adaptive Glow:** Displays circular high-resolution album art, song title, artist, ambient backlight matching the album palette, and animated equalizer bars.
- **Cascade Drop Integration:** When in Notch Mode, notifications smoothly descend directly below the notch (`y = dispY + 16`) to eliminate visual collisions.
- **Smart Hover Pause & Resume:** Automatically conceals itself if you move the cursor toward the notch controls and resumes for the remaining duration once the cursor departs.
- **Strict Album Art Sync:** Validated against active track video IDs to ensure artwork never displays stale covers from prior tracks.

### ⚡ Smart DJ Crossfade
- **Zero Silent Gaps:** Detects the last 3.2 seconds of any song, smoothly fades out volume, and skips YouTube Music’s silent tail directly into the next track.
- **Smooth Fade-In:** Ramps the incoming track volume from 15% to 100% over 2 seconds.
- **Interactive Control:** Toggleable via the cyan neon `⚡` button in the player or the system tray menu.

### 🔊 Real-Time Audio Normalizer (Acoustic Dynamics Compressor)
- **Web Audio Dynamics Compressor:** Operates directly on the audio stream in real-time.
- **Fast 3ms Attack:** Instantly cushions harsh, abrasive volume spikes across modern masterings.
- **Clean +2.0 dB Make-Up Gain:** Boosts quieter classical or acoustic tracks to create a uniform, comfortable listening experience.

### 🌌 4 Versatile Player Modes
1. **Normal Player (400 × 125 px):** High-res album art, draggable progress bar with seek, volume slider, opacity control, slide-out queue drawer, and instant search panel.
2. **Compact Pill (400 × 34 px / 54 px):** Ultra-slim horizontal bar featuring an active marquee track ticker and essential playback buttons.
3. **Floating Orion Badge (36 × 36 px / 42 × 42 px):** Ultra-compact floating neon badge with a reactive bass pulse.
   - **60 FPS Hardware Pointer Drag:** Fluid movement powered by `PointerEvents` and `requestAnimationFrame`.
   - **Snap to Edge:** Magnetically locks to the screen boundary when released near screen edges.
   - **Edge Drawer:** Tucks into the edge and slides out on mouse hover.
4. **Desktop Dynamic Notch (230 × 14 px / 380 × 64 px):**
   - **Idle State:** A 14px razor-thin bar anchored at the top-center of the screen displaying pure neon audio visualizer waves. Leaves all browser tabs and window titlebars 100% usable.
   - **Hover State:** Expands effortlessly upon mouse contact to 380 × 64 px, revealing full playback controls and a Return Button with coordinate memory.

### 🛡️ Continuous Stream & Focus Engine (Stream Optimizer)
- **Real-Time Stream Optimization:** Proactively cleans internal player metadata payloads, ensuring seamless track progression without unexpected stops.
- **Instant 0ms Interruption Auto-Recovery:** Immediately detects playback pauses or commercial interruptions, muting unwanted audio in 0ms and advancing directly to the musical content.
- **Dialogue & Popup Auto-Dismissal:** Automatically confirms *"Are you still listening?"* prompts (`ytmusic-you-there-renderer`) and dismisses upgrade dialogs.
- **Native Network Filter:** Discards heavy third-party telemetry beacons and tracker scripts at the Chromium socket layer to conserve bandwidth and system memory.

### 🎮 Discord Rich Presence
- Broadcasts current song title, artist, live playback state, and dynamic elapsed timestamps to your Discord profile.

### 🔒 Continuous Volume Lock
- Prevents YouTube Music from oscillating or resetting audio volume between track transitions.

---

## 🚀 Download & Installation (Windows 10 / 11)

### 📦 Official Windows Installer:
1. Navigate to the **[Releases](https://github.com/mattheusamaral/orion-music/releases)** page of this repository.
2. Download the official installer: **`OrionMusic-Setup-v1.2.0.exe`**.
3. Run the installer and complete the modern setup wizard.
4. Official shortcuts will be created on your **Desktop** and **Start Menu**.
5. Orion Music will launch immediately with full functionality, all 4 display modes, and continuous stream optimization active.

---

## 🔒 Security & Privacy

- **Zero Telemetry Collection:** Orion Music does not track, collect, or transmit your personal data.
- **Isolated Authentication:** Runs directly on YouTube Music within Electron's hardened isolated context (`contextIsolation: true`). Your Google credentials remain strictly on your local machine.
- **Clean Repository:** Sensitive configurations and development binaries are completely excluded.

---

## 📜 License & Credits

- **Author & Maintainer:** Matheus Amaral ([mattheus.amaaral@gmail.com](mailto:mattheus.amaaral@gmail.com))
- **Engine:** Electron 28, Chromium, Node.js, Web Audio API
- **License:** Proprietary / All Rights Reserved (see [LICENSE](LICENSE)).
  Copyright (C) 2026 Matheus Amaral. Unauthorized reproduction, modification, decompilation, or reverse engineering is strictly prohibited.
