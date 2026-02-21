# Train Station — Style Guide

A vintage railway design system with warm dark surfaces, brass and iron accents, departures boards, ticket stubs, route maps, and the timeless elegance of a grand terminus. Intended for timetables, service documents, operational guides, and any content that benefits from structured, status-driven presentation.

---

## Color Palette

### Station Surfaces (Backgrounds)

| Token          | Hex       | Usage                                  |
|----------------|-----------|----------------------------------------|
| `--bg`         | `#1c1a17` | Page background (warm brown-black)     |
| `--surface`    | `#262320` | Cards, panels, departures rows         |
| `--surface-2`  | `#302c28` | Nested surfaces, ticket backgrounds    |
| `--surface-warm` | `#2a2520` | Subtle warm highlight areas          |
| `--border`     | `#3d3830` | Borders, dividers                      |
| `--border-light` | `#4e4840` | Lighter borders for emphasis         |

### Text — Timetable Cream

| Token          | Hex       | Usage                                  |
|----------------|-----------|----------------------------------------|
| `--cream`      | `#f0e8d8` | Primary — headings, station names      |
| `--cream-dim`  | `#b0a890` | Body paragraphs, descriptions          |
| `--cream-faint`| `#706858` | Labels, metadata, platform numbers     |

### Brass & Iron (Material Accents)

| Token          | Hex       | Usage                                   |
|----------------|-----------|------------------------------------------|
| `--brass`      | `#c8a84c` | Primary accent — h3, platform numbers, emphasis |
| `--brass-dim`  | `#8a7430` | Muted brass, dim labels, hero label      |
| `--brass-fill` | `rgba(200,168,76,0.07)` | Callout/tag backgrounds    |
| `--iron`       | `#8a9098` | Secondary accent — structural elements   |
| `--iron-dim`   | `#58606a` | Muted iron, borders                      |
| `--iron-fill`  | `rgba(138,144,152,0.07)` | Iron tag backgrounds      |

### Signal Colours

Each has full, dim, and fill (7% opacity) variants.

| Token           | Hex       | Signal    | Typical Use              |
|-----------------|-----------|-----------|--------------------------|
| `--signal-red`  | `#c84040` | Danger    | Cancellations, disruption|
| `--signal-green`| `#4a9858` | Clear     | On time, good service    |
| `--signal-amber`| `#d0982c` | Caution   | Delays, planned changes  |
| `--midnight`    | `#4878a8` | Night     | Night services, special  |

---

## Typography

### Font Stack

| Role      | Family              | Google Fonts Import                              |
|-----------|---------------------|--------------------------------------------------|
| Headings  | Stint Ultra Expanded| `Stint+Ultra+Expanded`                           |
| Body      | Libre Franklin      | `Libre+Franklin:ital,wght@0,300;0,400;0,500;0,600;0,700;1,300;1,400` |
| Mono      | Inconsolata         | `Inconsolata:wght@400;500;600`                   |

