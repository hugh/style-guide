# Japanese Zen / Wabi-Sabi — Style Guide

Asymmetric minimalism — warm stone grey and off-white backgrounds, charcoal ink and muted indigo accents. Ink wash (sumi-e) texture feel, generous negative space (ma), wabi-sabi imperfection. Contemplative and serene.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                      |
|----------------|-----------|--------------------------------------------|
| `--bg`         | `#f5f0e8` | Page background (warm rice paper)          |
| `--surface`    | `#ece5d8` | Cards, panels, diagram containers          |
| `--surface-2`  | `#e0d8c8` | Nested surfaces, secondary panels (tatami) |
| `--surface-3`  | `#d4cab8` | Tertiary surface, row separators (stone)   |
| `--border`     | `#c0b4a0` | Card borders, section dividers             |

### Text

| Token          | Hex       | Usage                                              |
|----------------|-----------|----------------------------------------------------|
| `--text`       | `#1a1810` | Primary text, headings, bold/strong (sumi ink)     |
| `--text-dim`   | `#5a5448` | Body paragraphs, secondary descriptions (faded ink)|
| `--text-faint` | `#8a8478` | Labels, metadata, captions (ghost ink)             |

### Accent & Semantic Colors

Colors drawn from traditional Japanese aesthetics — natural dyes, temple architecture, and traditional crafts.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#2a4a6a` | Primary accent (Shibori Indigo)          |
| `--accent-dim`  | `#1a3a58` | Muted accent                             |
| `--capture`     | `#4a7a50` | Temple Moss Green — growth, nature       |
| `--capture-dim` | `#3a6040` | Muted moss                               |
| `--refine`      | `#b08830` | Lacquer Gold — warmth, craft, refinement |
| `--refine-dim`  | `#906820` | Muted gold                               |
| `--execute`     | `#b83828` | Torii Vermillion — action, energy        |
| `--execute-dim` | `#982818` | Muted vermillion                         |
| `--batch`       | `#2a4a6a` | Deep Indigo — depth, wisdom              |
| `--batch-dim`   | `#1a3a58` | Muted indigo                             |

Each semantic color also has a `-fill` variant at 10% opacity for tag backgrounds.

---

## Typography

### Font Stack

| Role      | Family              | Google Fonts Import                                               |
|-----------|---------------------|-------------------------------------------------------------------|
| Headings  | Cormorant Garamond  | `Cormorant+Garamond:wght@300;400;500;600;700`                    |
| Body      | Inter               | `Inter:wght@300;400;500;600`                                     |
| Labels    | IBM Plex Mono       | `IBM+Plex+Mono:wght@400;500`                                    |

### Type Scale & Weights

