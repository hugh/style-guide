# Board Game / Tabletop — Style Guide

Felt green and wooden tokens. A design system inspired by tabletop board games — player turn cards, dice rolls, score tracks, and rulebook callouts for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#1a3020` | Page background (felt-green table)       |
| `--surface`    | `#223828` | Cards, panels, diagram containers        |
| `--surface-2`  | `#2a4230` | Nested surfaces, headers                 |
| `--surface-3`  | `#324a38` | Tertiary surface, row separators         |
| `--border`     | `#405840` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#f0ece0` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#a8b898` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#688060` | Labels, metadata, round counters                |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                   |
|-----------------|-----------|----------------------------------------|
| `--accent`      | `#d8a850` | Primary accent (Wooden Token)          |
| `--accent-dim`  | `#a07830` | Muted accent                           |
| `--capture`     | `#58c858` | Roll Green — success, GO, safe         |
| `--capture-dim` | `#388838` | Muted green                            |
| `--refine`      | `#d8a850` | Token Gold — treasure, score, loot     |
| `--refine-dim`  | `#a07830` | Muted gold                             |
| `--execute`     | `#d85040` | Penalty Red — danger, lose turn        |
| `--execute-dim` | `#a03028` | Muted red                              |
| `--batch`       | `#4890d0` | Meeple Blue — player, resource, water  |
| `--batch-dim`   | `#286898` | Muted blue                             |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                               |
|-----------|-----------------|-----------------------------------------------------|
| Headings  | Nunito          | `Nunito:wght@400;500;600;700;800`                   |
| Body      | Quicksand       | `Quicksand:wght@400;500;600;700`                    |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                    |

```html
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;500;600;700;800&family=Quicksand:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                            | Weight | Line-height | Notes                                         |
|--------------------|-----------------|----------------------------------|--------|-------------|-----------------------------------------------|
| Hero h1            | Nunito          | `clamp(3rem, 8vw, 5.5rem)`     | 800    | 1.05        | Accent `<span>` for title word                |
| h2 (section)       | Nunito          | `2rem`                          | 800    | 1.2         |                                               |
| h3 (subsection)    | Nunito          | `1.3rem`                        | 800    | default     | `margin-top: 2.5rem`                          |
| h4 (card title)    | Nunito          | `0.85rem`                       | 700    |             | Uppercase, letter-spacing: 0.06em             |
| Body paragraph     | Quicksand       | `0.95rem`                       | 400    | 1.7         | Color: `--text-dim`                           |
| Hero subtitle      | Quicksand       | `1.05rem`                       | 400    | 1.8         | Color: `--text-dim`, max-width 560px          |
| Section label      | IBM Plex Mono   | `0.75rem`                       | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                        | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--accent`      |
| Tag                | IBM Plex Mono   | `0.7rem`                        | 400    |             | `letter-spacing: 0.06em`                      |

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
- Stacked vertically: game label, h1, subtitle, version
- **Board grid:** Faint 60px green grid lines via `::after`, evoking a game board
- **Warm glow:** Faint radial gradient in gold via `::before`
- **Title accent:** `<span>` inside h1 uses `--accent` (wooden token gold)
- **Staggered fade-up animation** on load

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Board Game-specific adjustments:
- Border-radius: `8px` (rounded, friendly, tactile)
- Hover lift uses `translateY(-2px)` with gold glow: `rgba(216, 168, 80, 0.12)`
- Principle numbers use Nunito at `2.2rem`, weight 800

---

## Unique Components

### Player Turn Card

Player cards showing meeple, name, and score with active turn indicator.

- **Grid:** `repeat(auto-fill, minmax(180px, 1fr))`, `1.25rem` gap
- **Card:** `--surface` background, `2px solid var(--border)`, `border-radius: 10px`, centered text
- **Active:** `.active` class adds accent border, gold box-shadow, and "YOUR TURN" badge via `::after`
- **Meeple colors:** `.p-red`, `.p-blue`, `.p-green`, `.p-yellow` set icon color to semantic colors
- **Score:** IBM Plex Mono, `1.2rem`, weight 600, accent color
- **Hover:** Lifts `translateY(-3px)` with deeper shadow

### Dice Roll

Dice with colored variants and result text.

- **Container:** Flex row with `1rem` gap, flex-wrap
- **Die:** `64x64px`, `border-radius: 10px`, `--text` background (white-ish), Nunito 800 at `1.8rem`, `--bg` color
- **Variants:** `.d-red` (execute bg), `.d-blue` (batch bg), `.d-gold` (refine bg)
- **Shadow:** `0 3px 8px rgba(0,0,0,0.3)` + `inset 0 -2px 0 rgba(0,0,0,0.1)` for depth
- **Result text:** IBM Plex Mono, `0.7rem`, faint, uppercase

### Score Track

Leaderboard with player bars and point totals.

- **Container:** `--surface` background, `1px solid var(--border)`, `border-radius: 8px`
- **Header:** `--surface-2` background, flex row with Nunito title and IBM Plex Mono round counter
- **Rows:** Flex with color dot (`12px` circle), player name, progress bar, point value
- **Bar:** `12px` tall, `--bg` background, `border-radius: 6px`, colored fill at percentage width
- **Points:** IBM Plex Mono, `0.75rem`, weight 600, right-aligned

### Rulebook Callout

Rulebook-style reference panel with page number.

- **Container:** `--surface` background, `1px solid var(--border)`, `border-radius: 8px`
- **Header:** `--surface-2` background, flex row with book icon, Nunito title, IBM Plex Mono page number
- **Body:** Standard paragraph text with optional `.rule-example` block
- **Example block:** `--bg` background, dashed border, IBM Plex Mono, `0.75rem`

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `4px`
- Border: `1px solid var(--border)`
- Color: `--accent` (wooden token gold)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Felt-green table** — backgrounds use warm green tones like the surface of a gaming table.
2. **Wooden token gold** — the primary accent is a warm gold inspired by natural wood game pieces.
3. **Three-tier text** — warm cream (--text), sage dim (--text-dim), forest faint (--text-faint).
4. **Rounded friendly headings** — Nunito Extra Bold delivers warm, approachable, tactile typography.
5. **Soft readable body** — Quicksand provides clean, rounded body text that feels playful yet legible.
6. **Game semantics** — roll green (success), token gold (score), penalty red (danger), meeple blue (player).
7. **Generous border-radius** — 8–10px rounding throughout gives everything a tactile, toylike quality.
8. **Board grid texture** — faint grid lines in the hero evoke a game board surface.
