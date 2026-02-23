# Western / Wanted Poster — Style Guide

Sun-bleached parchment under a desert sky. A design system inspired by the Wild West — wanted poster cards, sheriff badge markers, branding-iron dividers, and saloon-door panels for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#f0e4d0` | Page background (sun-bleached parchment) |
| `--surface`    | `#e6dac4` | Cards, panels, diagram containers        |
| `--surface-2`  | `#dcd0b4` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#d0c4a4` | Tertiary surface, row separators         |
| `--border`     | `#b8a880` | Card borders, rope lines, dividers       |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#2c2014` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#5c4830` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#907860` | Labels, bounty metadata, captions               |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#8b3010` | Primary accent (Burnt Sienna)            |
| `--accent-dim`  | `#6a2408` | Muted accent                             |
| `--capture`     | `#4a7848` | Cactus Green — frontier, money           |
| `--capture-dim` | `#345834` | Muted green                              |
| `--refine`      | `#c89020` | Dusty Gold — badge, treasure, sunset     |
| `--refine-dim`  | `#a07018` | Muted gold                               |
| `--execute`     | `#a82818` | Wanted Red — danger, bounty              |
| `--execute-dim` | `#801c10` | Muted red                                |
| `--batch`       | `#4870a0` | Denim Blue — sky, water, calm            |
| `--batch-dim`   | `#305478` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                                |
|-----------|-----------------|------------------------------------------------------|
| Headings  | Rye             | `Rye`                                                |
| Body      | Lora            | `Lora:ital,wght@0,400;0,500;0,600;0,700;1,400`    |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                   |

```html
<link href="https://fonts.googleapis.com/css2?family=Rye&family=Lora:ital,wght@0,400;0,500;0,600;0,700;1,400&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                              | Weight | Line-height | Notes                                          |
|--------------------|-----------------|---------------------------------------|--------|-------------|-------------------------------------------------|
| Hero h1            | Rye             | `clamp(2.4rem, 7vw, 4.5rem)`        | 400    | 1.1         | `<span>` in --accent for title word            |
| h2 (section)       | Rye             | `1.8rem`                             | 400    | 1.2         |                                                |
| h3 (subsection)    | Rye             | `1.15rem`                            | 400    | 1.3         | `margin-top: 2.5rem`                           |
| h4 (card title)    | Lora            | `0.82rem`                            | 700    |             | Uppercase, letter-spacing: 0.06em              |
| Body paragraph     | Lora            | `0.95rem`                            | 400    | 1.7         | Color: `--text-dim`                            |
| Hero subtitle      | Lora            | `1.05rem`                            | 400    | 1.8         | Color: `--text-dim`, max-width 560px           |
| Section label      | IBM Plex Mono   | `0.75rem`                            | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                             | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--text-faint`  |
| Tag                | IBM Plex Mono   | `0.7rem`                             | 400    |             | `letter-spacing: 0.06em`                       |

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
- **Woodgrain lines:** Repeating horizontal lines via `::before`, evoking weathered wood plank texture
- **Sun-bleached vignette:** Radial gradient darkening at edges via `::after`
- **Title accent:** `<span>` inside h1 uses `--accent` (burnt sienna)
- **Staggered fade-up animation** on load

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Western-specific adjustments:
- Border-radius: `2px` (rough, rustic edges)
- Hover uses warm shadow: `rgba(44, 32, 20, 0.1)`
- Principle numbers use Rye at `2.2rem` in `--accent`
- Light theme: parchment backgrounds with dark ink text

---

## Unique Components

### Wanted Poster

A classic wanted poster card with double-border frame, portrait, and reward.

- **Container:** `--surface` background, `4px solid var(--border)`, `border-radius: 2px`, centered text
- **Double border:** `::before` creates inner `2px` border at `4px` inset
- **Header:** Rye, `clamp(1.8rem, 5vw, 3rem)`, `--execute` red, `letter-spacing: 0.1em`
- **Subheader:** Rye, `0.85rem`, `--text`, `letter-spacing: 0.15em`, bottom border
- **Portrait:** `140px` square, `--surface-2` background, `3px solid var(--border)`, centered emoji
- **Name:** Rye, `1.3rem`, `--text`
- **Description:** `0.88rem`, `--text-dim`, max-width 400px
- **Reward:** Rye, `1.6rem`, `--refine` gold, top border, with IBM Plex Mono label

### Sheriff Badge

A star-shaped badge element as a section marker.

- **Container:** `100px x 100px`, centered
- **Star shape:** Two overlapping rotated squares (0° and 45°) via `::before`/`::after`, `--refine` gold fill
- **Center:** `44px` circle, `--surface` background, `--refine-dim` border
- **Text:** IBM Plex Mono, `0.5rem`, weight 600, `--refine-dim`, uppercase

### Branding Divider

A decorative horizontal divider with a centered motif.

- **Container:** Centered text, relative positioned
- **Line:** Full-width `2px` horizontal line via `::before` at 50%
- **Mark:** Inline-block Rye text in `--accent`, `--bg` background padding to "cut" the line, `1.2rem`

### Saloon Panel

A split two-column panel with swinging-door aesthetic.

- **Grid:** `1fr 1fr`, collapses to single column on mobile
- **Doors:** `--surface` background, `2px solid var(--border)`, first rounded left, second rounded right
- **Hinges:** Gold dots (`--refine`) positioned at top and bottom of the center gap via `::before`/`::after`
- **Title:** Rye, `0.95rem`, `--text`
- **Body:** `0.85rem`, `--text-dim`

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `2px`
- Border: `1px solid var(--border)`
- Color: `--text`

---

## Footer

- Top border: `2px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Sun-bleached parchment** — backgrounds use warm sandy tones like weathered wanted posters nailed to a post.
2. **Burnt sienna accent** — the primary color evokes branding irons, leather, and desert heat.
3. **Three-tier text** — dark wood (--text), worn ink (--text-dim), faded marking (--text-faint).
4. **Saloon display headings** — Rye delivers the ornate, Old West signage typography of frontier towns.
5. **Clean body serif** — Lora provides readable body text like a well-set territorial gazette.
6. **Frontier semantics** — cactus green (frontier), dusty gold (treasure), wanted red (danger), denim blue (sky).
7. **Western artifacts** — wanted posters, sheriff badges, branding dividers, and saloon panels bring the frontier into the design.
8. **Woodgrain texture** — repeating horizontal lines in the hero evoke weathered plank boards.
