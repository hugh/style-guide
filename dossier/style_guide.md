# Dossier — Style Guide

Classified intelligence files on manila paper. A light design system inspired by spy dossiers — rubber stamps, redacted text blocks, surveillance photos, and typewriter typography for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#c8b898` | Page background (manila folder tan)      |
| `--surface`    | `#d4c4a0` | Cards, panels, diagram containers        |
| `--surface-2`  | `#ddd0b0` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#e4d8bc` | Tertiary surface, row separators         |
| `--border`     | `#b0a080` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                            |
|----------------|-----------|--------------------------------------------------|
| `--text`       | `#1a1810` | Primary text, headings, bold/strong content      |
| `--text-dim`   | `#4a4430` | Body paragraphs, secondary descriptions          |
| `--text-faint` | `#7a7058` | Labels, file references, metadata, annotations   |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                   |
|-----------------|-----------|----------------------------------------|
| `--accent`      | `#b82020` | Primary accent (Classified Red)        |
| `--accent-dim`  | `#882020` | Muted accent                           |
| `--capture`     | `#b82020` | Stamp Red — classification, alert      |
| `--capture-dim` | `#882020` | Muted red                              |
| `--refine`      | `#a07818` | Ink Amber — annotation, highlight      |
| `--refine-dim`  | `#705010` | Muted amber                            |
| `--execute`     | `#1a1810` | Redacted Black — censorship, hidden    |
| `--execute-dim` | `#3a3828` | Muted black                            |
| `--batch`       | `#28508a` | Bureau Blue — official, archive        |
| `--batch-dim`   | `#183868` | Muted blue                             |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                                |
|-----------|-----------------|-----------------------------------------------------|
| Headings  | Special Elite   | `Special+Elite`                                     |
| Body      | Courier Prime   | `Courier+Prime:wght@400;700`                        |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                    |

```html
<link href="https://fonts.googleapis.com/css2?family=Special+Elite&family=Courier+Prime:wght@400;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                         |
|--------------------|-----------------|-------------------------------|--------|-------------|-----------------------------------------------|
| Hero h1            | Special Elite   | `clamp(2.8rem, 8vw, 5.5rem)` | 400    | 1.0         | Accent-colored `<span>` for title word        |
| h2 (section)       | Special Elite   | `2rem`                        | 400    | 1.15        | Uppercase, letter-spacing: 0.04em             |
| h3 (subsection)    | Special Elite   | `1.4rem`                      | 400    | default     | `margin-top: 2.5rem`                          |
| h4 (card title)    | IBM Plex Mono   | `0.8rem`                      | 600    |             | Uppercase, letter-spacing: 0.08em             |
| Body paragraph     | Courier Prime   | `0.92rem`                     | 400    | 1.7         | Color: `--text-dim`                           |
| Hero subtitle      | Courier Prime   | `1rem`                        | 400    | 1.8         | Color: `--text-dim`, max-width 560px          |
| Section label      | IBM Plex Mono   | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--accent`      |
| Tag                | IBM Plex Mono   | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                      |

---

## Layout

### Container

- Max-width: **900px**, centered
- Horizontal padding: `2rem`

### Sections

- Vertical padding: `5rem` top and bottom
- Separated by `1px dashed var(--border)` top border (dashed, not solid)
- Each section opens with a **monospace file-reference label** in the format `01 — Label`

### Full-Bleed Containers

- Max-width: **1100px**, auto horizontal margins
- Used with `.diagram-wrap.full-bleed`

---

## Hero Section

- Full viewport height (`min-height: 100vh`), flex-centered
- Stacked vertically: file-reference label, h1, subtitle, version
- **Paper texture:** Faint horizontal fiber lines and vertical fold marks via `::before`, simulating aged manila paper
- **Coffee stain:** Circular radial gradient via `::after` in amber at very low opacity, evoking old paper that has been handled
- **Title accent:** `<span>` inside h1 uses `--accent` (classified red)
- **Staggered fade-up animation** on load (same as other themes)

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Dossier-specific adjustments:
- Border-radius: `1px` (nearly sharp corners — government forms, not design)
- Hover lift uses subtle shadow: `0 2px 8px rgba(26, 24, 16, 0.15)`
- Principle numbers use Special Elite at `2rem` instead of the heading font
- Section borders use dashed lines instead of solid

---

## Unique Components

### Classified Stamp

Rubber-stamp text with slight rotation and double border.

- **Display:** Inline-block, `transform: rotate(-3deg)`, `opacity: 0.85`
- **Font:** Special Elite, `1.3rem`, uppercase, `letter-spacing: 0.15em`
- **Border:** `3px solid var(--accent)`, `border-radius: 2px`
- **Double border:** `::before` pseudo-element with `1px solid` at lower opacity
- **Variants:** Default (red), `.blue` (bureau blue), `.black` (ink black)

### Redacted Text

Inline black bars hiding text content.

- **Inline:** `.redacted` — `background: var(--text)`, `color: transparent`, `user-select: none`
- **Texture:** `::after` pseudo-element with faint vertical stripe pattern
- **Block:** `.redacted-block` — container with surface background for mixing visible and redacted paragraphs
- **Cursor:** `not-allowed` to reinforce the censorship metaphor

### Surveillance Card

Photo cards styled like surveillance evidence.

- **Grid:** `repeat(auto-fill, minmax(200px, 1fr))`, `1.5rem` gap
- **Card:** `--surface` background, `1px solid var(--border)`
- **Paper clip:** `::before` pseudo-element — `16x32px` open rectangle with rounded top, positioned at top-right
- **Photo area:** `aspect-ratio: 4/3`, `--surface-2` background
- **Timestamp overlay:** IBM Plex Mono, `0.55rem`, accent-colored, semi-transparent dark background, positioned bottom-right of photo
- **Info section:** `1rem` padding with ID (IBM Plex Mono, uppercase) and detail paragraph

### Dossier Tab Divider

A centered label between two horizontal lines, like a file folder tab.

- **Container:** Flex row with `align-items: center`, `1rem` gap
- **Lines:** Flex: 1, `1px solid var(--border)`
- **Label:** IBM Plex Mono, `0.65rem`, uppercase, `--text-faint`, `--surface` background, `1px solid var(--border)`, padded

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `1px`
- Border: `1px solid var(--border)`
- Color: `--accent` (classified red)

---

## Footer

- Top border: `1px dashed var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Manila, not white** — backgrounds use warm khaki and tan tones like aged manila folders, creating the feel of a physical intelligence file.
2. **Classified red** — the primary accent is a bold red inspired by rubber stamp ink used on classified documents.
3. **Three-tier text** — ink-dark (--text), dim (--text-dim), faint (--text-faint) on light backgrounds.
4. **Typewriter body** — Courier Prime delivers the feel of documents typed on a government-issue machine.
5. **Rubber-stamp headings** — Special Elite gives headings the irregular, pressed-ink character of a physical stamp.
6. **Intelligence semantics** — stamp red (classification), ink amber (annotation), redacted black (censorship), bureau blue (official).
7. **Spy artifacts** — classified stamps, redacted text, surveillance cards, and dossier tabs bring real intelligence tradecraft into the design.
8. **Paper texture** — faint fiber lines and a coffee-stain gradient in the hero evoke aged documents that have been passed between many hands.
