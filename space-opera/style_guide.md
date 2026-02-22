# Space Opera — Style Guide

A deep-space sci-fi design system — holographic cyan accents, nebula glows, HUD frames, and transmission logs for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#060a12` | Page background (deep space blue-black)  |
| `--surface`    | `#0d1520` | Cards, panels, diagram containers        |
| `--surface-2`  | `#141e2e` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#1c2840` | Tertiary surface, row separators         |
| `--border`     | `#263350` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#d0d8e8` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#7888a0` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#445570` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#00e5ff` | Primary accent (Holographic Cyan)        |
| `--accent-dim`  | `#007a99` | Muted accent                             |
| `--capture`     | `#00e5ff` | Holographic Cyan — shields, sensors      |
| `--capture-dim` | `#007a99` | Muted cyan                               |
| `--refine`      | `#e040a0` | Nebula Magenta — energy, warp            |
| `--refine-dim`  | `#882060` | Muted magenta                            |
| `--execute`     | `#ff3850` | Supernova Red — weapons, alerts          |
| `--execute-dim` | `#a01828` | Muted red                                |
| `--batch`       | `#4070ff` | Warp Blue — navigation, systems          |
| `--batch-dim`   | `#2040a0` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                                        |
|-----------|-----------------|-------------------------------------------------------------|
| Headings  | Orbitron        | `Orbitron:wght@400;500;600;700`                             |
| Body      | Exo 2           | `Exo+2:wght@300;400;500;600`                               |
| Labels    | Share Tech Mono | `Share+Tech+Mono`                                           |

```html
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700&family=Exo+2:wght@300;400;500;600&family=Share+Tech+Mono&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                     |
|--------------------|-----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Orbitron        | `clamp(2.8rem, 8vw, 5.5rem)` | 700    | 1.1         | Uppercase. Accent-colored `<span>` glows.  |
| h2 (section)       | Orbitron        | `1.8rem`                      | 600    | 1.15        | Uppercase, letter-spacing: 0.06em          |
| h3 (subsection)    | Orbitron        | `1.15rem`                     | 500    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | Exo 2           | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.06em          |
| Body paragraph     | Exo 2           | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Exo 2           | `1.1rem`                      | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | Exo 2           | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | Share Tech Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | Share Tech Mono | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Diagram label      | Share Tech Mono | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | Share Tech Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Table header       | Exo 2           | `0.7rem`                      | 600    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | Exo 2           | `0.82rem`                     | 400    |             | First column: `--text` + weight 600        |
| `<strong>` in body | Exo 2           | inherit                       | 600    |             | Color: `--text`                            |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace readout label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Star field overlay:** Scattered `radial-gradient` dots via `::before` in white, cyan, magenta, and blue at varying opacities — simulates distant stars
- **Nebula glow:** Faint elliptical `radial-gradient` layers via `::after` in cyan, magenta, and blue at very low opacity
- **Title glow:** The `<span>` inside h1 uses `--accent` color with `text-shadow: 0 0 40px rgba(0, 229, 255, 0.5), 0 0 80px rgba(0, 229, 255, 0.2)`
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
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 4px`, `padding: 1.5rem`
- **Hover:** Border color changes to `--accent`, gains `box-shadow: 0 0 16px rgba(0, 229, 255, 0.15)` plus a faint inner glow (holographic effect)
- **Top accent bar:** 3px colored bar at the top edge (via `::before`) with matching `box-shadow` glow. Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `1px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `4px`, last gets right border-radius `4px`. Adjacent stages share borders (`border-left: none`).
- **Top accent:** 3px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step number (Share Tech Mono, `0.7rem`, faint) → name (weight 600, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `1px solid var(--border)`, `border-radius: 4px`, `padding: 1.25rem`
- **Number:** Orbitron, `2rem`, weight 700, `--accent`, fixed `2rem` width, centered
- **Content:** h4 title (weight 600, `0.85rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `3px solid var(--accent)`
- Background: `rgba(0, 229, 255, 0.05)`
- Border-radius: `0 4px 4px 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (holographic cyan)

### Tags / Pills

Small inline labels with semantic colors.

- Font: Share Tech Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `3px`
- Background: transparent semantic color at 10% opacity
- Border: `1px solid` in dim semantic color
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** Uppercase, weight 600, `0.7rem`, `letter-spacing: 0.1em`, `--text-faint`, bottom border `1px solid var(--border)`
- **Body cells:** `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px solid var(--surface-3)`
- **First column** in body: `--text` color, weight 600

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `1px solid var(--border)`
- Border-radius: `4px`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in Share Tech Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Exo 2', sans-serif`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="12"`
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.5px`)

