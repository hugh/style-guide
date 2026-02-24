# Arctic / Ice — Style Guide

A light, frosted-glass design system evoking glacial landscapes, ice crystals, and aurora borealis color pops on a pale blue-white canvas. Cold, crystalline, serene.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#f0f4f8` | Page background (ice white with blue tint) |
| `--surface`    | `#e4eaf0` | Cards, panels, diagram containers        |
| `--surface-2`  | `#d8e0e8` | Nested surfaces, deeper frost            |
| `--surface-3`  | `#c8d4e0` | Tertiary surface, ice shadow             |
| `--border`     | `#b0c0d0` | Card borders, frost lines, section dividers |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#0c1828` | Primary text, headings, bold/strong (deep arctic navy) |
| `--text-dim`   | `#3a4e68` | Body paragraphs, secondary descriptions (cold grey-blue) |
| `--text-faint` | `#7088a0` | Labels, metadata, captions (frost grey)         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Colors are inspired by the aurora borealis spectrum.

| Token           | Hex       | Role                                     |
|-----------------|-----------|------------------------------------------|
| `--accent`      | `#0088cc` | Primary accent (Glacial Blue)            |
| `--accent-dim`  | `#0068a8` | Muted glacial blue                       |
| `--capture`     | `#00a878` | Aurora Green — observation, collection   |
| `--capture-dim` | `#008860` | Muted aurora green                       |
| `--refine`      | `#c8a030` | Cold Gold — analysis, refinement         |
| `--refine-dim`  | `#a88020` | Muted cold gold                          |
| `--execute`     | `#c848a0` | Aurora Pink — action, execution          |
| `--execute-dim` | `#a83888` | Muted aurora pink                        |
| `--batch`       | `#2868b8` | Deep Ice Blue — archival, batch          |
| `--batch-dim`   | `#1850a0` | Muted deep ice blue                      |

### Frost & Glass Tokens

| Token            | Value                          | Usage                       |
|------------------|--------------------------------|-----------------------------|
| `--frost-bg`     | `rgba(255, 255, 255, 0.45)`   | Frosted glass card backgrounds |
| `--frost-border` | `rgba(176, 192, 208, 0.5)`    | Frosted glass card borders  |
| `--frost-blur`   | `8px`                          | Backdrop blur amount        |
| `--aurora`       | `linear-gradient(135deg, ...)` | Aurora gradient (green to pink) |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                                  |
|-----------|---------------|------------------------------------------------------|
| Headings  | Outfit        | `Outfit:wght@300;400;500;600;700;800`                |
| Body      | Inter         | `Inter:wght@300;400;500;600`                         |
| Labels    | IBM Plex Mono | `IBM+Plex+Mono:wght@400;500`                        |

### Type Scale & Weights

| Element            | Family        | Size                          | Weight | Line-height | Notes                                     |
|--------------------|---------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Outfit        | `clamp(2.8rem, 8vw, 5.5rem)` | 700    | 1.05        | `letter-spacing: -0.02em`                  |
| h2 (section)       | Outfit        | `2rem`                        | 600    | 1.15        |                                            |
| h3 (subsection)    | Outfit        | `1.15rem`                     | 600    | 1.2         | `margin-top: 2.5rem`                       |
| h4 (card title)    | Inter         | `0.78rem`                     | 600    |             | Uppercase, `letter-spacing: 0.08em`        |
| Body paragraph     | Inter         | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`        |
| Tag                | IBM Plex Mono | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |

---

## Layout

- Container max-width: **900px**, centered, `2rem` horizontal padding
- Section padding: `5rem` vertical, `1px solid var(--border)` top border
- Section label format: `01 — Label`
- Full-bleed max-width: **1100px**
- Border radius: **12px** — soft, rounded like snow-covered edges

---

## Hero Section

- Full viewport height, flex-centered
- **Aurora gradient top bar:** `::before` creates a 6px bar with the aurora gradient (green to cyan to violet to pink)
- **Frost crystal pattern:** `::after` creates subtle radial gradients evoking frost formation
- **Aurora text:** Hero h1 span uses `background-clip: text` with the aurora gradient
- Staggered fade-up animation on load
- Light gradient background from slightly brighter ice blue to the standard `--bg`

---

## Standard Components

### Flow Cards
- 2-column grid, frosted glass background with `backdrop-filter: blur`
- Semantic top bar: `.capture`, `.refine`, `.execute`, `.batch`, `.accent`
- Border-radius: 12px

### Pipeline
- Horizontal stages with frosted glass backgrounds
- Top border matches semantic color
- Rounded ends (12px)

### Callout
- Left border: 4px solid `--accent` (glacial blue)
- Background: faint blue tint
- Rounded right corners (12px)

### Tags
- IBM Plex Mono, uppercase
- Semantic fill + border colors: `.t-capture`, `.t-refine`, `.t-execute`, `.t-batch`

### Principle List
- Frosted glass numbered items
- Number in `--accent`, Outfit font, weight 800

### Info Table
- Full-width, collapsed borders
- Monospace uppercase headers
- First column bold

### Diagram Wrap
- Frosted glass container
- Full-bleed option: `.full-bleed` expands to 1100px

---

## Unique Components

### Frost Card

A card with a frosted glass effect and crystal pattern overlay.

- **Background:** `var(--frost-bg)` (semi-transparent white)
- **Backdrop filter:** `blur(12px)`
- **Border:** `1px solid var(--frost-border)`
- **Border-radius:** `12px`
- **Crystal overlay:** `::before` with multiple radial-gradient spots evoking frost patterns
- **Content:** Label (IBM Plex Mono, accent color) + h4 + paragraph
- **Hover:** Subtle blue box-shadow

```html
<div class="frost-card">
  <div class="frost-label">Label text</div>
  <h4>Card Title</h4>
  <p>Card content text.</p>
