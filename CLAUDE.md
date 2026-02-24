# CLAUDE.md

This repo is a collection of 60+ HTML/CSS style guides and template systems for creating themed single-page documents. Each theme lives in its own subdirectory.

## Repo Structure

- `index.html` — Gallery page with iframe previews of all themes
- `ideas.txt` — Theme idea backlog (TODO/DONE tracking)

### Theme Directories

Each theme directory contains exactly 4 files:
- `tokens.css` — Drop-in stylesheet with CSS custom properties and all component styles
- `index.html` — Live style guide rendered in the theme's own style
- `template.html` — Starter HTML file demonstrating every component in a realistic scenario
- `style_guide.md` — Detailed style reference (colors, typography, spacing, component specs)

### Current Themes

- `vesper/` — Dark editorial (purple-tinted surfaces, serif headings)
- `circus/` — Big top spectacle
- `engineer/` — Blueprint technical
- `excalidraw/` — Hand-drawn whiteboard
- `mathematician/` — Chalkboard
- `physicist/` — Void and spectrum
- `terminal/` — CRT retro
- `train-station/` — Vintage railway
- `doodle/` — Sketchbook ink
- `art-deco/` — 1920s Gatsby-era gold & black
- `superhero/` — Classic comics thick-outline halftone
- `kaiju/` — Japanese monster movie poster (radiation green, hazard stripes)
- `space-opera/` — Sci-fi bridge (deep space blues, holographic cyan, nebula glows)
- `aliens/` — Xenomorph industrial (cold steel, acid yellow-green, motion trackers, airlock warnings)
- `nasa/` — 1960s–70s Mission Control (deep navy, GO green, telemetry readouts, countdown timers)
- `darkroom/` — Polaroid photography (warm charcoal, safelight red, film strips, contact sheets)
- `zen/` — Japanese Zen / Wabi-Sabi (warm rice paper, sumi ink, enso circles, stone garden badges)
- `dossier/` — Spy file (manila paper, classified stamps, redacted text, surveillance cards)
- `cassette/` — Mixtape analog (dark plastic, warm orange, handwritten tracklists, tape spools)
- `cafe/` — Chalkboard menu (dark slate green, chalk lettering, latte brown, menu boards)
- `vinyl/` — Record store (rich black, shelf amber, LP sleeves, groove dividers, crate tabs)
- `retro-game/` — 8-bit arcade (CRT blue-black, pixel fonts, health bars, character select)
- `board-game/` — Tabletop (felt-green table, wooden tokens, player cards, dice, score tracks)
- `musician/` — Classical score (manuscript cream, staff dividers, dynamic markings, rehearsal marks)
- `pinball/` — Arcade pinball (glossy black, neon pink, backglass panels, bumper targets)
- `cartographer/` — Antique map (aged parchment, burnt umber, contour lines, compass rose)
- `cartoon/` — Animated TV (bright white, thick outlines, candy colors, bouncy animations)
- `western/` — Wanted poster (sun-bleached parchment, burnt sienna, sheriff badges)
- `retro-americana/` — 1950s diner (warm cream, diner red, chrome gold, neon signs)
- `brutalist/` — Anti-design (raw concrete grey, thick black borders, system fonts)
- `aviation/` — Cockpit instruments (dark panel grey, amber gauges, altimeter dials)
- `weather/` — Meteorology (dark radar screen, Doppler green, barometer gauges)
- `pottery/` — Ceramics studio (warm clay linen, terracotta accents, kiln gauges)
- `victorian/` — Antique (aged parchment, ornate serifs, wax seals, filigree)
- `mid-century/` — Atomic-age (warm cream, mustard/teal/coral, starburst dividers)
- `alchemist/` — Medieval mystical (dark parchment, gold leaf, transmutation circles)
- `subway/` — Metro transit (dark tunnel grey, route-color stripes, arrival boards)
- `bakery/` — Patisserie (warm vanilla cream, caramel accents, recipe cards)
- `surveillance/` — CCTV (monitor black, REC red, camera feeds, evidence tags)
- `pop-art/` — Silver Age (bright yellow, Ben-Day dots, speech bubbles, POW badges)
- `pulp/` — Golden Age (yellowed paper, pulp red, slab serif woodcuts)
- `deep-sea/` — Underwater (abyssal navy, bioluminescent accents, sonar pings)
- `architect/` — Drafting (warm vellum, redline accent, dimension callouts, title blocks)
- `laboratory/` — Research (clinical white, safety orange, specimen cards)
- `noir/` — Film noir (high-contrast black & white, typewriter font, redacted text)
- `cyberpunk/` — Neon streets (rain-soaked black, hot pink & electric cyan, glitch effects)
- `tarot/` — Occult (midnight indigo, gold foil, star fields, tarot cards)
- `steampunk/` — Brass & leather (dark brown, polished brass, pressure gauges)
- `kodachrome/` — Film photography (warm cream, Kodachrome-saturated colors, slide mounts)
- `zine/` — Grunge zine (off-white newsprint, tape strips, ransom note blocks)
- `swiss/` — International Typographic Style (pure white, Swiss red, strict grid)
- `festival/` — Music festival / concert poster (deep purple-black, psychedelic gradients)
- `chalkboard/` — Classroom chalkboard (dark slate green, chalk-white, pastel accents)
- `origami/` — Paper craft (clean white, origami pink, folded corners, crane markers)
- `woodworking/` — Workshop (warm wood grain, walnut accents, blueprint cards, dovetail dividers)
- `arctic/` — Ice/frost (pale glacial blue-white, frosted glass, aurora badges)
- `pixel-art/` — Game Boy DMG (4-color green-grey, pixel fonts, dialogue boxes)
- `fairy-tale/` — Storybook (warm parchment, gilt gold, illuminated drop caps)
- `horror-vhs/` — Found footage VHS (CRT black, night-vision green, tracking glitches)
- `rough-woodworking/` — Rough woodworking Level 1 (uneven warmth, handwritten notes, slight rotations)
- `rougher-woodworking/` — Rough woodworking Level 2 (coffee rings, tape strips, pushpins, dog-ears)
- `extra-rough-woodworking/` — Rough woodworking Level 3 (sticky notes, torn edges, paper clips, chaotic spacing)

