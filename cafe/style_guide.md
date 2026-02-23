# Cafe / Chalkboard Menu — Style Guide

Chalk-lettered warmth on dark slate green. A design system inspired by cafe chalkboard menus — hand-lettered headings, latte brown accents, menu boards with dotted price lines, and coffee ring dividers for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#2a3428` | Page background (dark slate chalkboard)  |
| `--surface`    | `#323c30` | Cards, panels, diagram containers        |
| `--surface-2`  | `#3a4438` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#424c40` | Tertiary surface, row separators         |
| `--border`     | `#505848` | Card borders, section dividers           |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#f0ece0` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#b0a890` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#787868` | Labels, metadata, captions, annotations         |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.12)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                   |
|-----------------|-----------|----------------------------------------|
| `--accent`      | `#c8a070` | Primary accent (Latte Brown)           |
| `--accent-dim`  | `#907050` | Muted accent                           |
| `--capture`     | `#c8a070` | Latte Brown — warmth, comfort          |
| `--capture-dim` | `#907050` | Muted brown                            |
| `--refine`      | `#d89090` | Pastry Pink — sweet, delicate          |
| `--refine-dim`  | `#a06060` | Muted pink                             |
| `--execute`     | `#c85040` | Espresso Red — bold, intense           |
| `--execute-dim` | `#883028` | Muted red                              |
| `--batch`       | `#58a088` | Herbal Teal — fresh, natural           |
| `--batch-dim`   | `#387060` | Muted teal                             |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                               |
|-----------|-----------------|-----------------------------------------------------|
| Headings  | Kalam           | `Kalam:wght@300;400;700`                            |
| Body      | DM Sans         | `DM+Sans:wght@300;400;500;600`                      |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                    |

```html
<link href="https://fonts.googleapis.com/css2?family=Kalam:wght@300;400;700&family=DM+Sans:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                          | Weight | Line-height | Notes                                         |
|--------------------|-----------------|-------------------------------|--------|-------------|-----------------------------------------------|
| Hero h1            | Kalam           | `clamp(3rem, 9vw, 6rem)`     | 700    | 1.0         | Accent-colored `<span>` for title word        |
| h2 (section)       | Kalam           | `2.2rem`                      | 700    | 1.15        |                                               |
| h3 (subsection)    | Kalam           | `1.5rem`                      | 700    | default     | `margin-top: 2.5rem`                          |
| h4 (card title)    | DM Sans         | `0.85rem`                     | 600    |             | Uppercase, letter-spacing: 0.06em             |
| Body paragraph     | DM Sans         | `0.95rem`                     | 400    | 1.7         | Color: `--text-dim`                           |
| Hero subtitle      | DM Sans         | `1.05rem`                     | 400    | 1.8         | Color: `--text-dim`, max-width 560px          |
| Menu item name     | Kalam           | `1rem`                        | 400    |             | Color: `--text`                               |
| Section label      | IBM Plex Mono   | `0.75rem`                     | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                      | 400    |             | Uppercase, `letter-spacing: 0.2em`, `--accent`      |
| Tag                | IBM Plex Mono   | `0.7rem`                      | 400    |             | `letter-spacing: 0.06em`                      |
| Price              | IBM Plex Mono   | `0.8rem`                      | 500    |             | Color: `--accent`                             |

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
- Stacked vertically: hours label, h1, subtitle, version
- **Chalk dust texture:** Faint radial gradients in chalk-white and latte brown via `::before`, simulating chalk dust on the board
- **Ruled lines:** Faint horizontal lines via `::after` in board color, evoking lined chalkboard sections
- **Title accent:** `<span>` inside h1 uses `--accent` (latte brown)
- **Staggered fade-up animation** on load (same as other themes)

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Cafe-specific adjustments:
- Border-radius: `4px`
- Hover glow uses latte brown: `rgba(200, 160, 112, 0.12)`
- Principle numbers use Kalam at `2.2rem` instead of the heading font

---

## Unique Components

### Menu Board

A chalkboard-style menu card with hand-lettered items and prices.

- **Container:** `--surface` background, `2px solid var(--border)`, `border-radius: 4px`
- **Header:** `--surface-2` background, flex row with Kalam title (1.4rem, 700) and optional IBM Plex Mono badge (accent border)
- **Items:** Flex row with item name (Kalam, 1rem), dotted leader line (flex: 1, `1px dotted var(--border)`), and price (IBM Plex Mono, 0.8rem, accent)
- **Row separators:** `1px dotted var(--surface-3)`

### Daily Special

A featured item callout with centered layout and dashed border.

- **Container:** `--surface` background, `2px dashed var(--accent)`, `border-radius: 4px`, centered text
- **Badge:** IBM Plex Mono, `0.65rem`, uppercase, `--bg` on `--accent` background, `border-radius: 3px`
- **Name:** Kalam, `1.6rem`, 700, `--text`
- **Description:** DM Sans, `0.85rem`, `--text-dim`
- **Price:** IBM Plex Mono, `1.1rem`, 600, `--accent`

### Coffee Ring Divider

A circular stain mark used as a section separator.

- **Container:** `80x80px`, centered
- **Outer ring:** `::before` — `border-radius: 50%`, `3px solid` in accent at 15% opacity, with `box-shadow` for depth
- **Inner ring:** `::after` — slightly smaller circle, `1px solid` in accent at 8% opacity

### Order Ticket

A receipt-style card with itemized content and total.

- **Container:** `--surface` background, `1px solid var(--border)`, `border-radius: 4px`, `max-width: 360px`
- **Header:** `--surface-2` background, flex row with order number (IBM Plex Mono, 0.7rem, accent) and time (IBM Plex Mono, 0.6rem, faint)
- **Items:** Flex row with quantity (IBM Plex Mono, 0.7rem, faint), label (DM Sans, --text), and cost (IBM Plex Mono, --text-dim)
- **Total:** Dashed top border, flex row with bold label and accent-colored amount

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--accent` (latte brown)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Slate green chalkboard** — backgrounds use dark green-tinted tones like a real chalkboard, creating warmth and familiarity.
2. **Latte brown accent** — the primary accent is a warm brown inspired by steamed milk and wooden countertops.
3. **Three-tier text** — chalk-white (--text), dim (--text-dim), faint (--text-faint).
4. **Chalk lettering** — Kalam gives headings the feel of hand-lettered chalkboard menus, slightly imperfect and full of character.
5. **Clean body text** — DM Sans provides crisp readability like printed menus and cafe signage.
6. **Cafe semantics** — latte brown (warmth), pastry pink (sweet), espresso red (bold), herbal teal (fresh).
7. **Cafe artifacts** — menu boards, daily specials, coffee ring stains, and order tickets bring the physical cafe experience into the design.
8. **Chalk dust texture** — faint radial gradients and ruled lines in the hero evoke the dusty surface of a well-used chalkboard.
