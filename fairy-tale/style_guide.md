# Fairy Tale / Storybook — Style Guide

A warm illustrated storybook design — aged parchment backgrounds, gilt page edges, jewel-tone illumination, ornamental borders, and enchanted components for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#f8f0e0` | Page background (aged storybook parchment) |
| `--surface`    | `#efe4d0` | Cards, panels, diagram containers        |
| `--surface-2`  | `#e4d8c0` | Nested surfaces, illustration backgrounds |
| `--surface-3`  | `#d8cab0` | Tertiary surface, deeper panels          |
| `--border`     | `#c0ad8e` | Gilt edge lines, section dividers        |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#1e1810` | Primary text, headings, bold/strong (rich dark ink) |
| `--text-dim`   | `#4a3e30` | Body paragraphs, story prose, descriptions      |
| `--text-faint` | `#8a7e6e` | Chapter numbers, captions, metadata, labels     |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Colors are drawn from fairy tale jewel tones.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#b8860b` | Primary accent (Burnished Gold)          |
| `--accent-dim`  | `#946a08` | Muted gold                               |
| `--capture`     | `#2a7a40` | Enchanted Forest Green — nature, growth  |
| `--capture-dim` | `#1a5a30` | Muted forest green                       |
| `--refine`      | `#b8860b` | Treasure Gold — value, refinement        |
| `--refine-dim`  | `#946a08` | Muted treasure gold                      |
| `--execute`     | `#a82030` | Poisoned Apple Red — danger, action      |
| `--execute-dim` | `#881828` | Muted ruby red                           |
| `--batch`       | `#5a3088` | Magic Purple — mystery, wisdom           |
| `--batch-dim`   | `#482070` | Muted magic purple                       |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                                          |
|-----------|---------------|--------------------------------------------------------------|
| Headings  | Cinzel        | `Cinzel:wght@400;500;600;700;800;900`                        |
| Body      | Crimson Pro   | `Crimson+Pro:wght@300;400;500;600`                           |
| Labels    | IBM Plex Mono | `IBM+Plex+Mono:wght@400;500`                                |

### Type Scale & Weights

| Element            | Family        | Size                          | Weight | Line-height | Notes                                     |
|--------------------|---------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Cinzel        | `clamp(2.4rem, 7vw, 4.5rem)` | 700    | 1.1         | `letter-spacing: 0.02em`                  |
| h2 (section)       | Cinzel        | `1.8rem`                      | 600    | 1.2         |                                            |
| h3 (subsection)    | Cinzel        | `1.15rem`                     | 600    | 1.25        | `margin-top: 2.5rem`                      |
| h4 (card title)    | Crimson Pro   | `0.85rem`                     | 600    |             | Uppercase, `letter-spacing: 0.06em`       |
| Body paragraph     | Crimson Pro   | `1rem`                        | 400    | 1.75        | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`       |
| Tag                | IBM Plex Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |

---

## Layout

- Container max-width: **900px**, centered, `2rem` horizontal padding
- Section padding: `5rem` vertical, `2px solid var(--border)` top border with ornamental leaf (❧) centered above
- Section label format: `01 — Label`
- Full-bleed max-width: **1100px**
- Border radius: **6px** throughout (softly rounded like storybook pages)

---

## Hero Section

- Full viewport height, flex-centered
- **Gilt border:** `::before` creates a 6px gold gradient top bar that fades at edges
- **Parchment texture:** `::after` adds subtle radial gradients in gold, purple, and red
- Staggered fade-up animation on load
- Hero title uses `<span>` for gold accent on key words

---

## Standard Components

### Flow Cards

Two-column grid (`.flow-grid`). Each card has a semantic top bar color.

- `.flow-card.capture` — Enchanted Forest green
- `.flow-card.refine` — Treasure gold
- `.flow-card.execute` — Poisoned Apple red
- `.flow-card.batch` — Magic purple
- `.flow-card.accent` — Burnished gold accent

### Pipeline

Horizontal stages (`.pipeline > .pipe-stage`). Semantic top borders:

- `.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`, `.s-accent`

### Callout

Gold left-border callout (`.callout`). 4px left border, warm gold tinted background.

### Tags

Inline semantic badges (`.tag`):

- `.t-capture` — Forest green
- `.t-refine` — Gold
- `.t-execute` — Ruby red
- `.t-batch` — Magic purple

### Info Table

Standard table (`.info-table`). Mono header, warm parchment alternation.

### Principle List

Numbered items (`.principle-list > .principle`) with large Cinzel numerals in gold.

### Diagram Container

Bordered container (`.diagram-wrap`) with optional `.full-bleed` for 1100px width.

---

## Unique Components

### 1. Illuminated Drop Cap

A large decorative initial letter inspired by illuminated manuscripts.

- **Container:** `.drop-cap-block`
- **Initial:** `.drop-cap` — 5rem Cinzel 800, gold color
- **Border:** 3px double gold border with 4px border-radius
- **Background:** Subtle gold gradient
- **Flourishes:** `::before` and `::after` add ✦ ornaments at top-left and bottom-right corners
- Text wraps around the floated initial

```html
<div class="drop-cap-block">
  <span class="drop-cap">O</span>
  <p>nce upon a time, in a kingdom far away...</p>
