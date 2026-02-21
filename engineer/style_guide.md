# Engineer — Style Guide

A blueprint-inspired design system with deep navy backgrounds, graph-paper grid overlays, condensed uppercase headings, and the structured precision of architectural and engineering drawings.

---

## Color Palette

### Blueprint Surfaces

| Token         | Hex       | Usage                                    |
|---------------|-----------|------------------------------------------|
| `--bg`        | `#0a1929` | Page background (deep navy)              |
| `--surface`   | `#112240` | Cards, containers, diagram panels        |
| `--surface-2` | `#162d50` | Nested surfaces, code backgrounds        |
| `--border`    | `#1e3a5f` | Card borders, section dividers, table lines |
| `--border-light` | `#264a6e` | Lighter borders for secondary use     |
| `--grid`      | `rgba(255,255,255,0.025)` | Minor grid lines (20px)    |
| `--grid-accent` | `rgba(255,255,255,0.05)` | Major grid lines (100px)  |

### Text

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--text`       | `#e2e8f0` | Primary — headings, labels, specs        |
| `--text-dim`   | `#8ba3c4` | Body paragraphs, descriptions            |
| `--text-faint` | `#4a6a8a` | Metadata, section numbers, grid labels   |

### Blueprint Line (Primary Accent)

| Token        | Hex       | Usage                                     |
|--------------|-----------|-------------------------------------------|
| `--line`     | `#4fc3f7` | H3 headings, diagram strokes, active elements |
| `--line-dim` | `#1a6fa0` | Muted line color, hero label border       |
| `--line-fill` | `rgba(79,195,247,0.08)` | Callout/tag background      |

### Status Colors

Each has full, dim, and fill (8% opacity) variants.

| Token        | Hex       | Meaning                           |
|--------------|-----------|-----------------------------------|
| `--redline`  | `#ef5350` | Revisions, corrections, markups   |
| `--approved` | `#66bb6a` | Approved, signed off, complete    |
| `--caution`  | `#ffb74d` | Warnings, pending, attention      |
| `--note`     | `#ba68c8` | Annotations, references, comments |

---

## Typography

### Font Stack

| Role      | Family           | Google Fonts Import                    |
|-----------|------------------|----------------------------------------|
| Headings  | Barlow Condensed | `Barlow+Condensed:wght@400;500;600;700` |
| Body      | IBM Plex Sans    | `IBM+Plex+Sans:wght@300;400;500;600`  |
| Mono      | IBM Plex Mono    | `IBM+Plex+Mono:wght@400;500`          |