---

## How to Create a New Theme

### Step 1: Design Decisions

Before writing code, decide:
- **3 Google Fonts** — one for headings, one for body, one for labels/mono. Some themes use 4 (e.g., adding a handwriting font). Load via `@import` at the top of tokens.css.
- **Color palette** — background, 3 surface tiers, border, 3 text tiers, accent, plus the 4 semantic colors. Most themes have 15–25 CSS custom properties.
- **4 unique thematic components** — every theme gets 4 components that are specific to its aesthetic (e.g., woodworking gets blueprint cards, dovetail dividers, lumber stamps, tool racks). These should feel like they belong to the theme's world.
- **Background texture** — most themes have a subtle texture on `body` and/or `.hero` using `repeating-linear-gradient`, `radial-gradient`, or similar CSS-only techniques. No image files.

### Step 2: Write the 4 Files

**`tokens.css`** — The complete stylesheet. Structure:
1. Google Fonts `@import`
2. `:root` with all CSS custom properties
3. Reset (`*, *::before, *::after`)
4. Body styles with background texture
5. Typography (h1–h4, p, strong)
6. Layout (.container, section, .section-num)
7. Hero section
8. Standard components (flow cards, pipeline, principles, callout, tags, tables, diagram containers)
9. 4 unique thematic components
10. Inline code styles
11. Footer

**`index.html`** — Live style guide. Standard sections:
- Section 00: Overview / theme explanation
- Section 01: Color palette (swatch grids with hex values)
- Section 02: Typography specimens
- Section 03+: Component demos (standard and unique)
- Final sections: SVG diagram demo, principles/design notes

**`template.html`** — A realistic starter document. NOT generic placeholder text. Write it as if a real person is using this theme for its intended purpose (see "Template Content Quality" below).

**`style_guide.md`** — Markdown reference documenting colors, fonts, spacing, all components, and design principles.

### Step 3: Add to Gallery

Add a card to `index.html` (root gallery). Each card follows this structure:

```html
<div class="theme-card">
  <a href="themename/index.html" target="_blank" rel="noopener"></a>
  <div class="preview-frame">
    <iframe src="themename/index.html" loading="lazy" tabindex="-1" title="Theme Name preview"></iframe>
    <div class="preview-overlay"><span>Open preview</span></div>
  </div>
  <div class="theme-info">
    <h3>Theme Name</h3>
    <p>Short description — key visual traits</p>
    <div class="theme-colors">
      <span style="background:#hex1"></span>
      <span style="background:#hex2"></span>
      <span style="background:#hex3"></span>
      <span style="background:#hex4"></span>
      <span style="background:#hex5"></span>
      <span style="background:#hex6"></span>
    </div>
  </div>
</div>
```

