# Swiss / International Typographic Style — Style Guide

A minimalist design system rooted in the Swiss tradition — pure white canvas, clean grids, precise sans-serif typography, generous whitespace, single red accent, and absolute visual clarity for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#ffffff` | Page background (pure white)             |
| `--surface`    | `#f6f6f6` | Cards, panels, diagram containers        |
| `--surface-2`  | `#eeeeee` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#e4e4e4` | Tertiary surface, grid column lines      |
| `--border`     | `#d0d0d0` | Hairline borders, section dividers       |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#0a0a0a` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#4a4a4a` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#999999` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#e20000` | Primary accent (Swiss Red)               |
| `--accent-dim`  | `#b80000` | Muted accent                             |
| `--capture`     | `#00864a` | Green — input, collection                |
| `--capture-dim` | `#006838` | Muted green                              |
| `--refine`      | `#c89000` | Amber — processing, iteration            |
| `--refine-dim`  | `#a07000` | Muted amber                              |
| `--execute`     | `#e20000` | Red — action, output                     |
| `--execute-dim` | `#b80000` | Muted red                                |
| `--batch`       | `#0050c8` | Blue — grouped, automated                |
| `--batch-dim`   | `#003898` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family         | Google Fonts Import                                          |
|-----------|----------------|--------------------------------------------------------------|
| Headings  | Inter          | `Inter:wght@300;400;500;600;700;800;900`                     |
| Body      | Inter          | Same import — lighter weights                                |
| Labels    | JetBrains Mono | `JetBrains+Mono:wght@400;500;600`                           |

### Type Scale & Weights

| Element            | Family         | Size                          | Weight | Line-height | Notes                                     |
|--------------------|----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Inter          | `clamp(3rem, 8vw, 5.5rem)`   | 800    | 1.0         | `letter-spacing: -0.04em`                 |
| h2 (section)       | Inter          | `1.75rem`                     | 700    | 1.15        | `letter-spacing: -0.02em`                 |
| h3 (subsection)    | Inter          | `1.05rem`                     | 600    | 1.2         | Uppercase, `letter-spacing: 0.04em`        |
| h4 (card title)    | Inter          | `0.78rem`                     | 600    |             | Uppercase, `letter-spacing: 0.08em`        |
| Body paragraph     | Inter          | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Section label      | JetBrains Mono | `0.72rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`        |
| Tag                | JetBrains Mono | `0.68rem`                     | 400    |             | `letter-spacing: 0.06em`                  |

---

## Layout

- Container max-width: **900px**, centered, `2rem` horizontal padding
- Section padding: `5rem` vertical, `1px solid var(--border)` top border
- Section label format: `01 — Label` (JetBrains Mono, uppercase)
- Full-bleed max-width: **1100px**
- Border radius: **0px everywhere** — no rounding at all
- Shadows: **None** — flat surfaces only
- Gradients: **None** on surfaces

---

## Hero Section

- Full viewport height, flex-column, left-aligned (not centered)
- Max-width `900px`, auto-centered with padding
- **Red rule:** 80px-wide, 4px-tall red bar beneath the heading (`.hero-rule`)
- **No textures, no patterns** — pure white background
- Hero span text colored with `--accent` (Swiss red)

---

## Standard Components

### Flow Cards

- 2-column grid (`.flow-grid`), collapses to 1 column below 640px
- White background, 1px hairline border, **no border-radius**
- 3px semantic top bar: `.capture` (green), `.refine` (amber), `.execute` (red), `.batch` (blue), `.accent` (red)
- Card title is uppercase Inter at 0.78rem

### Pipeline

- Horizontal flex stages with top color bars
- Each stage: `.pipe-stage.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`
- No border-radius on any stage

### Callout

- Left border: `4px solid var(--accent)` (Swiss red)
- Background: `var(--surface)` (barely-grey)
- No border-radius

### Tags

- Inline-block, JetBrains Mono, uppercase
- Rectangular (no border-radius)
- Classes: `.t-capture`, `.t-refine`, `.t-execute`, `.t-batch`

### Info Table

