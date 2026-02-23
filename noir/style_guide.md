# Noir — Style Guide

High-contrast black and white with a single red accent. A design system inspired by film noir case files — typewriter text, manila evidence tags, redacted documents, crime board string connections, and classified stamps for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#0c0c0c` | Page background (deep black)             |
| `--surface`    | `#161616` | Cards, panels, diagram containers        |
| `--surface-2`  | `#1e1e1e` | Nested surfaces, manila shadow           |
| `--surface-3`  | `#2a2a2a` | Tertiary surface, folder edge            |
| `--border`     | `#3a3a3a` | Card borders, section dividers (film grain grey) |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#e8e8e8` | Primary text, headings, bold/strong (harsh white, spotlight) |
| `--text-dim`   | `#a0a0a0` | Body paragraphs, secondary descriptions (cigarette smoke grey) |
| `--text-faint` | `#606060` | Labels, case numbers, metadata, annotations (shadow) |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                  |
|-----------------|-----------|---------------------------------------|
| `--accent`      | `#c82020` | Primary accent (Blood Red)            |
| `--accent-dim`  | `#801414` | Muted accent                          |
| `--capture`     | `#508850` | Evidence Green — cleared, safe        |
| `--capture-dim` | `#305030` | Muted green                           |
| `--refine`      | `#b89030` | Manila Gold — pending, under review   |
| `--refine-dim`  | `#786020` | Muted gold                            |
| `--execute`     | `#c82020` | Blood Red — danger, wanted            |
| `--execute-dim` | `#801414` | Muted red                             |
| `--batch`       | `#4868a0` | Police Blue — authority, procedure    |
| `--batch-dim`   | `#2c4060` | Muted blue                            |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                              |
|-----------|-----------------|---------------------------------------------------|
| Headings  | Courier Prime   | `Courier+Prime:ital,wght@0,400;0,700;1,400;1,700` |
| Body      | Courier Prime   | (same import — unified typewriter aesthetic)       |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                  |

```html
<link href="https://fonts.googleapis.com/css2?family=Courier+Prime:ital,wght@0,400;0,700;1,400;1,700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                     |
|--------------------|-----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Courier Prime   | `clamp(2.8rem, 8vw, 5.5rem)` | 700    | 1.0         | Uppercase. Accent `<span>` for title word  |
| h2 (section)       | Courier Prime   | `2rem`                        | 700    | 1.1         | Uppercase                                  |
| h3 (subsection)    | Courier Prime   | `1.4rem`                      | 700    | default     | `margin-top: 2.5rem`                       |
| h4 (card title)    | Courier Prime   | `0.85rem`                     | 700    |             | Uppercase, letter-spacing: 0.08em          |
| Body paragraph     | Courier Prime   | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Courier Prime   | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Evidence item      | Courier Prime   | `1rem`                        | 700    | default     | Item name on evidence tags                 |
| Section label      | IBM Plex Mono   | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--accent`      |
| Tag                | IBM Plex Mono   | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |
| Case number        | IBM Plex Mono   | `0.7rem`                      | 500    |             | Uppercase, `letter-spacing: 0.15em`, `--refine` |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace case-file label** in the format `01 — Label`

### Full-Bleed Containers

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

### Border-Radius

- **0px on all elements.** No rounded corners anywhere. Sharp, hard-boiled, no softness.

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: case number label, h1, subtitle, version
- **Spotlight cone:** Bright radial gradient from above via `::before`, simulating a single desk lamp or interrogation spotlight illuminating the title
- **Vignette:** Dark radial gradient via `::after` closing in from the edges, creating the feeling of darkness surrounding the content
- **Title accent:** `<span>` inside h1 uses `--accent` (blood red)
- **Staggered fade-up animation** on load

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Noir-specific adjustments:
- Border-radius: `0` (sharp corners on everything)
- Hover effect: subtle manila tint `rgba(184, 144, 48, 0.03)` instead of glow
- Principle numbers use Courier Prime at `2.5rem` instead of a display font
- Table headers use IBM Plex Mono for the uppercase metadata style
- SVG diagram text uses Courier Prime

---

## Unique Components

### Evidence Tag

Police evidence tag with case number, date, item description, and officer fields.

