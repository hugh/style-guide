# Deep Sea — Style Guide

Dark and bioluminescent. A design system inspired by the abyssal ocean — translucent jellyfish-membrane surfaces, bathymetric contour-line textures, pressure-gauge depth indicators, sonar pings, and gentle wave-line dividers for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                      |
|----------------|-----------|--------------------------------------------|
| `--bg`         | `#060a14` | Page background (abyssal black-navy)       |
| `--surface`    | `#0c1220` | Cards, panels, diagram containers          |
| `--surface-2`  | `#121a2c` | Nested surfaces, secondary panels          |
| `--surface-3`  | `#1a2438` | Tertiary surface, row separators           |
| `--border`     | `#243050` | Card borders, section dividers             |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#c8d4e8` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#7088a8` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#3a5070` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                        |
|-----------------|-----------|---------------------------------------------|
| `--accent`      | `#00b8e0` | Primary accent (Electric Blue Bioluminescence) |
| `--accent-dim`  | `#005870` | Muted accent                                |
| `--capture`     | `#00a8a0` | Soft Teal — life, oxygen, specimens         |
| `--capture-dim` | `#005450` | Muted teal                                  |
| `--refine`      | `#8868c8` | Pale Violet — deep currents, analysis       |
| `--refine-dim`  | `#443464` | Muted violet                                |
| `--execute`     | `#e05030` | Thermal Vent — heat, danger, warnings       |
| `--execute-dim` | `#702818` | Muted red-orange                            |
| `--batch`       | `#2868c0` | Ocean Current Blue — pressure, systems      |
| `--batch-dim`   | `#143460` | Muted blue                                  |

### Frosted Glass Tokens

| Token              | Value                        | Usage                              |
|--------------------|------------------------------|------------------------------------|
| `--glass-bg`       | `rgba(12, 18, 32, 0.7)`     | Translucent card background        |
| `--glass-bg-hover` | `rgba(12, 18, 32, 0.85)`    | Hover state background             |
| `--glass-blur`     | `12px`                       | Backdrop-filter blur radius        |
| `--radius`         | `16px`                       | Primary border-radius (organic)    |
| `--radius-sm`      | `10px`                       | Secondary border-radius            |
| `--radius-xs`      | `6px`                        | Small elements (tags, code)        |

---

## Typography

### Font Stack

| Role      | Family         | Google Fonts Import                                |
|-----------|----------------|-----------------------------------------------------|
| Headings  | Nunito         | `Nunito:wght@700;800`                               |
| Body      | Inter          | `Inter:wght@400;500;600`                            |
| Labels    | IBM Plex Mono  | `IBM+Plex+Mono:wght@400;500`                       |

