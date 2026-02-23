# Surveillance — Style Guide

Clinical and menacing. A dark design system inspired by security monitoring equipment — harsh monitor greys, white text readouts, red REC indicators, multi-camera grid layouts, scan-line textures, evidence tags, and facial recognition bounding boxes for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#0a0a0c` | Page background (monitor black)          |
| `--surface`    | `#121214` | Cards, panels, diagram containers        |
| `--surface-2`  | `#1a1a1e` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#242428` | Tertiary surface, row separators         |
| `--border`     | `#333338` | Card borders, monitor frames             |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#d0d0d8` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#808088` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#505058` | Labels, metadata, timestamps, ghost text        |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                      |
|-----------------|-----------|-------------------------------------------|
| `--accent`      | `#e02020` | Primary accent (REC Red)                  |
| `--accent-dim`  | `#901414` | Muted accent                              |
| `--capture`     | `#30c050` | Active Green — recording, live feeds      |
| `--capture-dim` | `#1a7030` | Muted green                               |
| `--refine`      | `#d0a020` | Standby Amber — motion, tracking          |
| `--refine-dim`  | `#886810` | Muted amber                               |
| `--execute`     | `#e02020` | Alert Red — flagged, danger               |
| `--execute-dim` | `#901414` | Muted red                                 |
| `--batch`       | `#2878d0` | System Blue — info, archive               |
| `--batch-dim`   | `#184888` | Muted blue                                |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                                  |
|-----------|-----------------|------------------------------------------------------|
| Headings  | Share Tech Mono | `Share+Tech+Mono`                                    |
| Body      | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600;700`                |
| Labels    | IBM Plex Mono   | (same as body)                                       |

```html
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=IBM+Plex+Mono:wght@400;500;600;700&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                          |
|--------------------|-----------------|-------------------------------|--------|-------------|------------------------------------------------|
| Hero h1            | Share Tech Mono | `clamp(2.8rem, 8vw, 5.5rem)` | 400    | 1.0         | Uppercase. Accent-colored `<span>` glows red.  |
| h2 (section)       | Share Tech Mono | `1.8rem`                      | 400    | 1.1         | Uppercase, letter-spacing: 0.06em              |
| h3 (subsection)    | Share Tech Mono | `1.2rem`                      | 400    | default     | `margin-top: 2.5rem`                           |
| h4 (card title)    | IBM Plex Mono   | `0.8rem`                      | 600    |             | Uppercase, letter-spacing: 0.08em              |
| Body paragraph     | IBM Plex Mono   | `0.88rem`                     | 400    | 1.7         | Color: `--text-dim`                            |
| Hero subtitle      | IBM Plex Mono   | `0.95rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px           |
| Card body          | IBM Plex Mono   | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                            |
| Section label      | IBM Plex Mono   | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Diagram label      | IBM Plex Mono   | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | IBM Plex Mono   | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                       |
| Table header       | IBM Plex Mono   | `0.7rem`                      | 600    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | IBM Plex Mono   | `0.82rem`                     | 400    |             | First column: `--text` color, weight 500       |
| `<strong>` in body | IBM Plex Mono   | inherit                       | 600    |             | Color: `--text`                                |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: timestamp overlay, label, h1, subtitle paragraph, REC indicator, version tag
- **Camera grid overlay:** Repeating horizontal and vertical lines via `::before` — `repeating-linear-gradient` creating a faint 120px square grid simulating multi-camera monitor layout, `--border` color at 25% opacity
- **Vignette overlay:** Radial gradient via `::after` darkening edges, simulating CRT monitor vignette
- **Title glow:** The `<span>` inside h1 uses `--accent` color with `text-shadow: 0 0 30px rgba(224, 32, 32, 0.5)`
- **REC indicator:** `.hero-rec` element with pulsing red dot (8px circle, `recPulse` animation cycling opacity 1→0.3 over 1.5s ease-in-out infinite)
- **Timestamp overlay:** Positioned absolute top-right, Share Tech Mono, faint text showing camera ID and UTC time
- **Staggered fade-up animation** on load:
  - Label: 0s delay
  - h1: 0.15s delay
  - Subtitle: 0.3s delay
  - Version: 0.45s delay
  - REC: 0.6s delay
  - Animation: `opacity 0→1, translateY(20px→0)`, 0.8s ease-out

---

## Components

### Flow Cards (2-Column Grid)

A grid of cards used for listing related items.

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 2px`, `padding: 1.5rem`
- **Hover:** Border color changes to `--accent`, gains `box-shadow: 0 0 12px rgba(224, 32, 32, 0.1)` (red glow)
- **Top accent bar:** 3px colored bar at the top edge (via `::before`) with matching `box-shadow` glow. Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `1px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `2px`, last gets right border-radius `2px`. Adjacent stages share borders (`border-left: none`).
- **Top accent:** 3px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step number (IBM Plex Mono, `0.7rem`, faint) → name (Share Tech Mono, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `1px solid var(--border)`, `border-radius: 2px`, `padding: 1.25rem`
- **Number:** Share Tech Mono, `2rem`, `--accent`, fixed `2rem` width, centered
- **Content:** h4 title (`0.8rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `3px solid var(--accent)`
- Background: `rgba(224, 32, 32, 0.05)`
- Border-radius: `0 2px 2px 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (REC red)

### Tags / Pills

Small inline labels with semantic colors.

- Font: IBM Plex Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `2px`
- Background: transparent semantic color at 12% opacity
- Border: `1px solid` in dim semantic color
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** Uppercase, `0.7rem`, `letter-spacing: 0.1em`, `--text-faint`, bottom border `1px solid var(--border)`, font-weight 600
- **Body cells:** `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px solid var(--surface-3)`
- **First column** in body: `--text` color, font-weight 500

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `1px solid var(--border)`
- Border-radius: `2px`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in IBM Plex Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'IBM Plex Mono', monospace`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="12"`
- Labels inside nodes: Semantic color, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.5px`)

