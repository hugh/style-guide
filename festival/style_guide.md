# Music Festival / Concert Poster — Style Guide

Psychedelic gradients and bold layered type. Dark backgrounds with vibrant multi-color gradients (sunset pinks, electric purples, hot oranges). A concert poster come to life as a single-page design system.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#0c0814` | Page background (deep purple-black)      |
| `--surface`    | `#14101e` | Cards, panels, diagram containers        |
| `--surface-2`  | `#1c1828` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#242032` | Tertiary surface, row separators         |
| `--border`     | `#362e48` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#f0e8ff` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#a898c0` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#685880` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Colors are inspired by festival lighting and stage effects.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#ff6b2b` | Primary accent (Hot Orange)              |
| `--accent-dim`  | `#d85020` | Muted accent                             |
| `--capture`     | `#ff2d8a` | Electric Pink — headliners, energy       |
| `--capture-dim` | `#d02070` | Muted pink                               |
| `--refine`      | `#ff6b2b` | Sunset Orange — warmth, fire             |
| `--refine-dim`  | `#d85020` | Muted orange                             |
| `--execute`     | `#a040ff` | Vivid Purple — stage lights, VIP         |
| `--execute-dim` | `#8030d0` | Muted purple                             |
| `--batch`       | `#00d4ff` | Bright Cyan — cool, contrast, info       |
| `--batch-dim`   | `#00a8cc` | Muted cyan                               |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                                          |
|-----------|---------------|--------------------------------------------------------------|
| Headings  | Bebas Neue    | `Bebas+Neue`                                                 |
| Body      | Inter         | `Inter:wght@300;400;500;600;700`                             |
| Labels    | IBM Plex Mono | `IBM+Plex+Mono:wght@400;500;600`                            |

### Type Scale & Weights

