# Cartoon Network / Animated — Style Guide

Bright white backgrounds under candy-colored lights. A design system inspired by animated TV shows — thick rounded outlines, bubbly oversized type, bouncy hover animations, speech bubbles, action badges, and episode guide cards for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                      |
|----------------|-----------|----------------------------------------------|
| `--bg`         | `#ffffff` | Page background (bright white)               |
| `--surface`    | `#f6f4fa` | Cards, panels, diagram containers            |
| `--surface-2`  | `#eeeaf6` | Nested surfaces, secondary panels            |
| `--surface-3`  | `#e4e0ee` | Tertiary surface, tag backgrounds            |
| `--border`     | `#2a2a3a` | Thick card outlines, section dividers        |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#1a1a2e` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#5a5870` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#9088a0` | Labels, episode metadata, captions              |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                 |
|-----------------|-----------|--------------------------------------|
| `--accent`      | `#ff3e8a` | Primary accent (Hot Pink)            |
| `--accent-dim`  | `#d02870` | Muted accent                         |
| `--capture`     | `#00cc88` | Candy Green — go, safe, yes          |
| `--capture-dim` | `#009966` | Muted green                          |
| `--refine`      | `#ffb020` | Candy Orange — bonus, star, alert    |
| `--refine-dim`  | `#d09010` | Muted orange                         |
| `--execute`     | `#ff4455` | Candy Red — pow, danger, boom        |
| `--execute-dim` | `#d02838` | Muted red                            |
| `--batch`       | `#4488ff` | Bright Blue — cool, chill, info      |
| `--batch-dim`   | `#2860d0` | Muted blue                           |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                      |
|-----------|-----------------|------------------------------------------|
| Headings  | Fredoka         | `Fredoka:wght@400;500;600;700`           |
| Body      | Nunito          | `Nunito:wght@400;500;600;700`            |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`        |

```html
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500;600;700&family=Nunito:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                              | Weight | Line-height | Notes                                         |
|--------------------|-----------------|---------------------------------------|--------|-------------|-----------------------------------------------|
| Hero h1            | Fredoka         | `clamp(2.8rem, 7vw, 5rem)`          | 700    | 1.1         | `<span>` in --accent for colored title word   |
| h2 (section)       | Fredoka         | `1.8rem`                             | 700    | 1.2         |                                               |
| h3 (subsection)    | Fredoka         | `1.15rem`                            | 700    | 1.3         | `margin-top: 2.5rem`                          |
| h4 (card title)    | Nunito          | `0.82rem`                            | 700    |             | Uppercase, letter-spacing: 0.06em             |
| Body paragraph     | Nunito          | `0.95rem`                            | 400    | 1.7         | Color: `--text-dim`                           |
| Hero subtitle      | Nunito          | `1.05rem`                            | 400    | 1.8         | Color: `--text-dim`, max-width 560px          |
| Section label      | IBM Plex Mono   | `0.75rem`                            | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Tag                | IBM Plex Mono   | `0.7rem`                             | 500    |             | `letter-spacing: 0.06em`, `border-radius: 20px` |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `3px solid var(--border)` top border (thick cartoon outlines)
- Each section opens with a **monospace label** in the format `01 — Label`

### Full-Bleed Containers

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle, version
- **Candy shapes:** Scattered colorful circles via `::before` at low opacity, like floating candy dots
- **Title accent:** `<span>` inside h1 uses `--accent` (hot pink)
- **Bouncy entrance:** `bounceIn` animation with `cubic-bezier(0.34, 1.56, 0.64, 1)` overshoot

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Cartoon-specific adjustments:
- Border-radius: `16px` (big bubbly roundness)
- Borders: `3px solid var(--border)` (thick cartoon outlines)
- Hover uses bouncy transform: `translateY(-4px)` with overshoot `cubic-bezier(0.34, 1.56, 0.64, 1)`
- Tags use fully rounded `border-radius: 20px` pill shape with `2px` colored borders
- Principle numbers use Fredoka at `2.2rem` in `--accent`

---

## Unique Components

### Speech Bubble

A cartoon speech bubble with a triangular tail.

- **Container:** `--surface` background, `3px solid var(--border)`, `border-radius: 24px`
- **Tail:** CSS triangle via `::after` (border-based), points down-left. Inner fill via `::before` for solid appearance
- **Text:** Fredoka, `1.1rem`, weight 500, `--text`. Strong text in `--accent`
- **Author:** IBM Plex Mono, `0.7rem`, `--text-faint`, uppercase

### Action Badge

Bold colored badges for emphasis, like comic sound effects.

- **Base:** `inline-flex`, `border-radius: 24px`, `3px solid var(--border)`, white text
- **Type:** Fredoka, `1.4rem`, weight 700, uppercase
- **Color variants:** `.ab-pink` (accent), `.ab-red` (execute), `.ab-blue` (batch), `.ab-green` (capture), `.ab-orange` (refine, dark text)
- **Hover:** `scale(1.08) rotate(-2deg)` with bouncy easing
- **Starburst variant:** `.starburst` class — `border-radius: 4px`, default `rotate(-5deg)`, shadow

### Character Card

Cartoon character cards with circular avatars and trait tags.

- **Grid:** `repeat(auto-fill, minmax(180px, 1fr))`, `1.5rem` gap
- **Card:** `--surface` background, `3px solid var(--border)`, `border-radius: 20px`, centered text
- **Avatar:** `72px` circle, `3px solid var(--border)`, emoji centered. Color tint variants: `.av-pink`, `.av-blue`, `.av-green`, `.av-orange`
- **Name:** Fredoka, `1rem`, weight 700
- **Role:** `0.82rem`, `--text-faint`
- **Tags:** Flex wrap of small pills (`border-radius: 12px`), `--surface-2` background

### Episode Guide

TV episode guide cards with color-coded top bars.

- **Grid:** `repeat(auto-fill, minmax(200px, 1fr))`, `1.25rem` gap
- **Card:** `--surface` background, `3px solid var(--border)`, `border-radius: 16px`, overflow hidden
- **Color bar:** `8px` height. Variants: `.ep-pink`, `.ep-blue`, `.ep-green`, `.ep-orange`, `.ep-red`
- **Number:** IBM Plex Mono, `0.65rem`, `--text-faint`, uppercase
- **Title:** Fredoka, `0.95rem`, weight 600
- **Description:** `0.82rem`, `--text-dim`

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.5em`
- Border-radius: `8px`
- Border: `2px solid var(--surface-3)`
- Color: `--text`

---

## Footer

- Top border: `3px solid var(--border)` (thick cartoon outline)
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Bright white base** — backgrounds use clean white like animation cels, letting candy colors pop.
2. **Hot pink accent** — the primary color channels Powerpuff Girls / Teen Titans Go energy.
3. **Three-tier text** — dark ink (--text), muted purple (--text-dim), light lavender (--text-faint).
4. **Bubbly rounded headings** — Fredoka delivers playful, oversized cartoon title energy.
5. **Friendly body text** — Nunito provides warm, rounded readability for paragraphs.
6. **Candy-color semantics** — candy green (go), candy orange (star), candy red (pow), bright blue (cool).
7. **Thick cartoon outlines** — 3px dark borders on everything create the signature animated look.
8. **Bouncy animations** — hover transforms use `cubic-bezier(0.34, 1.56, 0.64, 1)` for playful overshoot.
