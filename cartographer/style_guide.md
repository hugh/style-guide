# Cartographer — Style Guide

Aged parchment under warm light. A design system inspired by antique maps and surveyor's notebooks — topographic contour lines, coordinate grids, legend boxes, compass-rose dividers, and location cards for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#f2ead8` | Page background (aged parchment)         |
| `--surface`    | `#e8e0cc` | Cards, panels, diagram containers        |
| `--surface-2`  | `#ded6c0` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#d4ccb4` | Tertiary surface, row separators         |
| `--border`     | `#c4bca0` | Card borders, contour lines, dividers    |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#2a2218` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#5c5240` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#8a8068` | Labels, coordinate metadata, captions           |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                        |
|-----------------|-----------|---------------------------------------------|
| `--accent`      | `#8b4020` | Primary accent (Burnt Umber)                |
| `--accent-dim`  | `#6a3018` | Muted accent                                |
| `--capture`     | `#2a7048` | Forest Green — vegetation, terrain          |
| `--capture-dim` | `#1e5434` | Muted green                                 |
| `--refine`      | `#b08820` | Goldenrod — elevation, contours, landmarks  |
| `--refine-dim`  | `#886818` | Muted gold                                  |
| `--execute`     | `#a83020` | Terra Cotta — boundaries, danger zones      |
| `--execute-dim` | `#802418` | Muted red                                   |
| `--batch`       | `#2a5488` | Cartographic Blue — water, ocean, rivers    |
| `--batch-dim`   | `#1e3e68` | Muted blue                                  |

---

## Typography

### Font Stack

| Role      | Family              | Google Fonts Import                                     |
|-----------|---------------------|---------------------------------------------------------|
| Headings  | Cormorant Garamond  | `Cormorant+Garamond:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500` |
| Body      | Source Serif 4      | `Source+Serif+4:ital,wght@0,300;0,400;0,500;0,600;1,400` |
| Labels    | IBM Plex Mono       | `IBM+Plex+Mono:wght@400;500;600`                       |

```html
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500&family=Source+Serif+4:ital,wght@0,300;0,400;0,500;0,600;1,400&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family              | Size                              | Weight | Line-height | Notes                                            |
|--------------------|---------------------|---------------------------------------|--------|-------------|--------------------------------------------------|
| Hero h1            | Cormorant Garamond  | `clamp(2.8rem, 7vw, 5rem)`          | 700    | 1.08        | Italic `<span>` in --accent for title word       |
| h2 (section)       | Cormorant Garamond  | `2rem`                               | 700    | 1.15        |                                                  |
| h3 (subsection)    | Cormorant Garamond  | `1.3rem`                             | 700    | 1.25        | `margin-top: 2.5rem`                             |
| h4 (card title)    | Source Serif 4      | `0.82rem`                            | 600    |             | Uppercase, letter-spacing: 0.06em                |
| Body paragraph     | Source Serif 4      | `0.95rem`                            | 400    | 1.7         | Color: `--text-dim`                              |
| Hero subtitle      | Source Serif 4      | `1.05rem`                            | 400    | 1.8         | Color: `--text-dim`, max-width 560px             |
| Section label      | IBM Plex Mono       | `0.75rem`                            | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono       | `0.8rem`                             | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--text-faint`  |
| Tag                | IBM Plex Mono       | `0.7rem`                             | 400    |             | `letter-spacing: 0.06em`                         |

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

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle, version
- **Contour lines:** Concentric elliptical gradients via `::before`, evoking topographic map contours
- **Aged vignette:** Radial gradient darkening at edges via `::after`, like age-worn parchment borders
- **Title accent:** `<span>` inside h1 uses italic `--accent` (burnt umber)
- **Paper grain:** Subtle overlay on `body::after` with warm color splotches
- **Staggered fade-up animation** on load

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Cartographer-specific adjustments:
- Border-radius: `3px` (subtle, like the sharp corners of a folded map)
- Hover uses warm paper shadow: `rgba(42, 34, 24, 0.08)`
- Principle numbers use Cormorant Garamond at `2.2rem` in `--accent`
- Light theme: parchment backgrounds with dark ink text

---

## Unique Components

### Legend Box

A map legend panel showing symbol definitions.

- **Container:** `--surface` background, `2px solid var(--border)`, `border-radius: 3px`
- **Title:** Cormorant Garamond, `1rem`, weight 700, uppercase, `letter-spacing: 0.08em`, bottom border
- **Entries:** Flex column with `0.6rem` gap
- **Symbol types:**
  - `.legend-symbol` — `28px x 16px` colored rectangle
  - `.legend-line` — `28px` width border-top (solid or `.dashed`)
  - `.legend-dot` — `10px` circle, centered within 28px width
- **Text:** `0.85rem`, `--text-dim`

### Compass Rose

A decorative compass element as a section divider.

- **Container:** `120px x 120px`, centered, relative positioned
- **Ring:** Circular border with inner ring via `::before`
- **Crosshair:** Vertical and horizontal lines via `::before`/`::after`
- **Directions:** Cormorant Garamond, `0.85rem`, weight 700. N is `--accent` colored, others `--text`
- **Center:** `8px` circle in `--accent`

### Coordinate Card

Location cards with coordinates, elevation, and terrain data.

- **Grid:** `repeat(auto-fill, minmax(220px, 1fr))`, `1.25rem` gap
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 3px`
- **Name:** Cormorant Garamond, `1.1rem`, weight 700, `--text`
- **Position:** IBM Plex Mono, `0.72rem`, `--accent`, with degree/minute/second notation
- **Details:** Key-value rows with IBM Plex Mono keys (`0.68rem`, `--text-faint`, uppercase) and Source Serif 4 values (`--text-dim`)

### Contour Divider

Wavy topographic contour lines as a section separator.

- **Container:** `40px` tall, overflow hidden
- **SVG:** Three wavy paths with `stroke: var(--border)`, varying stroke widths (1, 1, 1.5)
- **Paths:** Quadratic bezier curves creating organic undulation

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--text` (dark ink)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Aged parchment** — backgrounds use warm cream-tan tones like hand-drawn maps on aged paper.
2. **Burnt umber accent** — the primary color evokes sepia ink and hand-coloured cartographic details.
3. **Three-tier text** — dark ink (--text), sepia body (--text-dim), faded marking (--text-faint).
4. **Old-map serif headings** — Cormorant Garamond delivers the elegance of engraved map cartouches.
5. **Clean body serif** — Source Serif 4 provides crisp readability like well-set geographic descriptions.
6. **Cartographic semantics** — forest green (vegetation), goldenrod (elevation), terra cotta (boundaries), cartographic blue (water).
7. **Map artifacts** — legend boxes, compass roses, coordinate cards, and contour dividers bring the physical map into the design.
8. **Contour-line texture** — concentric elliptical gradients in the hero evoke topographic survey lines.
