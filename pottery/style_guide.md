# Pottery / Ceramics — Style Guide

A warm ceramics studio design system — terracotta accents, glaze recipe cards, kiln gauges, and potter's marks for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#f5ede4` | Page background (warm clay linen)        |
| `--surface`    | `#efe5da` | Cards, panels, diagram containers        |
| `--surface-2`  | `#e8dccf` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#ddd0c0` | Tertiary surface, row separators         |
| `--border`     | `#cfc0ac` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#3a2e24` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#7a6c5c` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#a89880` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Colors are inspired by glaze families and ceramic materials.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#c06030` | Primary accent (Terracotta)              |
| `--accent-dim`  | `#a04820` | Muted accent                             |
| `--capture`     | `#5a9868` | Celadon Green — glazed, finished, go     |
| `--capture-dim` | `#3e7a4c` | Muted green                              |
| `--refine`      | `#c89838` | Raw Clay Amber — drying, shaping         |
| `--refine-dim`  | `#a87828` | Muted amber                              |
| `--execute`     | `#b83828` | Iron Red — kiln fire, alert              |
| `--execute-dim` | `#982818` | Muted red                                |
| `--batch`       | `#3868a0` | Cobalt Blue — underglaze, decorative     |
| `--batch-dim`   | `#284888` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                                          |
|-----------|---------------|--------------------------------------------------------------|
| Headings  | Nunito Sans   | `Nunito+Sans:wght@300;400;500;600;700;800`                   |
| Body      | DM Sans       | `DM+Sans:wght@300;400;500;600;700`                           |
| Labels    | IBM Plex Mono | `IBM+Plex+Mono:wght@400;500;600`                            |

```html
<link href="https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@300;400;500;600;700;800&family=DM+Sans:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family        | Size                          | Weight | Line-height | Notes                                     |
|--------------------|---------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Nunito Sans   | `clamp(2.8rem, 8vw, 5.5rem)` | 800    | 1.05        |                                            |
| h2 (section)       | Nunito Sans   | `2rem`                        | 700    | 1.15        |                                            |
| h3 (subsection)    | Nunito Sans   | `1.15rem`                     | 700    | 1.2         | `margin-top: 2.5rem`                       |
| h4 (card title)    | DM Sans       | `0.78rem`                     | 700    |             | Uppercase, `letter-spacing: 0.08em`        |
| Body paragraph     | DM Sans       | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | DM Sans       | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | DM Sans       | `0.88rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Tag                | IBM Plex Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |

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
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Potter's wheel circles:** `::before` pseudo-element creates a 400px circle with concentric `box-shadow` rings at 30px, 60px, and 100px in faint terracotta
- **Wheel hub:** `::after` pseudo-element draws an 8px center dot in border color
- **Title accent:** The `<span>` inside h1 uses `--accent` color (terracotta)
- **Staggered fade-up animation** on load (0s, 0.15s, 0.3s, 0.45s delays)

---

## Components

### Flow Cards (2-Column Grid)

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 8px`, `padding: 1.5rem`
- **Top accent bar:** 3px colored bar via `::before`

### Pipeline (Horizontal Stages)

- Stages with `8px` border-radius on first/last. Adjacent stages share borders.
- Top accent: 3px solid top border with `s-` prefixed semantic class

### Principle / Numbered List

- **Number:** Nunito Sans, `2.4rem`, weight 800, `--accent`

### Callout

- Left border: `4px solid var(--accent)`
- Background: `rgba(192, 96, 48, 0.06)`
- `<strong>` uses `--accent` color

### Tags / Pills

- Font: IBM Plex Mono, `0.7rem`, border-radius `4px`

### Tables

- Header: IBM Plex Mono, uppercase, `--text-faint`
- Body first column: `--text`, weight 600

### Diagram Containers

- Background: `--surface`, `border-radius: 8px`, `padding: 2.5rem`

---

## Unique Components

### Kiln Gauge

A circular temperature dial with bezel and cone reference.

- **Size:** 200px diameter circle
- **Background:** `--surface` with `inset box-shadow: 0 0 20px rgba(0,0,0,0.06)`
- **Border:** `3px solid var(--border)`
- **Outer bezel:** `::before`, `inset: -8px`, `4px solid var(--surface-3)`
- **Inner scale ring:** `::after`, `inset: 12px`, `1px solid var(--border)`
- **Reading (centered):**
  - Value: IBM Plex Mono, `1.8rem`, weight 600, `--execute` (iron red — to evoke heat)
  - Unit: IBM Plex Mono, `0.55rem`, `--text-faint`
  - Label: Nunito Sans, `0.55rem`, weight 700, `--text-faint`
  - Cone: IBM Plex Mono, `0.6rem`, `--accent` (terracotta)

### Glaze Recipe Card

A structured card for recording glaze formulas.

- **Container:** `--surface`, `1px solid var(--border)`, `border-radius: 8px`
- **Header:** `--surface-2` background, flex row with:
  - Glaze name: Nunito Sans, `0.9rem`, weight 700
  - Color swatch: 24px circle with border
- **Ingredient list:** Unstyled list, flex rows with name + percentage (IBM Plex Mono, weight 500)
- **Footer:** `--surface-2` background, IBM Plex Mono `0.7rem`, firing parameters

### Pottery Mark

Circular stamp badges for identification and notation.

- **Size:** 64px diameter circle, `2px solid` border in accent color
- **Symbol:** Nunito Sans, `1.5rem`, weight 800
- **Label:** IBM Plex Mono, `0.55rem`, absolute-positioned below
- **Color variants:** `mark-celadon`, `mark-cobalt`, `mark-iron`, `mark-amber`

### Coil Divider

An SVG section separator with undulating coil-texture lines.

- Two sinusoidal `<path>` elements with decreasing opacity (0.25, 0.12)
- Stroke: `rgba(192,96,48, opacity)`, width 2–2.5px, round linecap
- Container: `max-width: 500px`, centered

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Border: `1px solid var(--border)`, `border-radius: 4px`
- Color: `--text`

---

## Footer

- Top border: `1px solid var(--border)`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`

---

## Summary of Key Patterns

1. **Warm clay backgrounds** — light linen and clay tones create an earthy, handmade feel.
2. **Terracotta accent** — rich fired-earthenware orange marks key interactive elements.
3. **Glaze-inspired semantics** — celadon green (finished), raw clay amber (in-progress), iron red (fire/alert), cobalt blue (decorative/info).
4. **Rounded organic shapes** — 8px border-radius gives components a softer, handmade ceramic feel.
5. **Organic heading font** — Nunito Sans delivers friendly, rounded headings.
6. **Studio workshop components** — kiln gauges, glaze recipe cards, pottery marks, and coil dividers.
7. **Potter's wheel hero** — concentric circles and center hub evoke the potter's wheel.
8. **Monospace measurements** — IBM Plex Mono for all temperatures, cone numbers, and percentages.
