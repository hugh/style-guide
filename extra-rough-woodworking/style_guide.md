# Extra-Rough Woodworking — Style Guide (Level 3)

The third and most extreme level of roughness in the woodworking theme family. This looks like someone's actual workshop notebook that got coffee spilled on it, was left open on the bench, has sawdust in the spine, and has been added to over months. Still readable and functional, but barely organized.

---

## Progression: Rough vs Rougher vs Extra-Rough

| Aspect | Rough (Level 1) | Rougher (Level 2) | Extra-Rough (Level 3) |
|--------|-----------------|-------------------|----------------------|
| Container width | 880px | 860px | 840px |
| Card rotations | 0.3–3° | 1–6° | 2–4°, overlapping (-0.25rem margins) |
| Stamp rotations | 0.5–3° | 2–6° | 4–8°, some barely readable |
| Callout rotation | -0.3° | -0.8° | -1.5° |
| Blueprint rotation | -0.2° | -1° | -2° |
| Section padding | 4rem/4.5rem | Slightly varied | Chaotic (2rem–6rem via nth-child) |
| Section borders | 2px/3px solid | Varied widths | Solid, dashed, dotted, double, none |
| Warm variants | 5 | 7 | 9 |
| Section numbers | IBM Plex Mono | Partially Caveat | ALL Caveat, large (1.3rem) |
| Some h3s | All Bitter | All Bitter | Odd h3s in Caveat (1.5rem) |
| Table headers | Mono, uppercase | Mono, uppercase | Caveat, handwritten |
| Table rows | Straight | Slight color | 0.5° alternating rotation, some Caveat cells |
| Card borders | 2px/2.5px solid | Varied widths | Solid, dashed, dotted, double mixed |
| Stamp opacity (faded) | 55% | 40% | 25% |
| Hero version font | IBM Plex Mono | Caveat | Caveat, rotated |
| Footer | Caveat | Caveat | All Caveat, rotated -0.8° |
| Coffee rings | — | Subtle | Large, dark, multiple placements |
| Tape strips | — | Clean | Yellowed, torn-edge, old variant |
| Pushpins | — | Small | Detailed with shadow |
| Sticky notes | — | — | 3 colors, torn bottom, heavy rotation |
| Paper clips | — | — | CSS wire shape |
| Torn edges | — | — | clip-path jagged polygon |
| Ink blots | — | — | Radial gradient splotches |
| Sideways notes | — | — | 90° rotated margin text |
| Dog ear | — | — | Folded corner triangle |
| Splatter | — | — | Scattered dots overlay |
| Crossed-out sections | — | — | Dimmed + diagonal strikethrough |
| Date stamps | — | — | Handwritten Caveat dates |
| Sawdust texture | — | — | Radial gradient dots on body |
| Wood grain | Moderate | Heavy | Very heavy (3 gradient layers) |

---

## Color Tokens

### Base Palette (shared with all woodworking themes)

```
--bg:        #f2e8d8    Background
--surface:   #e6d8c2    Card/component surface
--surface-2: #dac8ae    Deeper surface
--surface-3: #cebea0    Deepest surface
--border:    #b09878    Borders

--text:      #2a1c0e    Headings, bold
--text-dim:  #584830    Body text
--text-faint:#8a7858    Labels, captions

--accent:    #8b4520    Primary walnut accent
--accent-dim:#6a3418    Darker accent

--capture:   #4a7a38    Green (pine)
--refine:    #c89030    Amber (maple)
--execute:   #a83020    Red (cherry)
--batch:     #3868a0    Blue (steel)
```

### 9 Warm Variants (Level 3 adds warm-6 through warm-9)

```
--warm-1: #f0e4ce    Lightest
--warm-2: #ecdcc4
--warm-3: #e8d6bc
--warm-4: #e4d0b6
--warm-5: #f2e6d0
--warm-6: #e0caa8    New at Level 3
--warm-7: #e6d2b4    New at Level 3
--warm-8: #ead8c0    New at Level 3
--warm-9: #dcc4a0    New at Level 3
```