- **Container:** `--surface` background, `1px solid var(--border)`, `border-radius: 0`
- **Manila left strip:** `4px` wide `--refine` colored bar on the left via `::before`
- **Hole punch:** `16px` circle in top-right corner via `::after`, `--bg` fill with `--border` stroke
- **Header:** Flex row with case number (`IBM Plex Mono`, `--refine` color) and date (`IBM Plex Mono`, `--text-faint`)
- **Item name:** Courier Prime, `1rem`, weight 700, `--text`
- **Detail:** `0.82rem`, `--text-dim`
- **Officer line:** IBM Plex Mono, `0.65rem`, uppercase, `--text-faint`, dashed top border
- **Grid:** `.evidence-grid` for 2-column layout, `1.5rem` gap
- **Hover:** `rgba(184, 144, 48, 0.04)` background tint

### Redacted Block

Inline and block-level text redaction with black bars.

#### Inline (`.redacted`)
- `background: var(--text)` (white bar over text)
- `color: transparent`
- `user-select: none`
- `::after` overlay in near-black to create solid bar appearance

#### Block (`.redacted-block`)
- Container: `--surface` background, `1px solid var(--border)`
- Label: IBM Plex Mono, `0.65rem`, uppercase, `--accent`
- Lines: `0.9rem` height bars in `--text` color
- Width modifiers: `.short` (45%), `.medium` (75%), last-child (65%)

### Case Board

Detective's crime board with pinned items connected by string lines.

- **Container:** `--surface` background, `1px solid var(--border)`, `2rem` padding
- **Corkboard texture:** Faint radial gradients in manila/gold via `::before`
- **Board title:** IBM Plex Mono, `0.7rem`, uppercase, `--text-faint`
- **Items grid:** `repeat(auto-fill, minmax(180px, 1fr))`, `2rem` gap
- **Item cards:** `--surface-2` background, `1px solid var(--border)`
  - Red pin marker: `8px` circle in `--accent` positioned at top-center via `::before`
  - Label: IBM Plex Mono, `0.6rem`, uppercase, `--text-faint`
  - Title: Courier Prime, `0.85rem`, weight 700, `--text`
  - Description: `0.75rem`, `--text-dim`
  - Hover: border-color changes to `--accent`
- **String connections:** `.board-connections` flex row
  - `.conn-node`: Courier Prime, `0.75rem`, weight 700, uppercase, `--surface-2` background
  - `.conn-string`: `3rem` width, `2px dashed var(--accent)` top border

### Classified Stamp

Rotated stamp overlay text reading "CLASSIFIED" or "CONFIDENTIAL".

- **Overlay (`.classified-stamp`):** Absolutely positioned at center of `.classified-wrap` parent
  - `transform: translate(-50%, -50%) rotate(-8deg)`
  - Courier Prime, weight 700, `3rem` (or `1.5rem` for `.small`)
  - `--accent` color, `4px solid var(--accent)` border
  - `letter-spacing: 0.25em`, uppercase
  - `opacity: 0.7`, `pointer-events: none`
- **Standalone (`.stamp-block`):** Flex-centered container with `--surface` background
  - `.stamp-text`: Same styling as stamp, `opacity: 0.8`
  - `transform: rotate(-8deg)` on the text element

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `0`
- Border: `1px solid var(--border)`
- Color: `--accent` (blood red)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **High contrast, no mercy** — deep black backgrounds with harsh white text. Pure, cold, neutral greys. Like a spotlight in an interrogation room.
2. **Single red accent** — blood red (#c82020) is the only color accent. It hits like a gunshot against the monochrome.
3. **Zero border-radius** — every element has sharp, hard corners. No softness, no curves, no comfort.
4. **Typewriter everything** — Courier Prime for all headings and body text creates a unified case-file aesthetic, like words hammered out on a Smith Corona.
5. **Manila tint on interaction** — cards gain a subtle warm tint on hover, like pulling a folder into the desk lamp's cone of light.
6. **Case file semantics** — evidence green (cleared), manila gold (pending), blood red (dangerous), police blue (authority).
7. **Redaction & classification** — black bars over text and rotated rubber stamps bring government document vocabulary into the design language.
8. **Spotlight hero** — the hero section uses a bright cone gradient from above with a dark vignette, evoking a single desk lamp in a dark office.
