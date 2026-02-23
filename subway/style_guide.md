# Subway / Metro Transit — Style Guide

A dark transit system design — tunnel grey backgrounds, route-color stripe accents, station signs, arrival boards, and transfer badges for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#1a1a1e` | Page background (dark tunnel grey)       |
| `--surface`    | `#222226` | Cards, panels, diagram containers        |
| `--surface-2`  | `#2a2a2e` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#343438` | Tertiary surface, row separators         |
| `--border`     | `#444448` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#e8e8ec` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#a0a0a8` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#68686e` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Colors are inspired by transit route lines.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#f0c030` | Primary accent (Transit Yellow)          |
| `--accent-dim`  | `#c8a020` | Muted accent                             |
| `--capture`     | `#00a65c` | Line Green — uptown, go                  |
| `--capture-dim` | `#008848` | Muted green                              |
| `--refine`      | `#f0a020` | Line Orange — crosstown, transfer        |
| `--refine-dim`  | `#c88018` | Muted orange                             |
| `--execute`     | `#e03030` | Line Red — express, alert                |
| `--execute-dim` | `#c02020` | Muted red                                |
| `--batch`       | `#2060cc` | Line Blue — downtown, info               |
| `--batch-dim`   | `#1848a8` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                                          |
|-----------|---------------|--------------------------------------------------------------|
| Headings  | Overpass      | `Overpass:wght@300;400;500;600;700;800;900`                  |
| Body      | Inter         | `Inter:wght@300;400;500;600;700`                             |
| Labels    | IBM Plex Mono | `IBM+Plex+Mono:wght@400;500;600`                            |

### Type Scale & Weights

| Element            | Family        | Size                          | Weight | Line-height | Notes                                     |
|--------------------|---------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Overpass      | `clamp(2.8rem, 8vw, 5.5rem)` | 800    | 1.05        | `letter-spacing: -0.02em`                  |
| h2 (section)       | Overpass      | `2rem`                        | 700    | 1.15        |                                            |
| h3 (subsection)    | Overpass      | `1.15rem`                     | 700    | 1.2         | `margin-top: 2.5rem`                       |
| h4 (card title)    | Inter         | `0.78rem`                     | 700    |             | Uppercase, `letter-spacing: 0.08em`        |
| Body paragraph     | Inter         | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`        |
| Tag                | IBM Plex Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |

---

## Layout

- Container max-width: **900px**, centered, `2rem` horizontal padding
- Section padding: `5rem` vertical, `1px solid var(--border)` top border
- Section label format: `01 — Label`
- Full-bleed max-width: **1100px**

---

## Hero Section

- Full viewport height, flex-centered
- **Route color stripe:** `::before` creates an 8px top bar with 4 equal-width route color segments
- **Tunnel tile pattern:** `::after` creates a subtle grid of hairline white lines
- Staggered fade-up animation on load

---

## Unique Components

### Station Sign

A rounded-rectangle sign with station name and line badges.

- **Container:** `--surface`, `3px solid var(--text)`, `border-radius: 24px`, centered padding
- **Line badges:** 28px circles with route color backgrounds and white text
- **Variants:** `lb-red`, `lb-green`, `lb-yellow`, `lb-blue`

### Arrival Board

A dark countdown display showing incoming trains.

- **Container:** `#111114` background, `border-radius: 8px`
- **Header:** `--surface-2`, IBM Plex Mono, flex row
- **Rows:** Line badge (28px circle) + destination (Overpass 600) + time (IBM Plex Mono, `--accent`)

### Turnstile Divider

An SVG section separator with a centered pill-shaped gate marker.

- Horizontal rules in faint accent flanking a rounded rectangle with "ENTER" text
- Container: `max-width: 500px`, centered

### Transfer Badge

An inline pill-shaped badge showing connecting lines.

- **Container:** `--surface`, `2px solid var(--border)`, `border-radius: 24px`
- **Content:** Transfer icon + line dots (18px circles) + "Transfer" label
- Dots use route color backgrounds

---

## Summary of Key Patterns

1. **Dark tunnel backgrounds** — neutral grey with no warm/cool bias, like underground station walls.
2. **Transit yellow accent** — the universal metro wayfinding color.
3. **Route-color semantics** — green (uptown/go), orange (crosstown/transfer), red (express/alert), blue (downtown/info).
4. **Transport heading font** — Overpass channels the clean, functional wayfinding style.
5. **Route stripe hero** — 8px top bar with all four line colors.
6. **Station sign components** — rounded pill frames with line badges.
7. **Arrival board** — dark countdown display with monospace timing.
8. **Transfer badges** — inline connection indicators with route dots.
