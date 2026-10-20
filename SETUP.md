# breathing — Setup Guide

A single-file **breathing exercise web app** (`breathing.html`) that guides you through timed
breath cycles — 4-7-8 Relax, 4-4-4-4 Box, 5-5 Coherent, 2-2 Energize, 4-4-6-2 Sleep, and
3-6 Calm — with a fluid animated orb, optional binaural (theta-wave) beats that rise and
fall with your breath, and a live IST (Indian Standard Time) analog + digital clock.

It is a pure front-end project: one self-contained HTML file with inline CSS and JavaScript,
plus the Web Audio API for the binaural tones. No build step, no server, no dependencies.

**Made by Sudais Alam**

---

## Table of Contents

- [Project Overview](#project-overview)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running Locally](#running-locally)
- [Project Structure](#project-structure)
- [Troubleshooting](#troubleshooting)
- [Credit](#credit)

---

## Project Overview

**breathing** (titled *Fluid Energy Breathing* in the page) is a focus and relaxation tool
that runs entirely in the browser. You pick a breathing mode, follow the expanding/
contracting orb for inhale / hold / exhale cues, and optionally enable theta-wave binaural
beats that swell and fade in sync with each phase of your breath for deeper immersion. A
live IST clock is rendered in both analog and digital form.

Breathing modes included:

| Mode | Pattern | Use case |
|------|---------|----------|
| 4-7-8 Relax | inhale 4s · hold 7s · exhale 8s | Wind down, anxiety relief |
| 4-4-4-4 Box | inhale 4s · hold 4s · exhale 4s · hold 4s | Focus, composure |
| 5-5 Coherent | inhale 5s · exhale 5s | Heart-rate variability / coherence |
| 2-2 Energize | inhale 2s · exhale 2s | Quick alertness boost |
| 4-4-6-2 Sleep | inhale 4s · hold 4s · exhale 6s · hold 2s | Drift off to sleep |
| 3-6 Calm | inhale 3s · exhale 6s | General calm |

Extras:

- **Binaural beats**: theta-wave (~4–8 Hz) audio generated with the Web Audio API that
  rises and falls with the breath phase. Headphones recommended.
- **Live IST clock**: analog and digital clock ticking strictly on Indian Standard Time.
- **Settings panel**: tune timings, toggle audio, and switch ambient visuals.

---

## Prerequisites

| Tool | Version | Notes |
|------|---------|-------|
| **A modern web browser** | Chrome, Edge, Firefox, Safari (current) | Web Audio API + Canvas required |
| **Headphones** (optional) | any | Needed to actually hear binaural beats as intended |
| **Local web server** (optional) | any | Only needed if the file is served over `http://` instead of opened directly |

No Node.js, npm, or build tools are required — the app is one static HTML file.

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/sudaisalamboy/breathing.git
cd breathing
```

That's it — there are no dependencies to install.

### 2. (Optional) Serve it over HTTP

If you prefer `http://localhost` over opening the file directly (some browsers restrict
audio autoplay on `file://`), use any static server:

```bash
# Python 3
python3 -m http.server 8000

# Node.js (http-server)
npx http-server -p 8000
```

---

## Running Locally

### Option A — Open the file directly

Double-click `breathing.html`, or:

```bash
# macOS
open breathing.html
# Linux
xdg-open breathing.html
# Windows (from Explorer)
start breathing.html
```

### Option B — Serve and open

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/breathing.html
```

### Using the app

1. Pick a breathing mode from the buttons (4-7-8 Relax, Box, Coherent, Energize, Sleep, Calm).
2. Press **Start** and follow the orb — it expands on inhale, holds, and contracts on exhale.
3. Open the **settings** panel (gear icon, top-left) to enable binaural beats and adjust timings.
4. For binaural beats, **wear headphones**; the effect depends on stereo separation.
5. The IST clock runs continuously in the corner regardless of mode.

> Audio hint: most browsers require a user gesture before audio can play. Pressing **Start**
> or toggling the beats on counts as that gesture.

---

## Project Structure

```
breathing/
├── breathing.html                          # The entire app (HTML + CSS + JS, inline)
├── README.md                               # Short project description
├── SETUP.md                                # This file
├── Screenshot 2026-06-17 022907.png        # Original screenshot of the running app
└── preview/
    ├── preview.png                          # Dark-theme preview banner (1200x750)
    └── screenshot-1.png                     # Copy of the app screenshot for README embed
```

The whole application lives in `breathing.html`. There is no `src/` folder, no
`package.json`, and no build pipeline.

---

## Troubleshooting

**No sound / binaural beats silent**
- Binaural beats need **stereo headphones** — they will not work on mono speakers.
- Browsers block autoplay until you interact with the page. Click **Start** or toggle the
  beats on after the page loads.
- Check your OS / browser volume and that the tab isn't muted (speaker icon in the tab).

**Orb / animation looks static**
- Make sure hardware acceleration is enabled in your browser settings.
- Close other heavy tabs — the canvas animation is GPU/CPU driven.

**Clock shows the wrong time**
- The clock renders **Indian Standard Time (IST, UTC+5:30)** by design, not your local
  time. That is intended behaviour.

**Page opens as raw HTML / downloads instead of rendering**
- You are probably serving it with the wrong MIME type. Use `python3 -m http.server` or
  any standard static server, or just open `breathing.html` directly with `file://`.

**File does not open on double-click**
- Associate `.html` files with a browser in your OS settings, or use
  `open`/`xdg-open`/`start` from the command line as shown above.

---

## Credit

**Made by Sudais Alam** — <https://github.com/sudaisalamboy>
