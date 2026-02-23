# Brutalist Web — Style Guide

Raw concrete under harsh light. An anti-design system that rejects decoration — system fonts at jarring scales, zero border-radius, thick black borders, no hover transitions, and construction orange as the single loud accent. Everything static and heavy.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#c8c8c8` | Page background (raw concrete grey)      |
| `--surface`    | `#e0e0e0` | Cards, panels, diagram containers        |
| `--surface-2`  | `#d0d0d0` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#b8b8b8` | Tertiary surface, table headers          |
| `--border`     | `#000000` | All borders (pure black, thick)          |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#000000` | Primary text, headings (pure black)             |
| `--text-dim`   | `#1a1a1a` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#555555` | Labels, metadata, captions                      |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#ff5500` | Primary accent (Construction Orange)     |
| `--accent-dim`  | `#cc4400` | Muted accent                             |
| `--capture`     | `#00aa00` | Safety Green — safe, go, approved        |
| `--capture-dim` | `#008800` | Muted green                              |
| `--refine`      | `#ccaa00` | Warning Yellow — caution, review         |
| `--refine-dim`  | `#aa8800` | Muted yellow                             |
| `--execute`     | `#dd0000` | Danger Red — stop, rejected              |
| `--execute-dim` | `#aa0000` | Muted red                                |
| `--batch`       | `#0044cc` | Industrial Blue — info, neutral          |
| `--batch-dim`   | `#003399` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family                              | Notes                              |
|-----------|-------------------------------------|------------------------------------|
| Headings  | Arial, Helvetica, sans-serif        | System font. Weight 900. Uppercase.|
| Body      | Times New Roman, Times, serif       | System font. Deliberately mixed.   |
| Labels    | Courier New, Courier, monospace     | System font. Weight 700.           |

**No Google Fonts.** System fonts only. This is deliberate.

### Type Scale & Weights

| Element            | Family              | Size                              | Weight | Notes                                          |
|--------------------|---------------------|---------------------------------------|--------|-------------------------------------------------|
| Hero h1            | Arial               | `clamp(3.5rem, 12vw, 8rem)`         | 900    | Uppercase, tight line-height 0.9               |
| h2 (section)       | Arial               | `2.4rem`                             | 900    | Uppercase, letter-spacing -0.02em              |
| h3 (subsection)    | Arial               | `1.2rem`                             | 900    | Uppercase                                      |
| h4 (card title)    | Arial               | `0.75rem`                            | 900    | Uppercase, letter-spacing: 0.1em               |
| Body paragraph     | Times New Roman      | `1rem`                               | 400    | Color: `--text-dim`                            |
| Section label      | Courier New          | `0.8rem`                             | 700    | Uppercase, `letter-spacing: 0.15em`            |
| Tag                | Courier New          | `0.75rem`                            | 700    | Uppercase, `letter-spacing: 0.06em`            |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `4rem` top and bottom
- Separated by **`4px solid #000000`** top border (thick)
- Each section opens with a **monospace label** in the format `01 — Label`

### Full-Bleed Containers

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- **Left-aligned** (not centered — deliberate asymmetry)
- Oversized h1 at `clamp(3.5rem, 12vw, 8rem)` — intentionally jarring scale
- **No background decoration** — raw concrete only
- **No animations** — everything appears immediately, static
- **Title accent:** `<span>` inside h1 uses `--accent` (construction orange), displayed as block

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Brutalist adjustments:
- **Border-radius: `0` everywhere** — no rounded corners, ever
- **No hover transitions** — everything static and heavy
- **Thick borders:** `3px solid #000000` on all components
- **No box-shadows** — flat, raw, exposed
- Principle numbers use Arial at `3rem` in `--accent`
- Tags are rectangular blocks (no pill shape)
- Flow grid has no gap — cards share borders for visible grid structure
- Principle list items share borders with no gap between them

---

## Unique Components

### Monolith Block

A massive inverted-color block for high-impact statements.

- **Container:** `--text` (black) background, `4px solid var(--border)`, full-width
- **Padding:** `3rem 2.5rem` — heavy and spacious
- **Title:** Arial, `clamp(2rem, 6vw, 4rem)`, weight 900, uppercase, `--surface` color
- **Accent word:** `<em>` inside title uses `--accent` (construction orange), not italic
- **Body:** `1rem`, `--surface-3` color, max-width 500px

### Exposed Grid

A visible CSS grid with thick black borders showing raw structure.

- **Container:** 3-column grid, `4px solid var(--border)` outer border
- **Cells:** `var(--surface)` background, `2px solid var(--border)` each cell
- **Cell label:** Courier New, `0.65rem`, weight 700, uppercase, `--text-faint`
- **Cell value:** Arial, `1.6rem`, weight 900, uppercase, `--text`
- **Cell description:** `0.85rem`, `--text-dim`

### Hazard Stripe

A construction warning stripe divider.

- **Height:** `24px`
- **Pattern:** `repeating-linear-gradient(-45deg)` with 12px orange/black stripes
- **Borders:** `3px solid var(--border)` top and bottom
- **Yellow variant:** `.stripe-yellow` swaps orange for `--refine`

### Stencil Stamp

A construction-site stencil label.

- **Container:** Inline-block, `4px` solid border, Arial weight 900, uppercase
- **Rotation:** `transform: rotate(-2deg)` for hand-stamped feel
- **Letter-spacing:** `0.15em`
- **Variants:** `.stamp-approved` (green), `.stamp-rejected` (red), `.stamp-review` (yellow), `.stamp-urgent` (orange)

---

## Inline Code

- Font: Courier New, `0.85rem`, weight 700
- Background: `--surface`
- Padding: `0.1em 0.35em`
- Border: `2px solid #000000`
- **No border-radius**
- Color: `--text`

---

## Footer

- Top border: `4px solid #000000`
- Padding: `3rem 0`
- **Left-aligned** (not centered)
- Courier New, `0.8rem`, weight 700, `--text-faint`, uppercase

---

## Summary of Key Patterns

1. **Raw concrete** — backgrounds use flat grey tones like an unfinished concrete wall, no warmth, no texture.
2. **Construction orange** — the single loud accent demands attention like a safety vest on a building site.
3. **System fonts only** — Arial, Times New Roman, Courier. No imports. No web fonts. Deliberate constraint.
4. **Zero border-radius** — every corner is sharp. No exceptions. Raw and unfinished.
5. **No hover transitions** — nothing moves, nothing changes. Static and monolithic.
6. **Thick black borders** — 3–4px pure black on everything. The structure is exposed, not hidden.
7. **Jarring scale** — hero text at 8rem, body in Times New Roman. The contrast is the point.
8. **Industrial artifacts** — monolith blocks, exposed grids, hazard stripes, and stencil stamps bring the construction site into the design.
