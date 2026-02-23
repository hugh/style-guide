# Victorian / Antique — Style Guide

An aged parchment design system — ornate serif typography, wax-seal accents, filigree dividers, ribbon banners, and medallion section markers for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#f4ece0` | Page background (aged parchment)         |
| `--surface`    | `#ece2d4` | Cards, panels, diagram containers        |
| `--surface-2`  | `#e4d8c8` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#d8cab8` | Tertiary surface, row separators         |
| `--border`     | `#c4b498` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#2a2018` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#685848` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#9a8870` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#8b2020` | Primary accent (Wax Seal Burgundy)       |
| `--accent-dim`  | `#6a1818` | Muted accent                             |
| `--capture`     | `#3a7a40` | Ivy Green — flourishing, approved        |
| `--capture-dim` | `#2a5c2e` | Muted green                              |
| `--refine`      | `#b89030` | Antique Gold — craft, refine             |
| `--refine-dim`  | `#907020` | Muted gold                               |
| `--execute`     | `#a83020` | Wax Seal Red — urgent, decree            |
| `--execute-dim` | `#882018` | Muted red                                |
| `--batch`       | `#2a5898` | Royal Blue — authority, archive          |
| `--batch-dim`   | `#1a4078` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family           | Google Fonts Import                                          |
|-----------|------------------|--------------------------------------------------------------|
| Headings  | Playfair Display | `Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;0,800;1,400;1,500` |
| Body      | Lora             | `Lora:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500`       |
| Labels    | IBM Plex Mono    | `IBM+Plex+Mono:wght@400;500;600`                            |

### Type Scale & Weights

| Element            | Family           | Size                          | Weight | Notes                                     |
|--------------------|------------------|-------------------------------|--------|--------------------------------------------|
| Hero h1            | Playfair Display | `clamp(2.8rem, 8vw, 5.5rem)` | 800    | Italic, accent-colored `<span>` non-italic |
| h2 (section)       | Playfair Display | `2rem`                        | 700    |                                            |
| h3 (subsection)    | Playfair Display | `1.15rem`                     | 700    | Italic                                     |
| h4 (card title)    | Lora             | `0.82rem`                     | 700    | Uppercase, `letter-spacing: 0.12em`        |
| Body paragraph     | Lora             | `0.95rem`                     | 400    | `line-height: 1.75`                        |
| Section label      | IBM Plex Mono    | `0.75rem`                     | 400    | Uppercase, `letter-spacing: 0.15em`        |
| Tag                | IBM Plex Mono    | `0.7rem`                      | 400    | `letter-spacing: 0.06em`                  |

---

## Layout

- Container: **900px** max-width, `2rem` horizontal padding
- Sections: `5rem` vertical padding, `1px solid var(--border)` separator
- Border-radius: **2px** throughout (sharp, formal edges)
- Full-bleed: **1100px** for `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height, flex-centered
- **Ornamental rules:** `::before` and `::after` draw gradient lines at 15% from top and bottom with accent-colored center sections
- Title: Playfair Display italic, with accent-colored non-italic `<span>`
- Staggered fade-up animation on load

---

## Unique Components

### Wax Seal

A circular decorative element styled like a pressed wax seal.

- **Size:** 80px diameter circle
- **Background:** `--accent` (burgundy) with inset shadows for depth
- **Letter:** Playfair Display, `2rem`, weight 800, italic, white
- **Edge blur:** `::before` creates soft wax spread effect
- **Label:** IBM Plex Mono, absolute-positioned below

### Ribbon Banner

A horizontal banner with folded ribbon ends for titles and dates.

- **Center:** `--accent` background, Playfair Display `0.85rem`, weight 700, uppercase, white text
- **Ribbon ends:** `::before` and `::after` use `clip-path: polygon()` to create arrow-point folds in `--accent-dim`
- **Padding:** `0.5em 2.5em` for the center text

### Filigree Divider

An SVG section separator with ornamental dots and lines.

- Center cluster of circles at varying sizes and opacities in `--accent`
- Horizontal lines extending from center in `--border`
- Container: `max-width: 400px`, centered

### Medallion

A circular section marker with ornamental double ring.

- **Size:** 100px diameter, `3px double var(--border)` border
- **Outer ring:** `::before`, `inset: -10px`, `1px solid var(--border)`
- **Number:** Playfair Display, `1.6rem`, weight 800, italic, `--accent`
- **Label:** IBM Plex Mono, `0.45rem`, `--text-faint`

---

## Summary of Key Patterns

1. **Aged parchment backgrounds** — warm cream-tan tones evoke antique paper.
2. **Wax seal burgundy accent** — rich dark red marks key elements like a pressed seal.
3. **Ornate serif typography** — Playfair Display italic headings with Lora body create period elegance.
4. **Sharp formal edges** — 2px border-radius keeps the aesthetic crisp and institutional.
5. **Victorian semantics** — ivy green (approved), antique gold (craft), wax red (urgent), royal blue (authority).
6. **Ornamental motifs** — wax seals, ribbon banners, medallions, and filigree dividers bring period decoration into the design.
7. **Heavy decorative rules** — ornamental gradient lines frame the hero section.
