# Doodle — Style Guide

A warm sketchbook design system with ink textures, hand-drawn borders, typewriter metadata, and muted ink-tone semantic colors. Intended for single-page documents, creative briefs, and annotation-heavy write-ups.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                  |
|----------------|-----------|----------------------------------------|
| `--bg`         | `#f5f0e6` | Page background (warm cream)           |
| `--surface`    | `#ede8dc` | Cards, diagram containers, table rows  |
| `--surface-2`  | `#e6e0d2` | Nested surfaces, sketch panels         |
| `--surface-3`  | `#ddd7c8` | Tertiary surface (if needed)           |
| `--border`     | `#c8c0b0` | Borders, dividers, section separators  |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#2a2520` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#6b6358` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#a09888` | Labels, metadata, captions, subtle annotations  |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                          |
|-----------------|-----------|-------------------------------|
| `--accent`      | `#8b6914` | Primary accent (sepia)        |
| `--accent-dim`  | `#b8960e` | Muted accent                  |
| `--capture`     | `#2d6a3f` | Ink Green — input, creation   |
| `--capture-dim` | `#5a9970` | Muted green                   |
| `--refine`      | `#5b3a8c` | Ink Violet — processing       |
| `--refine-dim`  | `#8a6bb8` | Muted violet                  |
| `--execute`     | `#a83228` | Ink Red — action, execution   |
| `--execute-dim` | `#cc6860` | Muted red                     |
| `--batch`       | `#1a5276` | Ink Blue — grouping, review   |
| `--batch-dim`   | `#4a88b0` | Muted blue                    |

---

## Typography

### Font Stack

| Role      | Family                   | Google Fonts Import                            |
|-----------|--------------------------|------------------------------------------------|
| Headings  | Shadows Into Light Two   | `Shadows+Into+Light+Two`                       |
| Body      | Rubik                    | `Rubik:wght@300;400;500;600`                   |
| Mono      | Special Elite            | `Special+Elite`                                |

```html
<link href="https://fonts.googleapis.com/css2?family=Shadows+Into+Light+Two&family=Rubik:wght@300;400;500;600&family=Special+Elite&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family                 | Size                          | Weight | Line-height | Notes                                    |
|--------------------|------------------------|-------------------------------|--------|-------------|------------------------------------------|
| Hero h1            | Shadows Into Light Two | `clamp(3rem, 8vw, 5.5rem)`   | 400    | 1.15        | Fluid scaling. Accent-colored `<span>` for emphasis. |
| h2 (section)       | Shadows Into Light Two | `2.2rem`                      | 400    | 1.25        |                                          |
| h3 (subsection)    | Shadows Into Light Two | `1.5rem`                      | 400    | default     | `margin-top: 2.5rem`                    |
| h4 (card title)    | Rubik                  | `0.85rem`                     | 600    |             |                                          |
| Body paragraph     | Rubik                  | `0.95rem`                     | 300    | 1.7         | Color: `--text-dim`                      |
| Hero subtitle      | Rubik                  | `1.1rem`                      | 300    | 1.8         | Color: `--text-dim`, max-width 560px     |
| Card body          | Rubik                  | `0.82rem`                     | 300    | 1.6         | Color: `--text-dim`                      |
| Section label      | Special Elite          | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | Special Elite          | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--accent` |
| Diagram label      | Special Elite          | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | Special Elite          | `0.7rem`                      | 400    |             | `letter-spacing: 0.05em`                |
| Table header       | Rubik                  | `0.7rem`                      | 600    |             | Uppercase, `letter-spacing: 0.08em`, color: `--text-faint` |
| Table cell         | Rubik                  | `0.82rem`                     | 300    |             | First column: `--text` + weight 500      |
| `<strong>` in body | Rubik                  | inherit                       | 500    |             | Color: `--text`                          |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `2px dashed var(--border)` top border
- Each section opens with a **typewriter page label** in the format `Pg. 01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed` or `.sketch-panel.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- Background: ruled notebook lines via `repeating-linear-gradient` at 40% opacity
- **Staggered fade-up animation** on load:
  - Label: 0s delay
  - h1: 0.15s delay
  - Subtitle: 0.3s delay
  - Version: 0.45s delay
  - Animation: `opacity 0→1, translateY(20px→0)`, 0.8s ease-out
- Version tag: Special Elite, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Components

### Flow Cards (2-Column Grid)

A grid of cards used for listing related items.

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--surface` background, `--border` border, hand-drawn `border-radius`, `padding: 1.5rem`
- **Rotation:** Odd cards rotate -0.4deg, even cards rotate 0.3deg. Reset to 0deg on hover.
- **Top accent bar:** 3px colored bar at the top edge (via `::before`). Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `--border` border, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `12px`, last gets right border-radius `12px`. Adjacent stages share borders.
- **Top accent:** 3px solid top border in semantic color
- **Content:** Step number (Special Elite, `0.65rem`, faint) → name (weight 600, `0.8rem`) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `--border` border, hand-drawn `border-radius`, `padding: 1.25rem`
- **Number:** Shadows Into Light Two, `1.8rem`, `--accent`, fixed `2rem` width, centered
- **Content:** h4 title (weight 600, `0.85rem`) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `3px solid var(--accent)`
- Background: `rgba(139, 105, 20, 0.05)`
- Border-radius: hand-drawn on right side only
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (sepia)