```html
<link href="https://fonts.googleapis.com/css2?family=Stint+Ultra+Expanded&family=Libre+Franklin:ital,wght@0,300;0,400;0,500;0,600;0,700;1,300;1,400&family=Inconsolata:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale

| Element        | Family              | Size                          | Weight | Notes                        |
|----------------|---------------------|-------------------------------|--------|------------------------------|
| Hero h1        | Stint Ultra Expanded| `clamp(2.4rem, 6.5vw, 4.2rem)` | 400  | Naturally wide letterform    |
| Section h2     | Stint Ultra Expanded| `1.6rem`                      | 400    |                              |
| Subsection h3  | Libre Franklin      | `1.05rem`                     | 600    | Uppercase, `letter-spacing: 0.1em`, color: `--brass` |
| Card title h4  | Libre Franklin      | `0.85rem`                     | 600    |                              |
| Body           | Libre Franklin      | `0.92rem`                     | 400    | Color: `--cream-dim`         |
| Platform num   | Stint Ultra Expanded| `1.4rem`                      | 400    | Color: `--brass-dim`         |
| Section label  | Inconsolata         | `0.65rem`                     | 400    | Uppercase, `letter-spacing: 0.2em` |
| Tag            | Inconsolata         | `0.6rem`                      | 400    | Uppercase, `letter-spacing: 0.08em` |

**Key convention:** Stint Ultra Expanded has built-in width — no extra letter-spacing needed. H3 uses Libre Franklin uppercase with tracking for a brass-engraved feel. Labels and tags use Inconsolata for a timetable/ticker-tape aesthetic.

---

## Layout

- **Container:** max-width 880px, centered, 2rem horizontal padding
- **Sections:** 5rem vertical padding, `1px solid var(--border)` top divider
- **Border radius:** 0 everywhere — sharp corners, industrial and architectural
- **No shadows** — depth from surface colour layering
- **Full-bleed:** max-width 1040px for diagram containers

---

## Hero Section

- Full viewport, flex-centered, warm-dark background
- Subtle radial brass glow via `::before` pseudo-element
- Accent `<span>` in `--brass`
- Hero label: Libre Franklin, uppercase, wide tracking, `--brass-dim`
- Staggered fade-up animation

---

## Components

### Departures Board

The signature unique component — a timetable display inspired by split-flap departure indicators.

- **Header:** `--surface-2` background, Libre Franklin uppercase, `--brass` text, board clock in Inconsolata
- **Rows:** CSS Grid with 4 columns (`80px 1fr 120px 100px`), `--surface` background
- **Status classes:** `.on-time` (signal-green), `.delayed` (signal-amber), `.cancelled` (signal-red), `.boarding` (brass)
- **Responsive:** Platform column hides at 640px, grid shrinks to 3 columns

### Route Stops

Linear journey component with station dots at connection points.

- Flex row of route-stop cells, each with a brass top-rail (`::before`)
- Station dot (`::after`): 8px circle, `--surface` fill with `2px solid --brass` border
- Three lines per stop: time (Inconsolata, faint), station name (Libre Franklin, cream), note (faint)
- Last stop has no dot (journey terminus)

### Ticket Stub

Inline ticket component with punched-hole edges.

- `inline-flex`, `--surface-2` background, bordered
- Punched holes: 12px circles via `::before` and `::after`, background-coloured to create the cutout illusion
- From/To sections with tiny Inconsolata label and Libre Franklin station name
- Arrow separator in `--brass-dim`
- Class indicator: Stint Ultra Expanded in `--brass`, left-border separated

### Platform Cards (2-Column Grid)

- **Grid:** 2 columns, `1.25rem` gap
- **Card:** `--surface` bg, `1px` border, sharp corners, `1.5rem` padding
- **Top accent bar:** 3px, colour from class (`brass`, `iron`, `signal-red`, `signal-green`, `signal-amber`, `midnight`)
- **Platform number:** Stint Ultra Expanded, `1.4rem`, `--brass-dim`

### Callout Variants

| Variant    | Class                | Border Colour    | Background          |
|------------|----------------------|------------------|---------------------|
| Default    | `.callout`           | `--brass`        | `--brass-fill`      |
| Service    | `.callout.service`   | `--signal-amber` | `--signal-amber-fill` |
| Disruption | `.callout.disruption`| `--signal-red`   | `--signal-red-fill` |
| Running    | `.callout.running`   | `--signal-green` | `--signal-green-fill` |

Structure: `1px` border, `3px` coloured left border, matching fill background.

### Numbered List

- Vertical stack with shared borders (zero gap, `border-top: none` on siblings)
- Numbers: Stint Ultra Expanded, `1.4rem`, `--brass-dim`
- Sharp corners throughout

### Tags

- Inconsolata, `0.6rem`, uppercase, letter-spaced
- Bordered with `1px` solid dim colour, fill background, sharp corners
- Prefix: `t-` (e.g., `t-brass`, `t-iron`, `t-signal-red`)

### Tables

- Full width, collapsed borders
- **Headers:** Inconsolata, uppercase, `0.62rem`, letter-spaced, `--cream-faint`
- **Cells:** `0.85rem`, `--cream-dim`, `1px` bottom border
- **First column:** `--cream`, weight 500

### Ornamental Rule

- Centred decorative divider: `— ◆ —`
- `--brass-dim` colour, wide letter-spacing

### Diagram Container

- `--surface` background, `1px` border, sharp corners
- Label in Inconsolata, small uppercase
- SVG text in Libre Franklin

---

## Comparison with All Systems

| Aspect          | Vesper            | Excalidraw        | Engineer            | Mathematician       | Physicist            | Train Station         |
|-----------------|-------------------|-------------------|---------------------|---------------------|----------------------|-----------------------|
| Theme           | Dark (purple)     | Light (white)     | Dark (navy)         | Dark (green)        | Dark (void/black)    | Dark (warm brown)     |
| Background      | Flat              | Flat              | Grid overlay        | Flat                | Flat                 | Flat                  |
| Border radius   | 10–16px           | 8px               | 0                   | 0                   | 4px                  | 0                     |
| Heading font    | DM Serif Display  | Caveat            | Barlow Condensed    | EB Garamond         | Space Grotesk        | Stint Ultra Expanded  |
| Body font       | DM Sans           | Nunito            | IBM Plex Sans       | Source Serif 4      | Inter                | Libre Franklin        |
| Mono font       | JetBrains Mono    | Fira Code         | IBM Plex Mono       | JetBrains Mono      | Space Mono           | Inconsolata           |
| Letter-spacing  | Normal            | Normal            | Positive (wide)     | Normal              | Negative (tight)     | Natural (expanded)    |
| Primary accent  | Purple #c4a0ff    | (multi-color)     | Cyan #4fc3f7        | Yellow #f0d060      | Cyan #22d3ee         | Brass #c8a84c         |
| Color model     | 4 semantic        | 8 stroke + fill   | 1 + 4 status        | 5 chalk             | 1 primary + 5 spectrum| 2 material + 3 signal |
| Unique elements | —                 | Sticky notes      | Stamps, title block | Theorem/proof, QED  | Readout panel, spectrum bar | Departures board, ticket stub |
| Vibe            | Editorial         | Whiteboard        | Technical           | Academic            | Laboratory           | Railway               |
