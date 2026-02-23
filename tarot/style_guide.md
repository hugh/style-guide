# Tarot / Occult — Style Guide

A mystical occult design system — midnight indigo surfaces, gold-foil accents, celestial star fields, tarot card frames, crystal ball callouts, and zodiac markers for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--bg`         | `#0a0814` | Page background (midnight black-purple)         |
| `--surface`    | `#12101e` | Cards, panels, diagram containers               |
| `--surface-2`  | `#1a1828` | Nested surfaces, secondary panels               |
| `--surface-3`  | `#242234` | Tertiary surface, row separators                |
| `--border`     | `#36304a` | Card borders, section dividers (amethyst edge)  |

### Text

| Token          | Hex       | Usage                                           |
|----------------|-----------|--------------------------------------------------|
| `--text`       | `#e0d8f0` | Primary text, headings, bold/strong (moonlight)  |
| `--text-dim`   | `#9088a8` | Body paragraphs, descriptions (twilight grey)    |
| `--text-faint` | `#585068` | Labels, metadata, captions (shadow purple)       |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The dim variant is used for muted strokes and labels. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                       |
|-----------------|-----------|---------------------------------------------|
| `--accent`      | `#d4a830` | Primary accent (Gold Foil)                  |
| `--accent-dim`  | `#8a6e1c` | Muted gold                                  |
| `--capture`     | `#38a868` | Emerald — life, growth                      |
| `--capture-dim` | `#206840` | Muted emerald                               |
| `--refine`      | `#d4a830` | Gold — divination, insight                  |
| `--refine-dim`  | `#8a6e1c` | Muted gold                                  |
| `--execute`     | `#c83848` | Blood Ruby — danger, death                  |
| `--execute-dim` | `#802028` | Muted ruby                                  |
| `--batch`       | `#4868c8` | Sapphire — wisdom, the cosmos               |
| `--batch-dim`   | `#2c4080` | Muted sapphire                              |

---

## Typography

### Font Stack

| Role      | Family             | Google Fonts Import                                             |
|-----------|--------------------|-----------------------------------------------------------------|
| Headings  | Cinzel Decorative  | `Cinzel+Decorative:wght@400;700;900`                            |
| Body      | Crimson Pro        | `Crimson+Pro:wght@300;400;500;600;700`                          |
| Labels    | IBM Plex Mono      | `IBM+Plex+Mono:wght@400;500`                                   |

```html
<link href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@400;700;900&family=Crimson+Pro:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family             | Size                          | Weight | Line-height | Notes                                       |
|--------------------|--------------------|-------------------------------|--------|-------------|----------------------------------------------|
| Hero h1            | Cinzel Decorative  | `clamp(2.4rem, 7vw, 4.5rem)` | 900    | 1.1         | Accent-colored `<span>` glows gold.          |
| h2 (section)       | Cinzel Decorative  | `1.6rem`                      | 700    | 1.2         | `letter-spacing: 0.04em`                     |
| h3 (subsection)    | Cinzel Decorative  | `1.1rem`                      | 700    | default     | `margin-top: 2.5rem`                         |
| h4 (card title)    | Crimson Pro        | `0.85rem`                     | 600    |             | Uppercase, `letter-spacing: 0.08em`          |
| Body paragraph     | Crimson Pro        | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                          |
| Hero subtitle      | Crimson Pro        | `1.1rem`                      | 400    | 1.8         | Color: `--text-dim`, max-width 560px         |
| Card body          | Crimson Pro        | `0.82rem`                     | 400    | 1.6         | Color: `--text-dim`                          |
| Section label      | IBM Plex Mono      | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono      | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Diagram label      | IBM Plex Mono      | `0.7rem`                      | 400    |             | Uppercase, `letter-spacing: 0.12em`, color: `--text-faint` |
| Tag                | IBM Plex Mono      | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                     |
| Table header       | Crimson Pro        | `0.7rem`                      | 600    |             | Uppercase, `letter-spacing: 0.1em`, color: `--text-faint`  |
| Table cell         | Crimson Pro        | `0.82rem`                     | 400    |             | First column: `--text` + weight 600          |
| `<strong>` in body | Crimson Pro        | inherit                       | 600    |             | Color: `--text`                              |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace numeral label** in the format `01 — Label`

### Full-Bleed Containers

For diagrams or wide content that should break out of the 900px container:
- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Star field overlay:** Scattered `radial-gradient` dots via `::before` in white, gold, blue, and ruby at varying opacities — simulates a celestial night sky
- **Celestial glow:** Faint elliptical `radial-gradient` layers via `::after` in gold, sapphire, and ruby at very low opacity
- **Title glow:** The `<span>` inside h1 uses `--accent` color with `text-shadow: 0 0 30px rgba(212, 168, 48, 0.4), 0 0 60px rgba(212, 168, 48, 0.15)`
- **Staggered fade-up animation** on load:
  - Label: 0s delay
  - h1: 0.15s delay
  - Subtitle: 0.3s delay
  - Version: 0.45s delay
  - Animation: `opacity 0→1, translateY(20px→0)`, 0.8s ease-out

---

## Components

### Flow Cards (2-Column Grid)

A grid of cards used for listing related items.

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 4px`, `padding: 1.5rem`
- **Hover:** Border color changes to `--accent`, gains `box-shadow: 0 0 16px rgba(212, 168, 48, 0.12)` plus a faint inner glow (gold foil effect)
- **Top accent bar:** 3px colored bar at the top edge (via `::before`) with matching `box-shadow` glow. Color matches the card's semantic category.
- **Content:** Icon (emoji, `1.4rem`) → h4 title (uppercase) → body paragraph