### Tags / Pills

Small inline labels with ink borders.

- Font: Special Elite, `0.7rem`, `letter-spacing: 0.05em`
- Padding: `0.2em 0.6em`
- Border-radius: `3px`
- Background: transparent semantic color at 10% opacity
- Border: `1px solid` in semantic color
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** Uppercase, weight 600, `0.7rem`, `letter-spacing: 0.08em`, `--text-faint`, bottom border `2px solid var(--border)`
- **Body cells:** `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px dashed var(--border)`
- **First column** in body: `--text` color, weight 500

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `1.5px solid var(--border)`
- Border-radius: hand-drawn (`--radius-sketch`)
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in Special Elite faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Rubik', sans-serif`
- Node boxes: `--surface` fill, semantic color stroke, `rx="12"`
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.2px`)

---

## Unique Components

### Notebook Page

A ruled-line container mimicking a physical notebook page.

- Background: layered `linear-gradient` for red margin line at 2.5rem + `repeating-linear-gradient` for horizontal rules every 32px
- Left padding: `4rem` (to clear the margin line)
- Border: `1.5px solid var(--border)`, hand-drawn `border-radius`
- Text `line-height: 32px` to align with rules

### Ink Stamp

Rubber-stamp style inline labels.

- Font: Special Elite, `0.7rem`, uppercase, `letter-spacing: 0.1em`
- Border: `2px solid` in variant color
- `transform: rotate(-3deg)` for stamped-at-an-angle effect
- `opacity: 0.85` for faded ink look
- Variants: `.stamp-approve` (green), `.stamp-review` (blue), `.stamp-draft` (violet), default (red)

### Doodle Divider

An ornamental `~ ~ ~` separator.

- Generated via `::before` pseudo-element
- Font: Shadows Into Light Two, `1.2rem`, `--text-faint`
- `letter-spacing: 0.3em`, centered
- Margin: `3rem 0`

### Sketch Panel

A diagram container with crosshatch background pattern.

- Background: dual `repeating-linear-gradient` at 45deg and -45deg creating crosshatch
- Lines: `rgba(200, 192, 176, 0.15)`, 1px wide, every 9px
- Same border and padding treatment as `.diagram-wrap`
- Supports `.full-bleed` class for 1100px expansion

---

## Key Visual Techniques

### Hand-Drawn Border-Radius

```css
--radius-sketch: 255px 15px 225px 15px / 15px 225px 15px 255px;
```

Applied to cards, principles, diagram containers, and panels. Creates an organic, hand-drawn rectangle effect.

### Crosshatch Pattern

```css
background:
  repeating-linear-gradient(45deg, transparent, transparent 8px, rgba(200,192,176,0.15) 8px, rgba(200,192,176,0.15) 9px),
  repeating-linear-gradient(-45deg, transparent, transparent 8px, rgba(200,192,176,0.15) 8px, rgba(200,192,176,0.15) 9px);
```

Used on sketch panels. Creates a fine crosshatch like technical paper.

### Card Rotation

```css
.flow-card:nth-child(odd) { transform: rotate(-0.4deg); }
.flow-card:nth-child(even) { transform: rotate(0.3deg); }
```

Subtle alternating rotation creates a "scattered on desk" feel.

### Dashed Separators

Section borders use `2px dashed var(--border)` instead of solid lines, mimicking pencil rules or torn-paper edges.

---

## Footer

- Top border: `2px dashed var(--border)`
- Padding: `3rem 0`
- Centered text in Special Elite, `0.75rem`, `--text-faint`

---

## Summary of Key Patterns

1. **Warm paper, not white** — backgrounds use cream and parchment tones from a physical sketchbook.
2. **Hand-drawn borders** — asymmetric border-radius and subtle card rotation create an organic, sketched feel.
3. **Three-tier ink hierarchy** — dark sepia (--text), medium sepia (--text-dim), faded sepia (--text-faint).
4. **Typewriter for metadata** — Special Elite gives labels and section numbers a vintage stamped quality.
5. **Hand-lettered headings** — Shadows Into Light Two is reserved for h1–h3, creating an ink-pen feel.
6. **Ink-tone semantics** — four muted ink colors (green, violet, red, blue) plus sepia accent, each with full/dim/fill variants.
7. **Physical textures** — notebook rules, crosshatch patterns, ink stamps, dashed borders all reference real art supplies.
8. **No shadows, no gloss** — depth comes from layered paper tones and borders, not box-shadows or gradients.
