# Terminal — Style Guide

A pure CRT design system with black backgrounds, phosphor green accents, scanline overlays, all-monospace typography, blinking cursor animations, and command-prompt section headers. Intended for developer documentation, system logs, operational dashboards, and anything that should feel like a late-night terminal session.

---

## Color Palette

### CRT Black (Backgrounds)

| Token          | Hex       | Usage                                  |
|----------------|-----------|----------------------------------------|
| `--bg`         | `#080808` | Page background (near-pure black)      |
| `--surface`    | `#101010` | Cards, panels, table rows              |
| `--surface-2`  | `#181818` | Nested surfaces, code backgrounds      |
| `--border`     | `#222222` | Borders, dividers                      |
| `--border-light` | `#2c2c2c` | Lighter borders for emphasis         |

### Text — Gray Phosphor

| Token          | Hex       | Usage                                  |
|----------------|-----------|----------------------------------------|
| `--text`       | `#a0a0a0` | Primary — commands, headings, emphasis |
| `--text-dim`   | `#585858` | Body paragraphs, output, descriptions  |
| `--text-faint` | `#2e2e2e` | Comments, labels, metadata             |

### Phosphor Green (Primary Accent)

| Token           | Hex       | Usage                                   |
|-----------------|-----------|------------------------------------------|
| `--phosphor`    | `#33ff33` | H2 headings, prompts, active status, primary accent |
| `--phosphor-dim`| `#1a8a1a` | H3 headings, muted accents, borders    |
| `--phosphor-fill`| `rgba(51,255,51,0.05)` | Command block backgrounds  |

### ANSI Palette

Each has full, dim, and fill (5% opacity) variants.

| Token      | Hex       | ANSI Name | Typical Use              |
|------------|-----------|-----------|--------------------------|
| `--red`    | `#ff4444` | Red       | Errors, failures, stderr |
| `--amber`  | `#ffaa22` | Yellow    | Warnings, deprecations   |
| `--cyan`   | `#22cccc` | Cyan      | Success, info, done      |
| `--blue`   | `#4488ff` | Blue      | Links, references        |
| `--magenta`| `#cc44cc` | Magenta   | Special, debug           |

### Glow Effects

| Token       | Value                              | Usage                    |
|-------------|------------------------------------|--------------------------|
| `--glow`    | `0 0 10px rgba(51,255,51,0.25)`   | Hero h1 text-shadow      |
| `--glow-dim`| `0 0 5px rgba(51,255,51,0.12)`    | H2, pipe names glow      |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                         |
|-----------|-----------------|---------------------------------------------|
| Display   | VT323           | `VT323`                                     |
| Body      | Fira Code       | `Fira+Code:wght@300;400;500;600;700`       |
| System    | Share Tech Mono | `Share+Tech+Mono`                           |

```html
<link href="https://fonts.googleapis.com/css2?family=VT323&family=Fira+Code:wght@300;400;500;600;700&family=Share+Tech+Mono&display=swap" rel="stylesheet">
```

**Key convention:** Every font in the stack is monospace. No serif or sans-serif anywhere. This is the defining typographic choice of the system.

### Type Scale

| Element        | Family          | Size                          | Weight | Notes                         |
|----------------|-----------------|-------------------------------|--------|-------------------------------|
| Hero h1        | VT323           | `clamp(3rem, 8vw, 5rem)`     | 400    | `text-shadow: var(--glow)`    |
| Section h2     | VT323           | `1.8rem`                      | 400    | `text-shadow: var(--glow-dim)` |
| Subsection h3  | Share Tech Mono | `0.82rem`                     | 400    | Uppercase, `letter-spacing: 0.15em`, color: `--phosphor-dim` |
| Card title h4  | Fira Code       | `0.82rem`                     | 600    |                               |
| Body           | Fira Code       | `0.85rem`                     | 400    | Color: `--text-dim`           |
| PID / number   | VT323           | `1.4rem`                      | 400    | Color: `--text-faint`         |
| Section label  | Share Tech Mono | `0.65rem`                     | 400    | Prefixed with `$ ` via ::before |
| Tag            | Share Tech Mono | `0.6rem`                      | 400    | Uppercase, `letter-spacing: 0.08em` |

---

## Layout

- **Container:** max-width 880px, centered, 2rem horizontal padding
- **Sections:** 5rem vertical padding, `1px solid var(--border)` top divider
- **Border radius:** 0 everywhere — pixels don't curve
- **No shadows** — glow effects via text-shadow only
- **Full-bleed:** max-width 1040px for diagram containers

---

## CRT Effects

### Scanline Overlay

Applied via `body::after` as a fixed pseudo-element:
- `repeating-linear-gradient` with 4px period (3px transparent, 1px dark)
- `opacity: 0.1` for subtlety
- `pointer-events: none` and `z-index: 9999`

### CRT Vignette

Applied via `body::before` as a fixed pseudo-element:
- Radial gradient from transparent center to darkened edges
- Simulates the bezel darkening of a CRT monitor
- `pointer-events: none` and `z-index: 9998`

### Phosphor Glow

- `text-shadow: var(--glow)` on hero h1
- `text-shadow: var(--glow-dim)` on h2 and pipe stage names
- Simulates phosphor bleed/bloom

### Blinking Cursor

- `.cursor` class with `animation: blink 1s step-end infinite`
- Uses block character `█` (U+2588)
- Apply to `<span class="cursor">█</span>` after headings

---

## Hero Section

- Full viewport, flex-centered, pure black background
- Optional boot sequence lines (`.boot-line` with `.ok`, `.fail`, `.warn` spans)
- VT323 heading with phosphor glow and blinking cursor
- Staggered fade-up animation on all children (0.1s intervals)

