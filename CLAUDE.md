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
- `darkroom/` — Polaroid photography theme (warm charcoal, safelight red, film strips, contact sheets)
- `dossier/` — Spy file theme (manila paper, classified stamps, redacted text, surveillance cards)
- `cassette/` — Mixtape analog theme (dark plastic, warm orange, handwritten tracklists, tape spools)
- `cafe/` — Chalkboard menu theme (dark slate green, chalk lettering, latte brown, menu boards)
- `vinyl/` — Record store theme (rich black, shelf amber, LP sleeves, groove dividers, crate tabs)
- `retro-game/` — 8-bit arcade theme (CRT blue-black, pixel fonts, health bars, character select, achievements)
- `board-game/` — Tabletop theme (felt-green table, wooden tokens, player cards, dice, score tracks)
- `musician/` — Classical score theme (manuscript cream, staff dividers, dynamic markings, rehearsal marks)
- `pinball/` — Arcade pinball theme (glossy black, neon pink, backglass panels, tilt warnings, bumper targets)
- `cartographer/` — Antique map theme (aged parchment, burnt umber, contour lines, legend boxes, compass rose)
- `cartoon/` — Animated TV theme (bright white, thick outlines, candy colors, bouncy animations, speech bubbles)
- `western/` — Wanted poster theme (sun-bleached parchment, burnt sienna, sheriff badges, saloon doors)
- `retro-americana/` — 1950s diner theme (warm cream, diner red, chrome gold, neon signs, checkerboard panels)
- `brutalist/` — Anti-design theme (raw concrete grey, thick black borders, system fonts, no transitions, construction orange)
- `aviation/` — Cockpit instrument theme (dark panel grey, amber gauges, altimeter dials, ATC radio logs, black box recorders)
- `weather/` — Meteorology theme (dark radar screen, Doppler green, barometer gauges, forecast strips, storm warnings)
- `pottery/` — Ceramics studio theme (warm clay linen, terracotta accents, kiln gauges, glaze recipe cards, potter's marks)
- `victorian/` — Antique theme (aged parchment, ornate serifs, wax seals, filigree dividers, ribbon banners, medallions)
- `mid-century/` — Atomic-age theme (warm cream, mustard/teal/coral, starburst dividers, boomerang cards, Googie panels)
- `alchemist/` — Medieval mystical theme (dark parchment, gold leaf accents, drop caps, recipe cards, transmutation circles)
- `subway/` — Metro transit theme (dark tunnel grey, route-color stripes, station signs, arrival boards, transfer badges)
- `bakery/` — Patisserie theme (warm vanilla cream, caramel accents, recipe cards, timer badges, cake layer dividers)
- `surveillance/` — CCTV theme (monitor black, REC red, camera feeds, evidence tags, recognition boxes)
- `pop-art/` — Silver Age pop art theme (bright yellow, thick black outlines, Ben-Day dots, speech bubbles, POW badges)
- `pulp/` — Golden Age pulp theme (yellowed paper, pulp red, slab serif woodcuts, splatter borders, price stamps)
- `deep-sea/` — Underwater theme (abyssal navy, bioluminescent accents, frosted glass cards, depth gauges, sonar pings)
- `architect/` — Drafting theme (warm vellum, redline accent, drafting grids, dimension callouts, title blocks)
- `laboratory/` — Research theme (clinical white, safety orange, specimen cards, petri dishes, electrophoresis dividers)
- `noir/` — Film noir theme (high-contrast black & white, blood red accent, typewriter font, evidence tags, redacted text)
- `cyberpunk/` — Neon streets theme (rain-soaked black, hot pink & electric cyan, glitch effects, holographic cards)
- `tarot/` — Occult theme (midnight indigo, gold foil, star fields, tarot cards, zodiac markers, crystal balls)
- `steampunk/` — Brass & leather theme (dark brown, polished brass, pressure gauges, gear badges, ticker tape dividers)

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