The 6 color dots should show: background, text, accent, and 3 semantic colors. For light backgrounds, add `border-color:rgba(0,0,0,0.15)` so the dot is visible against the dark gallery.

### Step 4: Update Tracking

- Add the theme to the directory listing in this file (CLAUDE.md)
- If the theme came from `ideas.txt`, move it from TODO to DONE with `→ dirname/`

---

## Standard Component Set

Every theme must implement these components with these exact class names:

| Component | Classes | Description |
|-----------|---------|-------------|
| **Hero** | `.hero`, `.hero-label`, `.hero-version` | Full-viewport title section |
| **Flow Cards** | `.flow-grid`, `.flow-card`, `.card-icon` | 2-column grid with colored top bars |
| **Pipeline** | `.pipeline`, `.pipe-stage`, `.pipe-num`, `.pipe-name`, `.pipe-desc` | Horizontal connected stages |
| **Principle List** | `.principle-list`, `.principle`, `.principle-num` | Numbered items with large numbers |
| **Callout** | `.callout` | Left-bordered aside for important notes |
| **Tags** | `.tag` | Small monospace pills with tinted backgrounds |
| **Tables** | `.info-table` | Minimal borders, uppercase monospace headers |
| **Diagram Container** | `.diagram-wrap`, `.diagram-label` | Rounded surface panels for SVGs |
| **Inline Code** | `code`, `.inline-code` | Monospace with background |
| **Footer** | `footer` | Centered, minimal |

### Semantic Color Classes

Flow cards, pipeline stages, and tags use semantic color classes:

| Category | Flow Card | Pipeline | Tag | Typical Meaning |
|----------|-----------|----------|-----|-----------------|
| Green | `.capture` | `.s-capture` | `.t-capture` | Input, collection, start |
| Amber | `.refine` | `.s-refine` | `.t-refine` | Processing, iteration |
| Red | `.execute` | `.s-execute` | `.t-execute` | Action, output, critical |
| Blue | `.batch` | `.s-batch` | `.t-batch` | Automation, delivery |
| Accent | `.accent` | `.s-accent` | — | Theme-specific highlight |

Map these to whatever domain concepts fit the theme, but maintain the visual meaning (green = positive/start, amber = caution/middle, red = action/danger, blue = info/end).

### Text Hierarchy

Three tiers, used consistently across all themes:
- `--text` — Headings, `<strong>`, emphasis. Highest contrast.
- `--text-dim` — Body text, paragraphs. Default reading color.
- `--text-faint` — Labels, captions, metadata, section numbers. Lowest contrast.

---

## Font Conventions

Each theme chooses its OWN fonts — there is no single font set for the whole repo. However, most themes follow this pattern:
- **Heading font** — distinctive, sets the theme's personality (serif, display, handwriting, pixel, etc.)
- **Body font** — readable at small sizes (usually sans-serif or serif depending on theme)
- **Mono/label font** — for tags, measurements, section numbers, code (usually a monospace)

Some themes add a 4th font for special purposes (e.g., Caveat for handwriting in woodworking themes).

All fonts are loaded via `@import url('https://fonts.googleapis.com/css2?...')` at the top of `tokens.css`. No local font files.

---

## Template Content Quality

Templates should feel like a real person using the theme for its intended purpose. NOT generic placeholder text.

**Good template examples:**
- Woodworking theme → personal build notes for a walnut bookcase, with real opinions, mistakes, product names
- Aviation theme → a pilot's pre-flight checklist and route planning notes
- Laboratory theme → an actual experiment protocol with real reagents and procedures
- Western theme → a frontier town's notice board with wanted posters and land claims

**What makes a template feel real:**
- Specific details (dates, names, prices, measurements)
- Opinions and personality ("Anderson's had garbage this week")
- Mistakes and corrections (using `.struck` / `.amended` or equivalent)
- Domain-appropriate terminology
- References to real tools, products, or techniques when possible

Avoid: lorem ipsum, "Your Title Here", generic placeholder descriptions, or content that reads like documentation of the components rather than use of them.

