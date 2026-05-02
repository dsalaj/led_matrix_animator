```
 ██╗     ███████╗██████╗     ███╗   ███╗ █████╗ ████████╗██████╗ ██╗██╗  ██╗
 ██║     ██╔════╝██╔══██╗    ████╗ ████║██╔══██╗╚══██╔══╝██╔══██╗██║╚██╗██╔╝
 ██║     █████╗  ██║  ██║    ██╔████╔██║███████║   ██║   ██████╔╝██║ ╚███╔╝ 
 ██║     ██╔══╝  ██║  ██║    ██║╚██╔╝██║██╔══██║   ██║   ██╔══██╗██║ ██╔██╗ 
 ███████╗███████╗██████╔╝    ██║ ╚═╝ ██║██║  ██║   ██║   ██║  ██║██║██╔╝ ██╗
 ╚══════╝╚══════╝╚═════╝     ╚═╝     ╚═╝╚═╝  ╚═╝   ╚═╝   ╚═╝  ╚═╝╚═╝╚═╝  ╚═╝
                                                              A N I M A T O R
```

> *"The sky above the port was the color of television, tuned to a dead channel."*
> — William Gibson, **Neuromancer**

---

## // JACK IN

A **zero-dependency, single-file** animation studio for LED matrices. No server. No build step. No cloud. Open `index.html` in a browser and start pushing photons.

Built for the kind of hardware that glows in dark server rooms — P5 pixel panels, P10 outdoor matrices, custom RGB grids. Exports looping GIFs. Shares state via URL. Runs entirely in your browser.

---

## // SYSTEM REQUIREMENTS

```
HARDWARE:  Any machine with a modern browser
SOFTWARE:  Chrome / Firefox / Safari / Edge (2020+)
BACKEND:   NONE
INSTALL:   NONE
```

Clone the repo. Open `index.html`. That's it. The street finds its own uses for things.

---

## // FEATURES

### Matrix Resolution
Set any custom width × height for your LED grid. Landscape for marquees, portrait for tower panels. Orientation-sensitive controls auto-adapt when you switch modes.

### LED Pitch Modes
Simulate real-world hardware — from tight indoor displays to wide-pitch outdoor panels:

| Mode | Pitch | Real-world equiv. |
|------|-------|-------------------|
| Compact | 5:4 | — |
| Normal | 7:6 | indoor standard |
| Large | 10:9 | — |
| XL | 13:12 | — |
| Sparse S | 8:3 | **P5** |
| Sparse M | 10:4 | **P7** |
| Sparse L | 13:4 | **P10** |
| Sparse XL | 16:5 | **P16** |

### Animation Layers
Stack layers like a deck of ICE. Each is composited in order, top to bottom.

**MATRIX RAIN** — Cascading character rain with independent head/tail color control. Katakana, Latin, or mixed charset. Adjustable density, speed, and trail length. The classic.

**TEXT** — Scrolling, bouncing, pulsing, static, or typewriter text. Horizontal or vertical orientation with independent direction control (←/→/↑/↓). Per-layer glitch probability. Works with VT323, Share Tech Mono, or system monospace. Supports full Unicode — katakana welcome.

**GLITCH** — Corrupted display artifacts: block corruption, scanline tears, chromatic aberration, or raw noise. Dial the intensity from subtle interference to full signal death.

**NOISE** — Pixel-level phosphor noise. Adds analog warmth to any composition. Low intensity is invisible; high intensity looks like a dying CRT in the rain.

### Presets
Ten named presets loaded and ready:

| Name | Vibe |
|------|------|
| `MATRIX RAIN` | The classic green cascade |
| `SCROLL TEXT` | Simple red marquee |
| `GLITCH STORM` | Pure signal corruption |
| `CYBERPUNK` | Rain + scrolling text overlay |
| `JAPAN MODE` | Katakana rain, full-width text |
| `AMBER TERMINAL` | Retro phosphor flatline |
| `CHROME AND ICE` | Cool blue rain, white text |
| `RED ALERT` | Pulsing crimson emergency |
| `GHOST IN THE SHELL` | Dim kana rain, whispered text |
| `BINARY FLOOD` | Dense white-headed rain |

Plus a **RANDOMIZE** button that generates a unique composition using short quotes from *Neuromancer*. Hit it until the ice cracks.

### GIF Export
Renders a perfectly looping animated GIF at your chosen FPS and duration. Uses a full LZW encoder — no canvas-to-GIF libraries, no server upload. The file is yours the moment it's done.

### URL Sharing
Every parameter — matrix size, LED pitch, all layers and their properties — is serialized into the URL hash. Copy the address bar. Send it. The recipient opens it and sees exactly what you built. Static frontend only, no database.

---

## // CONTROLS REFERENCE

```
LEFT PANEL    — Layer stack. Add, remove, reorder layers.
CENTER        — Live preview canvas. Updates in real time.
RIGHT PANEL   — Properties for the selected layer.
BOTTOM BAR    — Matrix resolution, LED pitch, FPS, duration.
TOP RIGHT     — GIF export + URL copy.
PRESETS       — Right side panel tab.
```

**Layer types:**
- `[+] RAIN` — Add Matrix Rain layer
- `[+] TEXT` — Add Text layer  
- `[+] GLITCH` — Add Glitch layer
- `[+] NOISE` — Add Noise layer

---

## // ANIMATION MATH

All animations are deterministic functions of `t ∈ [0, 1)`. This guarantees perfect GIF loops — the last frame always flows back into the first.

Scroll, bounce, and pulse speeds are internally snapped to integers so the modulo condition `f(0) = f(1)` is always satisfied. Matrix Rain column speeds are also integer-snapped with per-column variation for organic feel without loop drift.

---

## // COLOR PALETTE

The UI ships with a cyberpunk-native palette:

```
NEON RED    #FF0033  — primary accent, alert, heat
AMBER       #FFB800  — legacy terminal, warning
MATRIX GREEN #00FF41 — the original
CYAN ICE    #00FFFF  — cold data, chrome
VOID        #040404  — background
```

---

## // TECH STACK

```
HTML/CSS/JS   — 100% vanilla, zero frameworks
Canvas API    — matrix rendering and text sampling
LZW encoder   — custom GIF89a implementation
Web Fonts     — VT323, Share Tech Mono (Google Fonts CDN)
URL hash      — TextEncoder + base64 state serialization
```

Single file. ~1600 lines. No node_modules. No webpack. No opinions.

---

## // KNOWN LIMITATIONS

- GIF palette is limited to 64 colors — rich gradients may posterize.
- Very wide matrices (200+ columns) may export slowly; the encoder runs on the main thread.
- Typewriter mode does not loop smoothly by design — it's meant for a one-shot reveal.

---

> *"Cyberspace. A consensual hallucination experienced daily by billions..."*

Leave the meat behind. Jack in. Ship the GIF.
