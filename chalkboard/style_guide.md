# Chalkboard (Dark) -- Style Guide

A dark classroom chalkboard design -- slate-green surfaces, chalk-white text, pastel chalk accents, hand-drawn borders, eraser smudge dividers, and lesson plan components for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#1a2a1e` | Page background (dark slate green)       |
| `--surface`    | `#223428` | Cards, panels, diagram containers        |
| `--surface-2`  | `#2a3e30` | Nested surfaces, chalk tray area         |
| `--surface-3`  | `#324838` | Tertiary surface, lighter panel          |
| `--border`     | `#4a5e50` | Faint chalk line borders                 |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#e8e4d8` | Primary text, headings, bold/strong (warm chalk white) |
| `--text-dim`   | `#a8a498` | Body paragraphs, faded chalk                    |
| `--text-faint` | `#687468` | Labels, metadata, ghost chalk / erased writing  |

### Accent & Semantic Colors (Chalk Sticks)

Each semantic color has full, dim, and transparent-fill variants. Colors represent pastel chalk sticks.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#f0d858` | Primary accent (Yellow Chalk)            |
| `--accent-dim`  | `#c8b040` | Muted yellow chalk                       |
| `--capture`     | `#68d880` | Green Chalk -- introduce, go             |
| `--capture-dim` | `#50b868` | Muted green chalk                        |
| `--refine`      | `#f0d858` | Yellow Chalk -- highlight, refine        |
| `--refine-dim`  | `#c8b040` | Muted yellow chalk                       |
| `--execute`     | `#f07888` | Pink Chalk -- alert, practice            |
| `--execute-dim` | `#d06068` | Muted pink chalk                         |
| `--batch`       | `#68a8e8` | Blue Chalk -- info, review               |
| `--batch-dim`   | `#5088c8` | Muted blue chalk                         |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                                          |
|-----------|---------------|--------------------------------------------------------------|
| Headings  | Patrick Hand  | `Patrick+Hand`                                               |
| Body      | Inter         | `Inter:wght@300;400;500;600;700`                             |
| Labels    | IBM Plex Mono | `IBM+Plex+Mono:wght@400;500;600`                            |

### Type Scale & Weights

| Element            | Family        | Size                          | Weight | Line-height | Notes                                     |
|--------------------|---------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Patrick Hand  | `clamp(2.8rem, 8vw, 5.5rem)` | 400    | 1.1         | Hand-drawn chalk feel                      |
| h2 (section)       | Patrick Hand  | `2rem`                        | 400    | 1.2         |                                            |
| h3 (subsection)    | Patrick Hand  | `1.35rem`                     | 400    | 1.25        | `margin-top: 2.5rem`                       |
| h4 (card title)    | Inter         | `0.78rem`                     | 700    |             | Uppercase, `letter-spacing: 0.08em`        |
| Body paragraph     | Inter         | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`        |
| Tag                | IBM Plex Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |

---

## Layout

- Container max-width: **900px**, centered, `2rem` horizontal padding
- Section padding: `5rem` vertical, `1px dashed var(--border)` top border
- Section label format: `01 -- Label` in monospace
- Full-bleed max-width: **1100px**
- Border radius: **4px** (slightly soft, like chalk-drawn corners)
- All borders use **dashed** style to simulate hand-drawn chalk lines

---

## Hero Section

- Full viewport height, flex-centered
- **Chalk stripe:** `::before` creates a 6px top bar with 4 chalk colors (slightly blurred)
- **Chalk dust glow:** `::after` creates subtle radial gradients of chalk color
- **Noise texture:** `body::after` overlays a subtle grain texture across the entire page
- Staggered fade-up animation on load

---

## Standard Components

### Flow Cards

Two-column grid (`.flow-grid`) of cards with dashed chalk borders and a colored top bar.

- Classes: `.flow-card.capture`, `.flow-card.refine`, `.flow-card.execute`, `.flow-card.batch`, `.flow-card.accent`
- Dashed border style, 4px border-radius
- 3px colored top bar (blurred 0.5px for chalk softness)

### Pipeline

Horizontal stage display (`.pipeline` > `.pipe-stage`).

- Stage classes: `.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`
- 3px colored top border, dashed side borders

### Callout

Yellow-accented sidebar callout (`.callout`).

- 4px solid `--accent` left border
- Faint yellow background tint

### Tags

Inline label pills (`.tag`).

- Classes: `.t-capture`, `.t-refine`, `.t-execute`, `.t-batch`
- IBM Plex Mono, uppercase, 4px radius

### Info Table

Standard data table (`.info-table`).

- Dashed bottom borders on rows
- Monospace uppercase headers

### Diagram Container

SVG diagram wrapper (`.diagram-wrap`).

- Dashed chalk border, 4px radius
- Use `.full-bleed` to expand to 1100px
- SVG diagrams: use dashed strokes (`stroke-dasharray: 6,3`) for chalk-drawn rectangles

### Principle List

Numbered design principles (`.principle-list` > `.principle`).

- Large Patrick Hand number in accent color
- Dashed bordered cards

---

## Unique Components

### Chalk Box

A card drawn with chalk-style dashed borders and a chalk dust smudge at the corner.

- **Container:** `--surface`, `2px dashed var(--border)`, `border-radius: 4px`
- **Title:** Patrick Hand, 1.3rem, `--text`
- **Dust smudge:** `::after` radial gradient at top-right corner
- **Color variants:** `.cb-green`, `.cb-yellow`, `.cb-pink`, `.cb-blue` -- changes border and title color

```html
<div class="chalk-box cb-green">
  <div class="chalk-box-title">Title</div>
  <div class="chalk-box-content"><p>Content here.</p></div>
