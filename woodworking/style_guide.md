# Woodworking / Workshop — Style Guide

A craftsman's design system — warm wood-grain backgrounds, sturdy 2px borders, honest materials, and hand-made precision for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                       |
|----------------|-----------|---------------------------------------------|
| `--bg`         | `#f4ece0` | Page background (raw pine / light wood)     |
| `--surface`    | `#e8dcc8` | Cards, panels, diagram containers           |
| `--surface-2`  | `#dcd0b8` | Nested surfaces, blueprint card background  |
| `--surface-3`  | `#d0c4a8` | Tertiary surface, row separators            |
| `--border`     | `#b8a888` | Card borders, section dividers (wood grain) |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#2a1e10` | Primary text, headings, bold/strong (dark walnut stain) |
| `--text-dim`   | `#5a4830` | Body paragraphs, secondary descriptions (medium wood stain) |
| `--text-faint` | `#8a7858` | Labels, metadata, captions, measurements (light wood stain) |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Colors are inspired by wood species and workshop materials.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#8b4520` | Primary accent (Rich Walnut)             |
| `--accent-dim`  | `#6a3418` | Muted walnut                             |
| `--capture`     | `#4a7a38` | Pine Green — fresh-cut wood, go          |
| `--capture-dim` | `#386028` | Muted pine                               |
| `--refine`      | `#c89030` | Maple Honey — amber, warmth              |
| `--refine-dim`  | `#a07020` | Muted honey                              |
| `--execute`     | `#a83020` | Cherry Red — cherry wood stain, alert    |
| `--execute-dim` | `#882418` | Muted cherry                             |
| `--batch`       | `#3868a0` | Steel Blue — tool steel, info            |
| `--batch-dim`   | `#285088` | Muted steel                              |

---

## Typography

### Font Stack

| Role      | Family         | Google Fonts Import                                        |
|-----------|----------------|------------------------------------------------------------|
| Headings  | Bitter         | `Bitter:wght@400;500;600;700`                              |
| Body      | Source Sans 3  | `Source+Sans+3:wght@300;400;500;600`                       |
| Labels    | IBM Plex Mono  | `IBM+Plex+Mono:wght@400;500;600`                          |

### Type Scale & Weights

| Element            | Family         | Size                          | Weight | Line-height | Notes                                     |
|--------------------|----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Bitter         | `clamp(2.6rem, 7vw, 4.5rem)` | 700    | 1.1         | `letter-spacing: -0.01em`                  |
| h2 (section)       | Bitter         | `1.85rem`                     | 700    | 1.2         |                                            |
| h3 (subsection)    | Bitter         | `1.15rem`                     | 600    | 1.25        | `margin-top: 2.5rem`                       |
| h4 (card title)    | Source Sans 3  | `0.8rem`                      | 600    |             | Uppercase, `letter-spacing: 0.06em`        |
| Body paragraph     | Source Sans 3  | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono  | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`        |
| Tag                | IBM Plex Mono  | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                   |

---

## Layout

- Container max-width: **900px**, centered, `2rem` horizontal padding
- Section padding: `5rem` vertical, `2px solid var(--border)` top border
- Section label format: `01 — Label`
- Full-bleed max-width: **1100px**
- Border radius: **2px** — barely rounded, like sanded wood edges
- Borders: **2px solid** — sturdy, like wood joinery

---

## Hero Section

- Full viewport height, flex-centered
- **Wood stain stripe:** `::before` creates an 8px top bar with four stain color segments (capture, refine, accent, execute)
- **Wood grain texture:** `::after` creates a subtle vertical grain pattern
- Staggered fade-up animation on load

---

## Standard Components

### Flow Cards

2-column grid of cards with semantic top bars.

- **Container:** `--surface`, `2px solid var(--border)`, `border-radius: 2px`
- **Top bar:** 4px height, colored by semantic class (`.capture`, `.refine`, `.execute`, `.batch`, `.accent`)

### Pipeline

Horizontal row of joined stages with semantic top borders (4px).

- Classes: `.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`
- Sturdy 2px borders, 2px border-radius on first/last

### Callout

Left-bordered blockquote.

- 4px left border in `--accent`
- Faint warm tint background (`rgba(139, 69, 32, 0.06)`)

### Tags

Inline labels with semantic coloring.

- Classes: `.t-capture`, `.t-refine`, `.t-execute`, `.t-batch`
- 2px border, `border-radius: 2px`

### Info Table

Standard data table with mono uppercase headers.

- 2px bottom border on header, 1px `--surface-3` row separators
- First column bold in `--text`

### Diagram Container

Wrapper for SVG diagrams.

- `--surface` background, `2px solid var(--border)`
- `.full-bleed` class extends to 1100px

### Principle List

Numbered list with large accent numerals.

- 2.4rem Bitter numbers in `--accent`
- `--surface` background, 2px border

---

## Unique Components

### Workshop Blueprint Card

A card styled like a workshop drawing on kraft paper.

- **Container:** `--surface-2` background, `2px solid var(--accent)` border, `border-radius: 2px`
- **Grid pattern:** CSS background-image with thin lines at 20px intervals
- **Inner border:** Dashed `::before` pseudo-element at 8px inset
- **Pin corners:** `::after` pseudo-element creates circular accent-colored pins at top corners
- **Title:** `.blueprint-title` — IBM Plex Mono, uppercase, accent-colored, with bottom border
- **Measurements:** `.blueprint-measurement` — mono badges with faint background and 1px border

```html
<div class="blueprint-card">
  <div class="blueprint-title">Drawing No. WB-001 — Workbench Top</div>
  <h3>Project Name</h3>
  <p>Description of the project or drawing.</p>
  <div>
    <span class="blueprint-measurement">72" × 24" × 34"</span>
    <span class="blueprint-measurement">Material: Hard Maple</span>
  </div>