---

## Components

### Process Table

The signature unique component — a `ps aux` style process listing.

- **Header:** `--surface-2` background, Share Tech Mono uppercase, `--phosphor-dim` text, uptime in Fira Code
- **Rows:** CSS Grid with 5 columns (`70px 1fr 110px 70px 70px`), `--surface` background
- **Status classes:** `.running` (phosphor), `.done` (cyan), `.failed` (red), `.waiting` (amber)
- **Responsive:** CPU and memory columns hide at 640px

### Pipeline

Unix pipe-style process chain.

- Flex row of stages, connected by `|` pipe characters via `::after`
- Stage names in VT323 with phosphor glow
- Numbers in Share Tech Mono, descriptions in Fira Code
- Green top accent bar (2px) on each stage

### Progress Bar

- Flex row: label (Share Tech Mono), track, percentage (Fira Code)
- Track: `--surface-2` background, `1px` border, 8px tall
- Fill: `--phosphor` with glow, width set via inline `style="width: 72%"`
- Color variants: `.amber`, `.red`, `.cyan` on the fill element

### Session Card (Connection)

- `inline-flex` layout, `--surface-2` background, `1px` border
- Local/Remote labels in Share Tech Mono, tiny uppercase
- Hostnames in Fira Code, `--phosphor` color
- Arrow separator in `--text-faint`
- Protocol tag in VT323, `--cyan` color, left-border separated

### Pane Cards (2-Column Grid)

- **Grid:** 2 columns, `1.25rem` gap
- **Card:** `--surface` bg, `1px` border, sharp corners, `1.5rem` padding
- **Top accent bar:** 2px, color from class (`phosphor`, `cyan`, `amber`, `red`, `blue`, `magenta`)
- **PID:** VT323, `1.4rem`, `--text-faint`

### Command Blocks (Callout)

| Variant  | Class              | Border Color     | Background        |
|----------|--------------------|------------------|-------------------|
| Default  | `.cmd-block`       | `--phosphor-dim` | `--phosphor-fill` |
| Error    | `.cmd-block.error` | `--red-dim`      | `--red-fill`      |
| Warning  | `.cmd-block.warning`| `--amber-dim`   | `--amber-fill`    |
| Success  | `.cmd-block.success`| `--cyan-dim`    | `--cyan-fill`     |

Structure: `1px` border, `3px` colored left border, matching fill background.

### Numbered List

- Vertical stack with shared borders (zero gap)
- Numbers: VT323, `1.6rem`, `--phosphor-dim`
- Sharp corners throughout

### Tags

- Share Tech Mono, `0.6rem`, uppercase, letter-spaced
- Bordered with `1px` solid dim color, fill background, sharp corners
- Prefix: `t-` (e.g., `t-phosphor`, `t-cyan`, `t-red`)

### Tables

- Full width, collapsed borders
- **Headers:** Share Tech Mono, uppercase, `0.62rem`, letter-spaced, `--text-faint`
- **Cells:** `0.82rem`, `--text-dim`, `1px` bottom border
- **First column:** `--text`, weight 500

### Diagram Container

- `--surface` background, `1px` border, sharp corners
- Label in Share Tech Mono, small uppercase
- SVG text in Fira Code

---

## Section Label Convention

Section labels use a command-prompt style with a `$ ` prefix added via CSS `::before`:

```
$ ./01-palette
$ ./02-typography
$ ./03-layout
```

The `$ ` is always in `--phosphor` green, the path is in `--phosphor-dim`.

---

## Comparison with All Systems

| Aspect          | Vesper            | Excalidraw        | Engineer            | Mathematician       | Physicist            | Train Station         | Terminal              |
|-----------------|-------------------|-------------------|---------------------|---------------------|----------------------|-----------------------|-----------------------|
| Theme           | Dark (purple)     | Light (white)     | Dark (navy)         | Dark (green)        | Dark (void/black)    | Dark (warm brown)     | Dark (pure black)     |
| Background      | Flat              | Flat              | Grid overlay        | Flat                | Flat                 | Flat                  | Scanlines + vignette  |
| Border radius   | 10–16px           | 8px               | 0                   | 0                   | 4px                  | 0                     | 0                     |
| Heading font    | DM Serif Display  | Caveat            | Barlow Condensed    | EB Garamond         | Space Grotesk        | Stint Ultra Expanded  | VT323                 |
| Body font       | DM Sans           | Nunito            | IBM Plex Sans       | Source Serif 4      | Inter                | Libre Franklin        | Fira Code             |
| Mono font       | JetBrains Mono    | Fira Code         | IBM Plex Mono       | JetBrains Mono      | Space Mono           | Inconsolata           | Share Tech Mono       |
| Letter-spacing  | Normal            | Normal            | Positive (wide)     | Normal              | Negative (tight)     | Natural (expanded)    | Normal                |
| Primary accent  | Purple #c4a0ff    | (multi-color)     | Cyan #4fc3f7        | Yellow #f0d060      | Cyan #22d3ee         | Brass #c8a84c         | Green #33ff33         |
| Color model     | 4 semantic        | 8 stroke + fill   | 1 + 4 status        | 5 chalk             | 1 primary + 5 spectrum| 2 material + 3 signal | 1 primary + 5 ANSI   |
| Unique elements | —                 | Sticky notes      | Stamps, title block | Theorem/proof, QED  | Readout panel, spectrum bar | Departures board, ticket stub | Process table, progress bar |
| Vibe            | Editorial         | Whiteboard        | Technical           | Academic            | Laboratory           | Railway               | Console               |