### Level 3 Utility Colors

```
--sticky-yellow: #fff8a0       Yellow Post-it
--sticky-pink:   #ffc0c8       Pink Post-it
--sticky-blue:   #c0e0ff       Blue Post-it
--tape:          rgba(235, 220, 180, 0.8)   Masking tape
--coffee:        rgba(100, 50, 10, 0.15)    Coffee ring stain
--coffee-dark:   rgba(80, 35, 5, 0.2)       Dark coffee center
--ink:           rgba(40, 20, 5, 0.1)       Ink blot
--sawdust:       rgba(180, 140, 80, 0.03)   Background scatter
```

---

## Typography

Four font families, same as Level 1 and Level 2:

| Font | Role | Level 3 Usage |
|------|------|--------------|
| **Bitter** | Headings (h1, h2, even h3s) | Still primary for h1/h2, but shares h3 with Caveat |
| **Source Sans 3** | Body text | Unchanged |
| **IBM Plex Mono** | Measurements, code | Reduced — section numbers moved to Caveat |
| **Caveat** | Handwritten layer | MASSIVELY expanded — section numbers, odd h3s, table headers, sticky notes, margin notes, hero label/version, footer, date stamps, pipe numbers |

At Level 3, Caveat is nearly a co-primary font. It appears on approximately 40% of all text elements.

---

## New Utility Classes (Level 3 Exclusive)

### `.sticky-note`

Post-it note overlay. All text is Caveat. Has torn bottom edge via clip-path. Rotated 3–5°.

