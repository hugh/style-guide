# CLAUDE.md

This repo is a collection of HTML/CSS style guides and template systems for creating themed single-page documents. Each theme lives in its own subdirectory.

## Repo Structure

- `index.html` — Gallery page with iframe previews of all themes
- `vesper/` — Dark editorial theme (purple-tinted surfaces, serif headings)
- `circus/` — Big top spectacle theme
- `engineer/` — Blueprint technical theme
- `excalidraw/` — Hand-drawn whiteboard theme
- `mathematician/` — Chalkboard theme
- `physicist/` — Void and spectrum theme
- `terminal/` — CRT retro theme
- `train-station/` — Vintage railway theme
- `doodle/` — Sketchbook ink theme
- `art-deco/` — 1920s Gatsby-era gold & black theme
- `superhero/` — Classic comics thick-outline halftone theme
- `kaiju/` — Japanese monster movie poster theme (radiation green, hazard stripes)
- `space-opera/` — Sci-fi bridge theme (deep space blues, holographic cyan, nebula glows)
- `aliens/` — Xenomorph industrial theme (cold steel, acid yellow-green, motion trackers, airlock warnings)
- `nasa/` — 1960s–70s Mission Control theme (deep navy, GO green, telemetry readouts, countdown timers)

Each theme subdirectory contains:
- `index.html` — Live style guide rendered in the theme's own style
- `style_guide.md` — Detailed style reference (colors, typography, spacing, component specs)
- `tokens.css` — Drop-in stylesheet with CSS custom properties and all component styles
- `template.html` — Starter HTML file demonstrating every component

## Style Rules

When creating or modifying HTML documents in this style:

- Use CSS custom properties defined in `tokens.css` — never hardcode color values
- Headings (h1–h3) use **DM Serif Display**. Body text and card titles use **DM Sans**. Labels, tags, and metadata use **JetBrains Mono**
- Body text defaults to `--text-dim`. Use `--text` for headings and `<strong>`. Use `--text-faint` for labels and captions
- Sections are numbered with monospace labels in the format `01 — Label`
- Flow cards require a semantic class (`capture`, `refine`, `execute`, `batch`, or `accent`) for the colored top bar
- Pipeline stages require a semantic class prefixed with `s-` (e.g., `s-capture`)
- Tags require a class prefixed with `t-` (e.g., `t-capture`)
- Container max-width is 900px. Use `full-bleed` class on diagram wraps to expand to 1100px
- Keep the four semantic color categories (green/amber/red/blue) consistent — map them to whatever domain concepts fit, but maintain the visual meaning of each color
- SVG diagrams: use `DM Sans` for text, dashed lines for connections (`stroke-dasharray: 4,3`), and `rx="12"` for node rounded corners
