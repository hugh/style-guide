# Mid-Century Modern — Style Guide

A warm atomic-age design system — mustard and teal accents, starburst dividers, boomerang shapes, Googie-inspired panels, and atomic badges for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#faf6ee` | Page background (warm cream)             |
| `--surface`    | `#f2ece2` | Cards, panels, diagram containers        |
| `--surface-2`  | `#eae2d6` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#ddd4c6` | Tertiary surface, row separators         |
| `--border`     | `#c8bca8` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#2a2420` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#6a5e50` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#9a8e7c` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Colors are inspired by the mid-century modern palette.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#d4982c` | Primary accent (Mustard Gold)            |
| `--accent-dim`  | `#b07820` | Muted accent                             |
| `--capture`     | `#1a8a7a` | Teal — fresh, modern, go                 |
| `--capture-dim` | `#126a5c` | Muted teal                               |
| `--refine`      | `#d4982c` | Mustard Gold — warm, craft               |
| `--refine-dim`  | `#b07820` | Muted mustard                            |
| `--execute`     | `#d05848` | Coral — bold, alert                      |
| `--execute-dim` | `#b04038` | Muted coral                              |
| `--batch`       | `#4870a0` | Slate Blue — cool, info                  |
| `--batch-dim`   | `#305888` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                                          |
|-----------|---------------|--------------------------------------------------------------|
| Headings  | Poppins       | `Poppins:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;1,400` |
| Body      | DM Sans       | `DM+Sans:wght@300;400;500;600;700`                           |
| Labels    | IBM Plex Mono | `IBM+Plex+Mono:wght@400;500;600`                            |

```html
<link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;1,400&family=DM+Sans:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family        | Size                          | Weight | Line-height | Notes                                     |
|--------------------|---------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Poppins       | `clamp(2.8rem, 8vw, 5.5rem)` | 800    | 1.05        | `letter-spacing: -0.02em`                  |
| h2 (section)       | Poppins       | `2rem`                        | 700    | 1.15        |                                            |
| h3 (subsection)    | Poppins       | `1.15rem`                     | 700    | 1.2         | `margin-top: 2.5rem`                       |
| h4 (card title)    | DM Sans       | `0.78rem`                     | 700    |             | Uppercase, `letter-spacing: 0.08em`        |
| Body paragraph     | DM Sans       | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | DM Sans       | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | DM Sans       | `0.88rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Tag                | IBM Plex Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`, pill-shaped `border-radius: 20px` |

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
- **Atomic starburst:** `::before` pseudo-element creates a 500px repeating-conic-gradient circle with alternating mustard rays
- **Boomerang accent:** `::after` pseudo-element draws a boomerang shape (`border-radius: 0 80px 0 80px`) in faint teal, rotated -15deg
- **Title accent:** The `<span>` inside h1 uses `--accent` color (mustard)
- **Staggered fade-up animation** on load (0s, 0.15s, 0.3s, 0.45s delays)

---

## Components

### Flow Cards (2-Column Grid)

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 12px`, `padding: 1.5rem`
- **Top accent bar:** 3px colored bar via `::before`

### Pipeline (Horizontal Stages)

- Stages with `12px` border-radius on first/last. Adjacent stages share borders.
- Top accent: 3px solid top border with `s-` prefixed semantic class

### Principle / Numbered List

- **Number:** Poppins, `2.4rem`, weight 800, `--accent`

### Callout

- Left border: `4px solid var(--accent)`
- Background: `rgba(212, 152, 44, 0.06)`
- `<strong>` uses `--accent` color

### Tags / Pills

- Font: IBM Plex Mono, `0.7rem`, **pill-shaped** with `border-radius: 20px`

### Tables

- Header: IBM Plex Mono, uppercase, `--text-faint`
- Body first column: `--text`, weight 600

### Diagram Containers

- Background: `--surface`, `border-radius: 12px`, `padding: 2.5rem`

---

## Unique Components

### Starburst Divider

An SVG section separator with radiating lines from a center dot, evoking the classic mid-century starburst motif.

- **Center:** Circle, `r="6"`, filled with `--accent`
- **Rays:** 8 lines radiating outward, `stroke: var(--accent)`, `stroke-width: 1.5`
- Container: `max-width: 200px`, centered

### Boomerang Card

A card with a decorative boomerang shape in the corner.

- **Container:** `--surface`, `1px solid var(--border)`, `border-radius: 12px`
- **Boomerang:** `::before` with `border-radius: 0 60px 0 60px`, rotated -20deg, faded opacity 0.1
- **Color variants:** `boom-teal`, `boom-mustard`, `boom-coral`, `boom-blue`
- **Structure:** `.boom-header` (border-bottom) + `.boom-body`

### Googie Angle Panel

A panel with asymmetric rounded corners inspired by Googie architecture.

- **Container:** `--surface`, `1px solid var(--border)`
- **Asymmetric corners:** `border-radius: 4px 40px 4px 40px`
- **Label:** IBM Plex Mono, `0.65rem`, uppercase
- **Color band variants:** `gp-teal`, `gp-mustard`, `gp-coral`, `gp-blue` (4px left border)

### Atomic Badge

A circular badge with an orbit ring and electron dot, evoking atomic-age imagery.

- **Size:** 72px diameter circle, `2px solid var(--accent)`, `--surface` background
- **Orbit ring:** `::before`, `inset: -10px`, `1px dashed var(--border)`
- **Electron dot:** `::after`, 6px circle, `--accent` background, positioned at top
- **Text:** Poppins, `0.7rem`, weight 700, `--accent`

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

1. **Warm cream backgrounds** — soft off-white tones create a warm, inviting retro canvas.
2. **Mustard gold accent** — the signature mid-century color marks key interactive elements.
3. **Atomic-age semantics** — teal (fresh/go), mustard (warm/craft), coral (bold/alert), slate blue (cool/info).
4. **Generous rounded corners** — 12px border-radius on all cards and panels gives a soft, modern feel.
5. **Pill-shaped tags** — 20px border-radius makes tags distinctively rounded.
6. **Geometric heading font** — Poppins delivers bold, clean headings with tight letter-spacing.
7. **Atomic starburst hero** — repeating-conic-gradient creates a subtle radiating pattern.
8. **Retro unique components** — starburst dividers, boomerang cards, Googie panels, and atomic badges.
