# Cyberpunk / Neon — Style Guide

A rain-soaked neon design system — hot pink and electric cyan accents, glitch effects, holographic shimmer, and data stream textures for single-page HTML documents. Blade Runner meets Ghost in the Shell.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                      |
|----------------|-----------|--------------------------------------------|
| `--bg`         | `#08080c` | Page background (rain-soaked black)         |
| `--surface`    | `#10101a` | Cards, panels, diagram containers           |
| `--surface-2`  | `#181828` | Nested surfaces, secondary panels           |
| `--surface-3`  | `#202038` | Tertiary surface, row separators            |
| `--border`     | `#2a2a48` | Card borders, section dividers (neon shadow) |

### Text

| Token          | Hex       | Usage                                           |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#e0e0f0` | Primary text, headings, bold/strong content      |
| `--text-dim`   | `#8888b0` | Body paragraphs, secondary descriptions          |
| `--text-faint` | `#505070` | Labels, metadata, captions, annotations          |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                      |
|-----------------|-----------|-------------------------------------------|
| `--accent`      | `#ff1493` | Primary accent (Hot Pink Neon)             |
| `--accent-dim`  | `#990c58` | Muted accent                              |
| `--capture`     | `#00e5ff` | Electric Cyan — recon, scanning, data      |
| `--capture-dim` | `#007a99` | Muted cyan                                |
| `--refine`      | `#e0d020` | Warning Neon Yellow — caution, decryption  |
| `--refine-dim`  | `#8a8010` | Muted yellow                              |
| `--execute`     | `#ff1493` | Hot Pink — critical, extraction, combat    |
| `--execute-dim` | `#990c58` | Muted pink                                |
| `--batch`       | `#4060ff` | Deep Electric Blue — secure, upload, relay |
| `--batch-dim`   | `#2030a0` | Muted blue                                |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                                        |
|-----------|-----------------|-------------------------------------------------------------|
| Headings  | Orbitron        | `Orbitron:wght@400;500;600;700;800;900`                     |
| Body      | JetBrains Mono  | `JetBrains+Mono:wght@300;400;500;600;700`                  |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@300;400;500;600`                       |

```html
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800;900&family=JetBrains+Mono:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@300;400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                     |
|--------------------|-----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Orbitron        | `clamp(2.8rem, 8vw, 5.5rem)` | 900    | 1.1         | Uppercase. Accent-colored `<span>` glows.  |
| h2 (section)       | Orbitron        | `1.8rem`                      | 700    | 1.15        | Uppercase, letter-spacing: 0.06em          |
| h3 (subsection)    | Orbitron        | `1.15rem`                     | 700    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | JetBrains Mono  | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.06em          |
| Body paragraph     | JetBrains Mono  | `0.9rem`                      | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | JetBrains Mono  | `1rem`                        | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | JetBrains Mono  | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono   | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Diagram label      | IBM Plex Mono   | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | IBM Plex Mono   | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Table header       | JetBrains Mono  | `0.7rem`                      | 600    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | JetBrains Mono  | `0.82rem`                     | 400    |             | First column: `--text` + weight 600        |
| `<strong>` in body | JetBrains Mono  | inherit                       | 600    |             | Color: `--text`                            |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Rain-streak overlay:** Thin diagonal `repeating-linear-gradient` lines in cyan, pink, and yellow at very low opacity via `::before`, with a subtle vertical drift animation (`translateY` over 8s)
- **Neon ambient glow:** Faint elliptical `radial-gradient` layers via `::after` in pink, cyan, and blue at low opacity — simulates distant neon light pollution
- **Title glow:** The `<span>` inside h1 uses `--accent` color with `text-shadow: 0 0 10px, 0 0 40px, 0 0 80px` in decreasing opacity — creates a neon tube effect
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
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 2px`, `padding: 1.5rem`
- **Hover:** Border color changes to `--accent`, gains `box-shadow: 0 0 12px rgba(255, 20, 147, 0.2), 0 0 4px rgba(255, 20, 147, 0.1)` (neon glow)
- **Top accent bar:** 3px colored bar at the top edge (via `::before`) with matching `box-shadow` glow. Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `1px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `2px`, last gets right border-radius `2px`. Adjacent stages share borders (`border-left: none`).
- **Top accent:** 3px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step number (IBM Plex Mono, `0.7rem`, faint) → name (weight 600, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `1px solid var(--border)`, `border-radius: 2px`, `padding: 1.25rem`
- **Number:** Orbitron, `2rem`, weight 700, `--accent`, fixed `2rem` width, centered, with `text-shadow: 0 0 12px rgba(255, 20, 147, 0.4)` neon glow
- **Content:** h4 title (weight 600, `0.85rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `3px solid var(--accent)`
- Background: `rgba(255, 20, 147, 0.05)`
- Border-radius: `0 2px 2px 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (hot pink neon)

### Tags / Pills

Small inline labels with semantic colors.

- Font: IBM Plex Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `2px`
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
- Border-radius: `2px`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in IBM Plex Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'JetBrains Mono', monospace`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="12"`
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.5px`)

---

## Unique Components

### Neon Sign

A featured text element with multi-layered CSS `text-shadow` glow that creates a neon tube signage effect. Includes a subtle flicker/pulse animation.

- Outer container: `padding: 2rem`, `text-align: center`, `--surface` background, `1px solid var(--border)`, `border-radius: 2px`
- Ambient glow: Faint `radial-gradient` in accent color via `::before`
- **Neon text (`.neon-text`):** Orbitron, weight 900, `clamp(1.8rem, 5vw, 3rem)`, uppercase, `letter-spacing: 0.1em`
  - Color: `--accent` (hot pink)
  - `text-shadow`: 5 layers at 7px, 20px, 42px, 82px, 120px blur radius with decreasing opacity — creates realistic neon tube luminance
  - Animation: `neonPulse` 3s infinite — brief flickers at irregular intervals to simulate unstable neon gas
- **Color variants:** `.neon-text.cyan` uses `--capture` with cyan glow layers; `.neon-text.yellow` uses `--refine` with yellow glow layers
- **Subtitle (`.neon-sub`):** IBM Plex Mono, `0.7rem`, `letter-spacing: 0.2em`, uppercase, `--text-faint`

### Glitch Block

A callout/card with a corrupted-data aesthetic: scan-line texture, glitch animation on hover, and a sweeping corrupted-data bar.

- Background: `--surface`, `border-left: 4px solid var(--capture)`, `border-radius: 0 2px 2px 0`
- **Scan-line texture:** `::before` pseudo-element with `repeating-linear-gradient` alternating transparent and faint cyan bands (2px spacing)
- **Corrupted data bar:** `::after` pseudo-element — a 2px horizontal line in `--capture` that sweeps vertically on hover via `glitchBar` keyframes
- **Glitch animation on hover:** `glitchShift` keyframes — brief `transform: translate` shifts combined with `clip-path: inset()` cuts that make the block appear to flicker and fragment
- **Header (`.glitch-header`):** IBM Plex Mono, `0.65rem`, `letter-spacing: 0.2em`, uppercase, `--capture`. Metadata spans in `--text-faint`.
- `<strong>` within the block uses `--capture` color

### Holographic Card

A translucent content panel with a shimmer gradient background that shifts on hover and a continuous holographic sweep animation.

- Background: Multi-stop `linear-gradient` at 135deg cycling through pink, cyan, blue, pink, cyan at 5% opacity each; `background-size: 200% 200%`; `background-position` shifts from `0% 0%` to `100% 100%` on hover
- Border: `1px solid var(--border)`, `border-radius: 2px`
- **Hover state:** Border changes to `--accent`, gains multi-layer `box-shadow` in pink and cyan, plus faint inner glow; background position shifts
- **Shimmer overlay (`::before`):** `linear-gradient` at 105deg with transparent → pink → cyan → transparent bands; `background-size: 200% 100%`; animated via `holoShimmer` from `-100%` to `200%` position over 4s
- **Heading:** `--accent` color
- **Grid layout:** `.holo-grid` provides a 2-column grid for holographic cards, same responsive behavior as `.flow-grid`

### Data Stream Divider

An SVG separator styled like streaming data or matrix rain — thin vertical lines of varying height and opacity.

- Container: `height: 60px`, centered, `overflow: hidden`
- SVG: `max-width: 800px`, `height: 60px`
- **Stream lines:** `<rect>` elements, each `1.5px` wide with varying heights (12–35px), `rx="0.5"` for subtle rounding
- Colors: Mix of `--capture` (cyan), `--accent` (pink), `--batch` (blue), and `--refine` (yellow) at varying opacities (0.3–0.7)
- **Animation:** `streamFall` keyframes — fade in, translate downward, fade out over 2s; staggered with `nth-child` rules varying `animation-duration` (1.5–2.5s) and `animation-delay` (0–1s)

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `2px`
- Border: `1px solid var(--border)`
- Color: `--accent` (hot pink neon)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Rain-soaked black, not pure black** — backgrounds use purple-tinted near-blacks like wet pavement at night, not pure #000.
2. **Neon glow is key** — multi-layered text-shadow on featured text, box-shadow blur on card borders, and radial-gradient ambient light on containers.
3. **Three-tier text** — neon white (--text), rain grey (--text-dim), shadow (--text-faint).
4. **Monospace body text** — JetBrains Mono for body copy gives the entire document a terminal/hacker feel.
5. **Geometric futuristic headings** — Orbitron delivers sharp angular uppercase headings evoking corporate megastructure signage.
6. **Cyberpunk semantics** — electric cyan (recon/data), warning neon yellow (caution/decryption), hot pink (critical/combat), deep electric blue (secure/upload).
7. **Glitch & corruption** — scan lines, clip-path shifts, and corrupted data headers reinforce the cyberpunk atmosphere.
8. **Holographic shimmer** — multi-color gradient overlays with animated position shifts create holographic projection surfaces.
9. **Sharp edges (2px radius)** — minimal border-radius creates a hard, angular, tech-industrial aesthetic throughout.
10. **Rain-streak textures** — thin diagonal repeating gradients at low opacity simulate rain on glass/neon reflections on wet surfaces.