</div>
```

### Tally Counter

Displays counts using tally marks -- groups of five with the diagonal slash.

- **Container:** Inline-flex, `--surface`, dashed border, 4px radius
- **Marks:** 2px wide, 22px tall lines in `--text`
- **Group of five:** `.tally-group.five` adds a diagonal slash via `::after`
- **Value:** Patrick Hand, 1.6rem, `--accent`

```html
<div class="tally-counter">
  <div class="tally-label">Present</div>
  <div class="tally-marks">
    <div class="tally-group five">
      <div class="mark"></div><div class="mark"></div>
      <div class="mark"></div><div class="mark"></div>
    </div>
    <div class="tally-group">
      <div class="mark"></div><div class="mark"></div>
    </div>
  </div>
  <div class="tally-value">7</div>
</div>
```

### Eraser Divider

A horizontal divider that looks like a chalkboard eraser smudge.

- **Height:** 16px container
- **Effect:** Two pseudo-elements with blurred linear gradients
- **Inner streak:** `::before` -- 4px, blur(3px), 80% width
- **Outer haze:** `::after` -- 8px, blur(6px), 90% width
- Organic, messy -- not a clean line

```html
<div class="eraser-divider"></div>
```

### Lesson Card

A structured lesson plan card with header, objective, and content area.

- **Container:** `--surface`, `2px solid var(--border)`, `border-radius: 4px`
- **Header:** `--surface-2` background, flex row with lesson tag (accent) and date (faint)
- **Objective:** Bordered section with monospace label + Patrick Hand objective text
- **Content:** Standard body text area with list support

```html
<div class="lesson-card">
  <div class="lesson-header">
    <div class="lesson-tag">Lesson 12</div>
    <div class="lesson-date">Mon 23 Feb 2026</div>
  </div>
  <div class="lesson-objective">
    <div class="lesson-objective-label">Objective</div>
    <p>Objective text here.</p>
  </div>
  <div class="lesson-content">
    <p>Lesson content goes here.</p>
  </div>
</div>
```

---

## Summary of Key Patterns

1. **Dark slate-green board** -- deep chalkboard green, warm undertones, like a seasoned classroom board.
2. **Warm chalk white text** -- slightly yellow-tinted, never pure clinical white.
3. **Pastel chalk semantics** -- green (introduce/go), yellow (highlight/refine), pink (alert/practice), blue (info/review).
4. **Hand-written headings** -- Patrick Hand gives a chalk-written, hand-drawn feel.
5. **Dashed chalk borders** -- all borders use dashed styles for hand-drawn simulation.
6. **Chalk dust texture** -- subtle noise grain overlay across the entire page.
7. **Eraser smudge dividers** -- blurred, organic separators instead of clean lines.
8. **Lesson plan cards** -- structured classroom components with header, objective, and content sections.
