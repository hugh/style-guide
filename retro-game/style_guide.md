# Retro Video Game — Style Guide

Pixel art meets CRT glow. A design system inspired by 8-bit and 16-bit era video games — chunky pixel fonts, health bar gauges, character select cards, achievement badges, and arcade continue screens for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#0c0c18` | Page background (deep CRT blue-black)    |
| `--surface`    | `#181828` | Cards, panels, diagram containers        |
| `--surface-2`  | `#202038` | Nested surfaces, stat bar backgrounds    |
| `--surface-3`  | `#282840` | Tertiary surface, row separators         |
| `--border`     | `#303050` | Card borders, panel edges                |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#e8e8f0` | Primary text, headings, strong content          |
| `--text-dim`   | `#9898b0` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#585878` | Labels, stat names, metadata                    |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                   |
|-----------------|-----------|----------------------------------------|
| `--accent`      | `#48d848` | Primary accent (Player Green)          |
| `--accent-dim`  | `#288828` | Muted accent                           |
| `--capture`     | `#48d848` | Health Green — HP, GO, safe            |
| `--capture-dim` | `#288828` | Muted green                            |
| `--refine`      | `#e8c840` | Coin Gold — treasure, stars, loot      |
| `--refine-dim`  | `#a89020` | Muted gold                             |
| `--execute`     | `#e84848` | Fire Red — damage, danger, stop        |
| `--execute-dim` | `#a82828` | Muted red                              |
| `--batch`       | `#4888e8` | Magic Blue — water, shields, mana      |
| `--batch-dim`   | `#2858a8` | Muted blue                             |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                               |
|-----------|-----------------|-----------------------------------------------------|
| Headings  | Press Start 2P  | `Press+Start+2P`                                    |
| Body      | VT323           | `VT323`                                              |
| Labels    | Press Start 2P  | (shared with headings)                               |

```html
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=VT323&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                            | Weight | Line-height | Notes                                         |
|--------------------|-----------------|----------------------------------|--------|-------------|-----------------------------------------------|
| Hero h1            | Press Start 2P  | `clamp(1.5rem, 5vw, 2.8rem)`   | 400    | 1.4         | Uppercase, accent `<span>` for title word     |
| h2 (section)       | Press Start 2P  | `1.1rem`                        | 400    | 1.5         | Uppercase                                     |
| h3 (subsection)    | Press Start 2P  | `0.8rem`                        | 400    | 1.5         | `margin-top: 2.5rem`                          |
| h4 (card title)    | Press Start 2P  | `0.55rem`                       | 400    | 1.6         | Uppercase                                     |
| Body paragraph     | VT323           | `1.15rem`                       | 400    | 1.6         | Color: `--text-dim`                           |
| Hero subtitle      | VT323           | `1.3rem`                        | 400    | 1.5         | Color: `--text-dim`, max-width 560px          |
| Section label      | Press Start 2P  | `0.5rem`                        | 400    |             | Uppercase, `letter-spacing: 0.1em`, `--text-faint` |
| Hero label         | Press Start 2P  | `0.55rem`                       | 400    |             | Uppercase, `--accent`, blinking cursor `::after` |
| Tag                | Press Start 2P  | `0.45rem`                       | 400    |             | `letter-spacing: 0.04em`                      |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `2px solid var(--border)` top border
- Each section opens with a **pixel label** in the format `01 — Label`

### Full-Bleed Containers

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: player label, h1, subtitle, version
- **Pixel grid:** Faint 32px green grid lines via `::before`, evoking graph paper / pixel grid
- **Starfield:** Scattered pixel dots in text-faint, accent, and refine via `::after`
- **Title accent:** `<span>` inside h1 uses `--accent` (player green)
- **Blinking cursor:** `::after` on hero-label blinks like a command prompt
- **Scanline overlay:** `body::after` applies faint repeating horizontal lines across the entire page
- **Staggered fade-up animation** on load

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Retro Game-specific adjustments:
- Border-radius: `0` (no rounding — everything is sharp and pixelated)
- Borders: `2px solid` (thicker, bolder borders)
- Hover glow uses green: `0 0 0 1px var(--accent), 0 0 16px rgba(72, 216, 72, 0.15)`
- Principle numbers use Press Start 2P at `1.2rem`

---

## Unique Components

### Health Bar

HP gauge with segmented fill blocks.

- **Container:** `--surface` background, `2px solid var(--border)`
- **Label:** Press Start 2P, `0.5rem`, flex row with heart icon (red `♥`)
- **Track:** `--bg` background, `2px solid var(--border)`, `24px` tall, flex row with `2px` gaps
- **Segments:** Each segment is a flex-equal block. Green (`--capture`) for filled, `--surface-2` for empty
- **Critical:** `.critical` class on segments applies red color + blink animation
- **Values:** Press Start 2P, `0.45rem`, right-aligned, faint

### Character Select Card

RPG character selection cards with portrait and stat bars.

- **Grid:** `repeat(auto-fill, minmax(220px, 1fr))`, `1.5rem` gap
- **Card:** `--surface` background, `2px solid var(--border)`, no radius
- **Portrait:** `aspect-ratio: 4/3`, `--surface-2` background, centered emoji icon, class badge in top-right corner
- **Selected:** `.selected` class adds accent border + box-shadow
- **Stats:** Rows with label (Press Start 2P, `0.35rem`, faint) and bar track. Bar fill uses width percentage. Color variants via `.bar-refine`, `.bar-execute`, `.bar-batch`
- **Hover:** Card gets accent border + green glow

### Achievement Badge

Unlocked/locked trophy badges with star ratings.

- **Grid:** `repeat(auto-fill, minmax(260px, 1fr))`, `1rem` gap
- **Badge:** Flex row with icon (2rem), info block (title, desc, stars)
- **Unlocked:** `.unlocked` class — gold dim border
- **Locked:** `.locked` class — 50% opacity, greyscale icon
- **Stars:** `star-on` in refine/gold, `star-off` in surface-3/dim

### Continue Screen

Arcade-style game over / continue countdown.

- **Container:** `--bg` background, `2px solid var(--execute)` border, centered text
- **Title:** Press Start 2P, `1.2rem`, `--execute` color, blinking animation
- **Count:** Press Start 2P, `3rem`, `--text` color (the countdown number)
- **Prompt:** Press Start 2P, `0.5rem`, `--text-faint`
- **Credits:** Press Start 2P, `0.45rem`, `--refine` color

---

## Inline Code

- Font: VT323, `1.1rem`
- Background: `--surface-2`
- Padding: `0.1em 0.4em`
- Border-radius: `0`
- Border: `1px solid var(--border)`
- Color: `--accent` (player green)

---

## Footer

- Top border: `2px solid var(--border)`
- Padding: `3rem 0`
- Centered text in VT323, `0.95rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **CRT blue-black** — backgrounds use cool blue-tinted near-blacks like a powered-on CRT monitor.
2. **Player green** — the primary accent is a vivid 8-bit green inspired by health bars and "GO" signals.
3. **Three-tier text** — bright pixel white (--text), dim (--text-dim), faint (--text-faint).
4. **Chunky pixel headings** — Press Start 2P delivers authentic 8-bit title screen typography.
5. **Terminal body text** — VT323 provides readable monospace text with retro CRT character.
6. **Game semantics** — health green (HP/safe), coin gold (treasure), fire red (damage), magic blue (mana).
7. **Zero border-radius** — no rounded corners anywhere, keeping everything sharp and blocky like pixel art.
8. **Scanline overlay** — faint horizontal lines across the entire page simulate a CRT monitor.
