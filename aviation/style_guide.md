# Aviation / Cockpit — Style Guide

A dark instrument-panel design system — amber gauge readouts, phosphor-green status indicators, altimeter dials, and ATC radio logs for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#0e1014` | Page background (instrument panel black) |
| `--surface`    | `#181c22` | Cards, panels, diagram containers        |
| `--surface-2`  | `#222830` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#2c3440` | Tertiary surface, row separators         |
| `--border`     | `#3a4250` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#d0ccc0` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#8a8878` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#585848` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#e09020` | Primary accent (Instrument Amber)        |
| `--accent-dim`  | `#b07018` | Muted accent                             |
| `--capture`     | `#30c850` | Phosphor Green — active, go, cleared     |
| `--capture-dim` | `#20a038` | Muted green                              |
| `--refine`      | `#e8b830` | Caution Amber — advisory, hold           |
| `--refine-dim`  | `#c09020` | Muted amber                              |
| `--execute`     | `#e03030` | Warning Red — alert, emergency, abort    |
| `--execute-dim` | `#b82020` | Muted red                                |
| `--batch`       | `#3888d0` | Navigation Blue — heading, info, route   |
| `--batch-dim`   | `#2868a8` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family           | Google Fonts Import                                          |
|-----------|------------------|--------------------------------------------------------------|
| Headings  | Barlow Condensed | `Barlow+Condensed:wght@400;500;600;700;800`                  |
| Body      | Inter            | `Inter:wght@300;400;500;600;700`                             |
| Labels    | IBM Plex Mono    | `IBM+Plex+Mono:wght@400;500;600`                            |

```html
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;500;600;700;800&family=Inter:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family           | Size                          | Weight | Line-height | Notes                                     |
|--------------------|------------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Barlow Condensed | `clamp(2.8rem, 8vw, 5.5rem)` | 800    | 1.0         | Uppercase, `letter-spacing: 0.04em`        |
| h2 (section)       | Barlow Condensed | `2rem`                        | 700    | 1.1         | Uppercase, `letter-spacing: 0.04em`        |
| h3 (subsection)    | Barlow Condensed | `1.15rem`                     | 700    | 1.2         | `margin-top: 2.5rem`                       |
| h4 (card title)    | Inter            | `0.78rem`                     | 700    |             | Uppercase, `letter-spacing: 0.08em`        |
| Body paragraph     | Inter            | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Inter            | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | Inter            | `0.88rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono    | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono    | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Diagram label      | IBM Plex Mono    | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Tag                | IBM Plex Mono    | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Table header       | IBM Plex Mono    | `0.7rem`                      | 500    |             | Uppercase, `letter-spacing: 0.06em`, color: `--text-faint` |
| Table cell         | Inter            | `0.88rem`                     | 400    |             | First column: `--text` + weight 600        |
| `<strong>` in body | Inter            | inherit                       | 700    |             | Color: `--text`                            |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace readout label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Instrument gauge rings:** `::before` pseudo-element creates a 600px circle with concentric `box-shadow` rings at 40px, 80px, and 160px radii in very faint amber
- **Horizon line:** `::after` pseudo-element draws a horizontal gradient line across the viewport center in faint amber, simulating an artificial horizon
- **Title accent:** The `<span>` inside h1 uses `--accent` color (instrument amber)
- **Hero label:** Uses `--accent` color (amber) instead of `--text-faint`
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
- **Hover:** Border color lightens to `--text-faint`
- **Top accent bar:** 3px colored bar at the top edge (via `::before`). Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `1px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `4px`, last gets right border-radius `4px`. Adjacent stages share borders (`border-left: none`).
- **Top accent:** 3px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step number (IBM Plex Mono, `0.7rem`, faint) → name (Barlow Condensed, weight 700, `1rem`, uppercase) → description (`0.85rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `1px solid var(--border)`, `border-radius: 4px`, `padding: 1.25rem`
- **Number:** Barlow Condensed, `2.4rem`, weight 800, `--accent` (amber), fixed `2.5rem` width, centered
- **Content:** h4 title (weight 700, `0.78rem`, uppercase) + body paragraph (`0.9rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `4px solid var(--accent)`
- Background: `rgba(224, 144, 32, 0.06)`
- Border-radius: `0 4px 4px 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (instrument amber)

### Tags / Pills

Small inline labels with semantic colors.

- Font: IBM Plex Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.3em 0.7em`
- Border-radius: `3px`
- Background: transparent semantic color at 10% opacity
- Border: `1px solid` in dim semantic color
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** Uppercase, weight 500, `0.7rem`, `letter-spacing: 0.06em`, `--text-faint`, bottom border `1px solid var(--border)`
- **Body cells:** `0.88rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px solid var(--surface-3)`
- **First column** in body: `--text` color, weight 600

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `1px solid var(--border)`
- Border-radius: `4px`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in IBM Plex Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Inter', sans-serif`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="4"` (matches theme's 4px radius)
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–11px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1px`)

