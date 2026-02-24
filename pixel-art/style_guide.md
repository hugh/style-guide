# Pixel Art / Game Boy -- Style Guide

A 4-color restricted palette design system inspired by the original Game Boy DMG-01 screen. Pixel fonts, chunky borders, dithered pattern fills, and sprite-sheet components for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces (Game Boy 4-Shade Palette)

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#c4cfa1` | Page background (GB lightest -- "white") |
| `--surface`    | `#8b956d` | Cards, panels, diagram containers        |
| `--surface-2`  | `#555f44` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#343d27` | Darker panels                            |
| `--border`     | `#2b331f` | Card borders, section dividers (GB darkest -- "black") |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#1a2010` | Primary text, headings, strong emphasis         |
| `--text-dim`   | `#2b331f` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#555f44` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Since Game Boy is monochrome, semantic roles are differentiated by shade rather than hue. Dither pattern backgrounds add further visual distinction.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#1a2010` | Primary accent (darkest shade)           |
| `--accent-dim`  | `#2b331f` | Muted accent                             |
| `--capture`     | `#2b331f` | Darkest -- primary semantic              |
| `--capture-dim` | `#1a2010` | Muted capture                            |
| `--refine`      | `#555f44` | Medium-dark semantic                     |
| `--refine-dim`  | `#343d27` | Muted refine                             |
| `--execute`     | `#1a2010` | Blackest -- critical/alert semantic      |
| `--execute-dim` | `#2b331f` | Muted execute                            |
| `--batch`       | `#8b956d` | Medium-light semantic                    |
| `--batch-dim`   | `#555f44` | Muted batch                              |

---

## Typography

### Font Stack

| Role      | Family         | Google Fonts Import                      |
|-----------|----------------|------------------------------------------|
| Headings  | Press Start 2P | `Press+Start+2P` (400)                   |
| Body      | Inter          | `Inter:wght@400;500;600`                 |
| Labels    | Press Start 2P | Same as headings                         |

### Type Scale & Weights

| Element            | Family         | Size                          | Weight | Line-height | Notes                              |
|--------------------|----------------|-------------------------------|--------|-------------|------------------------------------|
| Hero h1            | Press Start 2P | `clamp(1.4rem, 5vw, 2.4rem)` | 400    | 1.4         |                                    |
| h2 (section)       | Press Start 2P | `1rem`                        | 400    | 1.5         |                                    |
| h3 (subsection)    | Press Start 2P | `0.7rem`                      | 400    | 1.5         | `margin-top: 2.5rem`              |
| h4 (card title)    | Press Start 2P | `0.55rem`                     | 400    | 1.6         | Uppercase, `letter-spacing: 0.04em`|
| Body paragraph     | Inter          | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                |
| Section label      | Press Start 2P | `0.55rem`                     | 400    | 1.8         | Uppercase, `letter-spacing: 0.1em` |
| Tag                | Press Start 2P | `0.45rem`                     | 400    | 1.8         | `letter-spacing: 0.04em`          |

**Note:** Press Start 2P only has weight 400. It is a bitmap pixel font and does not support bold/italic variants.

---

## Layout

- Container max-width: **900px**, centered, `2rem` horizontal padding
- Section padding: `5rem` vertical, `4px solid var(--border)` top border
- Section label format: `01 -- Label` (Press Start 2P)
- Full-bleed max-width: **1100px**
- Base grid unit: **8px** -- all spacing should be multiples of 8
- Border radius: **0px** everywhere -- pixel-sharp corners only
- Border width: **2-4px** solid -- thick pixel borders

---

## Hero Section

- Full viewport height, flex-centered
- **Pixel grid overlay:** `::before` creates a faint 8px grid pattern using repeating linear gradients
- **Top border bar:** `::after` creates an 8px solid bar in `--border` color
- Staggered fade-up animation on load

---

## Standard Components

### Flow Cards

Two-column grid of cards with semantic top bar. Classes: `.capture`, `.refine`, `.execute`, `.batch`, `.accent`.

- **Background:** `--surface`
- **Border:** `3px solid var(--border)`, radius 0
- **Top bar:** 4px colored stripe via `::before`
- **Title:** Press Start 2P, 0.55rem

### Pipeline

Horizontal stage display with semantic top borders.

- **Stage classes:** `.s-capture`, `.s-refine`, `.s-execute`, `.s-batch`
- **Border:** 3px solid, radius 0
- **Stage name:** Press Start 2P

### Callout

- **Border:** 3px solid `--border`, 6px left border in `--text`
- **Background:** `--surface`
- **Radius:** 0

