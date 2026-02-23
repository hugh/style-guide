# Laboratory / Research — Style Guide

Clinical, sterile, precise. A design system inspired by research laboratories — specimen labels, gel electrophoresis bands, petri dish badges, and safety data sheets for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                         |
|----------------|-----------|-----------------------------------------------|
| `--bg`         | `#f6f8fa` | Page background (clinical off-white)           |
| `--surface`    | `#ffffff` | Cards, panels, diagram containers (pure white) |
| `--surface-2`  | `#eef0f4` | Nested surfaces, table headers (instrument panel) |
| `--surface-3`  | `#dce0e8` | Tertiary surface, row separators (lab bench grey) |
| `--border`     | `#c0c8d4` | Card borders, section dividers (stainless steel) |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#1a1e28` | Primary text, headings, bold/strong content (lab notebook ink) |
| `--text-dim`   | `#4a5060` | Body paragraphs, secondary descriptions (pencil notes) |
| `--text-faint` | `#8890a0` | Labels, metadata, captions, annotations (faded notation) |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.08)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                    |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#e86820` | Safety Orange — primary accent           |
| `--accent-dim`  | `#b04810` | Muted safety orange                      |
| `--capture`     | `#28a048` | Bio Green — safe, go, biological         |
| `--capture-dim` | `#1a7030` | Muted green                              |
| `--refine`      | `#d89020` | Caution Amber — chemical, warning        |
| `--refine-dim`  | `#a06810` | Muted amber                              |
| `--execute`     | `#d03030` | Hazard Red — danger, biohazard           |
| `--execute-dim` | `#a01818` | Muted red                                |
| `--batch`       | `#2070c8` | Clinical Blue — primary, informational   |
| `--batch-dim`   | `#104890` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                               |
|-----------|-----------------|---------------------------------------------------|
| Headings  | Inter           | `Inter:wght@300;400;500;600;700`                   |
| Body      | Inter           | (same as headings)                                 |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                   |

```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                     |
|--------------------|-----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Inter           | `clamp(2.8rem, 8vw, 5rem)`   | 700    | 1.05        | letter-spacing: -0.01em                    |
| h2 (section)       | Inter           | `1.8rem`                      | 600    | 1.2         | letter-spacing: -0.01em                    |
| h3 (subsection)    | Inter           | `1.2rem`                      | 600    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | Inter           | `0.8rem`                      | 700    |             | Uppercase, letter-spacing: 0.06em          |
| Body paragraph     | Inter           | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Inter           | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | Inter           | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono   | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--batch`       |
| Diagram label      | IBM Plex Mono   | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | IBM Plex Mono   | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Table header       | Inter           | `0.7rem`                      | 600    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | Inter           | `0.82rem`                     | 400    |             | First column: `--text` + weight 600        |
| `<strong>` in body | Inter           | inherit                       | 600    |             | Color: `--text`                            |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace lab notation label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Grid overlay:** Lab notebook grid paper — thin blue lines via `::before` using `linear-gradient` in both axes (24px spacing), evoking graph paper precision
- **Clinical glow:** Subtle blue and orange radial gradients via `::after` at the bottom edge
- **Title accent:** The `<span>` inside h1 uses `--batch` color (clinical blue)
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
- **Hover:** Border color changes to `--batch`, gains `box-shadow: 0 1px 8px rgba(32, 112, 200, 0.1)`
- **Top accent bar:** 3px colored bar at the top edge (via `::before`). Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `1px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `4px`, last gets right border-radius `4px`. Adjacent stages share borders.
- **Top accent:** 3px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step number (IBM Plex Mono, `0.7rem`, faint) → name (weight 600, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `1px solid var(--border)`, `border-radius: 4px`, `padding: 1.25rem`
- **Number:** Inter, `2rem`, weight 700, `--batch`, fixed `2rem` width, centered
- **Content:** h4 title (weight 700, `0.8rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `3px solid var(--batch)`
- Background: `rgba(32, 112, 200, 0.04)`
- Border-radius: `0 4px 4px 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--batch` color (clinical blue)

### Tags / Pills

Small inline labels with semantic colors.

- Font: IBM Plex Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `3px`
- Background: transparent semantic color at 8% opacity
- Border: `1px solid` in dim semantic color
- Text color: full semantic color

### Tables (Safety Data Sheet Style)