</div>
```

### Icicle Divider

A horizontal divider with icicle shapes hanging from a frost line.

- **Container:** `.icicle-divider`, max-width 600px, centered
- **SVG:** Horizontal line at top with pointed triangle shapes hanging down
- **Gradient:** Each icicle uses a linearGradient from `--border` at 60% opacity to transparent
- **Variation:** Icicles have varying heights (14–34px) for organic feel

```html
<div class="icicle-divider">
  <svg viewBox="0 0 600 40" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <linearGradient id="icicle-grad" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0%" stop-color="#b0c0d0" stop-opacity="0.6"/>
        <stop offset="100%" stop-color="#b0c0d0" stop-opacity="0"/>
      </linearGradient>
    </defs>
    <line x1="0" y1="2" x2="600" y2="2" stroke="#b0c0d0" stroke-width="1" stroke-opacity="0.5"/>
    <polygon points="40,2 44,22 36,22" fill="url(#icicle-grad)"/>
    <!-- more icicle polygons... -->
  </svg>
</div>
```

### Snowflake Marker

A section marker with a geometric snowflake SVG centered between thin frost-colored rules.

- **Container:** `.snowflake-marker`, flex row with gap
- **Rules:** 1px solid `--border`, flex-grow fills space
- **Snowflake:** 32x32 SVG with 6-fold symmetry
  - Three axes at 0°, 60°, 120° with branch tips
  - Central hexagon
  - Stroke: `--accent` (glacial blue), 1.2px width

```html
<div class="snowflake-marker">
  <div class="snowflake-rule"></div>
  <svg viewBox="0 0 32 32" ...><!-- snowflake SVG --></svg>
  <div class="snowflake-rule"></div>
</div>
```

### Aurora Badge

An inline pill-shaped badge with a northern lights gradient and soft glow.

- **Shape:** Pill (border-radius: 100px)
- **Background:** Aurora gradient (green → cyan → violet → pink)
- **Text:** White, IBM Plex Mono, uppercase
- **Glow:** `box-shadow` with aurora-colored soft glow
- **Variants:**
  - `.ab-full` — Full aurora spectrum gradient
  - `.ab-green` — Green to cyan segment
  - `.ab-violet` — Cyan to violet segment
  - `.ab-pink` — Violet to pink segment

```html
<span class="aurora-badge ab-full">Aurora Borealis</span>
<span class="aurora-badge ab-green">Green Band</span>
<span class="aurora-badge ab-violet">Violet Band</span>
<span class="aurora-badge ab-pink">Pink Band</span>
```

---

## SVG Diagram Conventions

- Font: `Inter` for text elements
- Dashed connections: `stroke-dasharray: 4,3`
- Node corners: `rx="12"` (matching border-radius)
- Node fill: `var(--surface)` or `#e4eaf0`
- Border strokes: Semantic colors for category
- Label text: `var(--text-faint)` for secondary info

---

## Summary of Key Patterns

1. **Frosted glass surfaces** — `backdrop-filter: blur` with semi-transparent white backgrounds create depth like looking through ice.
2. **Glacial blue accent** — deep crevasse blue for primary interactive elements.
3. **Aurora color semantics** — green (observation), gold (analysis), pink (action), deep blue (archival) mirror the northern lights spectrum.
4. **Clean geometric headings** — Outfit provides modern warmth against the cold palette.
5. **Crystal patterns** — subtle radial gradients and translucent overlays evoke frost formation.
6. **Light palette, deep contrast** — pale blue-white backgrounds with deep arctic navy text for crisp readability.
7. **Icicle dividers** — organic SVG separators with gradient-faded pointed shapes.
8. **Snowflake markers** — geometric 6-fold symmetry SVG section markers.
9. **Aurora badges** — northern lights gradient pills with soft spectral glow.
