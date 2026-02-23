# Pop Art — Style Guide

A bold Silver Age pop art design system inspired by Lichtenstein and Warhol. Larger Ben-Day dots, flat bright backgrounds at full saturation, speech bubbles as a core layout element, and primary colors pushed to maximum impact. More ironic and playful than newsprint — this is gallery-wall pop art for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--bg`         | `#fef430` | Page background (bright Lichtenstein yellow)    |
| `--surface`    | `#ffffff` | Cards, panels, speech bubbles (flat white)      |
| `--surface-2`  | `#f0f0f0` | Nested surfaces, secondary panels               |
| `--surface-3`  | `#e0e0e0` | Tertiary surface, row separators                 |
| `--border`     | `#1a1a1a` | Thick black comic outlines (3px)                 |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#1a1a1a` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#444444` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#888888` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                              |
|-----------------|-----------|-----------------------------------|
| `--accent`      | `#e02040` | Primary accent (Pop Red)          |
| `--accent-dim`  | `#a01830` | Muted accent                      |
| `--capture`     | `#00a840` | Bright Green — creation, go       |
| `--capture-dim` | `#007830` | Muted green                       |
| `--refine`      | `#f0c000` | Bright Yellow — processing, pop   |
| `--refine-dim`  | `#b89000` | Muted yellow                      |
| `--execute`     | `#e02040` | Bright Red — action, danger       |
| `--execute-dim` | `#a01830` | Muted red                         |
| `--batch`       | `#0060e0` | Bright Blue — grouping, cool      |
| `--batch-dim`   | `#0048a8` | Muted blue                        |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                              |
|-----------|-----------------|---------------------------------------------------|
| Headings  | Bangers         | `Bangers`                                         |
| Body      | Inter           | `Inter:wght@300;400;500;600`                      |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500`                      |

```html
<link href="https://fonts.googleapis.com/css2?family=Bangers&family=Inter:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                     |
|--------------------|-----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Bangers         | `clamp(3.5rem, 10vw, 7rem)`  | 400    | 1.05        | Accent-colored `<span>` for emphasis       |
| h2 (section)       | Bangers         | `2.4rem`                      | 400    | 1.15        | letter-spacing: 0.04em                     |
| h3 (subsection)    | Bangers         | `1.6rem`                      | 400    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | Inter           | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.04em          |
| Body paragraph     | Inter           | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Inter           | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | Inter           | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono   | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.12em`, `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--accent`     |
| Tag                | IBM Plex Mono   | `0.7rem`                      | 500    |             | Uppercase, `letter-spacing: 0.04em`, bold rectangular |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `3px solid var(--border)` top border (thick pop art outlines)
- Each section opens with a **monospace label** in the format `01 — Label`

### Full-Bleed Containers

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed` or `.benday-panel.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Bright yellow background** (`--bg: #fef430`) — the defining Lichtenstein color
- **Ben-Day dots:** Large `radial-gradient` dot pattern overlay via `::before` (3px dots, 18px spacing, faint red)
- **Color block accents:** Faint diagonal gradients via `::after` in blue and red
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
- **Card:** `--surface` background, **3px solid `--border`** (thick pop art outline), `border-radius: 0` (sharp, graphic), `padding: 1.5rem`
- **Hover:** `translateY(-3px)` lift with `4px 4px 0` hard shadow in `--border`
- **Top accent bar:** 5px colored bar at the top edge (via `::before`). Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, **3px solid `--border`**, `padding: 1.25rem`, centered text
- **Borders:** Sharp corners (`border-radius: 0`). Adjacent stages share borders.
- **Top accent:** 5px solid top border in semantic color
- **Content:** Step number (IBM Plex Mono, `0.7rem`, faint) → name (weight 600, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, **3px solid `--border`**, `border-radius: 0`, `padding: 1.25rem`
- **Number:** Bangers, `2rem`, `--accent`, fixed `2rem` width, centered
- **Content:** h4 title (weight 600, `0.85rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `5px solid var(--border)` (black, not accent — maintaining comic feel)
- Background: `--surface` (flat white)
- Border-radius: `0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (Pop Red)

### Tags / Pills

Small inline labels with bold rectangular borders.

- Font: IBM Plex Mono, `0.7rem`, weight 500, uppercase, `letter-spacing: 0.04em`
- Padding: `0.25em 0.65em`
- Border-radius: `0` (sharp, graphic)
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
- Border: `3px solid var(--border)` (thick pop art outline)
- Border-radius: `0` (sharp)
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in IBM Plex Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Inter', sans-serif`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="0"` (sharp corners for pop art)
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.2px`)

---

## Unique Components

### Speech Bubble

A callout styled as a comic speech bubble with a triangular tail, thick black border, and white fill.

- Background: `--surface`
- Border: `3px solid var(--border)`
- Border-radius: `24px` (rounded balloon shape)
- Triangle tail via `::after` (border-based CSS triangle) at bottom-left
- Inner fill triangle via `::before` to mask the border on the pointer
- Tail: 18px tall, positioned at `bottom: -18px`, `left: 2.5rem`

### Thought Bubble

Similar to speech bubble but with a cloud-like border and small circle trail instead of a pointed tail.

- Background: `--surface`
- Border: `3px solid var(--border)`
- Border-radius: `50% 50% 50% 50% / 40% 40% 60% 60%` (organic cloud shape)
- Two trailing circles via `::before` (16px) and `::after` (10px), both with `border-radius: 50%` and `3px solid --border`
- Extra bottom margin (`3.5rem`) to accommodate the circle trail

### Ben-Day Panel

A card with a radial dot pattern background for highlighting content.

- Background: `--surface`
- Border: `3px solid var(--border)`, `border-radius: 0`
- Dot overlay via `::before`: `radial-gradient(circle, rgba(224, 32, 64, 0.10) 2.5px, transparent 2.5px)`, 14px spacing
- Color variants: `.dots-blue`, `.dots-green`, `.dots-yellow`
- Supports `.full-bleed` class for 1100px expansion
- All children get `position: relative; z-index: 1` to sit above dots

### POW Badge

A starburst/explosion shape badge using `clip-path: polygon()`, bright background with black border, centered bold text.

- **Shape:** 22-point star via `clip-path: polygon()` on `::before`
- **Size:** 120x120px, `display: inline-flex`, centered content
- **Text:** Bangers, `1.6rem`, uppercase
- **Border:** 3px solid `--border` on the clipped `::before` element
- **Color variants:** `.badge-red`, `.badge-blue`, `.badge-green`, `.badge-yellow`
  - Red, blue, green badges use white text (`--surface`) on colored fill
  - Yellow badge uses black text (`--text`) on yellow fill

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `0` (sharp, graphic)
- Border: `2px solid var(--border)`
- Color: `--accent` (Pop Red)

---

## Footer

- Top border: `3px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Key Visual Techniques

### Bright Yellow Background

```css
--bg: #fef430;  /* Lichtenstein Yellow */
```

The defining visual of the Pop Art theme. Everything sits on a flat, saturated yellow that immediately evokes Lichtenstein gallery prints.

### Thick Black Outlines

```css
border: 3px solid var(--border);  /* --border: #1a1a1a */
```

Applied to all cards, panels, and containers. Sharp corners (`border-radius: 0`) reinforce the graphic, printed feel.

### Ben-Day Dot Pattern

```css
background: radial-gradient(circle, rgba(224, 32, 64, 0.10) 2.5px, transparent 2.5px);
background-size: 14px 14px;
```

Larger and more visible than subtle halftone — these are the iconic dots of pop art printing, used on Ben-Day panels and the hero section.

### Hard Shadow on Hover

```css
.flow-card:hover {
  transform: translateY(-3px);
  box-shadow: 4px 4px 0 var(--border);
}
```

A flat, hard-edged shadow that reinforces the graphic, screen-printed aesthetic.

### POW Badge Starburst

```css
clip-path: polygon(50% 0%, 63% 18%, 80% 5%, ...);
```

A 22-point star shape created entirely with CSS `clip-path`, delivering the iconic pop art explosion effect without SVGs.

---

## Summary of Key Patterns

1. **Bright yellow, not newsprint** — the background is flat, saturated Lichtenstein yellow at full intensity.
2. **Thick black outlines** — 3px solid borders on everything with sharp 0px border-radius for a graphic, printed feel.
3. **Three-tier text** — black ink (--text), dark grey (--text-dim), medium grey (--text-faint).
4. **Comic display headings** — Bangers delivers maximum pop art impact on h1-h3.
5. **Clean body contrast** — Inter provides clean, modern contrast against the bold comic headings.
6. **Primary-color semantics** — bright green, yellow, red, blue at full saturation, not muted.
7. **Ben-Day dots** — large radial-gradient dot patterns reference Lichtenstein's iconic printing technique.
8. **Speech and thought bubbles** — core layout elements, not afterthoughts. These are how pop art communicates.
