# Art Deco — Style Guide

A 1920s Gatsby-era design system with burnished gold accents, geometric ornaments, jewel-tone semantic colors, and Art Deco typography. Intended for long-form single-page documents, methodology write-ups, and presentations with vintage elegance.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                  |
|----------------|-----------|----------------------------------------|
| `--bg`         | `#0a0a08` | Page background                        |
| `--surface`    | `#151510` | Cards, diagram containers, table rows  |
| `--surface-2`  | `#1e1e16` | Nested surfaces (if needed)            |
| `--surface-3`  | `#282820` | Tertiary surface (if needed)           |
| `--border`     | `#2e2a1e` | Borders, dividers, section separators  |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#f0e8d0` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#b0a888` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#706848` | Labels, metadata, captions, subtle annotations  |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent fill variants. The dim variant is used for muted UI like numbered labels or subdued strokes. Fill variants use ~10% opacity for tinted tag backgrounds.

| Token            | Hex       | Role                          |
|------------------|-----------|-------------------------------|
| `--accent`       | `#c9a832` | Primary accent (burnished gold) |
| `--accent-dim`   | `#8a7020` | Muted gold                    |
| `--capture`      | `#2a9d6e` | Emerald — input, creation     |
| `--capture-dim`  | `#1a6848` | Muted emerald                 |
| `--refine`       | `#c47a2a` | Amber — processing, triage    |
| `--refine-dim`   | `#84521a` | Muted amber                   |
| `--execute`      | `#c43040` | Ruby — action, execution      |
| `--execute-dim`  | `#84202c` | Muted ruby                    |
| `--batch`        | `#3068a8` | Sapphire — grouping, review   |
| `--batch-dim`    | `#204870` | Muted sapphire                |

---

## Typography

### Font Stack

| Role      | Family              | Google Fonts Import                                |
|-----------|---------------------|----------------------------------------------------|
| Headings  | Playfair Display    | `Playfair+Display:wght@400;700`                    |
| Body      | Raleway             | `Raleway:wght@300;400;500;600`                     |
| Metadata  | Josefin Sans        | `Josefin+Sans:wght@300;400;600`                    |

```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Raleway:wght@300;400;500;600&family=Josefin+Sans:wght@300;400;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family           | Size                          | Weight | Letter-spacing | Notes                                    |
|--------------------|------------------|-------------------------------|--------|----------------|------------------------------------------|
| Hero h1            | Playfair Display | `clamp(3rem, 8vw, 6rem)`     | 400    | 0.08em         | Fluid scaling. Gold `<span>` for emphasis. |
| h2 (section)       | Playfair Display | `2.4rem`                      | 400    | 0.08em         |                                          |
| h3 (subsection)    | Playfair Display | `1.4rem`                      | 400    | 0.08em         | `margin-top: 2.5rem`                    |
| h4 (card title)    | Raleway          | `0.85rem`                     | 600    | 0.04em         |                                          |
| Body paragraph     | Raleway          | `0.95rem`                     | 300    |                | Color: `--text-dim`                      |
| Hero subtitle      | Raleway          | `1.1rem`                      | 300    |                | Color: `--text-dim`, max-width 560px     |
| Card body          | Raleway          | `0.82rem`                     | 300    |                | Color: `--text-dim`                      |
| Section label      | Josefin Sans     | `0.65rem`                     | 400    | 0.3em          | Uppercase, color: `--text-faint`         |
| Hero label         | Josefin Sans     | `0.7rem`                      | 400    | 0.3em          | Uppercase, color: `--accent-dim`         |
| Diagram label      | Josefin Sans     | `0.6rem`                      | 400    | 0.25em         | Uppercase, color: `--text-faint`         |
| Tag                | Josefin Sans     | `0.6rem`                      | 400    | 0.15em         | Uppercase                                |
| `<strong>` in body | Raleway          | inherit                       | 500    |                | Color: `--text`                          |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `6rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **section label** (Josefin Sans, faint, uppercase) in the format `— 01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with the `.diagram-wrap.full-bleed` pattern

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: monogram, label, h1, subtitle paragraph, version tag
- **Sunburst pattern** behind content via `conic-gradient` — alternating gold rays at 3% opacity
- **Gold line ornament** at bottom via `::after` — 200px centered gradient line
- **Staggered fade-up animation** on load (same timing as other themes)
- Version tag: Josefin Sans, `0.65rem`, `--text-faint`, `letter-spacing: 0.15em`, uppercase

---

## Components

### Monogram

A decorative initial letter in a geometric diamond frame.

- Size: 80x80px, centered text
- Font: Playfair Display, 2.4rem, weight 700, gold color
- Frame: Two nested rotated squares via `::before` (gold) and `::after` (border color)

### Gilded Frame

A double-bordered card with gold corner chevrons.

- Background: `--surface`
- Outer border: `1px solid var(--accent-dim)`
- Inner frame: `box-shadow: inset 0 0 0 3px var(--surface), inset 0 0 0 4px var(--border)`
- Corner chevrons: `::before` (top-left) and `::after` (bottom-right) with partial borders
- Padding: `2.5rem`
- No border-radius

### Deco Divider

A geometric ornamental separator using `◆` with extending lines.

- Diamond glyph as text content
- Lines extend via `::before` and `::after` pseudo-elements
- Color: `--accent-dim`
- Max line width: 120px each side

### Sunburst Panel

A diagram container with a subtle radial gold gradient.

- Class: `.diagram-wrap.sunburst`
- Background: `radial-gradient(ellipse at center, rgba(201,168,50,0.04) 0%, var(--surface) 70%)`

### Flow Cards (2-Column Grid)

A grid of cards used for listing related items.

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--surface` background, `--border` border, `padding: 1.5rem`, no border-radius
- **Top accent bar:** 2px colored bar at the top edge (via `::before`). Color matches semantic category.
- **Content:** Icon (diamond glyph, `1.4rem`) → h4 title → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally
- **Stage:** `--surface` background, `--border` border, `padding: 1.25rem`, centered text, no border-radius
- **Top accent:** 2px solid top border in semantic color
- **Content:** Step number (Josefin Sans, `0.55rem`, faint, uppercase) → name (weight 600) → description

