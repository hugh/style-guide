# Steampunk — Style Guide

A Victorian industrial design system — brass and copper on dark leather, gear-driven components, pressure gauges, and riveted panels for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                     |
|----------------|-----------|-------------------------------------------|
| `--bg`         | `#14100c` | Page background (dark leather)            |
| `--surface`    | `#1e1810` | Cards, panels, diagram containers         |
| `--surface-2`  | `#28201a` | Nested surfaces, secondary panels (patina)|
| `--surface-3`  | `#342a20` | Tertiary surface, row separators (aged wood) |
| `--border`     | `#4a3c2c` | Card borders, rivet lines, section dividers |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#e8d8c0` | Primary text, headings, bold/strong (parchment white) |
| `--text-dim`   | `#a89070` | Body paragraphs, secondary descriptions (aged brass) |
| `--text-faint` | `#6a5840` | Labels, metadata, captions, annotations (shadow) |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                         |
|-----------------|-----------|----------------------------------------------|
| `--accent`      | `#c89030` | Primary accent (Polished Brass)              |
| `--accent-dim`  | `#8a6420` | Muted brass                                  |
| `--capture`     | `#508848` | Patina Green — oxidized copper               |
| `--capture-dim` | `#305830` | Muted patina green                           |
| `--refine`      | `#c89030` | Polished Brass — refined metal               |
| `--refine-dim`  | `#8a6420` | Muted brass                                  |
| `--execute`     | `#c06030` | Heated Copper — forge work, alerts           |
| `--execute-dim` | `#804020` | Muted copper                                 |
| `--batch`       | `#4870a0` | Blued Steel — precision instruments          |
| `--batch-dim`   | `#304870` | Muted blue-steel                             |

---

## Typography

### Font Stack

| Role      | Family           | Google Fonts Import                                             |
|-----------|------------------|-----------------------------------------------------------------|
| Headings  | Playfair Display | `Playfair+Display:wght@400;500;600;700;800;900`                |
| Body      | Lora             | `Lora:wght@400;500;600;700`                                    |
| Labels    | IBM Plex Mono    | `IBM+Plex+Mono:wght@400;500;600`                               |

