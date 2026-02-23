# Kodachrome / Film Photography — Style Guide

A warm, saturated color film photography design system — rich Kodachrome colors on aged cream backgrounds, slide mounts, sprocket strips, contact sheets, and light leak badges for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                       |
|----------------|-----------|---------------------------------------------|
| `--bg`         | `#faf5eb` | Page background (warm cream, aged photo paper) |
| `--surface`    | `#f0ead8` | Cards, panels, diagram containers           |
| `--surface-2`  | `#e8e0cc` | Nested surfaces, secondary panels           |
| `--surface-3`  | `#ddd4be` | Tertiary surface, deeper panels             |
| `--border`     | `#c8b898` | Card borders, section dividers (warm tan)   |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#1a1408` | Primary text, headings, bold/strong (deep warm brown-black) |
| `--text-dim`   | `#5a4e38` | Body paragraphs, descriptions (warm brown)     |
| `--text-faint` | `#8a7e68` | Labels, metadata, captions (muted tan)         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Colors are inspired by Kodachrome slide film's signature saturated rendition.

| Token           | Hex       | Role                                          |
|-----------------|-----------|-----------------------------------------------|
| `--accent`      | `#c83020` | Primary accent (Kodachrome Red)               |
| `--accent-dim`  | `#a02818` | Muted accent                                  |
| `--capture`     | `#2a8838` | Kodachrome Green — lush vegetation            |
| `--capture-dim` | `#1a6828` | Muted green                                   |
| `--refine`      | `#d0a010` | Kodachrome Yellow — warm saturated sunlight   |
| `--refine-dim`  | `#a88008` | Muted yellow                                  |
| `--execute`     | `#c83020` | Kodachrome Red — saturated warm red           |
| `--execute-dim` | `#a02818` | Muted red                                     |
| `--batch`       | `#1860a8` | Kodachrome Blue — rich sky blue               |
| `--batch-dim`   | `#104888` | Muted blue                                    |

### Film-Specific Tokens

| Token              | Hex/Value                    | Usage                          |
|--------------------|------------------------------|--------------------------------|
| `--film-base`      | `#2a2218`                    | Dark film base color           |
| `--film-base-light`| `#3a3028`                    | Lighter film base              |
| `--orange-mask`    | `rgba(180, 100, 30, 0.08)`  | Orange mask tint for contact sheets |
| `--slide-mount`    | `#3a3028`                    | Slide mount cardboard color    |
| `--slide-mount-light` | `#504838`                 | Lighter mount variant          |

---

## Typography

### Font Stack

| Role      | Family         | Google Fonts Import                                          |
|-----------|----------------|--------------------------------------------------------------|
| Headings  | Libre Franklin | `Libre+Franklin:wght@400;500;600;700;800`                    |
| Body      | Source Serif 4 | `Source+Serif+4:wght@400;500;600`                            |
| Labels    | IBM Plex Mono  | `IBM+Plex+Mono:wght@400;500;600`                            |

### Type Scale & Weights

| Element            | Family         | Size                          | Weight | Line-height | Notes                                     |
|--------------------|----------------|-------------------------------|--------|-------------|--------------------------------------------|
| Hero h1            | Libre Franklin | `clamp(2.8rem, 8vw, 5.5rem)` | 800    | 1.05        | `letter-spacing: -0.02em`                  |
| h2 (section)       | Libre Franklin | `2rem`                        | 700    | 1.15        |                                            |
| h3 (subsection)    | Libre Franklin | `1.15rem`                     | 700    | 1.2         | `margin-top: 2.5rem`                       |
| h4 (card title)    | Source Serif 4 | `0.85rem`                     | 600    |             | Uppercase, `letter-spacing: 0.06em`        |
| Body paragraph     | Source Serif 4 | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                        |
| Section label      | IBM Plex Mono  | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`        |
| Tag                | IBM Plex Mono  | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                  |

---

## Layout

- Container max-width: **900px**, centered, `2rem` horizontal padding
- Section padding: `5rem` vertical, `1px solid var(--border)` top border
- Section label format: `01 — Label` in IBM Plex Mono
- Full-bleed max-width: **1100px**
- Border-radius: **4px** (slightly rounded, like photo corners)

---

## Hero Section

- Full viewport height, flex-centered
- **Kodachrome color stripe:** `::before` creates an 8px top bar with 4 equal-width segments (red, yellow, green, blue)
- **Film grain texture:** `::after` creates subtle warm color radials and a fractal noise grain overlay
- Staggered fade-up animation on load

---

## Standard Components

### Flow Cards
- 2-column grid with 1.5rem gap
- `--surface` background, `1px solid var(--border)`, `border-radius: 4px`
- 3px semantic top bar via `::before`
- Semantic classes: `.capture`, `.refine`, `.execute`, `.batch`, `.accent`
- Hover: brighter border + subtle shadow

### Pipeline
- Horizontal flex with connected stages
- 3px semantic top border
- First/last stages have 4px rounded corners on their outer edges

### Callout
- 4px left border in `--accent`
- Background: `rgba(200, 48, 32, 0.05)`
- Strong text inherits `--accent` color

### Tags
- IBM Plex Mono, 0.7rem, uppercase
- Semantic variants: `.t-capture`, `.t-refine`, `.t-execute`, `.t-batch`
- Each uses the corresponding fill/color/border-color triplet

### Info Table
- Full width, collapsed borders
- Header: IBM Plex Mono, 0.7rem, uppercase, faint color
- First column: `--text` color, weight 600

### Diagram Wrap
- `--surface` background, 1px border, 4px radius
- 2.5rem padding, `overflow-x: auto`
- `.full-bleed` variant expands to 1100px

### Principle List
- Vertical stack of numbered items
- Large accent-colored number (Libre Franklin 900, 2.4rem)
- Title + description in surface panel

---

## Unique Components

### Slide Mount

A card resembling a 35mm slide mount — dark cardboard-colored frame with a bright content window.

- **Outer frame:** `--slide-mount` (#3a3028) background, `border-radius: 6px`, 16px padding
- **Mount label:** IBM Plex Mono, 0.6rem, uppercase, semi-transparent white text — displays film type
- **Content window:** `--bg` background, 2px border in `--film-base-light`, 2px radius, 1.25rem padding
- **Window overlay:** `::after` adds subtle Kodachrome warm tint (yellow-to-red gradient)
- **Frame number:** IBM Plex Mono, 0.55rem, right-aligned, very faint — displays frame/roll ID
- **Grid:** `.slide-mount-grid` provides responsive layout, `minmax(260px, 1fr)`

```html
<div class="slide-mount">
  <div class="mount-label">Kodachrome 64 · KR</div>
  <div class="mount-window">
    <h4>Title</h4>
    <p>Description text.</p>
  </div>
  <div class="mount-frame-num">KR 64 • 24A</div>
