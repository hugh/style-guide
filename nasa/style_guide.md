# NASA Mission Control — Style Guide

Clean, confident, engineering-precise. A design system inspired by 1960s–70s NASA mission control — telemetry readouts, countdown timers, CAPCOM transmission logs, and mission patch badges for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#0a1020` | Page background (deep control room navy) |
| `--surface`    | `#101828` | Cards, panels, diagram containers        |
| `--surface-2`  | `#182030` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#202838` | Tertiary surface, row separators         |
| `--border`     | `#2a3448` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#e0dcd0` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#8890a0` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#505868` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                  |
|-----------------|-----------|---------------------------------------|
| `--capture`     | `#40c870` | GO Green — nominal, confirmed         |
| `--capture-dim` | `#208840` | Muted green                           |
| `--refine`      | `#e0a830` | Caution Amber — advisory, hold        |
| `--refine-dim`  | `#987018` | Muted amber                           |
| `--execute`     | `#e04040` | Abort Red — critical, emergency       |
| `--execute-dim` | `#a02020` | Muted red                             |
| `--batch`       | `#3880d0` | Flight Blue — procedural, systems     |
| `--batch-dim`   | `#204890` | Muted blue                            |

Special tokens:
| Token           | Hex       | Role                                  |
|-----------------|-----------|---------------------------------------|
| `--nasa-red`    | `#fc3d21` | NASA insignia red (decorative only)   |
| `--nasa-blue`   | `#0b3d91` | NASA insignia blue (decorative only)  |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                              |
|-----------|-----------------|---------------------------------------------------|
| Headings  | Space Grotesk   | `Space+Grotesk:wght@400;500;600;700`              |
| Body      | Space Grotesk   | (same as headings)                                |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                  |

