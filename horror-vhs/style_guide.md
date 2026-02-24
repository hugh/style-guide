# Horror VHS / Found Footage — Style Guide

A VHS horror design system — CRT black, night-vision green, tracking distortion, camcorder overlays, and degraded video scanlines for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#0a0a0a` | Page background (CRT black)              |
| `--surface`    | `#141414` | Cards, panels, diagram containers        |
| `--surface-2`  | `#1e1e1e` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#282828` | Tertiary surface, row separators         |
| `--border`     | `#333333` | Card borders, scanline grey              |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#c8c8c8` | Primary text, headings, strong (phosphor white) |
| `--text-dim`   | `#808080` | Body paragraphs, descriptions (dim phosphor)    |
| `--text-faint` | `#4a4a4a` | Labels, metadata, captions (ghost image)        |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Colors are inspired by VHS/found-footage video signals.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#30ff50` | Primary accent (Night-Vision Green)      |
| `--accent-dim`  | `#20cc40` | Muted accent                             |
| `--capture`     | `#30ff50` | Night-Vision Green — detection, scan     |
| `--capture-dim` | `#20cc40` | Muted green                              |
| `--refine`      | `#d0a020` | VCR Amber — timestamps, data            |
| `--refine-dim`  | `#a88018` | Muted amber                              |
| `--execute`     | `#e02020` | REC Red — recording indicator, alert     |
| `--execute-dim` | `#b81818` | Muted red                                |
| `--batch`       | `#4070c0` | Static Blue — channel noise, info        |
| `--batch-dim`   | `#3058a0` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                              |
|-----------|---------------|--------------------------------------------------|
| Headings  | VT323         | `VT323` (weight 400 only)                        |
| Body      | IBM Plex Mono | `IBM+Plex+Mono:wght@400;500;600`                 |
| Labels    | VT323         | Same as headings — VCR display aesthetic          |

### Type Scale & Weights

| Element            | Family        | Size                          | Weight | Line-height | Notes                                     |
|--------------------|---------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | VT323         | `clamp(3rem, 8vw, 6rem)`     | 400    | 1.05        | `letter-spacing: 0.04em`, uppercase        |
| h2 (section)       | VT323         | `2.2rem`                      | 400    | 1.15        | `letter-spacing: 0.03em`, uppercase        |
| h3 (subsection)    | VT323         | `1.4rem`                      | 400    | 1.2         | `margin-top: 2.5rem`, uppercase            |
| h4 (card title)    | VT323         | `1rem`                        | 400    |             | Uppercase, `letter-spacing: 0.08em`        |
| Body paragraph     | IBM Plex Mono | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Section label      | VT323         | `1rem`                        | 400    |             | Uppercase, `letter-spacing: 0.15em`        |
| Tag                | VT323         | `0.95rem`                     | 400    |             | `letter-spacing: 0.06em`                   |

---

## Layout

- Container max-width: **900px**, centered, `2rem` horizontal padding
- Section padding: `5rem` vertical, `1px solid var(--border)` top border
- Section label format: `01 — Label`
- Full-bleed max-width: **1100px**
- Border radius: **0px** on all components (sharp CRT edges)

---

## Global Effects

### Scanline Overlay

`body::after` creates a fixed overlay of repeating 2px transparent / 2px semi-transparent-black horizontal lines across the entire page. Sits at `z-index: 9999` and is pointer-events: none.

### CRT Vignette

`body::before` creates a fixed radial gradient that darkens corners and edges. Transparent at center, 40% black at 80%, 80% black at edges. Sits at `z-index: 9998`.

---

## Hero Section

- Full viewport height, flex-centered
- **VHS tracking noise bar:** `::before` creates a 6px top bar with alternating colour dashes and a `trackingShift` animation
- **Green tint lines:** `::after` creates subtle green-tinted horizontal lines
- **RGB split on h1:** `text-shadow` with red (+2px) and blue (-2px) offsets
- **Green glow on span:** Night-vision green with blur shadow
- Staggered fade-up animation on load

---