```html
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;500;600;700&family=IBM+Plex+Sans:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Type Scale

| Element        | Family           | Size                          | Weight | Notes                          |
|----------------|------------------|-------------------------------|--------|--------------------------------|
| Hero h1        | Barlow Condensed | `clamp(3rem, 8vw, 5.5rem)`   | 700    | Uppercase, `letter-spacing: 0.06em` |
| Section h2     | Barlow Condensed | `2.2rem`                      | 600    | Uppercase, `letter-spacing: 0.06em` |
| Subsection h3  | Barlow Condensed | `1.3rem`                      | 600    | Uppercase, color: `--line`     |
| Card title h4  | IBM Plex Sans    | `0.85rem`                     | 600    | Uppercase, `letter-spacing: 0.04em` |
| Body           | IBM Plex Sans    | `0.92rem`                     | 400    | Color: `--text-dim`            |
| Card body      | IBM Plex Sans    | `0.82rem`                     | 400    | Color: `--text-dim`            |
| Section label  | IBM Plex Mono    | `0.65rem`                     | 400    | Uppercase, `letter-spacing: 0.25em`, `border-bottom` underline |
| Tag            | IBM Plex Mono    | `0.6rem`                      | 400    | Uppercase, `letter-spacing: 0.08em` |
| Table header   | IBM Plex Mono    | `0.65rem`                     | 500    | Uppercase, `letter-spacing: 0.15em` |

**Key convention:** All headings (h1–h4) use `text-transform: uppercase` with letter-spacing.

---

## Layout

- **Container:** max-width 920px, centered, 2rem horizontal padding
- **Sections:** 5rem vertical padding, `1px solid var(--border)` top divider
- **Grid background:** two-scale `background-image` on body — 20px minor grid and 100px major grid using `linear-gradient` with semi-transparent white
- **Border radius:** zero everywhere — all components have sharp 90-degree corners
- **No shadows:** depth comes from border color differences and grid visibility, not box-shadows
- **Full-bleed:** max-width 1080px for diagram containers

---

## Hero Section

- Full viewport, flex-centered, deep navy background
- Subtle radial gradient glow (cyan, 4% opacity)
- Hero label: monospace, uppercase, with a 1px bordered box (not just text)
- Accent word in h1 via `<span>` in `--line` color
- Version string: monospace, uses "REV XX" format
- Staggered fade-up animation

---

## Components

### Spec Cards (2-Column Grid)

- **Grid:** 2 columns, `1.25rem` gap. Single column at `640px`.
- **Card:** `--surface` background, `1px` border, **no border-radius**, `padding: 1.5rem`
- **No hover effects** — static, precise
- **Top accent bar:** 2px, color set by status class (`line`, `redline`, `approved`, `caution`, `note`)
- **Card label:** monospace uppercase drawing number (e.g., `SPEC-001`)

### Pipeline

- Flex row, no gap — stages share borders (connected strip)
- Each stage: `--surface` background, `1px` border, sharp corners
- Top accent: 2px via `::before`, color from `s-` prefix class
- Labels: phase numbers in monospace, names in Barlow Condensed uppercase

### Spec List (Numbered)

- Vertical stack with **shared borders** (no gap, `border-top: none` on subsequent items)
- Creates a drawing-schedule look
- Numbers: Barlow Condensed, `1.8rem`, weight 700, `--line-dim`

### Callout Variants

Four callout types, each with a different left-border color and tinted background:

| Variant    | Class         | Border Color    | Background         |
|------------|---------------|-----------------|---------------------|
| Default    | `.callout`    | `--line`        | `--line-fill`       |
| Revision   | `.callout.revision` | `--redline` | `--redline-fill` |
| Approval   | `.callout.approval` | `--approved` | `--approved-fill` |
| Warning    | `.callout.warning`  | `--caution`  | `--caution-fill`  |

### Tags

- Monospace, uppercase, bordered — no border-radius
- Background: 8% opacity fill of the status color
- Border: 1px solid dim variant
- Class prefix: `t-` (e.g., `t-line`, `t-redline`)

### Stamps

- Barlow Condensed, weight 700, uppercase, letter-spaced
- 2px border in status color, slight rotation (`transform: rotate`)
- Mimics rubber stamps on engineering documents
- Variants: `.stamp.draft`, `.stamp.review`, `.stamp.revision`, `.stamp.approved`

### Title Block (Standalone)

- CSS Grid with labeled cells, mimicking the title block on engineering drawings
- Each cell: bordered, with a monospace uppercase label and a Barlow Condensed uppercase value
- Use for document metadata (project, drawing number, revision, date)

### Blueprint Container (Diagrams)

- `--surface` background, `1px` border, **no border-radius**, `padding: 2rem`
- **Title block** in the lower-right corner (via `::after` pseudo-element + positioned div)
- Title block shows drawing name + number
- SVG conventions:
  - All text in IBM Plex Mono
  - Nodes: no fill, `--line` stroke, sharp corners (`rx="0"`)
  - Labels: uppercase, letter-spaced, small
  - Connectors: dashed (`stroke-dasharray: 4,3`), `--line` color, small triangle arrowheads

### Tables

- Full width, collapsed borders
- **Headers:** IBM Plex Mono, uppercase, `0.65rem`, letter-spaced, `--text-faint`
- **Cells:** `0.82rem`, `--text-dim`, `1px` bottom border
- **First column:** monospace, `--text`, weight 500 (parameter name style)

---

## Comparison with Vesper and Excalidraw

| Aspect           | Vesper                | Excalidraw              | Engineer                  |
|------------------|-----------------------|-------------------------|---------------------------|
| Theme            | Dark (purple-tint)    | Light (warm white)      | Dark (deep navy)          |
| Background       | Flat                  | Flat                    | Grid overlay              |
| Border radius    | 10–16px               | 8px                     | 0 (sharp corners)         |
| Heading font     | DM Serif Display      | Caveat (handwritten)    | Barlow Condensed (uppercase) |
| Body font        | DM Sans               | Nunito                  | IBM Plex Sans             |
| Mono font        | JetBrains Mono        | Fira Code               | IBM Plex Mono             |
| Color model      | 4 semantic            | 8 stroke + 8 fill       | 1 accent + 4 status       |
| Shadows          | None                  | Three levels            | None                      |
| Unique elements  | —                     | Sticky notes, highlights | Stamps, title blocks, grid |
| Vibe             | Editorial, refined    | Sketch, whiteboard      | Technical, precise         |