---

## Unique Components

### Altimeter Gauge

A circular instrument dial displaying a primary reading, styled like an aircraft altimeter.

- **Size:** 180px diameter circle
- **Background:** `--surface` with `inset box-shadow: 0 0 20px rgba(0,0,0,0.3)`
- **Border:** `3px solid var(--border)`
- **Outer bezel:** `::before` pseudo-element, `inset: -8px`, `4px solid var(--surface-3)`, full circle
- **Inner tick ring:** `::after` pseudo-element, `inset: 8px`, `1px solid var(--border)`, full circle
- **Reading (centered):**
  - Value: IBM Plex Mono, `1.6rem`, weight 600, `--accent` (amber)
  - Unit: IBM Plex Mono, `0.55rem`, weight 500, `--text-faint`, uppercase
  - Label: Barlow Condensed, `0.55rem`, weight 600, `--text-faint`, uppercase

### Artificial Horizon

A rectangular indicator showing sky/ground split with a center crosshair, mimicking an attitude indicator.

- **Size:** 220px wide, 140px tall
- **Border-radius:** `4px`
- **Border:** `2px solid var(--border)`
- **Sky half (top 50%):** Linear gradient from `#1a3868` to `#3070b8`
- **Ground half (bottom 50%):** Linear gradient from `#7a5020` to `#4a3018`
- **Horizon line:** Absolute-positioned, full width, `2px solid var(--text)`, vertically centered
- **Center dot:** 12px circle, `2px solid var(--accent)`, centered
- **Wings indicator:** 80px wide bar, `2px solid var(--accent)`, centered horizontally
- **Label:** IBM Plex Mono, `0.5rem`, white at 50% opacity, bottom-positioned

### Radio Log

A communication log styled like an ATC radio transcript, with frequency header and timestamped entries.

- **Container:** `--surface` background, `1px solid var(--border)`, `border-radius: 4px`
- **Header:** `--surface-2` background, flex row with:
  - Frequency: IBM Plex Mono, `0.85rem`, weight 600, `--capture` (green) color
  - Label: IBM Plex Mono, `0.65rem`, weight 500, `--text-faint`, uppercase
- **Log entries:** Unstyled list, each entry is a flex row:
  - Time: IBM Plex Mono, `0.75rem`, `--text-faint`, 3.5rem min-width
  - Callsign: IBM Plex Mono, `0.8rem`, weight 600, `--accent` (amber), 6rem min-width
  - Message: `0.85rem`, `--text-dim`
- **Row dividers:** `1px solid var(--surface-3)`, last entry has no border

### Black Box

An orange-and-black striped warning panel, styled like a flight data recorder, for critical callout information.

- **Container:** `border-radius: 4px`, `1px solid var(--border)`, overflow hidden
- **Header:** Repeating diagonal stripe pattern (`-45deg`, alternating `--accent` and `--surface-3` at 8px intervals)
  - Title text sits on a `--bg` colored pill: Barlow Condensed, `0.8rem`, weight 700, uppercase, `letter-spacing: 0.12em`
- **Body:** `--surface` background, `padding: 1.5rem 1.25rem`
  - Body text: `0.9rem`, `--text-dim`
  - Data readout (`.bbox-data`): IBM Plex Mono, `0.8rem`, `--capture` (green), separated from body by `1px solid var(--border)` top border

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--text`

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Instrument panel dark** — backgrounds use cold grey-blue near-blacks, evoking an unlit cockpit at night.
2. **Amber instrument accent** — the primary accent is warm instrument amber, like classic cockpit gauge lighting.
3. **Three-tier text** — warm grey-tan (--text), dim (--text-dim), faint (--text-faint).
4. **Condensed cockpit headings** — Barlow Condensed delivers tight uppercase headings that echo instrument panel labels.
5. **Monospace readouts** — IBM Plex Mono gives all labels, tags, and data the feel of cockpit instrument readouts.
6. **Aviation semantics** — phosphor green (go/cleared), caution amber (advisory/hold), warning red (alert/emergency), navigation blue (heading/route).
7. **Instrument gauge motifs** — altimeter dial, artificial horizon, radio logs, and black box recorder components bring cockpit instruments into the design language.
8. **Subtle instrument glow** — the body has a faint radial overlay mixing amber and green to simulate dim cockpit lighting.