### Pipeline (Horizontal Stages)

A horizontal row of connected stages showing a linear process.

- **Layout:** `display: flex`, no gap, stages stretch equally (`flex: 1`, `min-width: 140px`)
- **Stage:** `--surface` background, `1px solid var(--border)`, `padding: 1.25rem`, centered text
- **Borders:** First stage gets left border-radius `4px`, last gets right border-radius `4px`. Adjacent stages share borders (`border-left: none`).
- **Top accent:** 3px solid top border in semantic color (`.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`)
- **Content:** Step numeral (IBM Plex Mono, `0.7rem`, faint) → name (weight 600, `0.8rem`, uppercase) → description (`0.7rem`, dim)

### Principle / Numbered List

A vertical stack of numbered items with bold display numbers.

- **Layout:** Flex column, `1rem` gap
- **Item:** Flex row, `1.25rem` gap, `--surface` background, `1px solid var(--border)`, `border-radius: 4px`, `padding: 1.25rem`
- **Number:** Cinzel Decorative, `2rem`, weight 700, `--accent`, fixed `2rem` width, centered
- **Content:** h4 title (weight 600, `0.85rem`, uppercase) + body paragraph (`0.82rem`, dim)

### Callout

A highlighted aside or important note.

- Left border: `3px solid var(--accent)`
- Background: `rgba(212, 168, 48, 0.05)`
- Border-radius: `0 4px 4px 0`
- Padding: `1.5rem`
- `<strong>` within callouts uses `--accent` color (gold foil)

### Tags / Pills

Small inline labels with semantic colors.

- Font: IBM Plex Mono, `0.7rem`, `letter-spacing: 0.06em`
- Padding: `0.2em 0.6em`
- Border-radius: `3px`
- Background: transparent semantic color at 10% opacity
- Border: `1px solid` in dim semantic color
- Text color: full semantic color

### Tables

- Full width, collapsed borders
- **Header row:** Uppercase, weight 600, `0.7rem`, `letter-spacing: 0.1em`, `--text-faint`, bottom border `1px solid var(--border)`
- **Body cells:** `0.82rem`, `--text-dim`, padding `0.75rem 1rem`, bottom border `1px solid var(--surface-3)`
- **First column** in body: `--text` color, weight 600

### Diagram Containers

Wrapper for SVGs and visual figures.

- Background: `--surface`
- Border: `1px solid var(--border)`
- Border-radius: `4px`
- Padding: `2.5rem`
- `overflow-x: auto` for horizontal scroll on small screens
- Diagram label at the top in IBM Plex Mono faint text

### SVG Diagrams

- Text inside SVGs uses `font-family: 'Crimson Pro', serif`
- Node boxes: `--surface` fill, semantic color stroke (2px), `rx="12"`
- Labels inside nodes: Semantic color, weight 600, uppercase, small size (`9–10px`)
- Descriptions inside nodes: `--text-faint`, `8–9px`
- Connecting lines: Dashed (`stroke-dasharray: 4,3`), faint colored, thin (`1–1.5px`)

---

## Unique Components

### Tarot Card

A tall portrait-ratio card with an ornate double-border frame, roman numeral at top, centered symbol, and card name at bottom.

