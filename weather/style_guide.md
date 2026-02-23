# Weather Station — Style Guide

A radar-screen meteorology design system — Doppler green accents, barometer gauges, forecast strips, and storm warning callouts for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#0a0e14` | Page background (radar screen dark)      |
| `--surface`    | `#121820` | Cards, panels, diagram containers        |
| `--surface-2`  | `#1a222c` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#242c38` | Tertiary surface, row separators         |
| `--border`     | `#303848` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#d0d4dc` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#7c8494` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#4c5464` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. The green-yellow-red progression mirrors Doppler radar intensity scales.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#40d870` | Primary accent (Radar Green)             |
| `--accent-dim`  | `#28a050` | Muted accent                             |
| `--capture`     | `#40d870` | Clear Green — fair, go, stable           |
| `--capture-dim` | `#28a050` | Muted green                              |
| `--refine`      | `#e0c840` | Advisory Yellow — watch, caution         |
| `--refine-dim`  | `#b8a030` | Muted yellow                             |
| `--execute`     | `#e04040` | Warning Red — severe, danger             |
| `--execute-dim` | `#b82828` | Muted red                                |
| `--batch`       | `#4088d8` | Data Blue — info, pressure, humidity     |
| `--batch-dim`   | `#2868b0` | Muted blue                               |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                                          |
|-----------|---------------|--------------------------------------------------------------|
| Headings  | Outfit        | `Outfit:wght@300;400;500;600;700;800`                        |
| Body      | Inter         | `Inter:wght@300;400;500;600;700`                             |
| Labels    | IBM Plex Mono | `IBM+Plex+Mono:wght@400;500;600`                            |

```html
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&family=Inter:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family        | Size                          | Weight | Line-height | Notes                                     |
|--------------------|---------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Outfit        | `clamp(2.8rem, 8vw, 5.5rem)` | 800    | 1.0         | Default casing, `letter-spacing: -0.01em`  |
| h2 (section)       | Outfit        | `2rem`                        | 700    | 1.15        |                                            |
| h3 (subsection)    | Outfit        | `1.15rem`                     | 700    | 1.2         | `margin-top: 2.5rem`                       |
| h4 (card title)    | Inter         | `0.78rem`                     | 700    |             | Uppercase, `letter-spacing: 0.08em`        |
| Body paragraph     | Inter         | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Hero subtitle      | Inter         | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px       |
| Card body          | Inter         | `0.88rem`                     | 400    | 1.6         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, color: `--text-faint` |
| Hero label         | IBM Plex Mono | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, color: `--accent`      |
| Tag                | IBM Plex Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px solid var(--border)` top border
- Each section opens with a **monospace readout label** in the format `01 — Label`

### Full-Bleed Containers

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: label, h1, subtitle paragraph, version tag
- **Radar rings:** `::before` pseudo-element creates a 500px circle with concentric `box-shadow` rings at 60px, 120px, and 200px in faint green
- **Radar sweep:** `::after` pseudo-element draws a 250px gradient line that rotates 360° over 8 seconds, simulating a Doppler radar sweep
- **Title accent:** The `<span>` inside h1 uses `--accent` color (radar green)
- **Hero label:** Uses `--accent` color (green) instead of `--text-faint`
- **Staggered fade-up animation** on load (0s, 0.15s, 0.3s, 0.45s delays)

---

## Components

### Flow Cards (2-Column Grid)

- **Grid:** 2 columns, `1.5rem` gap. Collapses to 1 column at `640px`.
- **Card:** `--surface` background, `1px solid var(--border)`, `border-radius: 6px`, `padding: 1.5rem`
- **Hover:** Border color lightens to `--text-faint`
- **Top accent bar:** 3px colored bar via `::before`
- **Content:** Icon → h4 title → body paragraph

### Pipeline (Horizontal Stages)

- **Layout:** `display: flex`, stages stretch equally
- **Borders:** First/last get 6px radius on outer edges. Adjacent stages share borders.
- **Top accent:** 3px solid top border with `s-` prefixed semantic class

### Principle / Numbered List