### Tags

- **Font:** Press Start 2P, 0.45rem
- **Border:** 2px solid, radius 0
- **Classes:** `.t-capture`, `.t-refine`, `.t-execute`, `.t-batch`

### Info Table

- **Header font:** Press Start 2P, 0.45rem
- **Border:** 3px bottom on header, 2px between rows
- **First column:** `--text` color, weight 600

### Diagram Container

- **Background:** `--surface`
- **Border:** 3px solid `--border`, radius 0
- **Full-bleed variant:** `.full-bleed` for 1100px max-width

### Principle List

- **Numbered items** with Press Start 2P number
- **Border:** 3px solid, radius 0

---

## Unique Components

### Dialogue Box

An RPG-style text box with double-border effect.

- **Container:** `--bg` background, `4px solid var(--border)` outer border, `inset box-shadow` creates inner border
- **Speaker name:** `.dialogue-speaker` -- Press Start 2P, 0.55rem, uppercase
- **Text:** `.dialogue-text` -- Inter, 0.95rem
- **Cursor:** `.dialogue-cursor` -- blinking down-arrow at bottom-right, `animation: blink 1s step-end infinite`

```html
<div class="dialogue-box">
  <div class="dialogue-speaker">Character Name</div>
  <div class="dialogue-text">Dialogue text goes here.</div>
  <div class="dialogue-cursor">&#9660;</div>
</div>
```

### Sprite Card

A card styled like a sprite sheet cell with pixel grid background.

- **Container:** `--bg` background, `3px solid var(--border)`, width 128px
- **Sprite area:** `.sprite-area` -- 96px height, 8px grid pattern overlay, centered content
- **Label:** `.sprite-label` -- Press Start 2P, 0.4rem, `--surface` background, format: `SPR XX,YY`

```html
<div class="sprite-card">
  <div class="sprite-area">&#9818;</div>
  <div class="sprite-label">SPR 00,00</div>
</div>
```

### Save Point Marker

A section divider with pixel-art cross icons flanking centered text.

- **Layout:** flexbox with dotted lines via `::before`/`::after`
- **Icon:** `.save-icon` -- 24x24px pixel cross made with CSS `box-shadow` technique
- **Text:** `.save-text` -- Press Start 2P, 0.5rem, "SAVE POINT"
- **Dotted lines:** `3px dotted var(--border)`

```html
<div class="save-point">
  <div class="save-icon"></div>
  <div class="save-text">SAVE POINT</div>
  <div class="save-icon"></div>
</div>
```

### HP Bar

A horizontal gauge styled like a video game health/status bar.

- **Label:** `.hp-label` -- Press Start 2P, 0.5rem, min-width 2.5rem
- **Track:** `.hp-track` -- `--bg` background, `3px solid var(--border)`, height 16px
- **Fill:** `.hp-fill` -- `--text` color by default, set width via inline style
- **Value:** `.hp-value` -- Press Start 2P, 0.45rem, right-aligned
- **Variants:** `.shade-dark`, `.shade-medium`, `.shade-light` for different fill shades
- **Critical state:** Add `.low` to `.hp-fill` for blinking animation

```html
<div class="hp-bar">
  <div class="hp-label">HP</div>
  <div class="hp-track"><div class="hp-fill" style="width: 75%;"></div></div>
  <div class="hp-value">150/200</div>
</div>
```

---

## Dither Pattern Utilities

Three utility classes for adding checkerboard dither pattern backgrounds:

| Class            | Pattern Color | Usage                    |
|------------------|---------------|--------------------------|
| `.dither-light`  | `--surface`   | Light dither overlay     |
| `.dither-medium` | `--surface-2` | Medium dither overlay    |
| `.dither-dark`   | `--border`    | Dark dither overlay      |

Each creates a 4x4px repeating checkerboard pattern using inline SVG data URIs.

---

## Summary of Key Patterns

1. **4-color constraint** -- everything renders in 4 shades of green-grey, recreating the Game Boy DMG-01 screen.
2. **Pixel-sharp edges** -- border-radius is always 0px. Every corner is square.
3. **8px grid system** -- the tile size used by Game Boy hardware for sprites and backgrounds.
4. **Pixel font headings** -- Press Start 2P for authentic bitmap typography.
5. **Thick pixel borders** -- 2-4px solid borders give a chunky, hardware-rendered feel.
6. **Game UI components** -- dialogue boxes, sprite cards, save points, and HP bars.
7. **Dither patterns** -- checkerboard SVG patterns simulate hardware dithering.
8. **Monochrome semantics** -- roles differentiated by shade, not color.