```html
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500&family=Inter:wght@400;500;600&family=Nunito:wght@700;800&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family         | Size                          | Weight | Line-height | Notes                                     |
|--------------------|----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Nunito         | `clamp(3rem, 9vw, 6rem)`     | 800    | 1.0         | Accent-colored `<span>` with glow          |
| h2 (section)       | Nunito         | `2rem`                        | 800    | 1.1         | letter-spacing: -0.01em                    |
| h3 (subsection)    | Nunito         | `1.3rem`                      | 700    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | Inter          | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.08em          |
| Body paragraph     | Inter          | `0.9rem`                      | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Inter          | `1rem`                        | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | Inter          | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono  | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono  | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Diagram label      | IBM Plex Mono  | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | IBM Plex Mono  | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Gauge readout      | IBM Plex Mono  | `0.7rem`                      | 500    |             | `letter-spacing: 0.1em`, color: `--accent` |
| Table header       | IBM Plex Mono  | `0.7rem`                      | 500    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | Inter          | `0.82rem`                     | 400    |             | First column: `--text` color               |
| `<strong>` in body | Inter          | inherit                       | 600    |             | Color: `--text`                            |

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
- **Background:** Subtle vertical gradient from `--bg` through deeper navy tones
- **Bathymetric contour lines:** Concentric elliptical radial gradients via `::before` simulating topographic depth map lines at very low opacity (0.008–0.03) in accent blue
- **Bioluminescent ambient glow:** Faint radial gradients via `::after` using accent blue, violet, and teal at very low opacity, simulating bioluminescent light in dark water
- **Title glow:** The `<span>` inside h1 uses `--accent` color with `text-shadow: 0 0 40px rgba(0, 184, 224, 0.4), 0 0 80px rgba(0, 184, 224, 0.15)`
- **Staggered fade-up animation** on load:
  - Label: 0s delay
  - h1: 0.15s delay
  - Subtitle: 0.3s delay
  - Version: 0.45s delay
  - Animation: `opacity 0→1, translateY(20px→0)`, 0.8s ease-out

---

## Components

### Flow Cards (2-Column Grid)

A grid of frosted-glass cards used for listing related items.

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--glass-bg` translucent background with `backdrop-filter: blur(var(--glass-blur))`, `1px solid var(--border)`, `border-radius: var(--radius)` (16px), `padding: 1.5rem`
- **Hover:** Border color changes to `--accent`, gains `box-shadow: 0 0 20px rgba(0, 184, 224, 0.1), 0 4px 24px rgba(0, 0, 0, 0.3)` (bioluminescent glow), background becomes `--glass-bg-hover`
- **Top accent bar:** 3px colored bar at the top edge (via `::before`) with matching `box-shadow` glow (0.4 opacity). Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase Inter 600) → body paragraph (Inter 0.82rem)

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--glass-bg` translucent background with backdrop-filter, `1px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left `var(--radius)`, last gets right `var(--radius)`. Adjacent stages share borders (`border-left: none`).
- **Top accent:** 3px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step number (IBM Plex Mono, `0.7rem`, faint) → name (Inter 600, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, frosted-glass background, `1px solid var(--border)`, `border-radius: var(--radius)`, `padding: 1.25rem`
- **Number:** Nunito, `2rem`, weight 800, `--accent`, fixed `2rem` width, centered, `text-shadow: 0 0 16px rgba(0, 184, 224, 0.3)`
- **Content:** h4 title (Inter 600, `0.85rem`, uppercase) + body paragraph (Inter, `0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `3px solid var(--accent)`
- Background: `rgba(0, 184, 224, 0.05)`
- Border-radius: `0 var(--radius) var(--radius) 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (electric blue)

### Tags / Pills

Small inline labels with semantic colors.

- Font: IBM Plex Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `var(--radius-xs)` (6px)
- Background: transparent semantic color at 12% opacity
- Border: `1px solid` in dim semantic color
- Text color: full semantic color

### Tables

Styled as submarine instrument panel readouts with frosted-glass backgrounds.

- Full width, `border-collapse: separate`, `border-spacing: 0`
- Frosted-glass background with `var(--glass-bg)` and backdrop-filter
- Outer border: `1px solid var(--border)`, `border-radius: var(--radius)`
- **Header row:** IBM Plex Mono, uppercase, `0.7rem`, `letter-spacing: 0.1em`, `--text-faint`, bottom border `1px solid var(--border)`, darker tinted background
- **Body cells:** Inter, `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px solid var(--surface-3)`
- **Last row:** No bottom border
- **First column** in body: `--text` color

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--glass-bg` with backdrop-filter
- Border: `1px solid var(--border)`
- Border-radius: `var(--radius)` (16px)
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in IBM Plex Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Inter', sans-serif`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="12"`
- Labels inside nodes: Semantic color, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.5px`)

---

## Unique Components

### Depth Gauge

A circular pressure gauge (200px) showing current depth reading in meters.

- Container: Flex column, centered, `2.5rem` vertical margin
- Label: IBM Plex Mono, `0.7rem`, `letter-spacing: 0.15em`, uppercase, `--text-faint`
- **Dial:** 200px circle, frosted-glass background with backdrop-filter, `2px solid var(--border)`
  - `box-shadow: inset 0 0 30px rgba(0, 0, 0, 0.4), 0 0 20px rgba(0, 184, 224, 0.08)` for depth and glow
- **Pressure rings:** Four concentric rings at 25%, 45%, 65%, 85% radius via `radial-gradient`, `--border` color, 40% opacity
- **Center dot:** 8px circle, `--accent` background with `box-shadow: 0 0 8px rgba(0, 184, 224, 0.6)`, positioned center via absolute + translate
- **Needle:** 40% width bar from center, `linear-gradient(90deg, var(--accent), transparent)`, rotated via `transform: rotate()`, with accent glow shadow
- **Reading:** IBM Plex Mono, `1.1rem`, weight 500, `--accent` color with `text-shadow: 0 0 10px rgba(0, 184, 224, 0.5)`, positioned at bottom-center of dial
- **Unit label:** IBM Plex Mono, `0.6rem`, `--text-faint`, uppercase, below the reading
- **Readout:** IBM Plex Mono, `0.7rem`, `--accent`, below the dial

### Specimen Card

A marine biology specimen label with Latin species name, depth found, and classification data grid.

- Container: Frosted-glass background with backdrop-filter, `1px solid var(--border)`, `border-radius: var(--radius)`
- **Header:** Flex row with space-between, darker tinted background
  - Species name: Nunito 700, `0.95rem`, `--text`; Latin name in `<em>` uses `--accent` color, italic
  - Classification badge: IBM Plex Mono, `0.65rem`, uppercase, teal background fill with teal text/border
- **Body:** 2-column grid (1fr specimen-data + 1fr specimen-visual). Collapses to 1 column at 640px.
- **Data grid:** Rows with label/value pairs separated by `--surface-3` borders
  - Labels: IBM Plex Mono, `--text-faint`, uppercase, `0.7rem`
  - Values: `--text` default, `.teal` = `--capture`, `.violet` = `--refine`, `.warning` = `--execute`, `.blue` = `--batch`, `.glow` = `--accent` with text-shadow
- **Visual panel:** Centered SVG wireframe (120x120px), `--accent` stroke, 50% opacity, border-left separator
  - Scanning line: `::after` pseudo-element, 2px height, `linear-gradient` from transparent through `--accent`, animates top position 10%→90% over 3s

### Wave Divider

An SVG section separator with gentle undulating sinusoidal wave paths in fading bioluminescent colors.

- Container: `3rem` vertical margin, centered, `max-width: 800px`
- SVG viewBox: `0 0 800 60`, full width, 60px height
- **Three layered sinusoidal wave paths:**
  1. Primary wave: `--accent` (#00b8e0), stroke-width `1.5`, opacity `0.4`
  2. Secondary wave: `--refine` (#8868c8), stroke-width `1`, opacity `0.2`, slightly offset vertically
  3. Tertiary wave: `--capture` (#00a8a0), stroke-width `0.75`, opacity `0.15`, further offset
- Waves use cubic Bezier curves (`C` commands) creating smooth sinusoidal undulations

### Sonar Ping

A circular badge with concentric rings and a pulsing animation, used as a section marker or status indicator.

- Container: Inline-flex column, centered
- Label: IBM Plex Mono, `0.65rem`, `letter-spacing: 0.12em`, uppercase, `--text-faint`
- **Circle:** 80px, rounded, `rgba(0, 184, 224, 0.08)` background, `2px solid var(--accent)`, `box-shadow: 0 0 16px rgba(0, 184, 224, 0.15)`
- **Center dot:** 10px circle, `--accent` background with `box-shadow: 0 0 10px rgba(0, 184, 224, 0.6)`
- **Pulse rings (3x):** Concentric rings that expand outward via `@keyframes sonarPulse`:
  - Start: 10px diameter, 0.6 opacity, 2px border
  - End: 80px diameter, 0 opacity, 1px border
  - Duration: 2.5s ease-out infinite
  - Staggered delays: 0s, 0.8s, 1.6s
- **Status text:** IBM Plex Mono, `0.65rem`, `--accent`, uppercase
- **Inline variant:** `.sonar-ping.inline` creates a 32px version for inline use within text

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `var(--radius-xs)` (6px)
- Border: `1px solid var(--border)`
- Color: `--accent` (electric blue)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`
- Links: `--text-faint` default, `--accent` on hover, underline with `text-underline-offset: 2px`

---

## Summary of Key Patterns

1. **Abyssal darkness** — backgrounds descend from deep navy to near-black, with no warm tones. Everything is cold, deep water.
2. **Bioluminescent accents** — electric blue primary accent mimics deep-sea organism glow, with text-shadows and box-shadows.
3. **Frosted glass membranes** — all cards use `rgba()` backgrounds with `backdrop-filter: blur()`, creating translucent jellyfish-membrane surfaces.
4. **Organic radii** — 16px border-radius everywhere. No sharp corners. Every shape is soft and rounded like deep-sea creatures.
5. **Three-tier text** — bioluminescent white (--text), deep water grey-blue (--text-dim), abyssal fade (--text-faint).
6. **Rounded headings** — Nunito (700-800) provides rounded, fluid-feeling headings evoking water motion.
7. **Clean body text** — Inter for body paragraphs gives precise readability against dark backgrounds.
8. **Instrument readouts** — IBM Plex Mono for labels, tags, and gauge readings gives a submarine instrument panel feel.
9. **Ocean semantics** — soft teal (life/oxygen), pale violet (deep currents), thermal vent red-orange (heat/danger), ocean current blue (pressure/systems).
10. **Bathymetric texture** — the hero uses concentric radial gradients simulating topographic depth map contour lines.
