# Darkroom — Style Guide

Chemical warmth under safelight red. A design system inspired by analog photography — Polaroid borders, contact sheets, developer-tray progress bars, and film-strip dividers for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#121110` | Page background (warm charcoal)          |
| `--surface`    | `#1a1918` | Cards, panels, diagram containers        |
| `--surface-2`  | `#222120` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#2c2a28` | Tertiary surface, row separators         |
| `--border`     | `#3a3835` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#e8e2d8` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#9a9488` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#605850` | Labels, EXIF metadata, captions, annotations    |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                  |
|-----------------|-----------|---------------------------------------|
| `--accent`      | `#c83030` | Primary accent (Safelight Red)        |
| `--accent-dim`  | `#802020` | Muted accent                          |
| `--capture`     | `#c83030` | Safelight Red — exposure, highlight   |
| `--capture-dim` | `#802020` | Muted red                             |
| `--refine`      | `#c89848` | Sepia Amber — toning, warmth          |
| `--refine-dim`  | `#886828` | Muted amber                           |
| `--execute`     | `#b83878` | Chemical Magenta — filter, process    |
| `--execute-dim` | `#782050` | Muted magenta                         |
| `--batch`       | `#4880a8` | Developer Blue — processing, cool     |
| `--batch-dim`   | `#2c5070` | Muted blue                            |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                              |
|-----------|-----------------|---------------------------------------------------|
| Headings  | Caveat          | `Caveat:wght@400;500;600;700`                     |
| Body      | DM Sans         | `DM+Sans:wght@300;400;500;600`                    |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500`                      |

```html
<link href="https://fonts.googleapis.com/css2?family=Caveat:wght@400;500;600;700&family=DM+Sans:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                     |
|--------------------|-----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Caveat          | `clamp(3.5rem, 10vw, 7rem)`  | 700    | 0.95        | Accent-colored `<span>` for title word     |
| h2 (section)       | Caveat          | `2.8rem`                      | 700    | 1.05        |                                            |
| h3 (subsection)    | Caveat          | `2rem`                        | 700    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | DM Sans         | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.06em          |
| Body paragraph     | DM Sans         | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | DM Sans         | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Polaroid caption   | Caveat          | `1rem`                        | 400    | 1.3         | Dark text on white Polaroid border         |
| Section label      | IBM Plex Mono   | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--accent`      |
| Tag                | IBM Plex Mono   | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| EXIF metadata      | IBM Plex Mono   | `0.55rem`                     | 400    |             | On Polaroid cards, `--text-faint` equivalent |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace EXIF-style label** in the format `01 — Label`

### Full-Bleed Containers

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: EXIF-style label, h1, subtitle, version
- **Grain texture:** Faint radial gradients in safelight red and amber via `::before`, simulating light scatter on darkroom walls
- **Light leak:** Diagonal linear gradients via `::after` in red and amber at very low opacity, evoking accidental light leaks in film cameras
- **Title accent:** `<span>` inside h1 uses `--accent` (safelight red)
- **Staggered fade-up animation** on load (same as other themes)

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Darkroom-specific adjustments:
- Border-radius: `4px` (slightly rounded, not sharp)
- Hover glow uses safelight red: `rgba(200, 48, 48, 0.1)`
- Principle numbers use Caveat at `2.5rem` instead of the heading font

---

## Unique Components

### Polaroid Cards

Instant-photo cards with thick white borders and handwritten captions.

- **Grid:** `repeat(auto-fill, minmax(200px, 1fr))`, `2rem` gap
- **Card:** `#f0ece4` (warm white) background, `12px` padding on top/sides, `48px` bottom padding
- **Rotation:** Each card has a CSS custom property `--rotate` for slight random tilt (-1deg to 2deg). Cards straighten to 0deg on hover with lift.
- **Shadow:** Layered `box-shadow` for depth (2px + 0px spread)
- **Photo area:** Square `aspect-ratio: 1`, `--surface` background, `1px solid var(--border)`
- **Caption:** Caveat, `1rem`, dark text (`#3a3530`), centered
- **EXIF metadata:** IBM Plex Mono, `0.55rem`, muted (`#8a8478`), centered

### Contact Sheet

A thumbnail grid mimicking a real photographic contact sheet.

- **Container:** `--surface` background, `1px solid var(--border)`, `border-radius: 4px`
- **Header:** `--surface-2` background, flex row with title and roll metadata
- **Grid:** `repeat(auto-fill, minmax(100px, 1fr))`, `2px` gap on `--surface-3` background
- **Frames:** `--bg` background, square `aspect-ratio: 1`, centered icon
  - Frame number: IBM Plex Mono, `0.5rem`, `--text-faint`, bottom-right positioned
  - `.selected` frames get a `2px solid var(--accent)` inset border via `::after`
  - Hover: `opacity: 0.7`

### Developer Tray

Progress bars styled as chemical processing baths.

- **Label:** IBM Plex Mono, `0.7rem`, uppercase, `--text-faint`
- **Bars:** Flex column, `0.75rem` gap
- **Each bar:** Flex row with label (5.5rem, right-aligned), track, and percentage
- **Track:** `--surface-2` background, `1px solid var(--border)`, `22px` height
- **Fill:** Gradient from dim to full semantic color. Classes: `.fill-capture`, `.fill-refine`, `.fill-execute`, `.fill-batch`
- **Percentage:** IBM Plex Mono, `0.7rem`, `--text-faint`

### Film Strip Divider

An SVG section separator mimicking 35mm film stock.

- **Container:** `3rem` margin, centered, `max-width: 700px`
- **Film base:** `--surface` filled rectangle, full width, `36px` height
- **Sprocket holes:** Rows of small rounded rectangles (8x5px) at top and bottom edges in `--bg` color
- **Frame dividers:** Vertical lines between sprocket pairs in `--surface-3`
- **Frame numbers:** IBM Plex Mono, `6px`, `--border` color (one highlighted in `--accent`)

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--accent` (safelight red)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Warm charcoal, not cold** — backgrounds use brown-tinted near-blacks like darkroom walls, creating intimacy and analog warmth.
2. **Safelight red** — the primary accent is a deep chemical red inspired by darkroom safelight bulbs.
3. **Three-tier text** — warm parchment (--text), dim (--text-dim), faint (--text-faint).
4. **Handwritten headings** — Caveat delivers the feel of captions scrawled on the back of a Polaroid.
5. **EXIF data labels** — IBM Plex Mono for all metadata gives timestamps and settings the precision of camera data.
6. **Chemistry semantics** — safelight red (exposure), sepia amber (toning), chemical magenta (filter), developer blue (processing).
7. **Analog artifacts** — Polaroid borders, contact sheets, film strips, and developer trays bring real photographic equipment into the design.
8. **Light leak texture** — faint diagonal gradients in the hero evoke accidental light leaks that give analog photography its character.
