# Kaiju — Style Guide

A dark, ominous design system inspired by Japanese monster movie posters — radiation-green accents, hazard stripes, emergency broadcasts, and seismograph dividers for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#0c0c0a` | Page background (ash/smoke black)        |
| `--surface`    | `#1a1a16` | Cards, panels, diagram containers        |
| `--surface-2`  | `#242420` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#2e2e28` | Tertiary surface, row separators         |
| `--border`     | `#3a3a32` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#e8e4d8` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#a0a090` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#686860` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                  |
|-----------------|-----------|---------------------------------------|
| `--accent`      | `#4ce038` | Primary accent (Radiation Green)      |
| `--accent-dim`  | `#2a8820` | Muted accent                          |
| `--capture`     | `#4ce038` | Radiation Green — mutation, growth    |
| `--capture-dim` | `#2a8820` | Muted green                           |
| `--refine`      | `#e89020` | Plasma Orange — fire, energy          |
| `--refine-dim`  | `#a06018` | Muted orange                          |
| `--execute`     | `#e03020` | Destruction Red — danger, attack      |
| `--execute-dim` | `#901810` | Muted red                             |
| `--batch`       | `#2870c8` | Deep Sea Blue — ocean, submersion     |
| `--batch-dim`   | `#184890` | Muted blue                            |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                             |
|-----------|-----------------|--------------------------------------------------|
| Headings  | Anton           | `Anton`                                          |
| Body      | Source Sans 3   | `Source+Sans+3:wght@300;400;500;600`             |
| Labels    | Share Tech Mono | `Share+Tech+Mono`                                |

```html
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Source+Sans+3:wght@300;400;500;600&family=Share+Tech+Mono&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                     |
|--------------------|-----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Anton           | `clamp(3.5rem, 10vw, 7rem)`  | 400    | 1.0         | Uppercase. Accent-colored `<span>` glows.  |
| h2 (section)       | Anton           | `2.4rem`                      | 400    | 1.1         | Uppercase, letter-spacing: 0.03em          |
| h3 (subsection)    | Anton           | `1.5rem`                      | 400    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | Source Sans 3   | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.06em          |
| Body paragraph     | Source Sans 3   | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Source Sans 3   | `1.1rem`                      | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | Source Sans 3   | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | Share Tech Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | Share Tech Mono | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Diagram label      | Share Tech Mono | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | Share Tech Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Table header       | Source Sans 3   | `0.7rem`                      | 600    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | Source Sans 3   | `0.82rem`                     | 400    |             | First column: `--text` + weight 600        |
| `<strong>` in body | Source Sans 3   | inherit                       | 600    |             | Color: `--text`                            |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace technical label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Scanline overlay:** Repeating horizontal lines via `::before` — `repeating-linear-gradient` alternating transparent and faint green bands (2px each)
- **Crack texture:** Faint diagonal lines via `::after` using multiple `linear-gradient` layers in green, red, and orange at very low opacity
- **Title glow:** The `<span>` inside h1 uses `--accent` color with `text-shadow: 0 0 40px rgba(76, 224, 56, 0.4)`
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
- **Hover:** Border color changes to `--accent`, gains `box-shadow: 0 0 12px rgba(76, 224, 56, 0.15)` (radiation glow)
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
- **Number:** Anton, `2rem`, `--accent`, fixed `2rem` width, centered
- **Content:** h4 title (weight 600, `0.85rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `3px solid var(--accent)`
- Background: `rgba(76, 224, 56, 0.06)`
- Border-radius: `0 4px 4px 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (radiation green)

### Tags / Pills

Small inline labels with semantic colors.

- Font: Share Tech Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `3px`
- Background: transparent semantic color at 12% opacity
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

- Text inside SVGs uses `font-family: 'Source Sans 3', sans-serif`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="12"`
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.5px`)

---

## Unique Components

### Warning Stripe

A header bar wrapped in diagonal yellow/black hazard stripes for critical warnings.

- Outer container: `repeating-linear-gradient` at 45deg alternating `#e89020` and `#1a1a16` in 10px bands
- Border-radius: `4px`
- Inner panel: `--surface` background, `padding: 1.25rem 1.5rem`, `border-radius: 2px`
- Inner heading: `--refine` color (plasma orange)
- Inner body: `--text-dim`

### Emergency Broadcast

A red-bordered alert box styled like an Emergency Broadcast System message.

- Background: `--surface`
- Border: `1px solid var(--execute-dim)`, `border-left: 4px solid var(--execute)`
- Border-radius: `0 4px 4px 0`
- **Pulsing animation:** Left border cycles between `--execute` and `--execute-dim` over 2s (`ease-in-out infinite`)
- Header: Share Tech Mono, `0.7rem`, `letter-spacing: 0.2em`, uppercase, `--execute` color
- `<strong>` within the broadcast uses `--execute` color

### Seismograph Divider

An inline SVG waveform mimicking a seismograph readout.

- Flat baseline with periodic spikes of activity
- SVG path: `stroke: #4ce038` (radiation green), `stroke-width: 1.5`, `opacity: 0.5`
- Container: `max-width: 600px`, centered
- Used between content sections for thematic separation

### Threat Level

A horizontal DEFCON-style indicator with five escalating color segments.

- Label: Share Tech Mono, `0.7rem`, uppercase, `--text-faint`
- Bar: Flex row with `3px` gap, `32px` height, `border-radius: 4px` on container with overflow hidden
- Five levels with escalating colors:
  - `.l-safe` — `--batch` (blue)
  - `.l-guarded` — `--capture` (green)
  - `.l-elevated` — `--refine` (orange)
  - `.l-high` — `--execute` (red)
  - `.l-severe` — `#c01810` (deep red)
- Text: Share Tech Mono, `0.6rem`, uppercase, `--bg` color (dark on colored background)
- Inactive segments: `opacity: 0.25`

---

## Inline Code

- Font: Share Tech Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--accent` (radiation green)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in Share Tech Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Ash & smoke, not black** — backgrounds use warm-tinted near-blacks like smoke and ash, not pure #000.
2. **Radiation glow** — the primary accent is vivid green with box-shadow glows on interactive elements.
3. **Three-tier text** — ash-white (--text), dim (--text-dim), faint (--text-faint).
4. **Military/technical labels** — Share Tech Mono gives section labels and tags a classified readout feel.
5. **Ultra-condensed headings** — Anton delivers uppercase headings echoing vintage Japanese monster movie poster type.
6. **Monster-movie semantics** — radiation green (mutation), plasma orange (fire), destruction red (danger), deep sea blue (ocean).
7. **Hazard patterns** — warning stripes, emergency broadcasts, and seismograph dividers bring real-world emergency infrastructure into the design.
8. **Scanline texture** — the hero uses repeating horizontal scanlines evoking CRT monster-tracking footage.