</div>
```

### 2. Enchanted Mirror Card

A card with an ornate double-frame border and decorative corner flourishes.

- **Container:** `.mirror-card` — surface background, 2px border, centered text
- **Inner frame:** `::before` creates a 1px gold accent inset border at 6px
- **Top ornament:** `::after` adds ✦ ✦ ✦ centered above the inner frame
- **Corner elements:** `.corner-tl`, `.corner-tr`, `.corner-bl`, `.corner-br` with ❁ characters
- **Content:** `.mirror-title` (Cinzel heading) + `.mirror-body` (italic prose)

```html
<div class="mirror-card">
  <span class="corner-tl">&#10049;</span>
  <span class="corner-tr">&#10049;</span>
  <span class="corner-bl">&#10049;</span>
  <span class="corner-br">&#10049;</span>
  <div class="mirror-title">Card Title</div>
  <p class="mirror-body">Card content in italic prose style.</p>
</div>
```

### 3. Scroll Callout

A callout styled like an unfurled scroll with curled edges.

- **Container:** `.scroll-callout` — surface-2 background, no side borders
- **Top curl:** `::before` — CSS gradient creating a rolled paper effect with bottom border
- **Bottom curl:** `::after` — CSS gradient creating a rolled paper effect with top border
- **Content:** `.scroll-label` (monospace, gold, centered) + `.scroll-title` (Cinzel heading) + `.scroll-body` (centered prose)

```html
<div class="scroll-callout">
  <div class="scroll-label">&#128220; Royal Proclamation</div>
  <div class="scroll-title">Scroll Title</div>
  <p class="scroll-body">Scroll content centered and styled as proclamation text.</p>
</div>
```

### 4. Crown Badge

An inline badge with a crown symbol and gold gradient background.

- **Container:** `.crown-badge` — inline-flex, gold gradient, parchment text, monospace
- **Crown:** `.crown-icon` with ♛ character
- **Variants:**
  - Default: Gold gradient
  - `.cb-capture`: Forest green gradient
  - `.cb-execute`: Ruby red gradient
  - `.cb-batch`: Magic purple gradient (with light text)

```html
<span class="crown-badge"><span class="crown-icon">&#9819;</span> Label Text</span>
<span class="crown-badge cb-capture"><span class="crown-icon">&#9819;</span> Forest</span>
<span class="crown-badge cb-execute"><span class="crown-icon">&#9819;</span> Dragon</span>
<span class="crown-badge cb-batch"><span class="crown-icon">&#9819;</span> Wizard</span>
```

### Bonus: Page-Turn Divider

An SVG section separator with ornamental flower markers flanked by gilt horizontal rules.

- Container: `max-width: 500px`, centered
- Gold lines flanking centered ✽ ✽ ✽ ornaments in Cinzel

```html
<div class="page-turn-divider">
  <svg viewBox="0 0 500 30" xmlns="http://www.w3.org/2000/svg">
    <line x1="0" y1="15" x2="195" y2="15" stroke="rgba(184,134,11,0.3)" stroke-width="1"/>
    <text x="250" y="19" text-anchor="middle" fill="#b8860b" font-family="Cinzel, serif" font-size="12" letter-spacing="0.15em">&#10045; &#10045; &#10045;</text>
    <line x1="305" y1="15" x2="500" y2="15" stroke="rgba(184,134,11,0.3)" stroke-width="1"/>
  </svg>
</div>
```

---

## Summary of Key Patterns

1. **Warm parchment backgrounds** — aged storybook paper tones, like a treasured illustrated volume.
2. **Burnished gold accents** — gilt page edges, treasure hoards, illuminated manuscript pigments.
3. **Jewel-tone semantics** — forest green (nature), treasure gold (value), poisoned apple red (danger), magic purple (mystery).
4. **Regal Cinzel headings** — elegant serifs with fairy-tale gravitas, each heading a chapter title.
5. **Ornamental section borders** — 2px borders with centered leaf (❧) ornaments.
6. **Illuminated drop caps** — 5rem floated initials with double borders and corner flourishes.
7. **Enchanted mirror cards** — double-frame cards with gold inner border and ❁ corners.
8. **Scroll callouts** — unfurled scroll panels with curled CSS gradient edges.
9. **Crown badges** — inline gold-gradient badges with ♛ crown symbols.
10. **Page-turn dividers** — gilt lines flanking ornamental flower markers.
