# Grunge / Zine — Style Guide

A torn paper collage aesthetic — off-white newsprint, photocopier distortion, mixed typography, tape-strip borders, cut-and-paste layered panels, Xerox-degraded textures, marker highlights, and sticker badges. Anarchic, raw, DIY punk zine energy.

---

## Color Palette

### Backgrounds & Surfaces (Newsprint)

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#f0ece4` | Page background (off-white newsprint)    |
| `--surface`    | `#e8e2d8` | Cards, panels (slightly yellowed paper)  |
| `--surface-2`  | `#ddd6ca` | Nested surfaces (layered paper)          |
| `--surface-3`  | `#d0c8ba` | Tertiary surface (cardboard)             |
| `--border`     | `#1a1a1a` | Bold black borders (marker/ink weight)   |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#0a0a0a` | Primary text, headings, strong (photocopier black) |
| `--text-dim`   | `#3a3a38` | Body paragraphs, descriptions (faded copy)      |
| `--text-faint` | `#6a6a68` | Labels, metadata, captions (light copy)          |

### Accent & Semantic Colors

Colors represent different marker/pen types found in the zine-maker's toolkit.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#d82050` | Primary accent (highlighter pink/red)    |
| `--accent-dim`  | `#b01840` | Muted accent                             |
| `--capture`     | `#18882a` | Green marker — gather, collect           |
| `--capture-dim` | `#106820` | Muted green                              |
| `--refine`      | `#c8a008` | Yellow highlighter — edit, refine        |
| `--refine-dim`  | `#a08008` | Muted yellow                             |
| `--execute`     | `#d82050` | Red marker — ship, execute               |
| `--execute-dim` | `#b01840` | Muted red                                |
| `--batch`       | `#1848b8` | Blue pen — batch, process                |
| `--batch-dim`   | `#103898` | Muted blue                               |

### Tape Strip Color

| Token            | Value                          | Usage                          |
|------------------|--------------------------------|--------------------------------|
| `--tape`         | `rgba(220, 210, 160, 0.6)`    | Scotch tape background         |
| `--tape-border`  | `rgba(180, 170, 120, 0.4)`    | Tape edge                      |

---

## Typography

### Font Stack

| Role       | Family           | Google Fonts Import                                  |
|------------|------------------|------------------------------------------------------|
| Headings   | Special Elite    | `Special+Elite` (weight 400)                         |
| Callouts   | Permanent Marker | `Permanent+Marker` (weight 400)                      |
| Body       | Inter            | `Inter:wght@400;500;600;700`                         |
| Labels     | IBM Plex Mono    | `IBM+Plex+Mono:wght@400;500;600`                    |

### Type Scale & Weights