</div>
```

### Dovetail Divider

An SVG section separator with interlocking dovetail joint shapes.

- Two paths: upper board (accent stroke, 2px) and lower board (border stroke, 1.5px)
- Alternating trapezoid teeth create the dovetail pattern
- Container: `max-width: 600px`, centered

```html
<div class="dovetail-divider">
  <svg viewBox="0 0 600 30" xmlns="http://www.w3.org/2000/svg">
    <path d="M0,14 L60,14 L68,2 L92,2 L100,14 L160,14 L168,2 L192,2 L200,14 L260,14 L268,2 L292,2 L300,14 L360,14 L368,2 L392,2 L400,14 L460,14 L468,2 L492,2 L500,14 L600,14"
      fill="none" stroke="#8b4520" stroke-width="2"/>
    <path d="M0,16 L60,16 L68,28 L92,28 L100,16 L160,16 L168,28 L192,28 L200,16 L260,16 L268,28 L292,28 L300,16 L360,16 L368,28 L392,28 L400,16 L460,16 L468,28 L492,28 L500,16 L600,16"
      fill="none" stroke="#b8a888" stroke-width="1.5"/>
  </svg>
</div>
```

### Lumber Stamp Badge

Inline badges styled like lumber grade stamps at the lumber yard.

- **Container:** `display: inline-block`, `3px solid` border, `border-radius: 2px`
- **Font:** Bitter 700, uppercase, `letter-spacing: 0.1em`
- **Default rotation:** `transform: rotate(-2deg)`
- **Color variants:** `.stamp-green`, `.stamp-honey`, `.stamp-cherry`, `.stamp-steel`
- **Rotation variants:** `.stamp-rotate-pos` (+1.5deg), `.stamp-rotate-neg` (-2.5deg)

```html
<span class="lumber-stamp">Grade A</span>
<span class="lumber-stamp stamp-green stamp-rotate-pos">Kiln Dried</span>
<span class="lumber-stamp stamp-honey">Select</span>
<span class="lumber-stamp stamp-cherry stamp-rotate-neg">FAS</span>
<span class="lumber-stamp stamp-steel stamp-rotate-pos">#1 Common</span>
```

### Tool Rack Card

A card displaying items on a horizontal rail, like tools on a pegboard.

- **Container:** `--surface` background, `2px solid var(--border)`, `border-radius: 2px`
- **Rail:** `.rack-rail` — 6px bar in `--accent` at the top
- **Items:** `.rack-items` — flex row, evenly spaced
- **Each item:** `.rack-item` with `::before` (peg circle) and `::after` (hanging wire)
- **Content:** `.rack-icon` (emoji/icon), `.rack-label` (mono, uppercase), `.rack-value` (Bitter, bold)

```html
<div class="tool-rack">
  <div class="rack-rail"></div>
  <div class="rack-items">
    <div class="rack-item">
      <div class="rack-icon">🔨</div>
      <div class="rack-label">Chisel</div>
      <div class="rack-value">1/2"</div>
    </div>
    <!-- more items... -->
  </div>
</div>
```

---

## Summary of Key Patterns

1. **Warm wood backgrounds** — light wood tones from raw pine to aged walnut, every surface feels like sanded wood.
2. **Rich walnut accent** — the deep walnut stain marks primary elements and interactive components.
3. **Wood species semantics** — pine green (fresh/go), maple honey (warm/refine), cherry red (alert/execute), steel blue (tool/info).
4. **Slab serif headings** — Bitter channels the sturdy, reliable feel of a workshop sign.
5. **Sturdy 2px borders** — minimal radius (2px), like sanded wood edges suggesting honest joinery.
6. **Blueprint cards** — grid-lined workshop drawings with pin corners and measurement badges.
7. **Dovetail dividers** — interlocking trapezoid teeth as section separators.
8. **Lumber stamps** — slightly rotated grade badges with thick borders.
9. **Tool rack cards** — pegboard-style item displays with hanging pegs and rail.