```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;600;700;800;900&family=Lora:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family           | Size                          | Weight | Line-height | Notes                                     |
|--------------------|------------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Playfair Display | `clamp(2.8rem, 8vw, 5.5rem)` | 900    | 1.1         | Accent-colored `<span>` has brass glow.   |
| h2 (section)       | Playfair Display | `1.8rem`                      | 700    | 1.15        | letter-spacing: 0.02em                     |
| h3 (subsection)    | Playfair Display | `1.15rem`                     | 700    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | Lora             | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.06em          |
| Body paragraph     | Lora             | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Lora             | `1.1rem`                      | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | Lora             | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono    | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono    | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Diagram label      | IBM Plex Mono    | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | IBM Plex Mono    | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Table header       | Lora             | `0.7rem`                      | 600    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | Lora             | `0.82rem`                     | 400    |             | First column: `--text` + weight 600        |
| `<strong>` in body | Lora             | inherit                       | 700    |             | Color: `--text`                            |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace telegraph label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Leather grain texture:** Scattered `radial-gradient` dots via `::before` in warm brass/copper tones at varying opacities — simulates leather grain and workshop dust
- **Brass mechanical glow:** Faint elliptical `radial-gradient` layers via `::after` in brass, copper, and patina green at very low opacity
- **Title glow:** The `<span>` inside h1 uses `--accent` color with `text-shadow: 0 0 30px rgba(200, 144, 48, 0.4), 0 0 60px rgba(200, 144, 48, 0.15)`
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
- **Card:** `--surface` background, `2px solid var(--border)`, `border-radius: 4px`, `padding: 1.5rem`
- **Hover:** Border color changes to `--accent`, gains `box-shadow: 0 2px 16px rgba(200, 144, 48, 0.15)` (warm brass glow)
- **Top accent bar:** 3px colored bar at the top edge (via `::before`). Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `2px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `4px`, last gets right border-radius `4px`. Adjacent stages share borders (`border-left: none`).
- **Top accent:** 3px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step number (IBM Plex Mono, `0.7rem`, faint) → name (weight 600, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `2px solid var(--border)`, `border-radius: 4px`, `padding: 1.25rem`
- **Number:** Playfair Display, `2rem`, weight 900, `--accent`, fixed `2rem` width, centered
- **Content:** h4 title (weight 600, `0.85rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note, styled like a pneumatic tube message.

- Left border: `3px solid var(--accent)`
- Background: `rgba(200, 144, 48, 0.06)`
- Border-radius: `0 4px 4px 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (polished brass)

### Tags / Pills

Small inline labels with semantic colors.

- Font: IBM Plex Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `3px`
- Background: transparent semantic color at 12% opacity
- Border: `1px solid` in dim semantic color
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** Uppercase, weight 600, `0.7rem`, `letter-spacing: 0.1em`, `--text-faint`, bottom border `2px solid var(--border)`
- **Body cells:** `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px solid var(--surface-3)`
- **First column** in body: `--text` color, weight 600

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `2px solid var(--border)`
- Border-radius: `4px`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in IBM Plex Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Lora', serif`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="12"`
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.5px`)

---

## Unique Components

### Pressure Gauge

A circular 200px gauge instrument with a brass bezel ring, inner dial, needle indicator, and monospace pressure reading.

- **Outer ring:** `border-radius: 50%`, layered `radial-gradient` for bezel rings — alternating `--surface`, `--surface-2`, `--border`, `--accent`, `--surface-3`, and `--border` at specific stops
- **Box-shadow:** Multiple layers — outer shadow, inner shadow, brass bezel ring (`0 0 0 6px var(--accent-dim)`)
- **Scale marks:** `::before` pseudo-element, 140px circle with `1px dashed var(--text-faint)` at 40% opacity
- **Inner dial:** `::after` pseudo-element, 100px circle with radial gradient from `--surface-2` to `--surface`
- **Needle:** 3px wide, 55px tall, gradient from `--execute` through `--accent` to `--text`, `transform-origin: bottom center`, rotated via `transform: rotate()`. Default position: `-30deg`
- **Center rivet:** `::after` on needle, 11px brass circle
- **Reading:** IBM Plex Mono, `0.8rem`, `--accent`, positioned at bottom with brass text-shadow
- **Label:** IBM Plex Mono, `0.55rem`, `--text-faint`, uppercase, positioned at top

### Rivet Panel

A content panel with decorative brass rivet dots in all four corners, evoking hand-riveted industrial enclosures.

- **Outer container:** `padding: 2rem`, `--surface` background, `2px solid var(--accent-dim)` border, `border-radius: 4px`
- **Corner rivets:** 10px circles with `radial-gradient` from `--accent` to `--accent-dim` to `--border`, with `1px solid var(--border)` and a subtle highlight via `box-shadow: inset 0 1px 2px rgba(232, 216, 192, 0.2)`
- **Top rivets:** `::before` (top-left, 8px inset) and `::after` (top-right, 8px inset) on `.rivet-panel`
- **Bottom rivets:** `::before` (bottom-left) and `::after` (bottom-right) on `.rivet-panel-inner`
- **Heading:** `--accent` color
- **Body:** `--text-dim`

### Ticker Tape Divider

A telegraph-style horizontal separator with dashed perforation borders and centered text.

- **Container:** `margin: 3rem 0`, centered text
- **Strip:** `display: inline-block`, `padding: 0.4rem 2rem`, `--surface` background
- **Dashed borders:** `2px dashed var(--accent-dim)` on top and bottom
- **Perforation tracks:** `::before` (above) and `::after` (below), 2px tall `repeating-linear-gradient` with `4px` dashes and `4px` gaps in `--border` color, offset `-6px` from the strip edges
- **Text:** IBM Plex Mono, `0.7rem`, `letter-spacing: 0.2em`, uppercase, `--accent` color

### Gear Badge

A circular badge with a cog/gear tooth border created via `clip-path: polygon()`.

- **Size:** 100px × 100px
- **Background:** `--accent` (polished brass)
- **Shape:** `clip-path: polygon()` defining gear teeth around the perimeter — approximately 16 teeth with concave valleys between them
- **Inner disc:** `::before` pseudo-element, 62px circle with `--surface` background and `2px solid var(--accent-dim)` border
- **Text:** IBM Plex Mono, `0.65rem`, weight 600, `--text`, uppercase, `letter-spacing: 0.1em`, centered
- **Hover animation:** `transform: rotate(15deg)`, `transition: 0.6s ease` — clockwork rotation effect

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--accent` (polished brass)

---

## Footer

- Top border: `2px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Dark leather, not black** — backgrounds use warm brown-tinted near-blacks like aged leather, not pure #000.
2. **Warm metallic accents** — the primary accent is polished brass with warm golden glow, not cold blue or white.
3. **Three-tier text** — warm parchment (--text), aged brass (--text-dim), shadow (--text-faint).
4. **Telegraph readout labels** — IBM Plex Mono gives section labels and tags a telegraph ticker tape and gauge readout feel.
5. **Victorian serif headings** — Playfair Display delivers ornate high-contrast serif headings echoing Victorian engineering manuals.
6. **Industrial semantics** — patina green (oxidized copper), polished brass (refined), heated copper (forge), blued steel (precision).
7. **Riveted construction** — 2px solid borders, corner rivet dots, and machined 4px border-radius create a hand-assembled workshop panel feel.
8. **Leather grain texture** — the hero uses scattered radial gradients in warm brass/copper tones to simulate leather grain and workshop atmosphere.