| Element            | Family        | Size                          | Weight | Line-height | Notes                                     |
|--------------------|---------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Bebas Neue    | `clamp(3.5rem, 10vw, 7rem)`  | 400    | 0.95        | Uppercase, `letter-spacing: 0.02em`        |
| h2 (section)       | Bebas Neue    | `2.8rem`                      | 400    | 1.0         | Uppercase, `letter-spacing: 0.03em`        |
| h3 (subsection)    | Bebas Neue    | `1.6rem`                      | 400    | 1.1         | Uppercase, `margin-top: 2.5rem`            |
| h4 (card title)    | Inter         | `0.78rem`                     | 700    |             | Uppercase, `letter-spacing: 0.08em`        |
| Body paragraph     | Inter         | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`        |
| Tag                | IBM Plex Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |

---

## Layout

- Container max-width: **900px**, centered, `2rem` horizontal padding
- Section padding: `5rem` vertical, `1px solid var(--border)` top border
- Section label format: `01 — Label`
- Full-bleed max-width: **1100px**
- Border radius: **8px** (friendly/modern)

---

## Hero Section

- Full viewport height, flex-centered
- **Psychedelic gradient:** `::before` creates overlapping radial gradients in pink, orange, purple, and cyan
- **Scanline texture:** `::after` creates subtle horizontal lines
- Hero h1 uses gradient text (pink-to-orange-to-purple) via `background-clip: text`
- Staggered fade-up animation on load

---

## Standard Components

### Flow Cards
- 2-column grid (`.flow-grid`)
- Semantic top-bar colors via `.capture`, `.refine`, `.execute`, `.batch`, `.accent`
- `8px` border-radius, surface background, border

### Pipeline
- Horizontal stages (`.pipeline` > `.pipe-stage`)
- Stage names in Bebas Neue, numbers in IBM Plex Mono
- Color variants: `.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`

### Callout
- Left border in accent color, faint orange background
- Strong text inherits accent color

### Tags
- Pill-shaped inline labels: `.tag.t-capture`, `.tag.t-refine`, `.tag.t-execute`, `.tag.t-batch`
- IBM Plex Mono, uppercase, bordered

### Info Table
- Full-width, collapse borders
- Mono headers, dim body, first-column bold

### Diagram Wrap
- Surface background, border, `8px` radius
- `.full-bleed` expands to 1100px
- SVG text uses Inter, dashed connections (`stroke-dasharray: 4,3`), `rx="12"` rounded corners

### Principle List
- Numbered list with large Bebas Neue numbers in accent color
- Surface card background per principle

---

## Unique Components

### Lineup Poster

A card mimicking a festival lineup poster with a multi-color gradient background.

- **Container:** Gradient overlay on `--surface`, `border-radius: 8px`, centered text
- **Structure:**
  - `.lineup-date` — IBM Plex Mono, small caps, date and location
  - `.lineup-headliner` — Bebas Neue, `clamp(3rem, 8vw, 5rem)`, biggest name
  - `.lineup-tier-2` — Bebas Neue, `clamp(1.6rem, 4vw, 2.4rem)`, second-tier acts separated by bullet spans
  - `.lineup-tier-3` — Inter, `0.85rem`, third-tier acts, separated by bullet spans
  - `.lineup-venue` — IBM Plex Mono, venue details at bottom
- Tiers separated by thin semi-transparent rules

### Wristband Badge

An inline badge shaped like a fabric festival wristband.

- **Container:** `border-radius: 100px` (full pill), repeating stripe texture via `background-image`
- **Clasp dot:** `::before` pseudo-element creates a small circle on the left
- **Variants:**
  - `.wb-pink` — Electric pink (`--capture`)
  - `.wb-orange` — Sunset orange (`--refine`)
  - `.wb-purple` — Vivid purple (`--execute`)
  - `.wb-cyan` — Bright cyan (`--batch`), dark text
  - `.wb-vip` — Gradient from pink to orange
- Text: IBM Plex Mono, weight 600, uppercase, white (or dark on cyan)

### Ticket Stub Divider

A horizontal divider that looks like a perforated ticket tear line.

- **Structure:** Flex container with `::before` and `::after` pseudo-elements creating dashed lines
- **Center text:** `.ticket-text` in Bebas Neue, e.g. "ADMIT ONE" or "SECTION BREAK"
- **Perforation dots:** `.perf-dot.left` and `.perf-dot.right` positioned at the ends
- Max-width: `600px`, centered

### Stage Card

A schedule card for a festival stage with time slots.

- **Container:** `--surface`, `border-radius: 8px`, overflow hidden
- **Header:** `.stage-header` with stage name (Bebas Neue) and day tag (IBM Plex Mono), color-coded top stripe
- **Color variants:** `.sc-pink`, `.sc-orange`, `.sc-purple`, `.sc-cyan`
- **Slots:** `.stage-slot` rows with:
  - `.slot-time` — IBM Plex Mono, 6rem width, faint color
  - `.slot-artist` — Inter, weight 600, primary text
  - `.slot-label` — IBM Plex Mono, small tag showing duration or "now"
- **Active slot:** `.stage-slot.active` gets accent-tinted background, left border, and highlighted time

---

## Summary of Key Patterns

1. **Dark purple-black backgrounds** — deep midnight tones that maximize contrast for vivid festival colors.
2. **Psychedelic gradient hero** — overlapping radial gradients in pink, orange, purple, and cyan.
3. **Bold poster typography** — Bebas Neue in large sizes delivers condensed, uppercase poster impact.
4. **Four-color energy** — electric pink, sunset orange, vivid purple, bright cyan clash vibrantly.
5. **Festival identity components** — lineup posters, wristbands, ticket stubs, and stage cards.
6. **Fabric wristband texture** — repeating thin stripes with clasp dot for authentic wristband feel.
7. **Schedule-focused stage cards** — time-slot grids with active-set highlighting for at-a-glance reading.
8. **Perforated ticket dividers** — dashed tear lines with "ADMIT ONE" text evoke physical tickets.
