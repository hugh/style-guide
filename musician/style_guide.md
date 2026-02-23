# Musician / Score — Style Guide

Cream manuscript paper under warm light. A design system inspired by classical music scores — staff-line dividers, dynamic markings, rehearsal mark section cards, and fermata pause callouts for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#f5f0e6` | Page background (manuscript cream)       |
| `--surface`    | `#ece6d8` | Cards, panels, diagram containers        |
| `--surface-2`  | `#e2dac8` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#d8d0bc` | Tertiary surface, row separators         |
| `--border`     | `#c8c0a8` | Card borders, staff lines, dividers      |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#1a1810` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#5a5440` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#908870` | Labels, tempo markings, metadata                |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                   |
|-----------------|-----------|----------------------------------------|
| `--accent`      | `#1a1810` | Primary accent (Ink Black)             |
| `--accent-dim`  | `#3a3828` | Muted accent                           |
| `--capture`     | `#b83020` | Forte Red — emphasis, accents, sfz     |
| `--capture-dim` | `#882018` | Muted red                              |
| `--refine`      | `#a08020` | Brass Gold — horns, warmth, highlight  |
| `--refine-dim`  | `#786018` | Muted gold                             |
| `--execute`     | `#7a4028` | Rosewood Brown — strings, depth        |
| `--execute-dim` | `#5a2e1c` | Muted brown                            |
| `--batch`       | `#3868a0` | Cool Blue — woodwinds, clarity         |
| `--batch-dim`   | `#284878` | Muted blue                             |

---

## Typography

### Font Stack

| Role      | Family            | Google Fonts Import                               |
|-----------|-------------------|-----------------------------------------------------|
| Headings  | Playfair Display  | `Playfair+Display:ital,wght@0,400;0,600;0,700;1,400` |
| Body      | Source Sans 3     | `Source+Sans+3:wght@300;400;500;600`                 |
| Labels    | IBM Plex Mono     | `IBM+Plex+Mono:wght@400;500;600`                     |

```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&family=Source+Sans+3:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family            | Size                            | Weight | Line-height | Notes                                         |
|--------------------|-------------------|----------------------------------|--------|-------------|-----------------------------------------------|
| Hero h1            | Playfair Display  | `clamp(3rem, 8vw, 5.5rem)`     | 700    | 1.05        | Italic `<span>` in --capture for title word   |
| h2 (section)       | Playfair Display  | `2.2rem`                        | 700    | 1.15        |                                               |
| h3 (subsection)    | Playfair Display  | `1.4rem`                        | 700    | default     | `margin-top: 2.5rem`                          |
| h4 (card title)    | Source Sans 3     | `0.85rem`                       | 600    |             | Uppercase, letter-spacing: 0.06em             |
| Body paragraph     | Source Sans 3     | `0.95rem`                       | 400    | 1.7         | Color: `--text-dim`                           |
| Hero subtitle      | Source Sans 3     | `1.05rem`                       | 400    | 1.8         | Color: `--text-dim`, max-width 560px          |
| Section label      | IBM Plex Mono     | `0.75rem`                       | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono     | `0.8rem`                        | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--text-faint`  |
| Tag                | IBM Plex Mono     | `0.7rem`                        | 400    |             | `letter-spacing: 0.06em`                      |

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
- Stacked vertically: opus label, h1, subtitle, version
- **Staff lines:** Faint repeating horizontal lines via `::before`, evoking manuscript paper
- **Warm vignette:** Radial gradient darkening at edges via `::after`, like aged paper
- **Title accent:** `<span>` inside h1 uses italic `--capture` (forte red)
- **Staggered fade-up animation** on load

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Musician-specific adjustments:
- Border-radius: `3px` (subtle, refined)
- Hover uses subtle shadow: `rgba(26, 24, 16, 0.08)`
- Principle numbers use Playfair Display at `2.2rem` in `--capture`
- Light theme: cream backgrounds with dark ink text

---

## Unique Components

### Staff Divider

A five-line musical staff with treble clef symbol.

- **Container:** `50px` tall, relative positioned
- **Staff lines:** `::before` — `repeating-linear-gradient` creating 5 horizontal lines every 8px in border color
- **Clef:** Unicode treble clef (&#119070;), `2.5rem`, `--text-faint`, positioned left

### Dynamic Markings

An intensity selector styled like musical dynamics from pp to ff.

- **Layout:** Flex row, no gap, horizontal overflow
- **Level:** `1rem` padding, centered, `--surface` background, `1px solid var(--border)`
- **Mark:** Playfair Display italic, `1.4rem`, `--text-faint`
- **Name:** IBM Plex Mono, `0.6rem`, uppercase, `--text-faint`
- **Active:** `.active` class — `--capture-fill` background, `--capture-dim` border, mark in `--capture` color
- **Corners:** First level rounded left, last rounded right

### Rehearsal Mark

Section cards with boxed letter markers and tempo annotations.

- **Grid:** `repeat(auto-fill, minmax(200px, 1fr))`, `1.25rem` gap
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 3px`
- **Mark:** `2rem x 2rem` box, `2px solid var(--text)`, Playfair Display `1rem`, centered
- **Title:** Source Sans 3, `0.85rem`, weight 600, uppercase
- **Tempo:** Playfair Display italic, `0.85rem`, `--text-faint` (e.g., "Allegro ♩ = 120")
- **Description:** `0.8rem`, `--text-dim`

### Fermata Callout

A centered pause/hold component for reflective asides.

- **Container:** `--surface` background, `1px solid var(--border)`, `border-radius: 3px`, centered text
- **Symbol:** Unicode fermata (&#119056;), `2.5rem`, `--text-faint`
- **Title:** Playfair Display italic, `1.2rem`, `--text`
- **Body:** `0.88rem`, `--text-dim`, max-width 500px, centered

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--text` (ink black)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Manuscript cream** — backgrounds use warm aged-paper tones like classical sheet music.
2. **Ink black accent** — the primary text color doubles as the accent, keeping the palette restrained like printed notation.
3. **Three-tier text** — ink black (--text), sepia dim (--text-dim), parchment faint (--text-faint).
4. **Elegant serif headings** — Playfair Display delivers the refinement of engraved music title pages.
5. **Clean body text** — Source Sans 3 provides crisp readability like well-typeset program notes.
6. **Orchestral semantics** — forte red (emphasis), brass gold (warmth), rosewood brown (depth), cool blue (clarity).
7. **Musical artifacts** — staff dividers, dynamic markings, rehearsal marks, and fermata callouts bring the physical score into the design.
8. **Staff-line texture** — repeating horizontal lines in the hero evoke manuscript paper ruling.
