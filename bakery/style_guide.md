# Bakery / Patisserie — Style Guide

Warm vanilla cream and powdered sugar. A design system inspired by the patisserie — recipe cards, timer badges, layered cake dividers, and pastry box packaging for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#fdf8f0` | Page background (warm vanilla cream)     |
| `--surface`    | `#f8f0e4` | Cards, panels, diagram containers        |
| `--surface-2`  | `#f0e6d6` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#e4d8c4` | Tertiary surface, row separators         |
| `--border`     | `#d4c4a8` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#3a2e20` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#7a6850` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#a89878` | Labels, measurements, captions, annotations     |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                  |
|-----------------|-----------|---------------------------------------|
| `--accent`      | `#c06838` | Primary accent (Caramel/Toffee)       |
| `--accent-dim`  | `#8a4828` | Muted accent                          |
| `--capture`     | `#5a9060` | Pistachio/Mint — fresh, natural       |
| `--capture-dim` | `#3a6840` | Muted green                           |
| `--refine`      | `#c89838` | Golden Crust — warmth, richness       |
| `--refine-dim`  | `#907020` | Muted gold                            |
| `--execute`     | `#c84858` | Raspberry — sweetness, urgency        |
| `--execute-dim` | `#903038` | Muted raspberry                       |
| `--batch`       | `#4878a0` | Blueberry — richness, depth           |
| `--batch-dim`   | `#305878` | Muted blue                            |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                              |
|-----------|-----------------|---------------------------------------------------|
| Headings  | Satisfy         | `Satisfy`                                         |
| Body      | DM Sans         | `DM+Sans:wght@300;400;500;600`                    |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500`                      |

```html
<link href="https://fonts.googleapis.com/css2?family=Satisfy&family=DM+Sans:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                     |
|--------------------|-----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Satisfy         | `clamp(3.5rem, 10vw, 7rem)`  | 400    | 0.95        | Accent-colored `<span>` for title word     |
| h2 (section)       | Satisfy         | `2.8rem`                      | 400    | 1.05        |                                            |
| h3 (subsection)    | Satisfy         | `2rem`                        | 400    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | DM Sans         | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.06em          |
| Body paragraph     | DM Sans         | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | DM Sans         | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Recipe title       | Satisfy         | `1.8rem`                      | 400    | 1.1         | In recipe card header                      |
| Section label      | IBM Plex Mono   | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--accent`      |
| Tag                | IBM Plex Mono   | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Timer value        | IBM Plex Mono   | `1.2rem`                      | 500    |             | Inside timer badge, semantic color         |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace measurement-style label** in the format `01 — Label`

### Full-Bleed Containers

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

### Border Radius

- Global: **10px** (soft, rounded like pastry)

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: measurement-style label, h1, subtitle, version
- **Warm radial glow:** Faint radial gradients in caramel and golden tones via `::before`, simulating warm oven light
- **Whisk/swirl pattern:** Concentric circle gradients via `::after` at very low opacity, evoking decorative pastry flourishes
- **Title accent:** `<span>` inside h1 uses `--accent` (caramel)
- **Staggered fade-up animation** on load (same as other themes)

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Bakery-specific adjustments:
- Border-radius: `10px` (soft, rounded like pastry)
- Hover glow uses caramel: `rgba(192, 104, 56, 0.1)`
- Principle numbers use Satisfy at `2.5rem` instead of a bold weight
- Tags use fully rounded border-radius (`10px`) for a pill shape

---

## Unique Components

### Recipe Card

A structured recipe card with title, ingredient checklist, and baking parameters.

- **Container:** `--surface` background, `1px solid var(--border)`, `border-radius: 10px`, subtle box-shadow
- **Header:** `--surface-2` background, flex row with Satisfy recipe title (`1.8rem`) and mono metadata
- **Ingredient list:** No list style, each item is a flex row with:
  - Checkbox (18x18px, `4px` radius, `--border` border, `--bg` background)
  - `.checked` variant: `--capture-fill` background, `--capture` border, checkmark in `--capture`
  - Quantity in IBM Plex Mono (`0.75rem`, `--accent`, min-width `4.5rem`)
  - Ingredient name in body text
  - Dashed `--surface-3` bottom border between items
- **Footer:** `--surface-2` background, flex row with parameter groups
  - Each param: mono label (`0.6rem`, uppercase, `--text-faint`) over value (`0.85rem`, `--text`)

### Timer Badge

Circular countdown badge for tracking baking times.

- **Size:** `80px` width and height, `border-radius: 50%`
- **Default:** `--execute-fill` background, `2px solid var(--execute)` border
- **Value:** IBM Plex Mono, `1.2rem`, weight 500, semantic color
- **Unit label:** IBM Plex Mono, `0.55rem`, uppercase, `--text-faint`
- **Variants:**
  - `.urgent` — raspberry (`--execute`), pulsing box-shadow animation
  - `.waiting` — golden crust (`--refine`), for in-progress items
  - `.ready` — pistachio (`--capture`), for completed items
- **Group:** Flex row with `1.5rem` gap, wraps

### Cake Layer Divider

An SVG section separator showing a layered cake cross-section.

- **Container:** `3rem` margin, centered, `max-width: 700px`
- **Layers:** Alternating rectangles in `--surface-3` (sponge) and `--surface` (frosting)
- **Top frosting:** Wavy path with drip effect in `--surface` color
- **Cherry decorations:** Small circles in `--execute` (raspberry) on top
- **Height:** `48px` total SVG viewBox

### Pastry Box

A packaging-style frame with decorative ribbon and bow.

- **Container:** `--surface` background, `2px solid var(--border)`, `border-radius: 10px`
- **Ribbon:** `::before` pseudo-element, 6px gradient bar across top (caramel-gold-caramel pattern)
- **Bow:** `::after` pseudo-element centered on ribbon, elliptical shape with side loops via box-shadow
- **Inner frame:** Dashed `--surface-3` border, `1.5rem` inset margin, `6px` radius
- **Content:** Centered text with mono label, Satisfy heading in `--accent`, body description

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `6px`
- Border: `1px solid var(--border)`
- Color: `--accent` (caramel)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Warm vanilla, not stark white** — backgrounds use cream tones like vanilla batter and parchment paper, creating a cozy bakery atmosphere.
2. **Caramel accent** — the primary accent is a rich toffee brown inspired by golden-baked crusts and caramelized sugar.
3. **Three-tier text** — dark chocolate (--text), milk chocolate (--text-dim), biscuit (--text-faint).
4. **Script headings** — Satisfy delivers the feel of handwritten bakery signage and recipe labels.
5. **Precise measurements** — IBM Plex Mono for all measurements and temperatures gives baking data the precision that pastry requires.
6. **Flavor semantics** — pistachio green (fresh), golden crust (warmth), raspberry pink (sweetness), blueberry blue (richness).
7. **Soft rounded corners** — 10px border-radius on all components creates the soft, rounded feel of pastry.
8. **Bakery artifacts** — recipe cards, timer badges, cake layer dividers, and pastry box packaging bring real patisserie elements into the design.