- **Outer frame** (`.tarot-card`): `aspect-ratio: 2 / 3.2`, `2px solid var(--accent)` border, `border-radius: 4px`, `padding: 6px`, `--surface` background
- **Inner frame** (`.card-inner`): `1px solid var(--accent-dim)` border, `border-radius: 2px`, flex column, aligned and justified center, with `padding: 1rem 0.75rem`
- **Star texture:** Faint radial-gradient dots via `::before` on `.card-inner` for celestial atmosphere
- **Numeral** (`.card-numeral`): IBM Plex Mono, `0.7rem`, `letter-spacing: 0.2em`, `--accent` color. Use roman numerals.
- **Symbol** (`.card-symbol`): `2.5rem` font size, flex centered in the middle area
- **Title** (`.card-title`): Cinzel Decorative, `0.7rem`, weight 700, `--accent`, uppercase, `letter-spacing: 0.08em`
- **Hover:** `translateY(-6px)` with gold box-shadow glow
- **Grid:** `.tarot-grid` — `repeat(auto-fill, minmax(180px, 1fr))`, `2rem` gap

### Crystal Ball

A circular callout panel styled as a scrying orb with radial gradient glow and sparkles.

- **Size:** `260px` width and height, `border-radius: 50%`
- **Background:** Layered radial gradients — faint gold highlight at upper-left, faint blue at lower-right, and a surface-to-bg gradient for depth
- **Border:** `2px solid var(--accent-dim)`
- **Box-shadow:** Outer gold glow at two distances (`40px` and `80px`) plus `inset 0 0 60px rgba(0,0,0,0.4)` for depth
- **Sparkles:** `::before` pseudo-element with scattered radial-gradient dots, animated with a slow `opacity` pulse over 4s
- **Gloss:** `::after` pseudo-element with a small elliptical white highlight near the top
- **Text** (`.ball-text`): Cinzel Decorative, `0.85rem`, weight 700, `--accent`, with gold text-shadow glow
- **Caption** (`.ball-caption`): IBM Plex Mono, `0.65rem`, `--text-faint`
- **Centered:** `margin: 2.5rem auto`

### Zodiac Marker

A circular badge with an astrological symbol, ornate ring border, and gold accent.

- **Size:** `56px` width and height, `border-radius: 50%`
- **Border:** `2px solid var(--accent)`
- **Ring effect:** `box-shadow: 0 0 0 4px var(--surface), 0 0 0 5px var(--accent-dim)` — creates a gap ring between the inner gold border and the outer thin gold-dim ring
- **Outer ornate ring:** `::before` pseudo-element, `inset: -8px`, `border-radius: 50%`, `1px solid var(--accent-dim)` at `0.4` opacity
- **Background:** `--surface-2`
- **Symbol:** `1.4rem`, `--accent` color
- **Section layout** (`.zodiac-section`): Flex row with marker and label. Label uses IBM Plex Mono, `0.75rem`, uppercase, `--text-faint`.

### Mystic Divider

An inline SVG section separator with a celestial moon-phase motif.

- **Pattern:** Stars — line — crescent moon — line — full moon — line — crescent moon — line — stars
- **Full moon:** Circle with 1.5px gold stroke at 0.8 opacity, filled circle inside at 0.15 opacity
- **Crescent moons:** Gold stroke circle partially masked by a bg-colored circle offset 4px to create the crescent shape
- **Lines:** Gold stroke at 0.5px, 0.3 opacity
- **Stars:** Small gold circles (r: 1–1.5) at varying opacities
- **Container:** `.mystic-divider`, centered, `max-width: 600px`, `height: 40px`

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--accent` (gold foil)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Midnight, not black** — backgrounds use deep indigo and purple-tinted near-blacks, never pure #000.
2. **Gold foil accents** — the primary accent is warm gold (#d4a830) evoking gilded tarot edges and candlelit metallic surfaces.
3. **Three-tier text** — moonlight (--text), twilight grey (--text-dim), shadow purple (--text-faint).
4. **Arcane typography** — Cinzel Decorative gives headings an ornamental, woodcut-engraved, grimoire quality.
5. **Clean serif body** — Crimson Pro provides elegant, readable body text balancing the ornate headings.
6. **Occult semantics** — emerald (life), gold (divination), blood ruby (danger), sapphire (wisdom).
7. **Ornate double borders** — tarot cards and zodiac markers use layered borders for the classic occult frame aesthetic.
8. **Celestial star fields** — the hero uses scattered radial gradients and ambient glows to simulate a night sky.