```html
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                     |
|--------------------|-----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Space Grotesk   | `clamp(3rem, 9vw, 6rem)`     | 700    | 1.0         | Uppercase, letter-spacing: 0.05em          |
| h2 (section)       | Space Grotesk   | `2rem`                        | 700    | 1.15        | Uppercase, letter-spacing: 0.05em          |
| h3 (subsection)    | Space Grotesk   | `1.3rem`                      | 600    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | Space Grotesk   | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.06em          |
| Body paragraph     | Space Grotesk   | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Space Grotesk   | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | Space Grotesk   | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono   | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--capture`     |
| Diagram label      | IBM Plex Mono   | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | IBM Plex Mono   | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Table header       | Space Grotesk   | `0.7rem`                      | 600    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | Space Grotesk   | `0.82rem`                     | 400    |             | First column: `--text` + weight 600        |
| `<strong>` in body | Space Grotesk   | inherit                       | 600    |             | Color: `--text`                            |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace telemetry label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Grid overlay:** Faint blue grid lines via `::before` using `linear-gradient` in both axes (40px spacing), evoking trajectory plotting boards
- **Horizon glow:** Subtle blue and green radial gradients via `::after` at the bottom edge, simulating Earth's limb glow from orbit
- **Title accent:** The `<span>` inside h1 uses `--capture` color (GO green)
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
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 6px`, `padding: 1.5rem`
- **Hover:** Border color changes to `--capture`, gains `box-shadow: 0 0 12px rgba(64, 200, 112, 0.1)`
- **Top accent bar:** 3px colored bar at the top edge (via `::before`). Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `1px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `6px`, last gets right border-radius `6px`. Adjacent stages share borders.
- **Top accent:** 3px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step number (IBM Plex Mono, `0.7rem`, faint) → name (weight 600, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `1px solid var(--border)`, `border-radius: 6px`, `padding: 1.25rem`
- **Number:** Space Grotesk, `2rem`, weight 700, `--capture`, fixed `2rem` width, centered
- **Content:** h4 title (weight 600, `0.85rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `3px solid var(--capture)`
- Background: `rgba(64, 200, 112, 0.05)`
- Border-radius: `0 6px 6px 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--capture` color (GO green)

### Tags / Pills

Small inline labels with semantic colors.

- Font: IBM Plex Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `3px`
- Background: transparent semantic color at 10% opacity
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
- Border-radius: `6px`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in IBM Plex Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Space Grotesk', sans-serif`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="12"`
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.5px`)

---

## Unique Components

### Mission Patch

A circular mission badge displaying the mission designation, number, and crew names.

- Container: Flex column, centered, `2.5rem` vertical margin
- **Badge:** `200px` circle, `--surface` background, `3px solid var(--border)`, inner ring at 6px inset
- **Mission label:** Space Grotesk, `0.6rem`, weight 700, uppercase, `letter-spacing: 0.2em`, `--text-faint`
- **Number:** Space Grotesk, `2.5rem`, weight 700, `--text`
- **Name:** IBM Plex Mono, `0.6rem`, uppercase, `--capture`
- **Crew:** IBM Plex Mono below badge, `0.7rem`, uppercase, `--text-faint`

### Countdown Timer

A T-minus countdown display with large monospace digits and status indicator.

- Container: `--surface` background, `1px solid var(--border)`, `border-radius: 6px`, centered text
- **Label:** IBM Plex Mono, `0.7rem`, uppercase, `--text-faint`
- **Display:** Flex row centered, prefix "T−" + digit groups separated by colons
  - Values: IBM Plex Mono, `3rem`, weight 600, `--text`
  - Units: IBM Plex Mono, `0.6rem`, uppercase, `--text-faint`
  - Separators: IBM Plex Mono, `2.5rem`, `--text-faint`
- **Status indicator:** IBM Plex Mono, `0.7rem`, uppercase
  - `.go` — `--capture` (solid)
  - `.hold` — `--refine` (blinking, 1.5s)
  - `.abort` — `--execute` (blinking, 0.8s)

### Telemetry Readout

An instrument panel grid showing values with labels, units, and color-coded status.

- Container: `--surface` background, `1px solid var(--border)`, `border-radius: 6px`
- **Header bar:** `--surface-2` background, flex row with title and status badge
  - Title: IBM Plex Mono, `0.7rem`, uppercase, `--text`
  - Status badge: IBM Plex Mono, `0.6rem`, with `.nominal` (green), `.caution` (amber), `.warning` (red) variants
- **Grid:** `repeat(auto-fill, minmax(160px, 1fr))`, cells with right/bottom borders
- **Cell:** Label (IBM Plex Mono, `0.6rem`, faint) → value (IBM Plex Mono, `1.25rem`, weight 600) → unit (IBM Plex Mono, `0.6rem`, faint)
- **Value colors:** `.go` = `--capture`, `.caution` = `--refine`, `.warning` = `--execute`

### CAPCOM Log

A capsule communicator transmission log with timestamped entries.

- Container: `--surface` background, `1px solid var(--border)`, `border-radius: 6px`
- **Header bar:** `--surface-2` background, IBM Plex Mono, `0.7rem`, uppercase, `--text`
- **Entries:** Flex row with time, source, and message
  - Time: IBM Plex Mono, `0.7rem`, `--text-faint`, fixed 6rem width
  - Source: IBM Plex Mono, `0.7rem`, weight 600, uppercase, fixed 5rem width
    - `.houston` — `--capture` (green)
    - `.crew` — `--batch` (blue)
    - `.flight` — `--refine` (amber)
    - `.alert` — `--execute` (red)
  - Message: `--text-dim`, flex 1

### Orbital Divider

An SVG trajectory arc with spacecraft dot, used as a thematic section separator.

- Container: `3rem` vertical margin, centered, `max-width: 600px`
- **Path:** Quadratic bezier curve, `stroke: #2a3448`, `stroke-dasharray: 4,3`
- **Spacecraft:** 3px filled circle in `--capture` with 6px outer ring at 40% opacity
- **Earth:** 4px filled circle in `--batch` at 30% opacity (left side)
- **Moon:** 3px filled circle in `--text-faint` at 40% opacity (right side)

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--capture` (GO green)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Deep navy, not black** — backgrounds use blue-tinted dark tones like a control room at night, not pure black.
2. **GO/NO-GO semantics** — four colors map to mission control indicators: GO green (nominal), caution amber (advisory), abort red (critical), flight blue (procedural).
3. **Three-tier text** — warm off-white (--text), dim (--text-dim), faint (--text-faint).
4. **Engineering monospace** — IBM Plex Mono for all telemetry, timestamps, and data readouts.
5. **Clean geometric headings** — Space Grotesk delivers confident uppercase headings echoing the NASA worm logo era.
6. **Instrument panel layout** — telemetry grids, countdown displays, and CAPCOM logs bring real mission control spatial organization into the design.
7. **Mission identity** — circular patch badges echo the tradition of unique embroidered crew patches.
8. **Subtle grid texture** — the hero uses faint grid lines evoking trajectory plotting boards.