---

## Unique Components

### HUD Frame

A content panel with corner bracket decorations and a faint grid background, evoking a starship heads-up display.

- Outer container: `padding: 2rem`, position relative
- Background: Dual `linear-gradient` grid pattern at `24px` spacing with very faint cyan lines (`rgba(0, 229, 255, 0.03)`) over `--surface`
- **Corner brackets:** `::before` and `::after` on the outer `.hud-frame` draw top-left and top-right brackets; `::before` and `::after` on `.hud-frame-inner` draw bottom-left and bottom-right brackets
- Bracket size: `20px × 20px`, `2px` solid `--accent` borders on two edges only
- Inner heading: `--accent` color
- Inner body: `--text-dim`

### Transmission Log

A cyan-bordered communication panel with metadata header, pulsing border, and scanline texture.

- Background: `--surface`
- Border: `1px solid var(--capture-dim)`, `border-left: 4px solid var(--accent)`
- Border-radius: `0 4px 4px 0`
- **Pulsing animation:** Left border and box-shadow cycle between bright and dim over 3s (`ease-in-out infinite`)
- **Scanline texture:** `::after` pseudo-element with `repeating-linear-gradient` alternating transparent and faint cyan bands (3px each)
- **Header:** Share Tech Mono, `0.65rem`, `letter-spacing: 0.2em`, uppercase, `--accent` color. Contains frequency and timestamp metadata as `<span>` elements in `--text-faint`.
- `<strong>` within the transmission uses `--accent` color

### Star Chart Divider

An inline SVG constellation pattern used as a section separator.

- Dots of varying sizes (r: 1.5–3px) in `--accent`, `--refine`, and `--batch` colors at varying opacities
- Connecting lines: `stroke: #00e5ff`, `stroke-width: 0.5`, `opacity: 0.35`
- Container: `max-width: 600px`, centered
- Groups of connected stars with gaps between constellations

### Systems Status

Horizontal power/shield bars with labels and percentages, like a starship readout.

- **Label:** Share Tech Mono, `0.7rem`, uppercase, `--text-faint`
- **Bars container:** Flex column with `0.75rem` gap
- **Each bar row:** Flex row with label (Share Tech Mono, `0.7rem`, `--text`, 5.5rem width, right-aligned), track, and percentage
- **Track:** `--surface-2` background, `1px solid var(--border)`, `border-radius: 2px`, `22px` height
- **Fill:** Semantic gradient (`dim → full` left to right) with matching `box-shadow` glow. Width set via inline `style="width: XX%"`.
  - `.fill-capture` — cyan gradient
  - `.fill-refine` — magenta gradient
  - `.fill-execute` — red gradient
  - `.fill-batch` — blue gradient
- **Percentage:** Share Tech Mono, `0.7rem`, `--text-faint`, 3rem width

---

## Inline Code

- Font: Share Tech Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--accent` (holographic cyan)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in Share Tech Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Deep space, not black** — backgrounds use cool blue-tinted near-blacks like deep space, not pure #000.
2. **Holographic glow** — the primary accent is vivid cyan with box-shadow glows on interactive elements.
3. **Three-tier text** — cool blue-white (--text), dim (--text-dim), faint (--text-faint).
4. **Starship readout labels** — Share Tech Mono gives section labels and tags a bridge console readout feel.
5. **Geometric display headings** — Orbitron delivers geometric uppercase headings echoing futuristic starship interfaces.
6. **Space-opera semantics** — holographic cyan (shields), nebula magenta (energy), supernova red (weapons), warp blue (navigation).
7. **HUD aesthetics** — corner brackets, grid backgrounds, systems bars, and transmission logs bring tactical displays into the design.
8. **Star field texture** — the hero uses scattered radial gradients and nebula glows to simulate deep space.