- Full width, collapsed borders
- **Header row:** Uppercase, weight 600, `0.7rem`, `letter-spacing: 0.1em`, `--text-faint`, `--surface-2` background, bottom border `2px solid var(--border)`
- **Body cells:** `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px solid var(--surface-3)`
- **First column** in body: `--text` color, weight 600
- **Row hover:** Background changes to `--surface-2`

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
- Node boxes: `--surface` fill, semantic color stroke (1.5px), `rx="4"`
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1px`)

---

## Unique Components

### Specimen Card

A card styled like a laboratory specimen label with specimen ID, classification, date collected, status, and a data grid layout in monospace.

- Container: `--surface` background, `1px solid var(--border)`, `border-radius: 4px`
- **Header bar:** `--surface-2` background, flex row with specimen ID and status badge
  - ID: IBM Plex Mono, `0.7rem`, weight 600, uppercase, `--text`
  - Status badge: IBM Plex Mono, `0.6rem`, with `.status-safe` (green), `.status-caution` (amber), `.status-hazard` (red), `.status-pending` (blue) variants
- **Data grid:** 2-column grid of fields separated by thin borders
  - Field label: IBM Plex Mono, `0.6rem`, faint, uppercase
  - Field value: IBM Plex Mono, `0.85rem`, weight 500, `--text`
- **Notes section:** Below grid, separated by top border, with label and body text

### Petri Dish Badge

Circular badges (80px) styled like petri dishes with thin border, inner ring, and centered label text. Used for status indicators or category markers.

- Size: `80px` circle, `--surface` background
- Border: `1px solid var(--border)` (default) or semantic color when using variant class
- Inner ring: `::before` pseudo-element, 4px inset, `1px solid var(--surface-3)`
- **Label:** IBM Plex Mono, `0.55rem`, uppercase, `--text-faint`
- **Value:** Inter, `0.85rem`, weight 700, `--text` (or semantic color)
- **Variants:** `.petri-capture`, `.petri-refine`, `.petri-execute`, `.petri-batch` — changes border color and value text color
- **Layout:** Wrapped in `.petri-dish-row` flex container with `2rem` gap, centered

### Electrophoresis Divider

An SVG section separator showing horizontal bands of varying thickness and opacity, like gel electrophoresis results.

- Container: `3rem` vertical margin, centered, `max-width: 700px`
- **Background:** `--surface-2` filled rectangle
- **Bands:** Multiple horizontal `<rect>` elements at varying y-positions, widths, heights, and opacities
  - Fill: `--batch` (#2070c8) at different opacities (0.2–0.7)
  - Widths vary to simulate band migration patterns
  - Heights vary between 2px and 5px
  - All bands have `rx="1"` for subtle rounding

### Safety Panel

Callout blocks with colored header strips, used for warnings and safety data.

- Container: `--surface` background, `1px solid var(--border)`, `border-radius: 4px`
- **Header:** Flex row with icon and label text
  - Font: IBM Plex Mono, `0.7rem`, weight 600, uppercase
  - Background and border-bottom change based on variant
- **Body:** `1.25rem` padding, `0.88rem` body text in `--text-dim`
- **Variants:**
  - `.safety-info` — `--batch-fill` background, `--batch` text, `2px solid var(--batch)` bottom border
  - `.safety-warning` — `--refine-fill` background, `--refine` text, `2px solid var(--refine)` bottom border
  - `.safety-danger` — `--execute-fill` background, `--execute` text, `2px solid var(--execute)` bottom border

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--batch` (clinical blue)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Clinical white, not warm** — backgrounds use cool off-whites and pure whites like a sterile lab. No warmth, no coziness.
2. **Safety color semantics** — four colors map to laboratory safety: bio green (safe), chemical amber (caution), hazard red (danger), clinical blue (informational).
3. **Three-tier text** — dark ink (--text), pencil notes (--text-dim), faded notation (--text-faint).
4. **Data in monospace** — IBM Plex Mono for all specimen IDs, chemical formulas, measurements, and labels.
5. **Clean clinical headings** — Inter delivers clean, precise headings that echo the sterile precision of scientific publications.
6. **Lab notebook grid** — the hero uses thin blue grid lines evoking graph paper and lab notebook precision.
7. **Thin precise borders** — all borders are 1px solid, border-radius is 4px. Clinical, minimal, exact.
8. **Safety data sheet tables** — tables use double-border headers with grey backgrounds and row hover states.
