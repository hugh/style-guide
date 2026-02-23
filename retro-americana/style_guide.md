# Retro Americana / 1950s — Style Guide

Chrome-trimmed cream under a starburst sky. A design system inspired by 1950s diners, drive-ins, and Route 66 — checkerboard panels, jukebox selection cards, neon sign callouts, and highway shield badges for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                   |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#faf5ec` | Page background (warm diner cream)       |
| `--surface`    | `#f0ebe0` | Cards, panels, diagram containers        |
| `--surface-2`  | `#e6e0d4` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#dcd6c8` | Tertiary surface, row separators         |
| `--border`     | `#c8c0ae` | Card borders, chrome trim, dividers      |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#1c1820` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#4c4640` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#8c8478` | Labels, metadata, captions                      |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#c82028` | Primary accent (Diner Red)               |
| `--accent-dim`  | `#a01820` | Muted accent                             |
| `--capture`     | `#2a8858` | Seafoam Mint — soda fountain, fresh      |
| `--capture-dim` | `#1e6840` | Muted mint                               |
| `--refine`      | `#d09828` | Chrome Gold — jukebox, chrome trim       |
| `--refine-dim`  | `#a87818` | Muted gold                               |
| `--execute`     | `#d04838` | Hot Rod Red — danger, stop               |
| `--execute-dim` | `#a83828` | Muted red                                |
| `--batch`       | `#2850a8` | Navy Blue — classic Americana            |
| `--batch-dim`   | `#1c3c80` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                                |
|-----------|-----------------|------------------------------------------------------|
| Headings  | Righteous       | `Righteous`                                          |
| Body      | Outfit          | `Outfit:wght@300;400;500;600;700`                   |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                   |

```html
<link href="https://fonts.googleapis.com/css2?family=Righteous&family=Outfit:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                              | Weight | Line-height | Notes                                          |
|--------------------|-----------------|---------------------------------------|--------|-------------|-------------------------------------------------|
| Hero h1            | Righteous       | `clamp(2.6rem, 7vw, 5rem)`          | 400    | 1.1         | `<span>` in --accent for title word            |
| h2 (section)       | Righteous       | `1.8rem`                             | 400    | 1.2         |                                                |
| h3 (subsection)    | Righteous       | `1.15rem`                            | 400    | 1.3         | `margin-top: 2.5rem`                           |
| h4 (card title)    | Outfit          | `0.82rem`                            | 700    |             | Uppercase, letter-spacing: 0.06em              |
| Body paragraph     | Outfit          | `0.95rem`                            | 400    | 1.7         | Color: `--text-dim`                            |
| Hero subtitle      | Outfit          | `1.05rem`                            | 400    | 1.8         | Color: `--text-dim`, max-width 560px           |
| Section label      | IBM Plex Mono   | `0.75rem`                            | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                             | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--text-faint`  |
| Tag                | IBM Plex Mono   | `0.7rem`                             | 400    |             | `letter-spacing: 0.06em`, pill-shaped (20px radius) |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `2px solid var(--border)` top border
- Each section opens with a **monospace label** in the format `01 — Label`

### Full-Bleed Containers

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle, version
- **Starburst pattern:** Repeating conic gradient with thin red-tinted lines radiating from center, evoking atomic-age sunburst motifs
- **Chrome strip:** Linear gradient at the bottom edge mimicking chrome diner trim
- **Title accent:** `<span>` inside h1 uses `--accent` (diner red)
- **Staggered fade-up animation** on load

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Retro Americana adjustments:
- Border-radius: `8px` (smooth, chrome-trimmed edges)
- Hover uses subtle lift: `translateY(-1px)` with warm shadow
- Principle numbers use Righteous at `2.2rem` in `--accent`
- Tags use pill shape (`border-radius: 20px`)
- Light theme: warm cream backgrounds with dark signage text

---

## Unique Components

### Checkerboard Panel

A display panel topped with a classic black-and-white checkerboard strip.

- **Container:** `--surface` background, `2px solid var(--border)`, `border-radius: 8px`, overflow hidden
- **Strip:** `24px` height, `repeating-linear-gradient` creating 24px black-and-white squares
- **Content:** Centered text with `2rem` padding
- **Title:** Righteous, `1.4rem`, `--text`
- **Subtitle:** IBM Plex Mono, `0.7rem`, uppercase, `letter-spacing: 0.15em`, `--text-faint`

### Jukebox Card

A music selection card with chrome-gradient header and track listing.

- **Container:** `--surface` background, `2px solid var(--border)`, `border-radius: 12px`, max-width 400px
- **Header:** Linear gradient from `--surface-2` to `--surface-3`, `3px` bottom border, icon + label
- **Tracks:** List items with selection code + song/artist info
- **Track code:** Righteous, `0.85rem`, `--accent` (e.g. A1, B2)
- **Track title:** Weight 600, `0.85rem`, `--text`
- **Track artist:** `0.78rem`, `--text-faint`
- **Hover:** Background shifts to `--surface-2`

### Neon Sign

A dark-background callout with glowing neon text effect.

- **Container:** `--text` background (dark), `border-radius: 8px`, centered text
- **Neon text:** Righteous, `1.6rem`, with multi-layer `text-shadow` glow
- **Color variants:** `.neon-red`, `.neon-mint`, `.neon-gold`, `.neon-blue`
- **Subtext:** IBM Plex Mono, `0.65rem`, `letter-spacing: 0.2em`, white at 35% opacity

### Route 66 Badge

A highway shield badge as a section marker.

- **Container:** `100px x 100px`, centered
- **Shield shape:** `::before` with bottom half rounded to 50%, `3px solid var(--text)` border
- **Inner shield:** `::after` at 6px inset, same shape, `2px` border
- **Route label:** IBM Plex Mono, `0.45rem`, weight 600, uppercase
- **Number:** Righteous, `1.6rem`, `--text`

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `4px`
- Border: `1px solid var(--border)`
- Color: `--text`

---

## Footer

- Top border: `2px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Warm diner cream** — backgrounds use cream tones like a Formica countertop under fluorescent light.
2. **Diner red accent** — the primary color evokes Coca-Cola signage, red vinyl booths, and tail fins.
3. **Three-tier text** — signage black (--text), soft ink (--text-dim), faded chrome (--text-faint).
4. **Retro display headings** — Righteous delivers the rounded, optimistic signage of drive-ins and bowling alleys.
5. **Clean friendly body** — Outfit provides approachable body text with a slightly rounded, modern feel.
6. **Americana semantics** — seafoam mint (soda fountain), chrome gold (jukebox), hot rod red (danger), navy blue (classic).
7. **Roadside artifacts** — checkerboard panels, jukebox cards, neon signs, and Route 66 badges bring the open road into the design.
8. **Starburst texture** — radiating conic gradient lines in the hero evoke atomic-age sunburst motifs.
