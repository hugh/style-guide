# Superhero — Style Guide

A bold comic book design system with thick black outlines, halftone dots, action lines, newsprint textures, and classic primary-color semantics. Intended for single-page documents, project briefs, and anything that deserves Kirby-era energy.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                  |
|----------------|-----------|----------------------------------------|
| `--bg`         | `#f5f0e0` | Page background (newsprint cream)      |
| `--surface`    | `#fffbf0` | Cards, panels, diagram containers      |
| `--surface-2`  | `#f0ead5` | Nested surfaces, halftone panels       |
| `--surface-3`  | `#e5dcc8` | Tertiary surface (if needed)           |
| `--border`     | `#1a1a1a` | Thick black comic outlines (3px)       |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#1a1a1a` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#4a4a48` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#8a8878` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags and bursts.

| Token           | Hex       | Role                              |
|-----------------|-----------|-----------------------------------|
| `--accent`      | `#d42020` | Primary accent (Heroic Red)       |
| `--accent-dim`  | `#8a1818` | Muted accent                      |
| `--capture`     | `#2d8c3c` | Hero Green — creation, success    |
| `--capture-dim` | `#1e6028` | Muted green                       |
| `--refine`      | `#e8a820` | Comic Yellow — processing, power  |
| `--refine-dim`  | `#b88018` | Muted yellow                      |
| `--execute`     | `#d42020` | Action Red — danger, action       |
| `--execute-dim` | `#8a1818` | Muted red                         |
| `--batch`       | `#2060c0` | Heroic Blue — grouping, defense   |
| `--batch-dim`   | `#184890` | Muted blue                        |

---

## Typography

### Font Stack

| Role      | Family           | Google Fonts Import                      |
|-----------|------------------|------------------------------------------|
| Headings  | Bangers          | `Bangers`                                |
| Body      | Barlow           | `Barlow:wght@300;400;500;600`            |
| Labels    | Permanent Marker | `Permanent+Marker`                       |

