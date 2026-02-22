# Aliens — Style Guide

Claustrophobic and industrial. A dark design system inspired by the corridors of deep-space freight vessels — corrugated metal textures, acid yellow-green accents, motion tracker radar sweeps, airlock warning panels, and bio-scan specimen cards for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#08080a` | Page background (cold void black)        |
| `--surface`    | `#111214` | Cards, panels, diagram containers        |
| `--surface-2`  | `#1a1b1e` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#222428` | Tertiary surface, row separators         |
| `--border`     | `#2e3035` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#c8c4b8` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#7a7870` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#4a4840` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                  |
|-----------------|-----------|---------------------------------------|
| `--accent`      | `#a8d430` | Primary accent (Acid Yellow-Green)    |
| `--accent-dim`  | `#5c7418` | Muted accent                          |
| `--capture`     | `#a8d430` | Acid Green — bio-scan, specimens      |
| `--capture-dim` | `#5c7418` | Muted green                           |
| `--refine`      | `#d4a020` | Caution Amber — warnings, advisories  |
| `--refine-dim`  | `#8a6810` | Muted amber                           |
| `--execute`     | `#d03020` | Emergency Red — hostile, danger       |
| `--execute-dim` | `#881810` | Muted red                             |
| `--batch`       | `#4878a8` | Cold Steel Blue — cryo, systems       |
| `--batch-dim`   | `#2c4c70` | Muted blue                            |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                             |
|-----------|-----------------|--------------------------------------------------|
| Headings  | Black Ops One   | `Black+Ops+One`                                  |
| Body      | Share Tech Mono | `Share+Tech+Mono`                                |
| Labels    | Share Tech Mono | (same as body)                                   |