| Element            | Family             | Size                          | Weight | Line-height | Notes                                      |
|--------------------|--------------------|-------------------------------|--------|-------------|---------------------------------------------|
| Hero h1            | Cormorant Garamond | `clamp(2.8rem, 8vw, 5rem)`   | 300    | 1.1         | `letter-spacing: -0.01em`                   |
| h2 (section)       | Cormorant Garamond | `1.85rem`                     | 400    | 1.2         |                                             |
| h3 (subsection)    | Cormorant Garamond | `1.25rem`                     | 500    | 1.25        | `margin-top: 2.5rem`                        |
| h4 (card title)    | Inter              | `0.78rem`                     | 600    |             | Uppercase, `letter-spacing: 0.08em`         |
| Body paragraph     | Inter              | `0.95rem`                     | 400    | 1.8         | Color: `--text-dim`                         |
| Section label      | IBM Plex Mono      | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`         |
| Tag                | IBM Plex Mono      | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                   |

---

## Layout

- Container max-width: **900px**, centered, `2.5rem` horizontal padding
- Section padding: `5rem` vertical, `1px solid var(--border)` top border
- Section label format: `01 — Label` (IBM Plex Mono)
- Full-bleed max-width: **1100px** for diagram wraps
- Border radius: **2px** globally — barely there, hand-cut imperfection
- Generous `line-height: 1.8` for body text — let content breathe

---

## Hero Section

- Full viewport height, flex-centered
- **Ink-wash texture:** `::before` creates subtle radial gradients simulating wash effects
- **Brush-stroke base:** `::after` creates a fading horizontal line at the bottom
- Staggered fade-up animation on load (slower, more contemplative than typical)
- Light heading weights (300) channel brush calligraphy delicacy

---

## Standard Components

### Flow Cards

Two-column grid (`.flow-grid`), collapsing to single column below 640px.

- Background: `--surface`, `1px solid var(--border)`, `2px` radius
- Top bar: `2px` height (thinner than typical — subtle)
- Semantic classes: `.capture`, `.refine`, `.execute`, `.batch`, `.accent`

### Pipeline

Horizontal stage display (`.pipeline` > `.pipe-stage`).

- Semantic border-top classes: `.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`
- Stage name uses Cormorant Garamond 600

### Callout

- Indigo left border (3px)
- Faint indigo background wash
- `2px` radius on right side only

### Tags

- Classes: `.tag.t-capture`, `.tag.t-refine`, `.tag.t-execute`, `.tag.t-batch`
- Fill background at 10% semantic color opacity

### Info Table

- Full-width, collapse borders
- Header: IBM Plex Mono, uppercase, faint color
- First column: `--text`, weight 600

### Principle List

- Numbered list with large Cormorant Garamond numerals in accent color
- Weight 300 numerals — light and calligraphic

### Diagram Wrap

- Surface background, border, `2px` radius
- `2.5rem` padding
- Use `.full-bleed` class to expand to 1100px
- SVG text uses Inter; dashed connections with `stroke-dasharray: 4,3`; `rx="2"` for node corners

---

## Unique Components

### Enso Circle (`.enso`)

A hand-brushed, intentionally incomplete circle — the Zen symbol of enlightenment and acceptance of imperfection. Used as a contemplative section marker.

- **Container:** Flex-centered, 160px default size
- **SVG path:** Open circle drawn with bezier curves, `stroke-linecap: round`, 0.5-0.6 opacity
- **Text:** Centered inside, Cormorant Garamond 500
- **Sizes:** `.enso-sm` (100px), default (160px), `.enso-lg` (220px)
- Stroke is sumi ink black (`--text`) or indigo (`--accent`)
- The circle is deliberately incomplete — the gap is the point

### Tokonoma Alcove (`.tokonoma`)

A recessed niche card inspired by the tokonoma alcove in traditional Japanese homes.

- **Container:** `--surface`, `1px` border (no left border), `2px` radius
- **Left edge:** `::before` pseudo-element draws a fading vertical line; `box-shadow: inset 6px 0 12px -4px` creates depth
- **Padding:** Asymmetric — `3rem` left, `2rem` right/top/bottom
- **Heading:** Cormorant Garamond 600, 1.15rem
- **Caption:** IBM Plex Mono, faint, uppercase

### Ink Wash Divider (`.ink-wash-divider`)

An organic SVG brush-stroke separator with sumi-e quality.

- **Container:** `max-width: 600px`, centered
- **SVG:** Two overlapping paths — primary stroke (2.5px) and ghost stroke (1px at 0.3 opacity)
- **Gradient:** `linearGradient` fades from transparent to 0.5 opacity and back — simulating ink concentration variation
- **Path:** Quadratic bezier curves create natural, slightly wavy line

### Stone Garden Badge (`.stone-badge`)

Organic blob-shaped badges using `clip-path` — each one slightly different, like stones in a karesansui garden.

- **Shapes:** Five variants via `.stone-1` through `.stone-5`
- **Clip-path:** Irregular polygons with 10 points each — organic, not geometric
- **Base style:** `--surface-2` background, IBM Plex Mono, uppercase
- **Semantic colors:** `.sb-capture`, `.sb-refine`, `.sb-execute`, `.sb-batch` set fill and text colors
- Mix different stone shapes in a row for natural variation

---

## Summary of Key Patterns

1. **Warm rice-paper backgrounds** — organic warmth, never cold or clinical. Aged washi paper feel.
2. **Generous negative space (ma)** — space is presence, not absence. Let content breathe.
3. **Imperfect edges** — 2px radius globally. Organic clip-paths. Nothing machine-perfect.
4. **Light-weight calligraphic headings** — Cormorant Garamond at weight 300-400 channels brush elegance.
5. **Traditional Japanese palette** — shibori indigo, temple moss, lacquer gold, torii vermillion.
6. **Ink-wash texture** — subtle gradients and organic SVG strokes simulate sumi-e painting.
7. **Enso section markers** — incomplete circles as contemplative pauses between sections.
8. **Tokonoma focus cards** — asymmetric recessed alcoves for singular, focused content.
9. **Stone garden badges** — organic blob shapes create natural irregularity in labels and tags.