```html
<link href="https://fonts.googleapis.com/css2?family=Bangers&family=Barlow:wght@300;400;500;600&family=Permanent+Marker&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family           | Size                          | Weight | Line-height | Notes                                    |
|--------------------|------------------|-------------------------------|--------|-------------|------------------------------------------|
| Hero h1            | Bangers          | `clamp(3.5rem, 10vw, 7rem)`  | 400    | 1.05        | Fluid scaling. Accent-colored `<span>` for emphasis. |
| h2 (section)       | Bangers          | `2.4rem`                      | 400    | 1.15        | letter-spacing: 0.04em                   |
| h3 (subsection)    | Bangers          | `1.6rem`                      | 400    | default     | `margin-top: 2.5rem`                    |
| h4 (card title)    | Barlow           | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.04em        |
| Body paragraph     | Barlow           | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                      |
| Hero subtitle      | Barlow           | `1.1rem`                      | 400    | 1.8         | Color: `--text-dim`, max-width 560px     |
| Card body          | Barlow           | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                      |
| Section label      | Permanent Marker | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint` |
| Hero label         | Permanent Marker | `0.9rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--accent` |
| Diagram label      | Permanent Marker | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint` |
| Tag                | Permanent Marker | `0.7rem`                      | 400    |             | `letter-spacing: 0.04em`                |
| Table header       | Barlow           | `0.7rem`                      | 600    |             | Uppercase, `letter-spacing: 0.08em`, color: `--text-faint` |
| Table cell         | Barlow           | `0.82rem`                     | 400    |             | First column: `--text` + weight 600      |
| `<strong>` in body | Barlow           | inherit                       | 600    |             | Color: `--text`                          |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `3px solid var(--border)` top border (thick comic outlines)
- Each section opens with a **hand-lettered label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed` or `.halftone-panel.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Action lines:** `conic-gradient` radiating from center with faint colored rays
- **Halftone dots:** `radial-gradient` dot pattern overlay via `::after`
- **Staggered fade-up animation** on load:
  - Label: 0s delay
  - h1: 0.15s delay
  - Subtitle: 0.3s delay
  - Version: 0.45s delay
  - Animation: `opacity 0→1, translateY(20px→0)`, 0.8s ease-out
- Version tag: Permanent Marker, `0.8rem`, `--text-faint`, `letter-spacing: 0.08em`

---

## Components

### Flow Cards (2-Column Grid)

A grid of cards used for listing related items.

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--surface` background, **3px solid `--border`** (thick comic outline), `border-radius: 4px`, `padding: 1.5rem`
- **Rotation:** Odd cards rotate -0.5deg, even cards rotate 0.4deg. Reset to 0deg on hover with 1.02 scale.
- **Top accent bar:** 4px colored bar at the top edge (via `::before`). Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, **3px solid `--border`**, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `4px`, last gets right border-radius `4px`. Adjacent stages share borders.
- **Top accent:** 4px solid top border in semantic color
- **Content:** Step number (Permanent Marker, `0.7rem`, faint) → name (weight 600, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, **3px solid `--border`**, `border-radius: 4px`, `padding: 1.25rem`
- **Number:** Bangers, `2rem`, `--accent`, fixed `2rem` width, centered
- **Content:** h4 title (weight 600, `0.85rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `4px solid var(--accent)`
- Background: `rgba(212, 32, 32, 0.06)`
- Border-radius: `0 4px 4px 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (Heroic Red)

### Tags / Pills

Small inline labels with bold borders.

- Font: Permanent Marker, `0.7rem`, `letter-spacing: 0.04em`
- Padding: `0.2em 0.6em`
- Border-radius: `3px`
- Background: transparent semantic color at 12% opacity
- Border: `2px solid` in semantic color
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** Uppercase, weight 600, `0.7rem`, `letter-spacing: 0.08em`, `--text-faint`, bottom border `3px solid var(--border)`
- **Body cells:** `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px solid var(--surface-3)`
- **First column** in body: `--text` color, weight 600

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `3px solid var(--border)` (thick comic outline)
- Border-radius: `4px`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in Permanent Marker faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Barlow', sans-serif`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="12"`
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.2px`)

---

## Unique Components

### Comic Panel

A content panel with thick black border, slight rotation, and halftone dot overlay.

- Border: `3px solid var(--border)`
- Border-radius: `4px`
- `transform: rotate(-0.5deg)` for dynamic energy
- Halftone dot overlay via `::before` using `radial-gradient`
- Dots: 6px spacing, `rgba(26, 26, 26, 0.06)`

### POW Burst

A starburst/explosion callout with overlapping rotated boxes.

- Font: Bangers, `1.5rem`, uppercase
- Two layered `::before` and `::after` boxes rotated at +3deg and -2deg
- Color variants: `.burst-red`, `.burst-blue`, `.burst-yellow`, `.burst-green`
- Each variant uses the corresponding semantic fill background and border color

### Speech Bubble

A callout with a CSS triangle pointer for dialogue.

- Background: `--surface`
- Border: `3px solid var(--border)`
- Border-radius: `16px` (rounded for balloon effect)
- Triangle pointer via `::after` (border-based CSS triangle) at bottom-left
- Inner fill triangle via `::before` to mask the border on the pointer

### Halftone Panel

A diagram container with dot pattern overlay for newsprint texture.

- Same structure as `.diagram-wrap` but with a halftone `::before` overlay
- Dots: 6px spacing, `radial-gradient` with `rgba(26, 26, 26, 0.07)`
- Supports `.full-bleed` class for 1100px expansion

---

## Key Visual Techniques

### Thick Black Outlines

```css
border: 3px solid var(--border);  /* --border: #1a1a1a */
```

Applied to all cards, panels, and containers. The defining visual trait of the comic aesthetic.

### Halftone Dot Pattern

```css
background: radial-gradient(circle, rgba(26, 26, 26, 0.07) 1px, transparent 1px);
background-size: 6px 6px;
```

Used on comic panels, halftone panels, and the hero section. Creates classic newsprint texture.

### Action Lines

```css
background: conic-gradient(from 0deg, transparent, colored-rays...);
```

Radiating colored rays from the center of the hero section. Uses alternating transparent and faintly-colored wedges.

### Card Rotation

```css
.flow-card:nth-child(odd) { transform: rotate(-0.5deg); }
.flow-card:nth-child(even) { transform: rotate(0.4deg); }
```

Subtle alternating rotation creates dynamic "tossed panels" energy.

### POW Burst Effect

```css
.pow-burst::before { transform: rotate(3deg); }
.pow-burst::after { transform: rotate(-2deg); }
```

Two overlapping rotated boxes behind the text create an explosion/starburst effect.

---

## Footer

- Top border: `3px solid var(--border)`
- Padding: `3rem 0`
- Centered text in Permanent Marker, `0.8rem`, `--text-faint`

---

## Summary of Key Patterns

1. **Newsprint, not white** — backgrounds use warm cream tones like vintage comic book paper.
2. **Thick black outlines** — 3px solid borders on everything define the comic book panel aesthetic.
3. **Three-tier text** — dark ink (--text), medium (--text-dim), faded (--text-faint).
4. **Hand-lettered labels** — Permanent Marker gives section labels and tags a comic lettering feel.
5. **Big bold headings** — Bangers is reserved for h1–h3, delivering maximum comic impact.
6. **Primary-color semantics** — classic comic palette (green, yellow, red, blue) with full/dim/fill variants.
7. **Halftone dots** — radial-gradient dot patterns reference vintage newsprint printing.
8. **Dynamic energy** — card rotation, action lines, and POW bursts inject Kirby-era kinetic energy.