| Element            | Family           | Size                          | Weight | Line-height | Notes                              |
|--------------------|------------------|-------------------------------|--------|-------------|-------------------------------------|
| Hero h1            | Special Elite    | `clamp(2.6rem, 7vw, 5rem)`   | 400    | 1.1         | Slight rotation (-1.5deg)           |
| h2 (section)       | Special Elite    | `1.8rem`                      | 400    | 1.2         |                                     |
| h3 (subsection)    | Special Elite    | `1.15rem`                     | 400    | 1.25        | `margin-top: 2.5rem`               |
| h4 (card title)    | Inter            | `0.78rem`                     | 700    |             | Uppercase, `letter-spacing: 0.08em`|
| Body paragraph     | Inter            | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                |
| Marker callout     | Permanent Marker | `1.2–2.4rem`                  | 400    |             | Used in hero spans, principle nums |
| Section label      | IBM Plex Mono    | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`|
| Tag                | IBM Plex Mono    | `0.7rem`                      | 600    |             | `letter-spacing: 0.06em`          |

---

## Layout

- **Container max-width:** 900px, centered, `2rem` horizontal padding
- **Section padding:** `5rem` vertical, `3px solid var(--border)` top border
- **Section label format:** `01 — Label` (IBM Plex Mono, uppercase)
- **Full-bleed max-width:** 1100px
- **Border radius:** `0px` on ALL elements — everything is torn/cut, no smooth curves
- **Borders:** Thick 2-3px black borders (var(--border)) on cards, tables, containers
- **Rotations:** Subtle 1-3 degree CSS rotations on cards, callouts, stickers for handmade feel

---

## Hero Section

- Full viewport height, flex-centered
- **Torn paper strip bar:** `::before` creates a 12px top bar with torn zigzag bottom edge, alternating semantic colors
- **Grid overlay:** `::after` creates subtle newsprint grid lines
- Title uses Special Elite with -1.5deg rotation
- Accent span uses Permanent Marker with +2deg rotation and pink highlight background
- Staggered fade-up animation on load

---

## Standard Components

### Flow Cards

Two-column grid (`.flow-grid`) with semantic color top bars.

- **Borders:** 2px solid var(--border), no border-radius
- **Hover:** Slight rotation (-0.5deg)
- **Variants:** `.capture`, `.refine`, `.execute`, `.batch`, `.accent`

### Pipeline

Horizontal stages (`.pipeline` > `.pipe-stage`).

- **Borders:** 2px solid, no radius, 4px semantic top border
- **Stage names:** Special Elite font
- **Variants:** `.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`

### Callout

Left-border callout with slight rotation.

- **Border:** 5px left accent + 2px black frame
- **Background:** var(--surface)
- **Transform:** rotate(0.3deg)

### Tags

Inline tag badges with semantic colors.

- **Font:** IBM Plex Mono, 0.7rem, uppercase, weight 600
- **Borders:** 2px solid semantic color, no radius
- **Variants:** `.t-capture`, `.t-refine`, `.t-execute`, `.t-batch`

### Info Table

Standard data table with thick header border.

- **Header border:** 3px solid var(--border)
- **Row borders:** 1px solid var(--surface-3)

### Principle List

Numbered list with Permanent Marker numerals.

- **Number:** Permanent Marker, 2.4rem, accent color
- **Container:** 2px black border, no radius

### Diagram Container

SVG diagram wrapper.

- **Border:** 2px solid var(--border), no radius
- **Background:** var(--surface)
- **Full-bleed:** `.full-bleed` class expands to 1100px

---

## Unique Components

### Tape Strip Card (`.tape-card`)

A card that looks taped to the page.

- **Body:** var(--surface) background, 2px black border
- **Rotation:** -0.8deg default (vary per instance)
- **Tape strips:** `::before` (left) and `::after` (right) pseudo-elements
  - Semi-transparent yellowish rectangles (var(--tape))
  - 70px x 24px, rotated -4deg (left) and +3deg (right)
- **Torn bottom edge:** `clip-path: polygon(...)` creates zigzag
- **Title:** Special Elite, 1.1rem

### Ransom Note Block (`.ransom-note`)

A callout where each word alternates between font styles.

- **Container:** 3px black border, var(--surface) background, line-height 2.2
- **Each child span** cycles through 6 styles via `:nth-child(6n+N)`:
  1. Special Elite, 1.3rem, rotated -1deg
  2. Inter bold, uppercase, inverted (white on black)
  3. IBM Plex Mono, 0.9rem, accent underline
  4. Permanent Marker, 1.2rem, accent color, rotated -2deg
  5. Inter regular, yellow highlight background
  6. Special Elite, 0.8rem, uppercase, bordered box, rotated 1.5deg

### Xerox Divider (`.xerox-divider`)

A horizontal divider that looks like a degraded photocopy line.

- **Height:** 8px
- **Background:** var(--border), opacity 0.7
- **Edges:** Jagged clip-path polygon with randomized points
- **Noise:** `::after` adds vertical line noise overlay
- **Margin:** 3rem auto

### Sticker Badge (`.sticker-badge`)

An inline badge that looks like a peeled sticker.

- **Font:** Permanent Marker, 0.85rem, uppercase
- **Border:** 2px solid var(--border), no radius
- **Shadow:** 3px 3px 0px rgba(0,0,0,0.25) — flat offset shadow
- **Rotation:** -2deg default, alternates via nth-child
- **Variants:**
  - Default: var(--accent) background, white text
  - `.sticker-green`: var(--capture) background
  - `.sticker-yellow`: var(--refine) background, dark text
  - `.sticker-red`: var(--execute) background
  - `.sticker-blue`: var(--batch) background

---

## Utility Classes

| Class              | Effect                                           |
|--------------------|--------------------------------------------------|
| `.rotate-left`     | `transform: rotate(-1.5deg)`                     |
| `.rotate-right`    | `transform: rotate(1.5deg)`                      |
| `.rotate-heavy`    | `transform: rotate(-3deg)`                       |
| `.marker-highlight`| Yellow marker highlight on text (55% transparent)|
| `.marker-pink`     | Pink marker highlight on text (55% transparent)  |
| `.inline-code`     | Monospace code snippet with border               |

---

## Summary of Key Patterns

1. **Newsprint backgrounds** — off-white yellowed paper, never pure white, layered like torn sheets.
2. **Bold black borders** — thick 2-3px marker-weight ink lines on everything.
3. **Zero border radius** — torn, cut, sharp. No smooth curves anywhere.
4. **Mixed typography** — Special Elite (typewriter), Permanent Marker (handwritten), Inter (readable body), IBM Plex Mono (labels).
5. **Slight rotations** — 1-3 degree transforms on elements for the hand-placed collage feel.
6. **Tape strip cards** — scotch tape pseudo-elements with torn bottom edges.
7. **Ransom note blocks** — nth-child cycling through 6 different type styles.
8. **Xerox dividers** — jagged clip-path degraded photocopy lines.
9. **Sticker badges** — offset drop shadows, rotations, bold color backgrounds.
10. **DIY punk energy** — every visual choice reinforces the handmade, photocopied, counter-cultural aesthetic.
