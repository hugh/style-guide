# Style Guide Gallery

A collection of themed HTML/CSS design systems for single-page documents. Each theme is self-contained with its own stylesheet and template.

**[Live Gallery](https://gamahugh.github.io/style-guide/)**

## Themes

| Theme | Description |
|-------|-------------|
| [Vesper](vesper/) | Dark editorial — purple-tinted surfaces, serif headings |
| [Circus](circus/) | Big top spectacle — dark purple, warm cream, bold stripes |
| [Engineer](engineer/) | Blueprint technical — deep navy, grid lines, redline accents |
| [Excalidraw](excalidraw/) | Hand-drawn whiteboard — light canvas, sketchy lines |
| [Mathematician](mathematician/) | Chalkboard — dark forest green, chalk-white text |
| [Physicist](physicist/) | Void and spectrum — deep black, neon accents |
| [Terminal](terminal/) | CRT retro — black screen, phosphor green, scanlines |
| [Train Station](train-station/) | Vintage railway — dark brown, brass accents |

## Quick Start

1. Pick a theme and copy its `template.html` and `tokens.css` into your project
2. Edit the hero, sections, and components in the HTML
3. Refer to the theme's `style_guide.md` for detailed specs when needed

## Fonts

The system uses three Google Fonts loaded via CSS import in `tokens.css`:

- **DM Serif Display** — headings (h1–h3, decorative numbers)
- **DM Sans** — body text, card titles, table content
- **JetBrains Mono** — labels, tags, metadata, section numbers

## Color System

Dark backgrounds with a purple undertone. Text uses a three-tier hierarchy (primary, dim, faint). Four semantic accent colors for categorization:

| Color | Token | Hex |
|-------|-------|-----|
| Purple (accent) | `--accent` | `#c4a0ff` |
| Green | `--capture` | `#6ecfb5` |
| Amber | `--refine` | `#f0b866` |
| Red | `--execute` | `#f07272` |
| Blue | `--batch` | `#6aaef0` |

## Components

- **Hero** — full-viewport title section with fade-up animation
- **Flow Cards** — 2-column grid with colored top accent bars
- **Pipeline** — horizontal connected stages for linear processes
- **Principle List** — numbered items with serif numbers
- **Callout** — left-bordered aside for important notes
- **Tags** — small monospace pills with tinted backgrounds
- **Tables** — minimal borders, uppercase headers
- **Diagram Containers** — rounded surface panels for SVGs

See `template.html` for working examples of each component.
