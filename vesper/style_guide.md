# Vesper — Style Guide

A dark, editorial design system with purple-tinted surfaces, semantic color coding, and typographic hierarchy. Intended for long-form single-page documents, methodology write-ups, and technical reports.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                  |
|----------------|-----------|----------------------------------------|
| `--bg`         | `#0c0b0f` | Page background                        |
| `--surface`    | `#16141c` | Cards, diagram containers, table rows  |
| `--surface-2`  | `#1e1b27` | Nested surfaces (if needed)            |
| `--surface-3`  | `#272433` | Tertiary surface (if needed)           |
| `--border`     | `#2e2a3a` | Borders, dividers, section separators  |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#e8e4f0` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#9b95aa` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#6b6578` | Labels, metadata, captions, subtle annotations  |

### Accent & Semantic Colors

Each semantic color has a full and dim variant. The dim variant is used for muted UI like numbered labels or subdued strokes. Semantic colors also have a transparent fill variant (`rgba(color, 0.06–0.12)`) used for tinted backgrounds on tags and card highlights.

| Token           | Hex       | Role                        |
|-----------------|-----------|-----------------------------|
| `--accent`      | `#c4a0ff` | Primary accent (purple)     |
| `--accent-dim`  | `#8b6abf` | Muted accent                |
| `--capture`     | `#6ecfb5` | Green — input, creation     |
| `--capture-dim` | `#2a6b58` | Muted green                 |
| `--refine`      | `#f0b866` | Amber — processing, triage  |
| `--refine-dim`  | `#8a6a2e` | Muted amber                 |
| `--execute`     | `#f07272` | Red — action, execution     |
| `--execute-dim` | `#8a3636` | Muted red                   |
| `--batch`       | `#6aaef0` | Blue — grouping, review     |
| `--batch-dim`   | `#2e5a8a` | Muted blue                  |

---

## Typography

### Font Stack

| Role      | Family              | Google Fonts Import                       |
|-----------|---------------------|-------------------------------------------|
| Headings  | DM Serif Display    | `DM+Serif+Display`                        |
| Body      | DM Sans             | `DM+Sans:wght@300;400;500;600`            |
| Mono      | JetBrains Mono      | `JetBrains+Mono:wght@400;500`             |

```html
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=DM+Sans:wght@300;400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family           | Size                          | Weight | Line-height | Notes                                    |
|--------------------|------------------|-------------------------------|--------|-------------|------------------------------------------|
| Hero h1            | DM Serif Display | `clamp(3rem, 8vw, 6rem)`     | 400    | 1.1         | Fluid scaling. Accent-colored `<span>` for emphasis. |
| h2 (section)       | DM Serif Display | `2.4rem`                      | 400    | 1.2         |                                          |
| h3 (subsection)    | DM Serif Display | `1.4rem`                      | 400    | default     | `margin-top: 2.5rem`                    |
| h4 (card title)    | DM Sans          | `0.85rem`                     | 600    |             |                                          |
| Body paragraph     | DM Sans          | `0.95rem`                     | 300    | 1.7         | Color: `--text-dim`                      |
| Hero subtitle      | DM Sans          | `1.1rem`                      | 300    | 1.8         | Color: `--text-dim`, max-width 560px     |
| Card body          | DM Sans          | `0.82rem`                     | 300    | 1.6         | Color: `--text-dim`                      |
| Section label      | JetBrains Mono   | `0.65rem`                     | 400    |             | Uppercase, `letter-spacing: 0.3em`, color: `--text-faint` |
| Hero label         | JetBrains Mono   | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.3em`, color: `--accent-dim` |
| Diagram label      | JetBrains Mono   | `0.6rem`                      | 400    |             | Uppercase, `letter-spacing: 0.25em`, color: `--text-faint` |
| Tag                | JetBrains Mono   | `0.6rem`                      | 400    |             | `letter-spacing: 0.1em`                 |
| Table header       | DM Sans          | `0.7rem`                      | 600    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint` |
| Table cell         | DM Sans          | `0.82rem`                     | 300    |             | First column: `--text` + weight 500      |
| `<strong>` in body | DM Sans          | inherit                       | 500    |             | Color: `--text` (stands out from dim body text) |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `6rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **section label** (monospace, faint, uppercase) in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with the `.diagram-wrap.full-bleed` pattern

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- Subtle radial gradient glow behind content: `radial-gradient(ellipse at center, rgba(196,160,255,0.06) 0%, transparent 70%)` — 800x800px, centered above
- **Staggered fade-up animation** on load:
  - Label: 0s delay
  - h1: 0.15s delay
  - Subtitle: 0.3s delay
  - Version: 0.45s delay
  - Animation: `opacity 0→1, translateY(20px→0)`, 0.8s ease-out