</div>
```

### Sprocket Strip

A horizontal film strip divider with sprocket holes along top and bottom edges.

- **Container:** `--film-base` (#2a2218) background, 2px radius
- **Sprocket holes:** Rows of 10px × 7px rectangles in `--bg` color, 1.5px radius, evenly spaced
- **Content area:** 3px gap between frames, 24px horizontal padding
- **Frames:** 80px × 56px cells in `--surface-2`, 1px radius, with icon and frame number

```html
<div class="sprocket-strip">
  <div class="sprocket-holes">
    <span class="hole"></span><!-- repeat 20 -->
  </div>
  <div class="sprocket-content">
    <div class="sprocket-frame"><span class="frame-icon">📷</span><span class="frame-label">01</span></div>
  </div>
  <div class="sprocket-holes">
    <span class="hole"></span><!-- repeat 20 -->
  </div>
</div>
```

### Contact Sheet

A grid layout mimicking a photographic contact sheet.

- **Container:** `--surface` background, 1px border, 4px radius
- **Header:** `--surface-2` background, flex row with title (IBM Plex Mono uppercase) and metadata
- **Grid:** Auto-fill columns, `minmax(100px, 1fr)`, 2px gap, `--film-base` gap color
- **Frames:** 3:2 aspect ratio, orange-mask tinted background, hover opacity transition
- **Frame numbers:** IBM Plex Mono 0.5rem, bottom-left positioned
- **Selected state:** `.selected` class adds 2px `--accent` inset border via `::after`

```html
<div class="contact-sheet">
  <div class="sheet-header">
    <span class="sheet-title">Roll 14 — Summer Road Trip</span>
    <span class="sheet-meta">KR 64 · 36 exp</span>
  </div>
  <div class="contact-grid">
    <div class="contact-frame"><span class="frame-icon">🌄</span><span class="frame-num">1</span></div>
    <div class="contact-frame selected"><span class="frame-icon">☀️</span><span class="frame-num">2</span></div>
  </div>
</div>
```

### Light Leak Badge

An inline badge with a warm gradient overlay simulating a film light leak.

- **Base:** Rounded pill (20px radius), IBM Plex Mono 0.7rem, uppercase, white text
- **Default gradient:** Orange → red → magenta, warm glow shadow
- **Highlight overlay:** `::after` adds a centered white shine strip
- **Variants:**
  - `.leak-warm` — orange-heavy warm gradient
  - `.leak-cool` — red → magenta → purple gradient
  - `.leak-golden` — yellow → orange → red, dark text

```html
<span class="light-leak">Default</span>
<span class="light-leak leak-warm">Warm</span>
<span class="light-leak leak-cool">Cool</span>
<span class="light-leak leak-golden">Golden</span>
```

---

## Summary of Key Patterns

1. **Warm cream backgrounds** — aged photo paper with golden undertones, like slides on a light table.
2. **Kodachrome red accent** — the iconic saturated warm red for primary emphasis.
3. **Film color semantics** — green (vegetation), yellow (sunlight), red (warmth), blue (sky) map to Kodachrome's signature color rendition.
4. **Mid-century geometric headings** — Libre Franklin channels 1960s–70s film packaging design.
5. **Warm serif body text** — Source Serif 4 provides intimate, readable warmth.
6. **Slide mount cards** — dark cardboard frames with bright content windows.
7. **Sprocket strip dividers** — film base strips with authentic sprocket hole cutouts.
8. **Contact sheet grids** — numbered frames with orange-mask tinting.
9. **Light leak badges** — warm gradient pills with glow effects.
