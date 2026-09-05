# 🌌 Orion Music v1.2.0 — The Quantum Leap Release
## 🚀 Official Release Notes & Comprehensive Changelog (v1.1.0 ➔ v1.2.0)

> **Official Release:** `v1.2.0`  
> **GitHub Tag:** `v1.2.0`  
> **Author & Maintainer:** Matheus Amaral ([mattheus.amaaral@gmail.com](mailto:mattheus.amaaral@gmail.com))  
> **Platform:** Windows 10 / 11 (x64) — Electron 28.3.3 / Chromium / Node.js  
> **Repository:** [github.com/mattheusamaral/orion-music](https://github.com/mattheusamaral/orion-music)

---

## 🌟 Executive Summary: The Evolution from v1.1.0 to v1.2.0

Version **v1.2.0** of **Orion Music** marks the most substantial architectural upgrade in the history of the project. What originated in v1.1.0 as an elegant floating mini-player has matured into a full-fledged desktop playback environment featuring **4 unified display modes**, a **refactored 60 FPS hardware-accelerated drag engine**, a **4-layer Continuous Stream Engine**, **Dynamic Island 2.0 with cascade collision avoidance**, and **Dynamic Ambilight**.

---

## 📊 Side-by-Side Comparison: v1.1.0 vs v1.2.0

| Feature / Capability | Version 1.1.0 | Version 1.2.0 (Current) |
|---|---|---|
| **Display Modes** | 3 Modes (Normal, Compact, Badge with instability) | **4 Official Modes** (+ New *Desktop Dynamic Notch*) |
| **Stream Continuity** | Basic (frequent pauses and external interruptions) | **4-Layer Continuous Stream Engine** (API Optimization + 0ms Auto-Recovery + Dialogue Suppression + Telemetry Filter) |
| **"Are You Still Listening?" Prompts** | Paused playback requiring manual user clicks | **Instant 0ms Auto-Confirmation** and background playback resumption |
| **Promo Modals & Upsell Overlays** | Displayed overlay dialogs with frozen dark backdrops | **Automatic suppression and instant dismissal** of dialogs and backdrops |
| **Orion Mode (Badge)** | Suffered from IPC stutter, lag, and center-screen snapping bugs | **Refactored 60 FPS PointerEvents Engine** with magnetic *Snap to Edge* and sliding *Edge Drawer* |
| **Playback Queue ("Up Next")** | Hidden or basic | **Left-Side Slide-Out Drawer with Neon Cascade** and *Zero-Blink* architecture |
| **Dynamic Island (Track HUD)** | Basic top-screen overlap | **Dynamic Island 2.0** with *Cascade Drop* (`y+16`) and Smart Hover Pause/Resume |
| **Ambient Glow (Ambilight)** | Static single colors | **Adaptive Real-Time Dynamic Ambilight** synchronized with album art palette |
| **Smart DJ Crossfade** | Simple volume fade | **Gapless transition** with intelligent silent-tail trimming and smooth fade-in |
| **Album Art Synchronization** | Occasionally displayed artwork from the previous song | **Triple-validated sync** (MediaSession cross-check + internal player video ID) |
| **Windows Security & Launch** | Occasional SmartScreen / App Control warnings | **Registered `AppUserModelId` & Strict Single-Instance Lock** |

---

## 🛡️ 1. The 4-Layer Continuous Stream Engine (*Stream Optimizer 4.0*)

Orion Music v1.2.0 introduces a multi-tier pipeline engineered to guarantee uninterrupted, fluid listening, eliminating forced pauses and interface freezing:

* **Layer 1 — Main-World API Optimization (`preload-yt.js`):**
  Intercepts network calls directly inside YouTube Music's execution world (`/youtubei/v1/player` and `/youtubei/v1/next`), sanitizing metadata payloads to guarantee that the player streams music tracks directly without scheduling external pauses or unrequested insertions.
* **Layer 2 — Instant 0ms Interruption Auto-Recovery (`MutationObserver` + Player API):**
  Monitors player DOM mutations with zero latency (0ms), reacting instantaneously to any playback disruption:
  * **Intelligent Preventive Muting (`video.muted = true`):** Zero abrasive sound escapes during unexpected interruptions.
  * **Assisted Playback Advance:** Triggers native player APIs (`player.skipAd()`) to return immediately to primary track audio.
  * **Adaptive Rate Acceleration:** Fast-forwards non-musical intervals directly to conclusion (`playbackRate = 16.0`, `currentTime = duration`).
  * **Full Audio Restoration:** Seamlessly restores original listening volume and speed once standard music playback resumes.
* **Layer 3 — Dialogue & Modal Auto-Dismissal:**
  * Auto-confirms *"Are you still listening?"* prompts (`ytmusic-you-there-renderer`) and immediately unpauses the background stream.
  * Auto-dismisses modal promotional dialogs (`ytmusic-upsell-dialog-renderer`) and purges backdrop overlays.
  * Injected stylesheet permanently hides obstructive sidebar banners and promo containers.
* **Layer 4 — Native Chromium Network Filter (`main.js`):**
  Operates at the Electron socket layer via `session.defaultSession.webRequest.onBeforeRequest`, dropping heavy third-party telemetry beacons and tracking scripts (`doubleclick.net`, `googleadservices.com`, `/pagead/`, telemetry endpoints) to conserve bandwidth and system RAM.

---

## 🎛️ 2. The 4th Official Mode: Desktop Dynamic Notch

One of the standout visual innovations in v1.2.0:

* **Idle State (230 × 14 px):**
  * Anchored at the top-center of your monitor with an ultra-thin 14px profile.
  * Displays **pure neon equalizer wavebars (12 animated bars)** synchronized with real-time audio frequencies via Web Audio API.
  * The clickable footprint is strictly confined to these 14 pixels, leaving browser tabs, maximized window buttons, and taskbars 100% accessible.
* **Expanded State on Hover (380 × 64 px):**
  * Effortlessly expands when your mouse touches the notch.
  * Reveals album cover art, song title, artist, progress scrubber, full transport controls (`⏮`, `⏯`, `⏭`), and a **Return Button** that memorizes the exact screen coordinates `(x, y)` and mode you were in previously.
  * **Instant Auto-Retraction:** Instantly collapses back to 14px as soon as the cursor departs.

---

## ⚡ 3. Refactored 60 FPS Orion Mode (Badge) Physics

* **Hardware-Accelerated `PointerEvents`:** Complete migration to pointer-capture events with 60 FPS frame-throttling via `requestAnimationFrame`.
* **Zero IPC Lag:** Coalesced position updates eliminate message-queue congestion between Renderer and Main processes.
* **Fixed Edge Boundary Math (`clampAndSnapBounds`):**
  * Eliminated the legacy bug that inadvertently jumped the badge to the center of the screen.
  * **Restored Magnetic Snap to Edge:** Dropping the badge within 24px of screen edges locks it firmly 12px from the perimeter.
  * **Sliding Edge Drawer:** Automatically conceals the badge into the screen bezel and slides out smoothly upon cursor proximity.

---

## 🏝️ 4. Dynamic Island 2.0 with Cascade Anti-Collision

* **Cascade Drop Effect:** When in Notch Mode, Dynamic Island notifications gracefully cascade **directly below the notch** (`y = dispY + 16`), preventing visual overlaps.
* **Smart Hover Pause & Resume:** Automatically conceals itself if the cursor approaches the notch controls, re-emerging seamlessly to conclude its display timer once the cursor departs.

---

## 📜 5. Left-Side Quick Queue Drawer & Zero-Blink

* **Seamless Side-Drawer Layout:** Expands to the left with neon cascade animations displaying upcoming songs.
* **Zero-Blink DWM Architecture:** Utilizes a pre-allocated transparent viewport, eliminating 100% of Windows DWM window repainting flickers.
* **One-Click Track Hopping:** Click any song in the queue to jump straight to it.

---

## 🎧 6. Dynamic Ambilight, Smart DJ Crossfade & Volume Compressor

* Real-time chromatic artwork palette extraction with soft ambient glow projection.
* Silent-tail trimming and automated fade-in / fade-out across track boundaries.
* Real-time Web Audio dynamics compressor preventing jarring volume spikes.

---

## 📦 Official Release File

| File | Description |
|---|---|
| 📦 **`OrionMusic-Setup-v1.2.0.exe`** | **Official Windows Setup Installer** with modern wizard (Creates Desktop & Start Menu shortcuts) |

---

## 💻 How to Install or Update

1. Download the official installer: **`OrionMusic-Setup-v1.2.0.exe`**.
2. Run the installer and advance through the setup wizard.
3. If updating from a previous version, your settings and preferences are preserved automatically.
4. Orion Music will launch immediately with full continuous playback and all features active.

---

## 📝 Credits & Author
* **Author & Maintainer:** Matheus Amaral ([mattheus.amaaral@gmail.com](mailto:mattheus.amaaral@gmail.com))
* **Engine:** Electron 28, Chromium, Node.js, Web Audio API
* **License:** All Rights Reserved. Copyright (C) 2026 Matheus Amaral.