- Full-width, collapsed borders
- Header: 2px solid `--text` bottom border, JetBrains Mono labels
- Rows: 1px solid `--border` bottom border

### Principle List

- Vertical stack with no gap
- Each principle has a top border, large red number, title, description
- Numbers: Inter weight 900 at 2.4rem in `--accent`

### Diagram Container

- Background: `var(--surface)`, 1px border, no border-radius
- Full-bleed variant: 1100px max-width
- SVG text uses Inter font family
- Dashed connections: `stroke-dasharray: 4,3`
- Node corners: `rx="0"` (square, not rounded)

---

## Unique Components

### Grid Module

A strict 12-column grid overlay card showing content in precise column spans.

- **Container:** 1px border, no radius, no background
- **Header:** Label + meta info (column count), bottom border
- **Body:** CSS Grid with `grid-template-columns: repeat(12, 1fr)`
- **Column lines:** Generated via repeating-linear-gradient on `::before` pseudo-element
- **Cells:** Use `.span-3` through `.span-12` classes for column spanning
- **Cell content:** Label (JetBrains Mono, faint) + content text

```html
<div class="grid-module">
  <div class="grid-module-header">
    <h4>Grid Module</h4>
    <div class="grid-module-meta">12 columns</div>
  </div>
  <div class="grid-module-body">
    <div class="grid-module-cell span-5">
      <div class="cell-label">Cols 1–5</div>
      <div class="cell-content"><strong>Primary</strong> content.</div>
    </div>
    <div class="grid-module-cell span-7">
      <div class="cell-label">Cols 6–12</div>
      <div class="cell-content">Secondary content.</div>
    </div>
  </div>
</div>
```

### Type Specimen

A showcase panel displaying a typeface at multiple sizes with precise measurements.

- **Container:** 1px border, no radius
- **Header:** Grey background, family name + weight label (JetBrains Mono)
- **Rows:** Size label (right-aligned, JetBrains Mono) + sample text at that size
- **Dividers:** Hairline border between rows

```html
<div class="type-specimen">
  <div class="type-specimen-header">
    <div class="spec-family">Inter — Sans-serif</div>
    <div class="spec-weight">Weight 800</div>
  </div>
  <div class="type-specimen-row">
    <div class="spec-size">48px</div>
    <div class="spec-sample" style="font-size:48px; font-weight:800;">Sample</div>
  </div>
</div>
```

### Red Rule Divider

A thick red horizontal rule (4px) used as a structural accent between sections.

- **With label:** Label left-aligned, red line fills remaining space
- **Without label:** Add `.no-label` class, rule spans full width
- Line height: 4px, color: `var(--accent)`

```html
<!-- With label -->
<div class="red-rule">
  <div class="red-rule-label">Section A</div>
  <div class="red-rule-line"></div>
</div>

<!-- Without label -->
<div class="red-rule no-label">
  <div class="red-rule-line"></div>
</div>
```

### Index Card

A numbered reference card with a bold oversized number, title, and description in a strict left-aligned grid.

- **Container grid:** `.index-card-grid` — 2-column grid, collapses at 640px
- **Card:** Top border only (1px solid `--text`), no other borders
- **Number:** Inter weight 900, 3.5rem, near-black, tight letter-spacing
- **Title:** Uppercase h4
- **Description:** Dim body text

```html
<div class="index-card-grid">
  <div class="index-card">
    <div class="index-card-number">01</div>
    <h4>Card Title</h4>
    <p>Card description text.</p>
  </div>
</div>
```

---

## Summary of Key Patterns

1. **Pure white canvas** — no textures, no patterns, no noise. Every mark earns its place.
2. **Single accent color** — Swiss red (#e20000) marks structure, never decoration.
3. **Typographic unity** — Inter at multiple weights creates hierarchy from a single family.
4. **Grid discipline** — all content aligns to a strict grid with asymmetric placement.
5. **Hairline borders** — 1px grey lines provide structure without visual weight.
6. **Zero radius** — no rounded corners anywhere. Sharp rectangles enforce geometric precision.
7. **No shadows** — flat surfaces only. Depth is communicated through spacing and borders.
8. **Generous whitespace** — space is an active structural element, not emptiness.