---

## Unique Components

### Camera Feed

A CCTV monitor card with camera ID, timestamp overlay, scan-line texture, and pulsing REC indicator.

- Container: `--surface` background, `2px solid var(--border)`, `border-radius: 2px`, relative positioning
- **Scan-line overlay:** `::before` pseudo-element with `repeating-linear-gradient` creating 2px transparent + 2px dark horizontal lines, `z-index: 3`, pointer-events none
- **Header:** Flex row with space-between alignment
  - Camera ID: Share Tech Mono, `0.7rem`, `letter-spacing: 0.12em`, uppercase, `--text`
  - Timestamp: Share Tech Mono, `0.65rem`, `--text-faint`
- **Body:** `--bg` background, `padding: 2rem 1.5rem`, `min-height: 180px`
- **Footer:** Flex row with space-between, border-top
  - REC indicator: Share Tech Mono, `0.65rem`, `--accent`, inline-flex with pulsing 8px red dot (`recPulse` animation — opacity 1→0.3 over 1.5s ease-in-out infinite, with red glow `box-shadow`)
  - Feed status: IBM Plex Mono, `0.6rem`, `--text-faint`

### Evidence Tag

A callout styled like an evidence bag label with case data fields in monospace grid.

- Container: `--surface` background, `2px dashed var(--border)`, `border-radius: 2px`
- **Header:** `--surface-2` background, dashed bottom border, flex row with space-between
  - Title: Share Tech Mono, `0.8rem`, `letter-spacing: 0.12em`, uppercase, `--accent`
  - Classification stamp: IBM Plex Mono, `0.6rem`, uppercase, red fill background with red text/border
- **Body:** `padding: 1.25rem`
- **Field grid:** 2-column CSS grid (`gap: 0.75rem 2rem`), collapses to 1 column at `480px`
  - Field label: IBM Plex Mono, `0.6rem`, `letter-spacing: 0.12em`, uppercase, `--text-faint`
  - Field value: Share Tech Mono, `0.85rem`, `--text`, bottom border `1px solid var(--surface-3)`
- **Notes section:** Top border `2px dashed var(--border)`, body text, `0.82rem`, `--text-dim`

### Static Divider

An SVG section separator that creates a TV static/noise band effect.

- Container: `3rem` vertical margin, centered, `max-width: 700px`
- **Static bands:** Horizontal `<rect>` elements at varying y positions, heights, and opacities using `--border` and `--text-faint` colors
- **Noise pixels:** Small scattered `<rect>` elements (2-4px) in `--text-dim` and `--text` colors at low opacity
- **Animation:** `staticFlicker` keyframes stepping through varying opacities (0.3–0.7) over 0.8s with `steps(5)` timing, staggered `animation-delay` (0s, 0.1s, 0.15s, 0.3s)

### Recognition Box

A card with dashed bounding-box border, corner bracket markers, crosshair overlay, and status label.

- Container: `--surface` background, `2px dashed var(--border)`, `border-radius: 2px`, `padding: 1.5rem`
- **Corner brackets:** `::before` and `::after` pseudo-elements (top-left, top-right) plus `.corner-bl` and `.corner-br` divs (bottom-left, bottom-right) — 20px L-shaped brackets in `--accent` color, 3px border width
- **Header:** Flex row with space-between alignment
  - Subject ID: Share Tech Mono, `0.8rem`, `letter-spacing: 0.1em`, uppercase, `--text`
  - Status label: IBM Plex Mono, `0.6rem`, uppercase, with semantic color variants:
    - `.status-match` — green fill/text/border
    - `.status-scanning` — amber fill/text/border, blinking animation (1.2s)
    - `.status-alert` — red fill/text/border, blinking animation (0.8s)
    - `.status-clear` — blue fill/text/border
- **Body:** 2-column grid (100px silhouette + 1fr stats), collapses to 1 column at `480px`
- **Silhouette panel:** `--bg` background, `1px solid var(--border)`, centered SVG wireframe figure
  - Crosshair overlay: `::before` with centered horizontal and vertical lines in `--accent` at 40% opacity
- **Stats grid:** Rows with label/value pairs separated by `--surface-3` borders
  - Labels: `--text-faint`, uppercase, `0.68rem`
  - Values: `--text` default, `.match` = `--capture`, `.alert` = `--execute`, `.pending` = `--refine`

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `2px`
- Border: `1px solid var(--border)`
- Color: `--accent` (REC red)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Monitor black, not warm** — backgrounds use cool-tinted near-blacks like powered-off CRT monitors, not warm tones or pure #000.
2. **REC red dominance** — the primary accent is a harsh recording-indicator red that pulses on active elements like a blinking camera light.
3. **Three-tier text** — harsh monitor white (--text), dim readout (--text-dim), ghost text (--text-faint).
4. **All-mono typography** — Share Tech Mono for headings, IBM Plex Mono for body. Both monospace, differentiated by weight and size rather than font variety.
5. **Operational semantics** — active green (recording), standby amber (motion/tracking), alert red (flagged), system blue (information/archive).
6. **Timestamp everything** — camera IDs and UTC timestamps appear on components like real security footage overlays.
7. **Evidence chain** — evidence tags, recognition boxes, and structured data grids evoke forensic documentation and chain-of-custody procedures.
8. **Signal interference** — scan-line overlays, static noise dividers, and flickering animations bring analog video surveillance imperfections into the design.
