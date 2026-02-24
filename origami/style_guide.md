# Origami / Paper Craft — Style Guide

Folded paper shadows and geometric faceted shapes — clean white/cream backgrounds with soft pastel accents and crisp fold-line borders. The entire aesthetic evokes folded paper: clean geometric shapes, subtle shadows suggesting depth, crisp crease lines as dividers. Light, airy, delicate.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#fafafa` | Page background (clean white paper)      |
| `--surface`    | `#f0f0f0` | Cards, panels (folded paper shadow)      |
| `--surface-2`  | `#e8e8e8` | Nested surfaces (deeper fold shadow)     |
| `--surface-3`  | `#dedede` | Tertiary surface (crease shadow)         |
| `--border`     | `#d0d0d0` | Card borders, fold lines                 |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#2a2a2a` | Primary text (dark ink), headings, bold/strong  |
| `--text-dim`   | `#5a5a5a` | Body paragraphs (lighter ink)                   |
| `--text-faint` | `#8a8a8a` | Labels, metadata, captions (pencil marks)       |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Colors are inspired by traditional origami paper.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#e85070` | Primary accent (Origami Pink)            |
| `--accent-dim`  | `#c84060` | Muted accent                             |
| `--capture`     | `#38a060` | Paper Green — sage green origami paper   |
| `--capture-dim` | `#288048` | Muted green                              |
| `--refine`      | `#d0a020` | Paper Gold — gold foil origami paper     |
| `--refine-dim`  | `#a88018` | Muted gold                               |
| `--execute`     | `#e85070` | Paper Red — traditional red              |
| `--execute-dim` | `#c84060` | Muted red                                |
| `--batch`       | `#3878c8` | Paper Blue — sky blue origami paper      |
| `--batch-dim`   | `#2860a8` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                                          |
|-----------|---------------|--------------------------------------------------------------|
| Headings  | Nunito        | `Nunito:wght@300;400;500;600;700;800`                        |
| Body      | Inter         | `Inter:wght@300;400;500;600`                                 |
| Labels    | IBM Plex Mono | `IBM+Plex+Mono:wght@400;500`                                |

### Type Scale & Weights

| Element            | Family        | Size                          | Weight | Line-height | Notes                                     |
|--------------------|---------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Nunito        | `clamp(2.8rem, 8vw, 5.5rem)` | 800    | 1.05        | `letter-spacing: -0.02em`                  |
| h2 (section)       | Nunito        | `2rem`                        | 700    | 1.15        |                                            |
| h3 (subsection)    | Nunito        | `1.15rem`                     | 700    | 1.2         | `margin-top: 2.5rem`                       |
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
- Border-radius: **0px** throughout — crisp folded edges, no rounding

---

## Hero Section

- Full viewport height, flex-centered
- **Geometric paper fold pattern:** `::before` creates a zigzag triangular pattern along the top edge using repeating CSS gradients
- **Diamond grid pattern:** `::after` creates a subtle 45-degree crosshatch pattern across the hero
- Staggered fade-up animation on load

---

## Standard Components

### Flow Cards

2-column grid cards with a 3px semantic color top bar. Classes: `capture`, `refine`, `execute`, `batch`, `accent`. Crisp 0px border-radius with subtle offset paper shadow.

### Pipeline

Horizontal stages with semantic top borders. Stage classes: `s-capture`, `s-refine`, `s-execute`, `s-batch`, `s-accent`. No border-radius.

### Callout

Left-bordered callout with faint accent background wash. Uses `--accent` for the 4px left border.

### Tags

Inline mono labels with semantic border colors. Classes: `t-capture`, `t-refine`, `t-execute`, `t-batch`. 0px border-radius.

### Info Table

Clean data table with mono uppercase headers and fold-line row separators.

### Principle List

Numbered list with large Nunito numerals in accent pink.

### Diagram Wrap

Container for SVG diagrams. Background: `--surface`, border: `--border`, 0px radius, paper shadow.

---

## Unique Components

### Folded Card

A card component that appears to have a folded corner (triangle in top-right using CSS `::after` with a border-based triangle). Subtle shadow beneath the fold. Content area is clean with a thin top accent stripe.

- **Container:** `--surface` background, `1px solid var(--border)`, `0px` border-radius
- **Accent stripe:** `::before` creates a 3px top bar
- **Folded corner:** `::after` creates a 36px triangle in the top-right corner using `border-width: 0 36px 36px 0`
- **Shadow:** `2px 2px 0 rgba(0,0,0,0.05)` paper offset shadow
- **Variants:** Default (accent pink), `.capture`, `.refine`, `.execute`, `.batch`

### Crane Marker

A section marker featuring a simple origami crane SVG (geometric/low-poly style). Centered between thin horizontal rules.

- **Layout:** Flex row with crane SVG centered between two `--border` colored lines
- **Crane SVG:** 48x48px, faceted polygons in surface tones with accent-colored beak
- **Lines:** Max-width 200px each, 1px height, `--border` color
- **Margin:** `3rem` top and bottom

### Crease Divider

A horizontal divider that looks like a paper crease/fold line. Thin line with a subtle shadow on one side.

- **Height:** 2px total
- **Visual:** Gradient from dark shadow (top) to light highlight (bottom), simulating light hitting a real paper fold
- **Line:** 1px `--border` line via `::after` pseudo-element
- **Margin:** `3rem` top and bottom

### Fortune Teller Badge

An inline badge shaped like a paper fortune teller (cootie catcher) viewed from above — a diamond with four colored quadrants.

- **Container:** Inline-flex, centered, 56px square (default) or 72px (`.fortune-lg`)
- **Diamond:** Rotated 45 degrees via CSS `transform`, contains four quadrant divs
- **Quadrants:** Top-left (capture-fill), top-right (refine-fill), bottom-left (batch-fill), bottom-right (execute-fill)
- **Border:** 1px `--border` on each quadrant and on the outer diamond
- **Label:** IBM Plex Mono, centered, z-index 1 to float above the diamond

---

## Summary of Key Patterns

1. **Clean paper backgrounds** — white and light grey surfaces layered like folded sheets.
2. **Origami pink accent** — traditional red-pink origami paper marks key elements.
3. **Crisp geometric edges** — 0px border-radius everywhere, matching folded paper.
4. **Paper fold shadows** — subtle offset box-shadows suggest layered paper depth.
5. **Friendly rounded headings** — Nunito brings soft geometric warmth against sharp containers.
6. **Paper color semantics** — sage green, gold foil, traditional red, sky blue from real origami paper colors.
7. **Folded corner cards** — CSS triangle in the top-right corner with shadow suggests a turned page.
8. **Geometric crane separator** — low-poly origami crane SVG as a decorative section divider.
