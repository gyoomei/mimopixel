# 🎨 MiMoPixel

### Browser Pixel Art Editor — Powered by Xiaomi MiMo V2.5

A fully client-side pixel art editor that runs entirely in your browser. No servers, no API keys, no accounts. Draw pixel art with classic gaming palettes, create animations frame-by-frame, and export as PNG, sprite sheets, or animated GIFs. Zero dependencies, single HTML file.

[![Live Demo](https://img.shields.io/badge/Live-Demo-000?style=for-the-badge&logo=github)](https://gyoomei.github.io/mimopixel/)
[![Try Now](https://img.shields.io/badge/Try-Now-6366f1?style=for-the-badge&logo=googlechrome)](https://gyoomei.github.io/mimopixel/)
[![AI](https://img.shields.io/badge/AI-Xiaomi%20MiMo%20V2.5-f97316?style=for-the-badge)](https://mimo.xiaomi.com/)
[![Zero API](https://img.shields.io/badge/Zero-API-22c55e?style=for-the-badge)](#)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

---

## 📖 The Problem

Pixel art editors online are either heavyweight (Aseprite, Photoshop), require accounts (Piskel), or lack animation support. Mobile users are completely left out. There's no instant, zero-friction pixel art tool that works on any device with retro gaming palettes built in.

## ✨ How it works

```
You pick:     NES palette, 32×32 grid
You draw:     Pencil, fill, shapes, mirror mode
You animate:  Add frames, set FPS, preview loop
You export:   PNG (1×/4×/8×), sprite sheet, or animated GIF
```

**That's the entire UX** — draw, animate, export. No accounts, no uploads, no waiting.

## 🎯 Core Features

| Capability | Detail |
|---|---|
| Grid Sizes | 32×32, 48×48, 64×64 — switch anytime |
| Classic Palettes | NES (54 colors), PICO-8 (16), Game Boy (4) |
| Drawing Tools | Pencil, eraser, flood fill, eyedropper, line, rectangle, circle |
| Mirror Mode | Real-time horizontal symmetry for character design |
| Layers | Add/remove/toggle visibility — stack unlimited layers |
| Animation | Frame-by-frame timeline, duplicate/delete, adjustable FPS |
| Onion Skinning | Preview previous frame while drawing current |
| Live Preview | Animated playback at configurable FPS (1–30) |
| Export PNG | 1×, 4×, or 8× scale for crisp pixel art |
| Export GIF | Animated GIF with proper looping via LZW encoder |
| Sprite Sheet | All frames in a single grid image for game engines |
| Dark/Light Theme | Toggle with persistence |
| Mobile Ready | Touch drawing, responsive panels, horizontal scroll |
| Keyboard Shortcuts | B/E/G/I/L/R/C/M for tools, Ctrl+Z/Ctrl+Shift+Z undo/redo |

## 🏗️ Architecture

```
┌──────────────────────────────────────────────┐
│  Canvas 2D ── Layer Stack ── Frame Timeline  │
│       │              │              │         │
│  Pixel Grid    Visibility      GIF Encoder   │
│  (32-64)       Toggle         (LZW compress) │
│       │              │              │         │
│  Tools:        Layer Mgmt      Export:        │
│  pencil/eraser/    add/rm      PNG/GIF/       │
│  fill/eyedropper/  reorder     Sprite Sheet   │
│  line/rect/circle                              │
└──────────────────────────────────────────────┘
```

## 💡 Architecture Decisions

**Why single HTML?** Zero-API creative tools need zero build steps. One file opens everywhere — desktop, mobile, even offline. No npm, no bundler, no CORS issues.

**Why Canvas 2D?** Pixel art is fundamentally a grid of colored squares. Canvas 2D's `fillRect` is the most natural and performant primitive. `image-rendering: pixelated` keeps exports crisp at any scale.

**Why built-in GIF encoder?** External GIF libraries (gif.js, omggif) add 50KB+ and worker complexity. A minimal LZW encoder in ~80 lines handles the simple case (≤256 colors, no transparency optimization) perfectly for pixel art.

## 🧪 Try these examples

| Action | Result |
|---|---|
| Select NES palette → draw a 16×16 character | Classic retro game sprite |
| Mirror mode ON → draw left half of a face | Perfect symmetrical character |
| 4 frames at 8 FPS → export GIF | Smooth walk cycle animation |
| Game Boy palette → 4-shade landscape | Authentic GB aesthetic |
| Fill tool → checkerboard pattern → export 8× | High-res pixel art wallpaper |

## 🛠️ Stack

- **Frontend:** Vanilla JavaScript, single HTML file (~46KB)
- **Canvas:** HTML5 Canvas 2D with `image-rendering: pixelated`
- **GIF:** Custom LZW encoder (zero dependencies)
- **Fonts:** [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) + [Outfit](https://fonts.google.com/specimen/Outfit) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono)
- **Storage:** localStorage for theme preference
- **Hosting:** GitHub Pages (zero infra cost)

## 🚀 Quick Start

```bash
git clone https://github.com/gyoomei/mimopixel.git
open mimopixel/index.html
# or
python3 -m http.server 8080 -d mimopixel
```

## 📄 License

MIT — free for personal and commercial use.

**Built with 🧠 [Xiaomi MiMo V2.5](https://mimo.xiaomi.com/) · Submitted to [MiMo 100T program](https://mimo.xiaomi.com/)**