**Color variants:**
- `.sticky-yellow` — Yellow (#fff8a0), default
- `.sticky-pink` — Pink (#ffc0c8)
- `.sticky-blue` — Blue (#c0e0ff)

```html
<div class="sticky-note sticky-yellow">Don't forget: buy more clamps</div>
<div class="sticky-note sticky-pink">URGENT: check moisture content</div>
<div class="sticky-note sticky-blue">Cool idea for later...</div>
```

### `.paper-clipped`

Adds a silver paper clip shape in the upper-right corner via CSS pseudo-elements (::before and ::after). Uses borders and border-radius to create the wire shape.

```html
<div class="callout paper-clipped">
  <p>This note is paper-clipped to the page.</p>
</div>
```

### `.torn`

Torn paper edge on the bottom via clip-path polygon with jagged points. Adds `padding-bottom: 2rem` to compensate for clipped area.

```html
<div class="flow-card capture torn">
  <h4>Torn Edge Card</h4>
  <p>The bottom looks ripped.</p>
</div>
```

### `.ink-blot`

Decorative radial-gradient splotch in the upper-left area. Uses multiple overlapping radial gradients for an organic blob shape. Via ::before pseudo-element.

```html
<div class="callout ink-blot">
  <p>There's an ink splotch on this.</p>
</div>
```

### `.sideways`

Text rotated -90° for margin annotations. Needs `position: absolute` within a `position: relative` parent. Font is Caveat, opacity 0.65.

```html
<div style="position: relative;">
  <div class="sideways">important!</div>
  <p>Main content here.</p>
</div>
```

### `.sketch-arrow`

Container for hand-drawn SVG arrows. The SVG should use wobbly paths and crude arrowheads.

```html
<div class="sketch-arrow">
  <svg viewBox="0 0 80 30">
    <path d="M5,15 C15,12 25,18 35,14 C45,10 55,17 70,15"
          fill="none" stroke="var(--accent)" stroke-width="1.5"/>
    <polygon points="70,15 64,11 65,19" fill="var(--accent)"/>
  </svg>
</div>
```

### `.splatter`

Scattered dots/drips overlay via ::after pseudo-element. Simulates sawdust particles or wood stain drips.

```html
<div class="diagram-wrap splatter">
  <p>Content with sawdust scattered across it.</p>
</div>
```

### `.dog-ear`

Folded corner triangle in the upper-right. Uses ::after for the fold and ::before for the shadow underneath.

```html
<div class="flow-card capture dog-ear">
  <h4>Dog-Eared Card</h4>
  <p>Someone folded the corner over.</p>
</div>
```

### `.coffee-ring`

Coffee mug ring stain. Large (110px), visible, with a darker center gradient. Via ::before pseudo-element.

**Placement variants:**
- Default: upper-right
- `.coffee-left` — upper-left
- `.coffee-bottom` — lower-right
- `.coffee-sm` — smaller (70px) version

```html
<div class="blueprint-card coffee-ring">...</div>
<div class="diagram-wrap coffee-ring coffee-left coffee-sm">...</div>
```

### `.taped`

Masking tape strip across the top center. Slightly torn edges via clip-path.

**Variants:**
- `.taped-corner` — angled tape in upper-right corner
- `.taped-old` — yellowed, aged tape

```html
<div class="blueprint-card taped">...</div>
<div class="callout taped taped-corner taped-old">...</div>
```

### `.pushpin`

Red pushpin at top center with shadow. Via ::after pseudo-element.

**Variants:**
- `.pushpin-left` — pin on left side
- `.pushpin-right` — pin on right side

```html
<div class="flow-card capture pushpin pushpin-right">...</div>
```

### `.crossed-out`

Dims content to 40% opacity and adds a diagonal strikethrough line (3px, var(--execute) color, rotated -1.5°). Use for abandoned sections.

```html
<div class="crossed-out">
  <p>This whole section was wrong. Ignore it.</p>
</div>
```

### `.date-stamp`

Handwritten date in Caveat, slightly rotated. Inline-block.

```html
<div class="date-stamp">feb 15 — disaster</div>
```

### `.margin-note.contradicts`

A margin note with red/cherry border instead of walnut, indicating it contradicts a previous note.

```html
<div class="margin-note contradicts">Actually, ignore what I said above...</div>
```

### `.lumber-stamp.double-border`

Stamp with misaligned box-shadow to simulate a double-stamped effect.

```html
<span class="lumber-stamp double-border">INSPECTED</span>
```

---

## Combining Classes

Classes are designed to be layered. Some useful combinations:

| Combination | Effect |
|-------------|--------|
| `.blueprint-card.coffee-ring.taped` | Blueprint that's been taped up and had coffee spilled on it |
| `.callout.paper-clipped.ink-blot` | Callout that's clipped to the page with an ink splotch |
| `.flow-card.pushpin.dog-ear` | Card pinned to the board with a folded corner |
| `.diagram-wrap.splatter.coffee-ring` | Diagram with sawdust and a coffee stain |
| `.blueprint-card.taped.coffee-ring.dog-ear` | Maximum chaos blueprint |

---

## Key Design Principles

1. **Physical artifacts** — Coffee rings, tape, pins, clips, ink blots. The notebook lives in a real workshop.
2. **Caveat everywhere** — It's no longer an accent. It's on section numbers, some headings, table headers, sticky notes, the footer. Almost co-primary.
3. **Genuine crookedness** — 2–4° card rotations, 4–8° stamp rotations, -1.5° callouts. Noticeably crooked, not just slightly off.
4. **Chaotic spacing** — Every section has different padding. Borders alternate between 5 different styles. The rhythm is intentionally broken.
5. **Destructive marks** — Sticky notes cover content. Coffee obscures corners. Tape holds things together. The document shows wear.
6. **Still functional** — Despite the chaos, everything is readable. Colors have contrast. Components work. The grid holds. Messy, not broken.

---

## Compatibility

Uses the same class names as `rough-woodworking/` and `woodworking/`. Swapping `tokens.css` changes the roughness level while keeping the layout intact. Level 3 adds new classes but doesn't rename existing ones.

---

## Fonts Import

```css
@import url('https://fonts.googleapis.com/css2?family=Bitter:wght@400;500;600;700&family=Caveat:wght@400;500;600;700&family=Source+Sans+3:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500;600&display=swap');
```
