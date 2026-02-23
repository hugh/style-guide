# Pinball Machine — Style Guide

Glossy black playfield under neon lights. A design system inspired by arcade pinball machines — chrome bumper borders, backglass art panels, tilt warning callouts, and multi-player score displays for single-page HTML documents.

---

## Color Palette

### Backgrounds & Surfaces

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--bg`         | `#08080c` | Page background (glossy black playfield) |
| `--surface`    | `#12121a` | Cards, panels, diagram containers        |
| `--surface-2`  | `#1c1c26` | Nested surfaces, secondary panels        |
| `--surface-3`  | `#262630` | Tertiary surface, bumper edges           |
| `--border`     | `#38384a` | Card borders, chrome trim, dividers      |

### Text

| Token          | Hex       | Usage                                          |
|----------------|-----------|-------------------------------------------------|
| `--text`       | `#f0ecf8` | Primary text, headings, bold/strong content     |
| `--text-dim`   | `#9890a8` | Body paragraphs, secondary descriptions         |
| `--text-faint` | `#585068` | Labels, score metadata, captions                |

### Accent & Semantic Colors

Each semantic color has full, dim, and transparent-fill variants. Fill variants use `rgba(color, 0.10)` for tinted backgrounds on tags.

| Token           | Hex       | Role                                   |
|-----------------|-----------|----------------------------------------|
| `--accent`      | `#ff2080` | Primary accent (Neon Pink)             |
| `--accent-dim`  | `#b81060` | Muted accent                           |
| `--capture`     | `#40e868` | Neon Green — jackpots, multiball       |
| `--capture-dim` | `#28a848` | Muted green                            |
| `--refine`      | `#ffe020` | Hot Yellow — bonus, score multipliers  |
| `--refine-dim`  | `#c8a810` | Muted yellow                           |
| `--execute`     | `#ff2080` | Neon Pink — tilt, danger, drain        |
| `--execute-dim` | `#b81060` | Muted pink                             |
| `--batch`       | `#20a0ff` | Electric Blue — locks, targets, ramps  |
| `--batch-dim`   | `#1070c0` | Muted blue                             |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                               |
|-----------|-----------------|-----------------------------------------------------|
| Headings  | Russo One       | `Russo+One`                                         |
| Body      | Inter           | `Inter:wght@300;400;500;600`                        |
| Labels    | IBM Plex Mono   | `IBM+Plex+Mono:wght@400;500;600`                   |