### Principle / Numbered List

A vertical stack of numbered items.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `--surface` background, `--border` border, no border-radius
- **Number:** Playfair Display, `1.6rem`, `--accent-dim`, fixed `2rem` width
- **Content:** h4 title + body paragraph

### Callout

A highlighted aside or important note.

- Left border: `2px solid var(--accent-dim)`
- Background: `rgba(201,168,50,0.03)`
- No border-radius (geometric sharp edges)
- `<strong>` within callouts uses `--accent` color (gold)

### Tags / Pills

Small inline labels.

- Font: Josefin Sans, `0.6rem`, `letter-spacing: 0.15em`, uppercase
- No border-radius
- Background: transparent semantic color at ~10% opacity
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** Uppercase, weight 600, `0.7rem`, gold bottom border (`1px solid var(--accent-dim)`)
- **Body cells:** `0.82rem`, `--text-dim`, border at ~50% opacity
- **First column** in body: `--text` color, weight 500

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `1px solid var(--border)`
- No border-radius (geometric)
- Padding: `2.5rem`
- `overflow-x: auto`
- Diagram label in Josefin Sans faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Raleway', sans-serif`
- Node boxes: `--surface` fill, semantic color stroke, `rx="12"`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint color, thin

---

## Global Reset & Defaults

```css
* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: 'Raleway', sans-serif;
  font-weight: 300;
  line-height: 1.7;
  overflow-x: hidden;
}
```

---

## Footer

- Top border: `1px solid var(--border)` with centered 60px gold accent line overlay
- Padding: `3rem 0`
- Centered text, `0.75rem`, `--text-faint`

---

## Summary of Key Patterns

1. **Dark with golden warmth** — backgrounds carry a subtle warm golden undertone, not pure black or gray.
2. **Geometric precision** — no border-radius on cards, containers, or tags. Sharp corners throughout.
3. **Gold ornamental accents** — burnished gold used for dividers, frames, monograms, and emphasis.
4. **Three-tier text hierarchy** — cream primary (`--text`), dim (`--text-dim`), faint (`--text-faint`). Body defaults to dim.
5. **Wide letterspacing** — headings at 0.08em, labels at 0.3em for characteristic Art Deco rhythm.
6. **Jewel-tone semantics** — Emerald, Amber, Ruby, Sapphire with full, dim, and fill variants.
7. **Sunburst & conic patterns** — radial gold gradients on hero and diagram panels via pure CSS.
8. **Diamond motifs** — diamond glyphs replace dots and circles as decorative elements.
9. **Generous spacing** — large section padding (`6rem`), comfortable card padding (`1.5rem`), open layout.
10. **Responsive** — fluid hero type with `clamp()`, card grids collapse below `640px`.
