# Cassette / Mixtape — Style Guide

Warm analog nostalgia on dark plastic. A design system inspired by cassette tapes and boombox culture — handwritten tracklists, tape spool animations, side A/side B dividers, and VU meter bars for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#1a1816` | Page background (dark cassette shell)    |
| `--surface`    | `#242220` | Cards, panels, diagram containers        |
| `--surface-2`  | `#2e2c28` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#383530` | Tertiary surface, row separators         |
| `--border`     | `#4a4640` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#f0e8d8` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#a89880` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#706858` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                   |
|-----------------|-----------|----------------------------------------|
| `--accent`      | `#e08030` | Primary accent (Warm Orange)           |
| `--accent-dim`  | `#a05820` | Muted accent                           |
| `--capture`     | `#e08030` | Warm Orange — recording, input         |
| `--capture-dim` | `#a05820` | Muted orange                           |
| `--refine`      | `#d8c050` | Cream Yellow — hi-fi, mastering        |
| `--refine-dim`  | `#a09030` | Muted yellow                           |
| `--execute`     | `#c83838` | Tape Red — stop, record button         |
| `--execute-dim` | `#882020` | Muted red                              |
| `--batch`       | `#4888c0` | FM Blue — radio, stereo output         |
| `--batch-dim`   | `#2c6090` | Muted blue                             |

---

## Typography

### Font Stack

| Role      | Family           | Google Fonts Import                               |
|-----------|------------------|-----------------------------------------------------|
| Headings  | Permanent Marker | `Permanent+Marker`                                  |
| Body      | Inter            | `Inter:wght@300;400;500;600`                        |
| Labels    | IBM Plex Mono    | `IBM+Plex+Mono:wght@400;500;600`                    |

```html
<link href="https://fonts.googleapis.com/css2?family=Permanent+Marker&family=Inter:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family           | Size                          | Weight | Line-height | Notes                                     |
|--------------------|------------------|-------------------------------|--------|-------------|-----------------------------------------------|
| Hero h1            | Permanent Marker | `clamp(3rem, 9vw, 6rem)`     | 400    | 1.0         | Accent-colored `<span>` for title word        |
| h2 (section)       | Permanent Marker | `2.2rem`                      | 400    | 1.15        |                                               |
| h3 (subsection)    | Permanent Marker | `1.5rem`                      | 400    | default     | `margin-top: 2.5rem`                          |
| h4 (card title)    | Inter            | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.06em             |
| Body paragraph     | Inter            | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                           |
| Hero subtitle      | Inter            | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px          |
| Section label      | IBM Plex Mono    | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono    | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--accent`      |
| Tag                | IBM Plex Mono    | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                      |

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
- Stacked vertically: tape format label, h1, subtitle, version
- **Magnetic tape texture:** Faint horizontal lines and vertical fold marks via `::before`, simulating the parallel tracks of magnetic tape
- **LED glow:** Centered radial gradient via `::after` in warm orange at very low opacity, evoking a boombox LED display
- **Title accent:** `<span>` inside h1 uses `--accent` (warm orange)
- **Staggered fade-up animation** on load (same as other themes)

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Mixtape-specific adjustments:
- Border-radius: `6px` (slightly rounded, like molded plastic edges)
- Hover glow uses warm orange: `rgba(224, 128, 48, 0.15)`
- Principle numbers use Permanent Marker at `2.2rem` instead of the heading font

---

## Unique Components

### Cassette Label

A tape label card with handwritten tracklist.

- **Container:** `--surface` background, `1px solid var(--border)`, `border-radius: 8px`
- **Header:** `--surface-2` background, flex row with Permanent Marker title (1.1rem, accent) and IBM Plex Mono metadata (0.6rem, faint)
- **Tracklist:** Ordered list with no default styling. Each item is a flex row:
  - Track number: IBM Plex Mono, `0.65rem`, faint, right-aligned in `1.5rem` width
  - Track name: Permanent Marker, `0.9rem`, primary text color
  - Duration: IBM Plex Mono, `0.65rem`, faint
- **Row separators:** `1px dashed var(--surface-3)`

### Side Divider

A labeled section break for side A / side B.

- **Container:** Flex row with `align-items: center`, `1.25rem` gap
- **Lines:** Flex: 1, `2px` height, dashed `repeating-linear-gradient` pattern in border color
- **Label:** Permanent Marker, `1rem`, accent color, `2px solid var(--accent)` border, `border-radius: 20px` (pill shape), `--bg` background

### Tape Deck

VU-meter-style progress bars.

- **Container:** `--surface` background, `1px solid var(--border)`, `border-radius: 8px`, `1.5rem` padding
- **Label:** IBM Plex Mono, `0.7rem`, uppercase, faint
- **Bars:** Flex column, `0.75rem` gap
- **Each bar:** Flex row with label (5.5rem, right-aligned), track, and percentage
- **Track:** `--surface-2` background, `1px solid var(--border)`, `22px` height, `border-radius: 4px`
- **Fill:** Gradient from dim to full semantic color. Classes: `.fill-capture`, `.fill-refine`, `.fill-execute`, `.fill-batch`

### Tape Spool

Animated spinning spool pair.

- **Container:** Centered, `max-width: 400px`
- **Spools:** `80x80px` circles, `3px solid var(--border)`, with inner `24x24px` hub circle
- **Animation:** CSS `@keyframes spin` — left spool rotates at 4s, right spool at 2.5s (simulating tape transfer)
- **Tape bridge:** Horizontal line connecting the two spools
- **Status:** IBM Plex Mono, `0.7rem`, accent, uppercase with play icon

### Boombox Knobs

Dial-style indicators.

- **Row:** Flex row, `2rem` gap, centered, wrapping
- **Dial:** `56x56px` circle, `--surface-2` background, `2px solid var(--border)`
- **Pointer:** `::after` pseudo-element — `2px × 16px` bar in accent color, `transform-origin: bottom center`
- **Position classes:** `.pos-1` through `.pos-5` rotate the pointer from -60deg to +60deg in 30deg increments
- **Label:** IBM Plex Mono, `0.6rem`, uppercase, faint

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--accent` (warm orange)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Dark plastic shell** — backgrounds use warm brown-tinted charcoals like cassette housing plastic.
2. **Warm orange glow** — the primary accent is inspired by tape labels, VU needles, and boombox LEDs.
3. **Three-tier text** — warm cream (--text), dim (--text-dim), faint (--text-faint).
4. **Handwritten headings** — Permanent Marker delivers the feel of tracklists scrawled on a tape label with a felt-tip pen.
5. **Clean body text** — Inter provides crisp readability like printed liner notes beside a hand-labeled tape.
6. **Analog audio semantics** — warm orange (recording), cream yellow (hi-fi), tape red (stop/record), FM blue (stereo).
7. **Tape artifacts** — cassette labels, spinning spools, side A/B dividers, VU meter bars, and boombox knobs bring real analog equipment into the design.
8. **Magnetic tape texture** — faint horizontal lines in the hero evoke the parallel tracks of magnetic recording tape.
