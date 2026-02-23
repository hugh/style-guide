# Pulp — Style Guide

A gritty, aged design system inspired by Golden Age pulp magazines — yellowed paper, cheap ink, blood-red duochrome, woodcut energy, ink splatter borders, and newsstand price stamps for single-page HTML documents. Closer to EC horror comics than Superman.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                       |
|----------------|-----------|---------------------------------------------|
| `--bg`         | `#f0e4c8` | Page background (heavily yellowed paper)    |
| `--surface`    | `#e8d8b8` | Cards, panels, diagram containers           |
| `--surface-2`  | `#deccaa` | Nested surfaces, stained paper              |
| `--surface-3`  | `#d0be98` | Tertiary surface, foxed page, row borders   |
| `--border`     | `#a08860` | Card borders, section dividers (aged ink)   |

### Text

| Token          | Hex       | Usage                                              |
|----------------|-----------|----------------------------------------------------|
| `--text`       | `#1a1008` | Primary text, headings, bold/strong (near-black ink)|
| `--text-dim`   | `#4a3820` | Body paragraphs, secondary descriptions (faded ink) |
| `--text-faint` | `#7a6840` | Labels, metadata, captions (ghost print)            |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                    |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#b82018` | Primary accent (Pulp Red / blood)        |
| `--accent-dim`  | `#801410` | Muted accent                             |
| `--capture`     | `#2a6830` | Swamp Green — adventure, growth          |
| `--capture-dim` | `#1a4820` | Muted green                              |
| `--refine`      | `#a87818` | Aged Gold — mystery, treasure            |
| `--refine-dim`  | `#785410` | Muted gold                               |
| `--execute`     | `#b82018` | Pulp Crimson — horror, danger            |
| `--execute-dim` | `#801410` | Muted red                                |
| `--batch`       | `#1a2840` | Midnight Ink — detective noir, deep dark |
| `--batch-dim`   | `#0e1828` | Muted midnight                           |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                                      |
|-----------|-----------------|----------------------------------------------------------|
| Headings  | Bitter          | `Bitter:wght@400;500;600;700;800;900`                    |
| Body      | Source Serif 4  | `Source+Serif+4:wght@300;400;500;600;700`                |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                        |