- Version tag: JetBrains Mono, `0.65rem`, `--text-faint`, `letter-spacing: 0.15em`

---

## Components

### Flow Cards (2-Column Grid)

A grid of cards used for listing related items.

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--surface` background, `--border` border, `border-radius: 12px`, `padding: 1.5rem`
- **Top accent bar:** 2px colored bar at the top edge (via `::before` pseudo-element). Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`, `margin-bottom: 0.75rem`) → h4 title → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `--border` border, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `12px`, last gets right border-radius `12px`. Adjacent stages share borders (`border-left: none` on non-first).
- **Top accent:** 2px solid top border in semantic color
- **Content:** Step number (monospace, `0.55rem`, faint) → name (weight 600, `0.8rem`) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `--border` border, `border-radius: 10px`, `padding: 1.25rem`
- **Number:** DM Serif Display, `1.6rem`, `--accent-dim`, fixed `2rem` width, centered
- **Content:** h4 title (weight 600, `0.85rem`) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `2px solid var(--accent-dim)`
- Background: `rgba(196,160,255,0.03)`
- Border-radius: `0 10px 10px 0` (rounded on right side only)
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (purple)

### Tags / Pills

Small inline labels.

- Font: JetBrains Mono, `0.6rem`, `letter-spacing: 0.1em`
- Padding: `0.2em 0.6em`
- Border-radius: `4px`
- Background: transparent semantic color at ~12% opacity
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** Uppercase, weight 600, `0.7rem`, `letter-spacing: 0.1em`, `--text-faint`, bottom border `1px solid var(--border)`
- **Body cells:** `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border at ~50% opacity
- **First column** in body: `--text` color, weight 500 (acts as row label)

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `1px solid var(--border)`
- Border-radius: `16px`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in monospace faint text (e.g., "Figure 1 — Title")

### SVG Diagrams

- Text inside SVGs uses `font-family: 'DM Sans', sans-serif`
- Node boxes: `--surface` fill, semantic color stroke, `rx="12"` (or `rx="8"` for smaller nodes)
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3` or `3,2`), semantic colored, thin (`1–1.2px`)
- Arrow markers: Small chevron in matching semantic color

---

## Global Reset & Defaults

```css
* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: 'DM Sans', sans-serif;
  font-weight: 300;
  line-height: 1.7;
  overflow-x: hidden;
}
```

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text, `0.75rem`, `--text-faint`

---

## Summary of Key Patterns

1. **Dark with purple tint** — backgrounds are not pure black/gray but have a subtle purple undertone.
2. **Three-tier text hierarchy** — primary (`--text`), dim (`--text-dim`), faint (`--text-faint`). Body defaults to dim; headings and emphasis use primary.
3. **Monospace for metadata** — section numbers, labels, tags, and diagram annotations all use JetBrains Mono at small sizes with generous letter-spacing and uppercase.
4. **Serif for headings only** — DM Serif Display is reserved for h1–h3 and decorative large numbers. Everything else is DM Sans.
5. **Semantic color system** — four named categories (capture/refine/execute/batch) each with full, dim, and transparent-fill variants. Cards, pipeline stages, tags, and diagram elements all reference these.
6. **Subtle surfaces** — cards and containers use `--surface` against `--bg`, creating gentle depth without heavy shadows. Borders are the same purple-tinted tone.
7. **Generous spacing** — large section padding (`6rem`), comfortable card padding (`1.5rem`), and wide container margins keep the layout open and readable.
8. **Responsive** — fluid hero type with `clamp()`, card grids collapse to single column below `640px`, diagrams scroll horizontally.
