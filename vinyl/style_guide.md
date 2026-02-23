# Vinyl / Record Store — Style Guide

Rich black wax under warm shelf-light. A design system inspired by vinyl record shops — LP sleeve cards, groove-line dividers, crate-dig tabs, and liner note tracklists for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#0e0e0c` | Page background (rich vinyl black)       |
| `--surface`    | `#1a1918` | Cards, panels, diagram containers        |
| `--surface-2`  | `#242220` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#2e2c28` | Tertiary surface, row separators         |
| `--border`     | `#3a3830` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#f0e8d0` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#a09878` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#686050` | Labels, catalog numbers, metadata               |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                   |
|-----------------|-----------|----------------------------------------|
| `--accent`      | `#d8a030` | Primary accent (Shelf Amber)           |
| `--accent-dim`  | `#a07820` | Muted accent                           |
| `--capture`     | `#d8a030` | Shelf Amber — discovery, warmth        |
| `--capture-dim` | `#a07820` | Muted amber                            |
| `--refine`      | `#e07830` | Sleeve Orange — packaging, design      |
| `--refine-dim`  | `#a85820` | Muted orange                           |
| `--execute`     | `#c83030` | Label Red — branding, identity         |
| `--execute-dim` | `#882020` | Muted red                              |
| `--batch`       | `#4080b8` | Cool Wax Blue — pressing, production   |
| `--batch-dim`   | `#285888` | Muted blue                             |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                               |
|-----------|-----------------|-----------------------------------------------------|
| Headings  | Bebas Neue      | `Bebas+Neue`                                        |
| Body      | Inter           | `Inter:wght@300;400;500;600`                        |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                    |

```html
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Inter:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                            | Weight | Line-height | Notes                                         |
|--------------------|-----------------|----------------------------------|--------|-------------|-----------------------------------------------|
| Hero h1            | Bebas Neue      | `clamp(3.5rem, 10vw, 7rem)`    | 400    | 0.95        | Uppercase, accent `<span>` for title word     |
| h2 (section)       | Bebas Neue      | `2.4rem`                        | 400    | 1.1         | Uppercase, letter-spacing: 0.04em             |
| h3 (subsection)    | Bebas Neue      | `1.6rem`                        | 400    | default     | `margin-top: 2.5rem`                          |
| h4 (card title)    | Inter           | `0.85rem`                       | 600    |             | Uppercase, letter-spacing: 0.06em             |
| Body paragraph     | Inter           | `0.95rem`                       | 400    | 1.7         | Color: `--text-dim`                           |
| Hero subtitle      | Inter           | `1.05rem`                       | 400    | 1.8         | Color: `--text-dim`, max-width 560px          |
| Section label      | IBM Plex Mono   | `0.75rem`                       | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                        | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--accent`      |
| Tag                | IBM Plex Mono   | `0.7rem`                        | 400    |             | `letter-spacing: 0.06em`                      |

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

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: RPM label, h1, subtitle, version
- **Shelf-light glow:** Faint radial gradients in amber, orange, and red via `::before`, simulating warm incandescent lighting
- **Groove texture:** Concentric circle pattern via `::after` using `repeating-radial-gradient`, evoking the micro-grooves of a vinyl record
- **Title accent:** `<span>` inside h1 uses `--accent` (shelf amber)
- **Staggered fade-up animation** on load

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Vinyl-specific adjustments:
- Border-radius: `4px`
- Hover glow uses amber: `rgba(216, 160, 48, 0.12)`
- Principle numbers use Bebas Neue at `2.2rem`

---

## Unique Components

### LP Sleeve

Album sleeve cards with square art and vinyl peeking out.

- **Grid:** `repeat(auto-fill, minmax(200px, 1fr))`, `1.5rem` gap
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 4px`
- **Art area:** Square `aspect-ratio: 1`, `--surface-2` background, centered icon
- **Vinyl peek:** `::after` pseudo-element — `60x60px` circle in `--bg` with `--surface-3` border, positioned right edge. Slides in on hover
- **Hover:** Card lifts `translateY(-3px)` with deeper shadow
- **Info:** Title (Inter, 600, 0.82rem), artist (0.75rem, dim), catalog metadata (IBM Plex Mono, 0.6rem, faint)

### Groove Divider

A circular section separator with concentric grooves.

- **Container:** `120x120px`, centered, `border-radius: 50%`, `--bg` background
- **Grooves:** `::before` — `repeating-radial-gradient` of thin lines every 6–7px in border color at 40% opacity
- **Center label:** `::after` — `20x20px` circle in `--accent` with `--bg` border

### Crate Tabs

Genre/category selectors like record store crate dividers.

- **Layout:** Flex row, no gap, horizontal overflow scroll
- **Tab:** `0.75rem 1.5rem` padding, Bebas Neue `1rem`, uppercase, `--text-faint`, `--surface` background, `1px solid var(--border)`
- **Active tab:** `--accent` color, `--surface-2` background, `2px solid var(--accent)` bottom border
- **Corners:** First tab rounded top-left, last tab rounded top-right

### Liner Notes

A tracklist component styled like LP sleeve back cover.

- **Container:** `--surface` background, `1px solid var(--border)`, `border-radius: 4px`
- **Header:** `--surface-2` background, flex row with Bebas Neue title and IBM Plex Mono catalog number
- **Tracks:** Flex rows with track number (mono, 0.65rem, faint), name (Inter, 500, text), duration (mono, 0.65rem, faint)
- **Row separators:** `1px solid var(--surface-3)`
- **Footer:** IBM Plex Mono, `0.6rem`, faint — recording credits and copyright

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--accent` (shelf amber)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Rich black wax** — backgrounds use warm brown-tinted near-blacks like the surface of a vinyl record.
2. **Shelf-light amber** — the primary accent is a warm amber inspired by incandescent record store lighting.
3. **Three-tier text** — warm cream (--text), dim (--text-dim), faint (--text-faint).
4. **Bold condensed headings** — Bebas Neue delivers tall, narrow uppercase type echoing album spines and poster typography.
5. **Clean body text** — Inter provides crisp readability like well-typeset gatefold liner notes.
6. **Record store semantics** — shelf amber (discovery), sleeve orange (packaging), label red (branding), cool wax blue (pressing).
7. **Vinyl artifacts** — LP sleeves, groove dividers, crate tabs, and liner notes bring the physical record store experience into the design.
8. **Groove texture** — concentric circle patterns in the hero evoke the micro-grooves that carry the music on vinyl.