```html
<link href="https://fonts.googleapis.com/css2?family=Bitter:wght@400;500;600;700;800;900&family=Source+Serif+4:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                         | Weight | Line-height | Notes                                      |
|--------------------|-----------------|------------------------------|--------|-------------|---------------------------------------------|
| Hero h1            | Bitter          | `clamp(3rem, 9vw, 6rem)`    | 800    | 0.95        | Uppercase. Accent-colored `<span>`.         |
| h2 (section)       | Bitter          | `2.2rem`                     | 800    | 1.1         | Uppercase, letter-spacing: 0.02em           |
| h3 (subsection)    | Bitter          | `1.4rem`                     | 800    | default     | `margin-top: 2.5rem`                        |
| h4 (card title)    | Source Serif 4  | `0.85rem`                    | 700    |             | Uppercase, letter-spacing: 0.06em           |
| Body paragraph     | Source Serif 4  | `0.95rem`                    | 400    | 1.7         | Color: `--text-dim`                         |
| Hero subtitle      | Source Serif 4  | `1.05rem`                    | 400    | 1.8         | Color: `--text-dim`, max-width 560px        |
| Card body          | Source Serif 4  | `0.82rem`                    | 400    | 1.6         | Color: `--text-dim`                         |
| Section label      | IBM Plex Mono   | `0.75rem`                    | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                     | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Diagram label      | IBM Plex Mono   | `0.7rem`                     | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | IBM Plex Mono   | `0.7rem`                     | 400    |             | `letter-spacing: 0.06em`                   |
| Table header       | Source Serif 4  | `0.7rem`                     | 600    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | Source Serif 4  | `0.82rem`                    | 400    |             | First column: `--text` + weight 700         |
| `<strong>` in body | Source Serif 4  | inherit                      | 700    |             | Color: `--text`                             |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `2px solid var(--border)` top border (heavier than other themes — matches pulp aesthetic)
- Each section opens with a **monospace label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Ink splatter noise texture:** `::before` uses multiple `repeating-radial-gradient` layers to simulate the noise of cheap ink on pulpwood paper — tiny dots at various positions and opacities in dark ink and faint red
- **Aged stain overlay:** `::after` uses `radial-gradient` ellipses to simulate foxing/age stains and a subtle vignette via `linear-gradient`
- **Title accent:** The `<span>` inside h1 uses `--accent` color (pulp red)
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
- **Card:** `--surface` background, `2px solid var(--border)`, `border-radius: 0`, `padding: 1.5rem`
- **Hover:** Border color changes to `--text`, gains `box-shadow: 3px 3px 0 var(--border)` (rough offset shadow, like a misregistered print plate)
- **Top accent bar:** 4px colored bar at the top edge (via `::before`). Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `2px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** No border-radius (sharp edges). Adjacent stages share borders (`border-left: none`).
- **Top accent:** 4px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step number (IBM Plex Mono, `0.7rem`, faint) → name (weight 700, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `2px solid var(--border)`, `border-radius: 0`, `padding: 1.25rem`
- **Number:** Bitter, `2rem`, weight 900, `--accent`, fixed `2rem` width, centered
- **Content:** h4 title (weight 700, `0.85rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `4px solid var(--accent)` (heavier than other themes)
- Background: `rgba(184, 32, 24, 0.06)`
- Border-radius: `0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (pulp red)

### Tags / Pills

Small inline labels with semantic colors.

- Font: IBM Plex Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `0` (sharp edges)
- Background: transparent semantic color at 12% opacity
- Border: `1px solid` in dim semantic color
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** Uppercase, weight 600, `0.7rem`, `letter-spacing: 0.1em`, `--text-faint`, bottom border `2px solid var(--border)` (heavy header rule)
- **Body cells:** `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px solid var(--surface-3)`
- **First column** in body: `--text` color, weight 700

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `2px solid var(--border)`
- Border-radius: `0`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in IBM Plex Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Source Serif 4', serif`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="0"` (sharp corners)
- Labels inside nodes: Semantic color, weight 700, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.5px`)

---

## Unique Components

### Pulp Cover

A card styled like a pulp magazine cover with bold title, dramatic tagline, issue number, and heavy black border frame.

- **Outer border:** `4px solid var(--text)` (near-black)
- **Inner frame:** `2px solid var(--text)` with `6px` margin from outer edge, creating classic pulp double-border
- **Inner padding:** `2rem` horizontal and top, `1.5rem` bottom
- **Text centered** within the frame
- **Issue metadata:** IBM Plex Mono, `0.65rem`, `letter-spacing: 0.2em`, uppercase, `--text-faint`
- **Title:** Bitter, `2.4rem`, weight 900, `--accent` color, uppercase
- **Tagline:** Source Serif 4, `1rem`, italic, `--text-dim`
- **Footer:** IBM Plex Mono, `0.6rem`, uppercase, `--text-faint`, top border `2px solid var(--border)`

### Splatter Border

An inline SVG divider with ink splatter/drip effects along a horizontal line.

- **Main line:** 2px stroke, `--text` color at 0.7 opacity
- **Splatter blobs:** Circles of varying radii (1–5px) at irregular positions, alternating `--text` and `--accent` colors
- **Drip drops:** Smaller circles below main blobs, offset downward, lower opacity
- **Fine spatter:** Tiny 1–1.5px circles scattered above and below the line
- Container: max-width 700px, centered
- SVG viewBox: `0 0 700 24`

### Woodcut Badge

A rectangular badge with heavy borders and crosshatch-style background pattern.

- **Border:** `3px solid var(--text)` (default), with color variants for accent/capture/refine
- **Background:** `repeating-linear-gradient` at 45deg alternating transparent and faint-colored 2px bands, layered over `--surface`
- **Font:** Bitter, weight 900, `0.8rem`, uppercase, `letter-spacing: 0.12em`
- **Padding:** `0.6em 1.2em`
- **Variants:**
  - `.woodcut-badge` — default (black border, black text)
  - `.badge-accent` — red border and text
  - `.badge-capture` — green border and text
  - `.badge-refine` — gold border and text

### Price Stamp

A small circular stamp mimicking a newsstand price tag.

- **Default size:** `56px` width/height, `3px` border, `1rem` font
- **Large variant:** `.stamp-large` — `72px`, `4px` border, `1.3rem` font
- **Inner ring:** `::before` pseudo-element with `1px solid var(--border)`, inset `3px`
- **Font:** Bitter, weight 900
- **Background:** `--bg` (matches page background for punch-out effect)
- **Variants:**
  - `.price-stamp` — default (black border, black text)
  - `.stamp-accent` — red border and text
  - `.stamp-large` — larger size

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `0`
- Border: `1px solid var(--border)`
- Color: `--accent` (pulp red)

---

## Footer

- Top border: `2px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Yellowed, not white** — backgrounds use warm-tinted aged paper tones, never clean white. The feel is a magazine from 1938 that has been sitting in a box for decades.
2. **Blood-red duochrome** — the primary accent is a deep crimson inspired by the limited two-color printing of pulp magazines. Red + black on yellowed paper.
3. **Three-tier ink** — near-black (--text), faded ink (--text-dim), ghost print (--text-faint).
4. **Slab serif woodcuts** — Bitter delivers heavy, blocky uppercase headings evoking hand-carved woodblock type for mastheads and cover titles.
5. **Cheap print labels** — IBM Plex Mono for metadata gives issue numbers and price stamps the feel of linotype slugs and press registration marks.
6. **Zero border-radius** — every element uses sharp, raw edges. Nothing is polished or refined — rough cuts and hard corners, like pages cut with a guillotine trimmer.
7. **Heavy borders** — 2px solid borders throughout (4px on pulp covers and callouts), heavier than typical design systems to match the crude ink lines of pulp printing.
8. **Ink splatter texture** — the hero uses repeating radial gradients for ink noise, and SVG splatter borders bring messy print artifacts into the design language.
