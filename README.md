# Style Guide Gallery

A collection of 60+ themed HTML/CSS design systems for single-page documents. Each theme is self-contained with its own stylesheet and template.

**[Live Gallery](https://gamahugh.github.io/style-guide/)**

## Themes

Over 60 themes spanning different aesthetics — from dark editorial to retro arcade, from Victorian antique to brutalist anti-design. Each theme includes a live style guide, a complete CSS design system, and a realistic starter template.

Browse the [gallery](https://gamahugh.github.io/style-guide/) to preview them all, or explore individual theme directories below.

<details>
<summary>Full theme list</summary>

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
| [Doodle](doodle/) | Sketchbook ink — cream paper, hand-drawn borders |
| [Art Deco](art-deco/) | 1920s Gatsby-era — burnished gold, geometric ornaments |
| [Superhero](superhero/) | Classic comics — thick outlines, halftone dots |
| [Kaiju](kaiju/) | Monster movie — ash-dark, radiation green, hazard stripes |
| [Space Opera](space-opera/) | Sci-fi bridge — deep space blues, holographic cyan |
| [Aliens](aliens/) | Xenomorph industrial — cold steel, acid yellow-green |
| [NASA](nasa/) | 1960s Mission Control — deep navy, GO green, telemetry |
| [Darkroom](darkroom/) | Photography — warm charcoal, safelight red, film strips |
| [Zen](zen/) | Japanese Wabi-Sabi — rice paper, sumi ink, enso circles |
| [Dossier](dossier/) | Spy file — manila paper, classified stamps, redacted text |
| [Cassette](cassette/) | Mixtape analog — dark plastic, warm orange |
| [Cafe](cafe/) | Chalkboard menu — dark slate green, chalk lettering |
| [Vinyl](vinyl/) | Record store — rich black, shelf amber, LP sleeves |
| [Retro Game](retro-game/) | 8-bit arcade — CRT blue-black, pixel fonts |
| [Board Game](board-game/) | Tabletop — felt-green, wooden tokens, dice |
| [Musician](musician/) | Classical score — manuscript cream, staff dividers |
| [Pinball](pinball/) | Arcade machine — glossy black, neon pink |
| [Cartographer](cartographer/) | Antique map — aged parchment, contour lines |
| [Cartoon](cartoon/) | Animated TV — bright white, candy colors |
| [Western](western/) | Wanted poster — sun-bleached parchment, burnt sienna |
| [Retro Americana](retro-americana/) | 1950s diner — warm cream, chrome gold |
| [Brutalist](brutalist/) | Anti-design — raw concrete, thick black borders |
| [Aviation](aviation/) | Cockpit — dark panel grey, amber gauges |
| [Weather](weather/) | Meteorology — dark radar, Doppler green |
| [Pottery](pottery/) | Ceramics studio — warm clay, terracotta accents |
| [Victorian](victorian/) | Antique — aged parchment, wax seals, filigree |
| [Mid-Century](mid-century/) | Atomic age — mustard/teal/coral, starburst |
| [Alchemist](alchemist/) | Medieval mystical — dark parchment, gold leaf |
| [Subway](subway/) | Metro transit — route-color stripes, arrival boards |
| [Bakery](bakery/) | Patisserie — vanilla cream, caramel accents |
| [Surveillance](surveillance/) | CCTV — monitor black, REC red |
| [Pop Art](pop-art/) | Silver Age — bright yellow, Ben-Day dots |
| [Pulp](pulp/) | Golden Age — yellowed paper, slab serif woodcuts |
| [Deep Sea](deep-sea/) | Underwater — abyssal navy, bioluminescent |
| [Architect](architect/) | Drafting — warm vellum, redline accent |
| [Laboratory](laboratory/) | Research — clinical white, safety orange |
| [Noir](noir/) | Film noir — high-contrast B&W, typewriter font |
| [Cyberpunk](cyberpunk/) | Neon streets — hot pink, electric cyan, glitch |
| [Tarot](tarot/) | Occult — midnight indigo, gold foil, star fields |
| [Steampunk](steampunk/) | Brass & leather — pressure gauges, gear badges |
| [Kodachrome](kodachrome/) | Film photography — warm cream, saturated colors |
| [Zine](zine/) | Grunge collage — newsprint, tape strips, ransom type |
| [Swiss](swiss/) | International Typographic Style — pure white, strict grid |
| [Festival](festival/) | Concert poster — psychedelic gradients, wristbands |
| [Chalkboard](chalkboard/) | Classroom — dark slate green, chalk-white, pastels |
| [Origami](origami/) | Paper craft — clean white, folded corners, cranes |
| [Woodworking](woodworking/) | Workshop — warm wood grain, blueprint cards |
| [Arctic](arctic/) | Ice/frost — glacial blue-white, frosted glass |
| [Pixel Art](pixel-art/) | Game Boy DMG — 4-color green-grey, pixel fonts |
| [Fairy Tale](fairy-tale/) | Storybook — warm parchment, gilt gold, drop caps |
| [Horror VHS](horror-vhs/) | Found footage — CRT black, night-vision green |
| [Rough Woodworking](rough-woodworking/) | Level 1 rough — handwritten notes, slight rotations |
| [Rougher Woodworking](rougher-woodworking/) | Level 2 rough — coffee rings, tape strips, dog-ears |
| [Extra-Rough Woodworking](extra-rough-woodworking/) | Level 3 rough — sticky notes, torn edges, paper clips |

</details>

## Quick Start

1. Pick a theme and copy its `template.html` and `tokens.css` into your project
2. Edit the hero, sections, and components in the HTML
3. Refer to the theme's `style_guide.md` for detailed specs when needed

## Theme Structure

Each theme directory contains exactly 4 files:

| File | Purpose |
|------|---------|
| `tokens.css` | Complete CSS design system — custom properties, all component styles, fonts |
| `index.html` | Live style guide that demonstrates every component in the theme's own style |
| `template.html` | Realistic starter document showing components in context |
| `style_guide.md` | Markdown reference for colors, typography, spacing, and components |

## Standard Components

Every theme implements this shared set of components:

- **Hero** — full-viewport title section
- **Flow Cards** — 2-column grid with colored top accent bars (`.capture`, `.refine`, `.execute`, `.batch`)
- **Pipeline** — horizontal connected stages for linear processes
- **Principle List** — numbered items with large decorative numbers
- **Callout** — left-bordered aside for important notes
- **Tags** — small monospace pills with tinted backgrounds
- **Tables** — minimal borders, uppercase headers
- **Diagram Container** — surface panels for inline SVGs

Plus **4 unique thematic components** per theme (e.g., blueprint cards and dovetail dividers for woodworking, motion trackers and airlock warnings for aliens).

## Color System

Every theme defines its own palette but follows a shared structure:

- **Background tiers** — `--bg`, `--surface`, `--surface-2`, `--surface-3`
- **Text tiers** — `--text` (headings), `--text-dim` (body), `--text-faint` (labels)
- **Accent** — `--accent` (theme's signature color)
- **Semantic colors** — `--capture` (green), `--refine` (amber), `--execute` (red), `--batch` (blue)

All colors are CSS custom properties in `:root`. Never hardcode hex values in HTML.

## The Roughness Experiment

The woodworking theme exists at 4 levels of polish, exploring how to make digital designs feel more human-made:

| Level | Effect |
|-------|--------|
| **Polished** (`woodworking/`) | Clean, systematic, all cards identical |
| **Rough** (`rough-woodworking/`) | Varied card warmth, handwritten notes, slight rotations |
| **Rougher** (`rougher-woodworking/`) | Coffee rings, tape strips, pushpins, bigger rotations |
| **Extra Rough** (`extra-rough-woodworking/`) | Sticky notes, torn edges, paper clips, overlapping cards |

See `CLAUDE.md` for detailed techniques on creating rough variants of any theme.
