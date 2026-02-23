# Architect / Drafting — Style Guide

Precise, clean, technical. A design system inspired by architectural drawings — warm vellum backgrounds, fine technical pen lines, dimension annotations, floor-plan grids, section-cut dividers, and title blocks for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                     |
|----------------|-----------|-------------------------------------------|
| `--bg`         | `#f8f4ec` | Page background (warm white vellum)       |
| `--surface`    | `#f0ece2` | Cards, panels, diagram containers         |
| `--surface-2`  | `#e8e2d6` | Nested surfaces, heavier tracing paper    |
| `--surface-3`  | `#dcd4c6` | Tertiary surface, cardboard mount board   |
| `--border`     | `#c0b8a4` | Card borders, section dividers (pencil line grey) |

### Text

| Token          | Hex       | Usage                                           |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#2a2620` | Primary text, headings, bold/strong (drafting ink) |
| `--text-dim`   | `#6a6050` | Body paragraphs, secondary descriptions (light pencil) |
| `--text-faint` | `#9a9080` | Labels, metadata, captions, annotations (ghost line) |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                  |
|-----------------|-----------|---------------------------------------|
| `--accent`      | `#c83030` | Redline markup (primary accent)       |
| `--accent-dim`  | `#982020` | Muted redline                         |
| `--capture`     | `#2a8848` | Site / Landscape Green                |
| `--capture-dim` | `#1a5c30` | Muted green                           |
| `--refine`      | `#c89830` | Material / Wood Amber                 |
| `--refine-dim`  | `#8a6a1c` | Muted amber                           |
| `--execute`     | `#c83030` | Redline / Markup Red                  |
| `--execute-dim` | `#982020` | Muted red                             |
| `--batch`       | `#2868a8` | Blueprint / Water Blue                |
| `--batch-dim`   | `#1a4870` | Muted blue                            |

---

## Typography

### Font Stack

| Role       | Family          | Google Fonts Import                                      |
|------------|-----------------|-----------------------------------------------------------|
| Headings   | Archivo         | `Archivo:wght@400;500;600;700`                            |
| Body       | Inter           | `Inter:wght@300;400;500;600`                              |
| Labels     | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                          |