## Standard Components

### Flow Cards

Two-column grid (`.flow-grid`) with semantic-colored top bars:
- `.capture` — night-vision green
- `.refine` — VCR amber
- `.execute` — REC red
- `.batch` — static blue
- `.accent` — primary accent

### Pipeline

Horizontal stage display (`.pipeline > .pipe-stage`):
- Classes: `.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`
- 3px colored top border per stage

### Callout

Left-bordered box with green tint:
- 4px left border in `--accent`
- Faint green background tint
- `strong` renders in accent colour

### Tags

Inline labels (`.tag`):
- `.t-capture`, `.t-refine`, `.t-execute`, `.t-batch`
- VT323 font, uppercase, border matches semantic colour

### Info Table

Standard data table (`.info-table`):
- VT323 uppercase headers in `--text-faint`
- First column bold in `--text`
- 1px bottom borders

### Diagram Container

`.diagram-wrap` — surface background, 1px border, 2.5rem padding. Add `.full-bleed` for 1100px width. SVG text uses IBM Plex Mono.

---

## Unique Components

### REC Indicator

A camcorder-style recording indicator showing a pulsing red dot, "REC" text, and a timestamp.

- **Container:** `.rec-indicator` — inline-flex, surface background, 1px border
- **Red dot:** `.rec-dot` — 12px circle, `--execute` background, `recPulse` animation (1.2s fade in/out), red glow shadow
- **REC text:** `.rec-text` — VT323, 1.3rem, `--execute` colour
- **Timestamp:** `.rec-timestamp` — VT323, 1.1rem, `--text-dim`
- **Floating variant:** Add `.rec-float` for absolute positioning (top-right corner of relative parent, transparent background)

### Tracking Glitch

A horizontal divider simulating VHS tracking distortion.

- **Container:** `.tracking-glitch` — 40px height, overflow hidden
- **Bars:** 5x `.glitch-bar` elements — absolute positioned, varying widths, offsets, and heights
- **RGB separation:** `box-shadow` adds red (+offset) and blue (-offset) color channel shift
- **Animated variant:** Add `.animated` class for `glitchSlide` animation (3s, stepped)

### Night Vision Card

A green-tinted card with infrared camera aesthetics.

- **Container:** `.night-vision-card` — black background, green border (`rgba(48, 255, 80, 0.3)`)
- **Scanline overlay:** `::before` — repeating green-tinted horizontal lines
- **Green tint:** `::after` — faint green overlay
- **Crosshairs:** 4x `.nv-crosshair` elements (`.top-left`, `.top-right`, `.bottom-left`, `.bottom-right`) — L-shaped corner markers in green
- **Timestamp:** `.nv-timestamp` — absolute top-right, faint green text
- **Content:** h4 in accent with green glow, p in faint green

### Static Block

A corrupted-data callout with animated TV static noise.

- **Container:** `.static-block` — surface background, 1px border
- **Noise overlay:** `::before` — SVG turbulence filter scaled 200%, `staticShift` animation (0.3s, stepped)
- **Scan line:** `::after` — subtle moving brightness gradient
- **Label:** `.static-label` — VT323, uppercase, prefixed with red `//`
- **High-static variant:** Add `.high-static` for more visible noise and faster animation

---

## Summary of Key Patterns

1. **CRT black backgrounds** — near-black with no warm/cool bias, like a dead television screen.
2. **Night-vision green accent** — the signature colour of infrared camera footage.
3. **Four-signal semantics** — green (detection), amber (timestamp), red (REC/alert), blue (static/info).
4. **VCR typography** — VT323 channels on-screen camcorder displays; all-caps, pixelated monospace.
5. **Scanline & vignette overlays** — body pseudo-elements add global CRT screen effects.
6. **Sharp CRT edges** — zero border-radius on everything; hard right angles like video signal boundaries.
7. **RGB channel separation** — red/blue text-shadow offsets simulate colour bleed on degraded video.
8. **Tracking distortion** — offset horizontal bars with chromatic aberration create the "bad tracking" effect.