```html
<link href="https://fonts.googleapis.com/css2?family=Russo+One&family=Inter:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type Scale & Weights

| Element            | Family          | Size                             | Weight | Line-height | Notes                                         |
|--------------------|-----------------|-----------------------------------|--------|-------------|-----------------------------------------------|
| Hero h1            | Russo One       | `clamp(2.2rem, 6vw, 4rem)`      | 400    | 1.1         | `<span>` in --accent for neon glow word       |
| h2 (section)       | Russo One       | `1.6rem`                         | 400    | 1.2         | Uppercase                                     |
| h3 (subsection)    | Russo One       | `1rem`                           | 400    | 1.3         | `margin-top: 2.5rem`                          |
| h4 (card title)    | Inter           | `0.8rem`                         | 600    |             | Uppercase, letter-spacing: 0.06em             |
| Body paragraph     | Inter           | `0.95rem`                        | 400    | 1.6         | Color: `--text-dim`                           |
| Hero subtitle      | Inter           | `1.05rem`                        | 400    | 1.8         | Color: `--text-dim`, max-width 560px          |
| Section label      | IBM Plex Mono   | `0.75rem`                        | 400    |             | Uppercase, `letter-spacing: 0.15em`, `--text-faint` |
| Hero label         | IBM Plex Mono   | `0.8rem`                         | 400    |             | Uppercase, `letter-spacing: 0.2em`, neon glow pulse |
| Tag                | IBM Plex Mono   | `0.7rem`                         | 400    |             | `letter-spacing: 0.06em`                      |

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
- Stacked vertically: label, h1, subtitle, version
- **Playfield lights:** Scattered neon-colored dots via `::before`, like pinball playfield insert lights
- **Radial vignette:** Dark edges via `::after`, focus attention center
- **Title accent:** `<span>` inside h1 uses `--accent` with neon `text-shadow` glow
- **Neon pulse:** Hero label pulses with a neon pink glow animation
- **Staggered fade-up animation** on load
- **Glass reflection:** Subtle diagonal gradient overlay on `body::after`

---

## Components

### Flow Cards, Pipeline, Principle List, Callout, Tags, Tables, Diagram Containers

All standard components follow the same patterns as other themes with these Pinball-specific adjustments:
- Border-radius: `6px` (chrome bumper roundness)
- Hover uses neon glow: `box-shadow` with colored spread
- Accent bars on flow cards emit a `box-shadow: 0 0 10px` glow in their color
- Principle numbers use Russo One at `2rem` in `--accent` with neon text-shadow

---

## Unique Components

### Backglass Panel

A decorative art card mimicking the lit backglass artwork of a pinball machine.

- **Container:** `--surface` background, `2px solid var(--border)`, `border-radius: 8px`, overflow hidden
- **Header:** `linear-gradient(135deg, var(--accent), var(--batch))` — neon pink-to-blue gradient
- **Light dots:** `::before` — row of dot characters along top edge, `rgba(255, 255, 255, 0.45)`
- **Title:** Russo One, `1.8rem`, white, uppercase, text-shadow glow
- **Subtitle:** IBM Plex Mono, `0.7rem`, white 70% opacity, uppercase
- **Score:** IBM Plex Mono, `2.5rem`, weight 600, `--refine` yellow, neon text-shadow
- **Description:** `0.88rem`, `--text-dim`, centered

### Tilt Warning

An alert panel with hazard stripes for danger states.

- **Container:** `--surface` background, `2px solid var(--execute)`, `border-radius: 6px`
- **Hazard bar:** `::before` — `repeating-linear-gradient(-45deg)` diagonal stripes in `--execute` pink
- **Label:** Russo One, `2rem`, `--execute`, uppercase, `letter-spacing: 0.15em`, neon text-shadow
- **Blink:** `.tilting` class triggers `tiltBlink` animation — `0.5s step-end infinite` opacity toggle
- **Message:** `0.9rem`, `--text-dim`, strong text in `--execute`

### Score Display

A multi-player scoreboard like a pinball DMD (dot matrix display).

- **Container:** `#0a0a10` background (darker than surface), `2px solid var(--border)`, `border-radius: 8px`
- **Header:** Flex row with Russo One title and ball indicator dots
- **Ball dots:** `12px` circles, `--surface-3` default, `.active` gets `--accent` with neon glow
- **Player grid:** `repeat(auto-fit, minmax(120px, 1fr))` grid
- **Player card:** Centered, `--surface` background, `border-radius: 4px`
- **Active player:** `--accent` border with pink glow shadow
- **Score:** IBM Plex Mono, `1.8rem`, weight 600, `--refine` yellow with text-shadow glow
- **Active score:** Switches to `--accent` pink
- **Multiplier:** IBM Plex Mono, `0.7rem`, `--capture` green, uppercase

### Bumper Targets

Circular bumper-shaped elements with neon glow effects.

- **Grid:** `repeat(auto-fill, minmax(140px, 1fr))`, `1.5rem` gap
- **Bumper:** `aspect-ratio: 1`, `border-radius: 50%`, `3px solid` border, `--surface` background
- **Hover:** `transform: scale(1.05)`, intensified glow
- **Color variants:** `.b-pink` (accent), `.b-blue` (batch), `.b-yellow` (refine), `.b-green` (capture)
- **Each variant:** Colored border + outer glow (`box-shadow: 0 0 20px`) + inner glow (`inset 0 0 20px`)
- **Value:** Russo One, `1.4rem`, `--text`, uppercase
- **Label:** IBM Plex Mono, `0.6rem`, `--text-faint`, uppercase

---

## Inline Code

- Font: IBM Plex Mono, `0.82rem`
- Background: `--surface-2`
- Padding: `0.15em 0.4em`
- Border-radius: `3px`
- Border: `1px solid var(--border)`
- Color: `--accent` (neon pink)

---

## Footer

- Top border: `1px solid var(--border)`
- Padding: `3rem 0`
- Centered text in IBM Plex Mono, `0.75rem`, `--text-faint`, `letter-spacing: 0.1em`

---

## Summary of Key Patterns

1. **Glossy black playfield** — backgrounds use deep near-black tones like the polished surface of a pinball table.
2. **Neon pink accent** — the primary color evokes hot pink neon tubes and playfield insert lights.
3. **Three-tier text** — bright white (--text), muted lavender (--text-dim), ghost purple (--text-faint).
4. **Bold condensed headings** — Russo One delivers the punchy, all-caps energy of pinball backglass art.
5. **Clean body text** — Inter provides crisp readability against the dark playfield.
6. **Arcade semantics** — neon green (jackpot), hot yellow (bonus), neon pink (tilt/danger), electric blue (lock/target).
7. **Pinball artifacts** — backglass panels, tilt warnings, score displays, and bumper targets bring the physical machine into the design.
8. **Neon glow effects** — box-shadow and text-shadow create the characteristic neon light bloom on hover and active states.