---

## The Roughness Experiment

The woodworking theme exists at 4 levels of polish, demonstrating how to make themes feel more human-made:

| Level | Directory | Container | Rotations | Key Features |
|-------|-----------|-----------|-----------|--------------|
| 0 (Polished) | `woodworking/` | 900px | None | Clean, systematic, identical cards, animations |
| 1 (Rough) | `rough-woodworking/` | 880px | 0.3°–3° | 5 warm variants, Caveat annotations, no animation |
| 2 (Rougher) | `rougher-woodworking/` | 860px | 1°–6° | Coffee rings, tape strips, pushpins, dog-ears |
| 3 (Extra Rough) | `extra-rough-woodworking/` | 840px | 2°–8° | Sticky notes, paper clips, torn edges, ink blots, overlapping cards |

### Roughness Techniques (CSS)

- **Varied card warmth** — Multiple `--warm-N` tokens applied via `nth-child` so no two adjacent cards match
- **Slight rotations** — `transform: rotate()` on callouts, stamps, tags, cards. Escalate by level.
- **Imperfect spacing** — Section padding that doesn't match top to bottom, via `nth-child` rules
- **Uneven borders** — Alternating border widths, mixing solid/dashed/dotted
- **Handwriting layer** — Caveat font for margin notes, inline scrawl, principle numbers
- **Physical artifacts** — Coffee rings (radial-gradient), tape strips (pseudo-elements with clip-path), pushpins (::before circles), dog-ears (CSS triangles), sticky notes, paper clips, torn edges
- **No animation** — Remove all transitions and fade-ups. Things just appear.
- **Negative margins** — Cards slightly overlapping neighbors at higher roughness levels

### Roughness Techniques (Content)

- **Personal voice** — First person, opinions, humor, self-deprecation
- **Struck/amended** — Crossed-out text with corrections
- **Margin notes** — Asides that comment on or argue with the main text
- **Specific details** — Real dates, shop names, prices, weather, moods
- **Mistakes** — "Cut the shelf 1/4" too long", measurement changes, plan revisions
- **Stream of consciousness** — At higher levels, more rambling, tangential asides

These techniques can be applied to ANY theme to create a "rough" variant. The key insight: roughness isn't about making things look bad — it's about making them look like a person made them instead of a system.

---

## Workflow for Building Multiple Themes

When building themes in batches (typically 4 at a time):

1. Launch 4 parallel Task agents, one per theme, with detailed design specs
2. Each agent creates all 4 files in its theme directory
3. After all agents complete, update root files:
   - Add gallery cards to `index.html`
   - Add directory entries to `CLAUDE.md`
   - Move ideas from TODO to DONE in `ideas.txt` (if applicable)
4. Commit and push

Each agent needs:
- The theme name and directory name
- Specific font choices (3–4 Google Fonts)
- Full color palette with hex values
- Descriptions of the 4 unique components
- The template scenario (what the "user" is documenting)

---

## ideas.txt Format

The ideas file tracks theme concepts:

```
TODO
----
Theme Name
  Description paragraph with aesthetic details, component ideas,
  font suggestions, color notes.

DONE
----
Theme Name
  → directory-name/
```

When implementing a theme from ideas.txt, move it from TODO to DONE and add the `→ dirname/` reference.

---

## Gallery Page (index.html)

The root `index.html` is a dark gallery with:
- Hero section with title
- CSS grid of theme cards (auto-fill, minmax 340px)
- Each card has an iframe preview at 1200x900 scaled to 0.3, plus metadata
- Cards link to the theme's `index.html`
- The gallery uses its own inline styles (DM Sans/DM Serif Display/JetBrains Mono)

---

## Common Pitfalls

- **Don't hardcode colors** — Always use CSS custom properties from `:root`
- **Don't forget the 4 unique components** — Every theme needs them, not just reskinned standard components
- **Don't write generic templates** — The template should tell a story in the theme's world
- **Don't skip the gallery card** — It's easy to forget after building the theme files
- **Don't use image files** — All textures and decorations are CSS-only (gradients, pseudo-elements, SVG inline)
- **Don't forget light-background color dots** — Add `border-color:rgba(0,0,0,0.15)` on light-colored swatches in the gallery
- **Section numbering** — Use `01 — Label` format with the em-dash, not a regular hyphen