```html
<link href="https://fonts.googleapis.com/css2?family=Black+Ops+One&family=Share+Tech+Mono&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                     |
|--------------------|-----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Black Ops One   | `clamp(3rem, 9vw, 6rem)`     | 400    | 1.0         | Uppercase. Accent-colored `<span>` glows.  |
| h2 (section)       | Black Ops One   | `2rem`                        | 400    | 1.1         | Uppercase, letter-spacing: 0.04em          |
| h3 (subsection)    | Black Ops One   | `1.3rem`                      | 400    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | Share Tech Mono | `0.85rem`                     | 400    |             | Uppercase, letter-spacing: 0.08em          |
| Body paragraph     | Share Tech Mono | `0.9rem`                      | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Share Tech Mono | `1rem`                        | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | Share Tech Mono | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | Share Tech Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | Share Tech Mono | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Diagram label      | Share Tech Mono | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | Share Tech Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Table header       | Share Tech Mono | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | Share Tech Mono | `0.82rem`                     | 400    |             | First column: `--text` color               |
| `<strong>` in body | Share Tech Mono | inherit                       | 400    |             | Color: `--text`                            |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace terminal label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Corrugated metal overlay:** Repeating horizontal lines via `::before` — `repeating-linear-gradient` simulating ribbed hull plating (8px transparent + 1px faint green bands), plus vertical structural ribs (60px spacing)
- **Condensation texture:** Faint radial gradients via `::after` using green and blue at very low opacity, simulating moisture on cold surfaces
- **Title glow:** The `<span>` inside h1 uses `--accent` color with `text-shadow: 0 0 40px rgba(168, 212, 48, 0.4)`
- **Staggered fade-up animation** on load:
  - Label: 0s delay
  - h1: 0.15s delay
  - Subtitle: 0.3s delay
  - Version: 0.45s delay
  - Animation: `opacity 0→1, translateY(20px→0)`, 0.8s ease-out

---

## Components

### Flow Cards (2-Column Grid)

A grid of cards used for listing related items.

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 2px`, `padding: 1.5rem`
- **Hover:** Border color changes to `--accent`, gains `box-shadow: 0 0 12px rgba(168, 212, 48, 0.1)` (acid glow)
- **Top accent bar:** 3px colored bar at the top edge (via `::before`) with matching `box-shadow` glow. Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `1px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `2px`, last gets right border-radius `2px`. Adjacent stages share borders (`border-left: none`).
- **Top accent:** 3px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step number (Share Tech Mono, `0.7rem`, faint) → name (`0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `1px solid var(--border)`, `border-radius: 2px`, `padding: 1.25rem`
- **Number:** Black Ops One, `2rem`, `--accent`, fixed `2rem` width, centered
- **Content:** h4 title (`0.85rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `3px solid var(--accent)`
- Background: `rgba(168, 212, 48, 0.05)`
- Border-radius: `0 2px 2px 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (acid green)

### Tags / Pills

Small inline labels with semantic colors.

- Font: Share Tech Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `2px`
- Background: transparent semantic color at 12% opacity
- Border: `1px solid` in dim semantic color
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** Uppercase, `0.7rem`, `letter-spacing: 0.1em`, `--text-faint`, bottom border `1px solid var(--border)`
- **Body cells:** `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px solid var(--surface-3)`
- **First column** in body: `--text` color

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `1px solid var(--border)`
- Border-radius: `2px`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in Share Tech Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Share Tech Mono', monospace`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="12"`
- Labels inside nodes: Semantic color, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.5px`)

---

## Unique Components

### Motion Tracker

A circular radar display with animated sweep arm, range rings, crosshairs, and pulsing contact blips.

- Container: Flex column, centered, `2.5rem` vertical margin
- Label: Share Tech Mono, `0.7rem`, `letter-spacing: 0.15em`, uppercase, `--text-faint`
- **Scope:** `280px` circle, `--surface` background, `2px solid var(--border)`
- **Range rings:** Three concentric rings at 25%, 50%, 75% radius via `radial-gradient`, `--border` color, 50% opacity
- **Crosshairs:** Centered horizontal and vertical lines via `linear-gradient`, `--border` color, 40% opacity
- **Sweep arm:** Rotates 360deg over 3s linear infinite. Uses `conic-gradient` for a trailing fade (30deg arc, acid green at 15% opacity) and a solid leading edge line
- **Blips:** 6px circles, `--accent` background with `box-shadow: 0 0 6px rgba(168, 212, 48, 0.6)`, pulsing opacity/scale animation (1.5s ease-in-out infinite)
- **Readout:** Share Tech Mono below the scope, `0.7rem`, `--accent` color

### Airlock Warning

An industrial hazard panel with yellow/black chevron stripe header and bolted frame.

- Container: `--surface` background, `2px solid var(--border)`, `border-radius: 2px`
- **Hazard stripe:** 8px height bar with `repeating-linear-gradient` at 45deg alternating `--refine` and `--bg` in 8px bands
- **Corner bolts:** `::before` and `::after` pseudo-elements creating 10px circles with `--surface-3` fill and `--border` stroke at bottom corners
- **Header:** Black Ops One, `0.85rem`, `letter-spacing: 0.12em`, uppercase, `--refine` color
- **Body:** `--text-dim`, 0.85rem
- **Status indicators:** Inline flex row, Share Tech Mono, `0.65rem`, uppercase
  - `.active` — acid green background fill, green text/border
  - `.warning` — red background fill, red text/border, blinking animation (1s)

### Bio-Scan Card

A specimen analysis card with taxonomy-style header, classification stamp, vital stats grid, and animated scanning line.

- Container: `--surface` background, `1px solid var(--border)`, `border-radius: 2px`
- **Header:** Flex row with space-between alignment, `1px solid var(--border)` bottom
  - Specimen ID: Black Ops One, `0.85rem`, uppercase
  - Classification stamp: Share Tech Mono, `0.65rem`, uppercase, red background fill with red text/border
- **Body:** 2-column grid (160px silhouette + 1fr stats). Collapses to 1 column at 640px.
- **Silhouette panel:** `--bg` background, centered SVG wireframe outline (100x120px), `--accent` stroke, 40% opacity
  - Scanning line: `::after` pseudo-element, 2px height, `linear-gradient` from transparent through `--accent`, animates top position 10%→90% over 2.5s
- **Stats grid:** Rows with label/value pairs separated by `--surface-3` borders
  - Labels: `--text-faint`, uppercase, `0.7rem`
  - Values: `--text` default, `.danger` = `--execute`, `.caution` = `--refine`, `.nominal` = `--accent`

### Acid Drip Divider

An SVG section separator with a corroded line and dripping acid-green blobs.

- Container: `3rem` vertical margin, centered, `max-width: 700px`
- **Base line:** Irregular path with small vertical variations, `stroke: #a8d430`, `stroke-width: 1.5`, `opacity: 0.4`
- **Drips:** Teardrop-shaped paths (`Q` curves) in acid green at varying opacities (0.35–0.5), positioned at intervals along the line
- **Animation:** Each drip group has a `translateY` bounce animation (0→3px→0) over 2s ease-in-out infinite, with staggered `animation-delay` (0s, 0.3s, 0.5s, 0.8s, 1s)

---

## Inline Code

- Font: Share Tech Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `2px`
- Border: `1px solid var(--border)`
- Color: `--accent` (acid green)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in Share Tech Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Cold steel, not black** — backgrounds use blue-tinted near-blacks like ship hull plating, not warm tones or pure #000.
2. **Acid blood glow** — the primary accent is a sickly yellow-green evoking molecular acid, with subtle glows on interactive elements.
3. **Three-tier text** — terminal phosphor (--text), dim (--text-dim), faint (--text-faint).
4. **All-mono body** — Share Tech Mono for all body text gives the entire document the feel of a Nostromo crew terminal.
5. **Stencil-stamped headings** — Black Ops One delivers military stencil headings echoing WEYLAND-YUTANI corporate markings.
6. **Industrial semantics** — acid green (bio-scan), caution amber (warning), emergency red (hostile), cold steel blue (cryogenics).
7. **Ship hardware** — motion trackers, airlock warnings, bio-scan cards, and acid drip dividers bring deep-space industrial infrastructure into the design.
8. **Corrugated texture** — the hero uses repeating gradients simulating ribbed hull plating and structural ribs.