```html
<link href="https://fonts.googleapis.com/css2?family=Archivo:wght@400;500;600;700&family=Inter:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                     |
|--------------------|-----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Archivo         | `clamp(3rem, 9vw, 6rem)`     | 700    | 1.0         | Uppercase, letter-spacing: 0.02em          |
| h2 (section)       | Archivo         | `2rem`                        | 700    | 1.15        | Uppercase, letter-spacing: 0.04em          |
| h3 (subsection)    | Archivo         | `1.3rem`                      | 600    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | Inter           | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.06em          |
| Body paragraph     | Inter           | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Inter           | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | Inter           | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono   | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Diagram label      | IBM Plex Mono   | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | IBM Plex Mono   | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Table header       | IBM Plex Mono   | `0.7rem`                      | 500    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | Inter           | `0.82rem`                     | 400    |             | First column: `--text` + weight 600        |
| `<strong>` in body | Inter           | inherit                       | 600    |             | Color: `--text`                            |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace annotation label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

### Border Radius

- **0px everywhere.** All components use sharp corners for a precise, technical, drafting aesthetic. No rounding on cards, panels, tags, callouts, or any other element.

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Drafting grid overlay:** via `::before` using `linear-gradient` in both axes — major grid (80px, 25% opacity) and minor grid (16px, 8% opacity) in pencil-line grey, evoking architectural planning grids
- **Vignette:** Subtle radial gradient via `::after` darkening the edges, simulating vellum paper aging at borders
- **Title accent:** The `<span>` inside h1 uses `--accent` color (redline red)
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
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 0`, `padding: 1.5rem`
- **Hover:** Border color changes to `--text`, gains subtle `box-shadow: 0 1px 4px rgba(42, 38, 32, 0.08)`
- **Top accent bar:** 3px colored bar at the top edge (via `::before`). Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `1px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** All stages have `border-radius: 0`. Adjacent stages share borders.
- **Top accent:** 3px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step number (IBM Plex Mono, `0.7rem`, faint) → name (weight 600, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `1px solid var(--border)`, `border-radius: 0`, `padding: 1.25rem`
- **Number:** Archivo, `2rem`, weight 700, `--accent` (redline red), fixed `2rem` width, centered
- **Content:** h4 title (weight 600, `0.85rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `3px solid var(--accent)`
- Background: `rgba(200, 48, 48, 0.04)`
- Border-radius: `0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (redline red)

### Tags / Pills

Small inline labels with semantic colors.

- Font: IBM Plex Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `0`
- Background: transparent semantic color at 10% opacity
- Border: `1px solid` in dim semantic color
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** IBM Plex Mono, weight 500, `0.7rem`, `letter-spacing: 0.1em`, uppercase, `--text-faint`, bottom border `2px solid var(--text)` (heavier than body rows)
- **Body cells:** `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px solid var(--border)`
- **First column** in body: `--text` color, weight 600

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `1px solid var(--border)`
- Border-radius: `0`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in IBM Plex Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Inter', sans-serif`
- Node boxes: `--surface` fill, semantic color stroke (1.5px), `rx="0"` (no rounding)
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1px`)

---

## Unique Components

### Dimension Callout

Architectural dimension annotations with extension lines and a measurement label.

- Container: Flex column, centered, `2.5rem` vertical margin
- **SVG-based:** Two vertical extension lines, a horizontal dimension line split by a measurement label, and tick marks at each end
- **Extension lines:** Thin (0.75px), `--text` color
- **Tick marks:** Heavier (1.5px), `--text` color, 10px tall
- **Measurement text:** IBM Plex Mono, `11px`, `letter-spacing: 0.05em`, `--text` color
- Can be stacked for multi-segment dimensions

### Title Block

A footer-style component mimicking the title block on architectural drawings.

- Container: `2px solid var(--text)` border (heavier than standard), `--surface` background
- **Header row:** `--surface-2` background, `2px solid var(--text)` bottom border
- **Cells:** Grid of `flex: 1` cells with `1px solid var(--border)` right borders
  - `.tb-wide` — `flex: 2` for wider cells
  - `.tb-narrow` — `flex: 0 0 120px` for fixed-width cells
- **Label:** IBM Plex Mono, `0.55rem`, uppercase, `letter-spacing: 0.12em`, `--text-faint`
- **Value:** IBM Plex Mono, `0.8rem`, weight 500, `--text`
- **Large value:** Archivo, `1rem`, weight 700, uppercase (for project name)
- **Revision history:** Flex rows with rev number (weight 600), date (faint), and description

### Section Cut Divider

An SVG divider styled like an architectural section-cut line.

- Container: `3rem` vertical margin, centered, `max-width: 600px`
- **Line:** Heavy `1.5px` stroke in `--text` color, split by center label
- **End circles:** `r="10"`, `--bg` fill, `--text` stroke (1.5px), containing a section letter/number
- **Letters/numbers:** IBM Plex Mono, `10px`, weight 600, `--text` color
- **Center label:** IBM Plex Mono, `9px`, `letter-spacing: 0.15em`, `--text-faint`
- Variant: Use `--accent` color for redline markup sections

### Grid Overlay Panel

A card-style container with a faint floor-plan grid background.

- Container: `--surface` background, `1px solid var(--border)`, `border-radius: 0`, `padding: 2rem`
- **Grid:** CSS `::before` pseudo-element with four-layer `linear-gradient`:
  - Major grid lines: 60px spacing, 20% opacity
  - Minor grid lines: 12px spacing, 6% opacity
  - Both horizontal and vertical
- **Label (optional):** `.grid-panel-label` — IBM Plex Mono, `0.65rem`, uppercase, `letter-spacing: 0.12em`, `--text-faint`, with border-bottom separator
- All child content has `position: relative; z-index: 1` to sit above the grid

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `0`
- Border: `1px solid var(--border)`
- Color: `--accent` (redline red)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Warm vellum, not white** — backgrounds use warm off-white tones reminiscent of tracing paper and vellum, not pure white.
2. **Zero border-radius** — all components use sharp 0px corners for a precise, technical drafting aesthetic.
3. **Thin pen lines** — 1px solid borders everywhere, with a heavier 2px border on table headers and title blocks for hierarchy.
4. **Redline markup accent** — the primary accent is redline red (#c83030), echoing the architectural tradition of revision annotations.
5. **Three-tier text** — drafting ink (--text), light pencil (--text-dim), ghost line (--text-faint).
6. **Three-font hierarchy** — Archivo for geometric headings, Inter for clean body text, IBM Plex Mono for all technical annotations and dimensions.
7. **Architectural components** — dimension callouts, section-cut dividers, grid overlay panels, and title blocks bring the spatial language of construction drawings into the design system.
8. **Drafting grid texture** — the hero and grid panels use faint repeating grid lines evoking floor-plan planning grids.
