# Alchemist — Style Guide

A mystical design system of dark parchment and gold leaf — ornamental drop caps, recipe cards, transmutation circles, and manuscript dividers for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#1a1510` | Page background (dark parchment)         |
| `--surface`    | `#221c14` | Cards, panels, diagram containers        |
| `--surface-2`  | `#2a2218` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#342a1e` | Tertiary surface, row separators         |
| `--border`     | `#4a3c2a` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#e8dcc8` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#a89878` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#6e5e48` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Colors are inspired by classical alchemical substances.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#c8a030` | Primary accent (Gold Leaf)               |
| `--accent-dim`  | `#a08020` | Muted accent                             |
| `--capture`     | `#4a9858` | Viridian Green — growth, verdant         |
| `--capture-dim` | `#387842` | Muted green                              |
| `--refine`      | `#c8a030` | Gold — transmutation, value              |
| `--refine-dim`  | `#a08020` | Muted gold                               |
| `--execute`     | `#c04030` | Cinnabar Red — mercury, danger           |
| `--execute-dim` | `#a03020` | Muted red                                |
| `--batch`       | `#3868a8` | Lapis Blue — wisdom, knowledge           |
| `--batch-dim`   | `#284888` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                                          |
|-----------|---------------|--------------------------------------------------------------|
| Headings  | Cinzel        | `Cinzel:wght@400;500;600;700;800;900`                        |
| Body      | Crimson Pro   | `Crimson+Pro:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400;1,500` |
| Labels    | IBM Plex Mono | `IBM+Plex+Mono:wght@400;500;600`                            |

```html
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;500;600;700;800;900&family=Crimson+Pro:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400;1,500&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family        | Size                          | Weight | Line-height | Notes                                     |
|--------------------|---------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Cinzel        | `clamp(2.5rem, 7vw, 4.5rem)` | 800    | 1.1         | `letter-spacing: 0.04em`                   |
| h2 (section)       | Cinzel        | `1.75rem`                     | 700    | 1.2         | `letter-spacing: 0.02em`                   |
| h3 (subsection)    | Cinzel        | `1.1rem`                      | 700    | 1.25        | `letter-spacing: 0.02em`, `margin-top: 2.5rem` |
| h4 (card title)    | Crimson Pro   | `0.82rem`                     | 600    |             | Uppercase, `letter-spacing: 0.12em`        |
| Body paragraph     | Crimson Pro   | `1rem`                        | 400    | 1.75        | Color: `--text-dim`                        |
| Hero subtitle      | Crimson Pro   | `1.1rem`                      | 400    | 1.8         | Italic, color: `--text-dim`, max-width 540px |
| Card body          | Crimson Pro   | `0.9rem`                      | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Tag                | IBM Plex Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`, `border-radius: 2px` |

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
- Stacked vertically: label, h1, subtitle paragraph (italic), version tag
- **Illuminated glow:** `::before` pseudo-element creates a 400px radial gradient in faint gold
- **Ornamental circle:** `::after` pseudo-element draws a 300px circle outline in faint gold
- **Title accent:** The `<span>` inside h1 uses `--accent` color (gold leaf)
- **Staggered fade-up animation** on load (0s, 0.15s, 0.3s, 0.45s delays)

---

## Components

### Flow Cards (2-Column Grid)

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 4px`, `padding: 1.5rem`
- **Top accent bar:** 3px colored bar via `::before`

### Pipeline (Horizontal Stages)

- Stages with `4px` border-radius on first/last. Adjacent stages share borders.
- Top accent: 3px solid top border with `s-` prefixed semantic class

### Principle / Numbered List

- **Number:** Cinzel, `2.4rem`, weight 800, `--accent`

### Callout

- Left border: `4px solid var(--accent)`
- Background: `rgba(200, 160, 48, 0.04)`
- `<strong>` uses `--accent` color

### Tags

- Font: IBM Plex Mono, `0.7rem`, `border-radius: 2px`

### Tables

- Header: IBM Plex Mono, uppercase, `--text-faint`, 2px gold bottom border
- Body first column: `--text`, weight 600

### Diagram Containers

- Background: `--surface`, `border-radius: 4px`, `padding: 2.5rem`

---

## Unique Components

### Illuminated Drop Cap

An ornamental initial letter inspired by medieval illuminated manuscripts.

- **Size:** 80px square, `float: left`, `margin: 0.2rem 1.25rem 0.5rem 0`
- **Border:** `2px solid var(--accent)`, `border-radius: 4px`
- **Inner frame:** `::before` with `inset: 3px`, `1px solid rgba(200,160,48,0.2)`
- **Letter:** Cinzel, `2.8rem`, weight 800, `--accent`

### Recipe Card

A structured card for recording alchemical formulas and procedures.

- **Container:** `--surface`, `1px solid var(--border)`, `border-radius: 4px`
- **Header:** `--surface-2` background, flex row with recipe name (Cinzel, 0.95rem, weight 700) + symbol (1.4rem, `--accent`)
- **Ingredient list:** Unstyled list, flex rows with name + quantity (IBM Plex Mono, weight 500, `--accent`)
- **Footer:** `--surface-2` background, IBM Plex Mono `0.7rem`, process parameters

### Transmutation Circle

An SVG diagram with interlocking geometric forms for decorative use.

- Two concentric circles (r=90, r=70) in faint gold
- Two overlapping equilateral triangles (Star of David / hexagram) in faded gold
- Central filled circle (r=8) with gold stroke
- Container: `max-width: 300px`, centered

### Manuscript Divider

An SVG section separator with a centered ornamental cluster.

- Two horizontal rules in faint gold flanking a center group
- Center: three circles (r=5 filled, r=3 faded) creating a cluster
- Container: `max-width: 400px`, centered

### Sigil Badge

Circular double-ringed badges for elemental symbols and classification.

- **Size:** 72px diameter circle, `2px solid var(--accent)`, `--surface` background
- **Outer ring:** `::before`, `inset: -8px`, `1px solid rgba(200,160,48,0.2)`
- **Inner ring:** `::after`, `inset: 4px`, `1px solid rgba(200,160,48,0.15)`
- **Text:** Cinzel, `0.8rem`, weight 700, `--accent`

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Border: `1px solid var(--border)`, `border-radius: 2px`
- Color: `--text`

---

## Footer

- Top border: `1px solid var(--border)`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`

---

## Summary of Key Patterns

1. **Dark parchment backgrounds** — near-black with warm brown undertones, like aged vellum by candlelight.
2. **Gold leaf accent** — rich gold marks key elements, evoking gilt manuscript illumination.
3. **Alchemical semantics** — viridian green (growth), gold (transmutation), cinnabar red (danger), lapis blue (wisdom).
4. **Sharp carved corners** — 4px border-radius evokes stone tablets and manuscript borders.
5. **Scholarly serif typography** — Cinzel for ornamental headings, Crimson Pro for readable body text.
6. **Mystical unique components** — drop caps, recipe cards, transmutation circles, manuscript dividers, sigil badges.
7. **Illuminated hero** — radial gold glow and ornamental circle evoke gilt manuscript pages.
8. **Gold table headers** — 2px gold bottom border on table headers adds a touch of precious metal.