- **Number:** Outfit, `2.4rem`, weight 800, `--accent`
- **Content:** h4 title + body paragraph

### Callout

- Left border: `4px solid var(--accent)`
- Background: `rgba(64, 216, 112, 0.05)`
- `<strong>` uses `--accent` color

### Tags / Pills

- Font: IBM Plex Mono, `0.7rem`, border-radius `3px`
- Background/border/text in semantic color variants

### Tables

- Header: IBM Plex Mono, uppercase, `--text-faint`
- Body first column: `--text`, weight 600

### Diagram Containers

- Background: `--surface`, `border-radius: 6px`, `padding: 2.5rem`

---

## Unique Components

### Barometer Gauge

A circular dial displaying barometric pressure with a trend indicator.

- **Size:** 200px diameter circle
- **Background:** `--surface` with `inset box-shadow: 0 0 24px rgba(0,0,0,0.3)`
- **Border:** `3px solid var(--border)`
- **Outer bezel:** `::before`, `inset: -8px`, `4px solid var(--surface-3)`
- **Inner scale ring:** `::after`, `inset: 12px`, `1px solid var(--border)`
- **Reading (centered):**
  - Value: IBM Plex Mono, `1.8rem`, weight 600, `--accent`
  - Unit: IBM Plex Mono, `0.55rem`, `--text-faint`
  - Label: Outfit, `0.55rem`, weight 600, `--text-faint`
  - Trend: IBM Plex Mono, `0.6rem`, `--capture` (green)

### Forecast Strip

A horizontal multi-day forecast panel showing conditions for each day.

- **Container:** `display: flex`, no gap, `1px solid var(--border)`, `border-radius: 6px`
- **Day panel:** `flex: 1`, `min-width: 120px`, centered, `--surface` background
- **Today variant:** Class `today` adds `--surface-2` background and `3px solid var(--accent)` top border
- **Content per day:**
  - Day label: IBM Plex Mono, `0.65rem`, `--text-faint`
  - Icon: Emoji, `1.8rem`
  - High temp: IBM Plex Mono, `1.3rem`, weight 600, `--text`
  - Low temp: IBM Plex Mono, `0.8rem`, `--text-faint`
  - Condition: `0.7rem`, `--text-dim`

### Storm Warning

A bold alert panel for severe weather warnings with two severity variants.

- **Container:** `border-radius: 6px`, overflow hidden, border in `--execute-dim`
- **Header (severe):** `--execute` background, white text
  - Icon + title (Outfit, `0.8rem`, weight 700, uppercase) + timestamp (IBM Plex Mono, right-aligned)
- **Body:** `--surface` background
  - Description text + data readout in `--execute` color
- **Advisory variant:** Class `advisory` changes header to `--refine` background, border to `--refine-dim`, data readout to `--refine`

### Isobar Divider

An SVG section separator with smooth atmospheric pressure contour lines.

- Three sinusoidal `<path>` elements with decreasing opacity (0.25, 0.15, 0.08)
- Stroke color: `rgba(64,216,112, opacity)`
- Pressure labels (1013, 1008, 1003) in IBM Plex Mono at matching opacity
- Container: `max-width: 600px`, centered

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Border: `1px solid var(--border)`, `border-radius: 3px`
- Color: `--text`

---

## Footer

- Top border: `1px solid var(--border)`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`

---

## Summary of Key Patterns

1. **Radar screen dark** — backgrounds use cool blue-tinted near-blacks with a rotating radar sweep in the hero.
2. **Doppler gradient semantics** — green/yellow/red mirrors radar intensity scales for clear/advisory/warning.
3. **Clean geometric headings** — Outfit delivers modern, data-dashboard headings.
4. **Monospace readouts** — IBM Plex Mono gives labels the feel of METAR reports and weather instruments.
5. **Alert hierarchy** — storm warning panels use NWS-style color coding (red severe, yellow advisory).
6. **Forecast strip layout** — horizontal multi-day panels follow familiar weather app patterns.
7. **Isobar contour motifs** — smooth sinusoidal SVG lines create atmospheric pressure separators.
8. **Barometer gauge motif** — circular instrument dials bring real weather station instruments into the design.
