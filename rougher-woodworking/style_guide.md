# Rougher Woodworking — Style Guide (Level 2)

A further-roughened variant of the Woodworking theme. Builds on `rough-woodworking/` (Level 1) by escalating rotations, border variation, and texture — and adding physical-artifact classes like coffee rings, masking tape, pushpins, and dog-ears.

Not as extreme as a hypothetical Level 3. This is still readable, still structured. It just feels like the plans have been sitting on the workbench for a couple weeks.

---

## Rough vs Rougher — Comparison

| Property | Rough (Level 1) | Rougher (Level 2) |
|----------|-----------------|-------------------|
| Container width | 880px | 860px |
| Card backgrounds | 5 warm variants | 7 warm variants (+ warm-6, warm-7) |
| Card rotation | None | 1--2deg via nth-child |
| Card padding | 1.5rem uniform | 1.25--1.75rem, varies per card |
| Card borders | 2px / 2.5px solid | 1.5--3px, some dashed |
| Stamp rotation | 0.5--3deg | 3--6deg |
| Stamp opacity (faded) | 55% | 40% |
| Stamp variants | Basic | + `.double-border` |
| Callout rotation | -0.3deg | -0.8deg |
| Tag rotation | +/-0.8deg | +/-1.5--2deg |
| Section padding | 4rem / 4.5rem | 3rem--5.5rem wildly varied per nth-child |
| Section border widths | 2px / 3px (alternating) | 1.5px, 2px, 3px, 4px per nth-child |
| Section border styles | All solid | Some dashed |
| Margin note font size | 1.05rem | 1.2rem |
| Margin note opacity | 0.85 | 0.9 |
| Margin note margin | left: 1rem | left: -0.5rem (intrudes into content) |
| Margin note border | 2px | 3px |
| Hero label font size | 1.2rem | 1.5rem (Caveat) |
| Hero subtitle | Normal | Slightly rotated (-0.8deg) |
| Principle numbers | 2.8rem | 3.5rem, alternating rotation |
| Body grain texture | 2 layers | 3 layers + knot marks |
| Blueprint card rotation | -0.2deg | -1deg / +0.8deg (nth-child) |
| Blueprint grid | 18px | 16px (denser) |
| Dovetail divider | Straight | Rotated 0.5deg |
| Table rows | Alternating tint | + rotation (0.2deg), uneven cell padding |
| Tool rack background | warm-2 | warm-6 |
| New artifact tokens | -- | `--tape`, `--coffee` |
| New utility classes | -- | `.coffee-ring`, `.taped`, `.pinned`, `.dog-ear`, `.pencil-underline`, `.double-border` |

---

## Additional CSS Tokens (beyond Level 1)

```
--warm-6: #e0caa8      Even deeper warm, for more card variety
--warm-7: #f4e8d4      Another light variant
--tape: rgba(240, 230, 200, 0.7)   Semi-transparent masking tape color
--coffee: rgba(120, 70, 20, 0.12)  Faint brown for coffee ring
```

All Level 1 tokens (`--warm-1` through `--warm-5`, `--bg`, `--surface`, `--accent`, etc.) are identical.

---

## New Utility Classes (Level 2)

### `.coffee-ring`
A faint brown ring (~80px) positioned in the top-right corner via `::after`. The element needs `position: relative` or equivalent. The ring is purely decorative and does not affect layout. Uses the `--coffee` token.

### `.taped`
A masking tape strip across the top center of the element via `::before`. About 90px wide, slightly transparent off-white, rotated -2.5deg, with rough edges via clip-path. The tape extends a few pixels above the element's top edge, so `overflow: visible` may be needed on the parent.

### `.pinned`
A red pushpin dot (12px) in the top-left corner via `::before`. Includes a radial gradient for a 3D look and a subtle drop shadow.

### `.dog-ear`
A folded-corner triangle (24px) in the top-right corner via `::after`. The fold color is `--bg` so it appears as if the corner has been bent back. Applies `overflow: hidden` to the element.

### `.pencil-underline`
A wavy underline in the accent color applied to inline text. Uses `text-decoration-style: wavy` with `text-decoration-color: var(--accent)`. Thickness is 1.5px with a 3px offset.

### `.double-border`
Applied to `.lumber-stamp` elements. Adds an `outline` in `currentColor` with a 2px offset, creating a double-border effect that makes the stamp look more official or worn.

---

## Pseudo-Element Conflicts

Be aware of class combinations that share the same pseudo-element:

| Pseudo-element | Classes that use it |
|---------------|-------------------|
| `::before` | `.taped`, `.pinned` |
| `::after` | `.coffee-ring`, `.dog-ear` |

Combining two classes that use the same pseudo-element will cause one to override the other. Choose one per pseudo-element per element.

Note: `.flow-card` uses `::before` for its colored top bar. Adding `.taped` or `.pinned` to a flow card will conflict with the top bar. If you need tape or a pin on a flow card, wrap it or use a different card type.

Similarly: `.blueprint-card` uses both `::before` (inner dashed border) and `::after` (pin dot). Adding `.coffee-ring` or `.dog-ear` will override the pin; adding `.taped` or `.pinned` will override the inner border.

---

## Content Voice (Level 2)

The template voice is more personal than Level 1:

- **Specific dates**: "Tuesday morning, Feb 11th"
- **Named shops with opinions**: "Anderson's had garbage this week"
- **Prices**: "$12.50/bf for the cherry, which is highway robbery"
- **Weather and conditions**: "Heater broke again, working in 45 deg F"
- **Frequent corrections**: At least 3 `.struck` / `.amended` pairs
- **Argumentative margin notes**: Notes that disagree with or undercut the main text
- **Self-deprecating humor**: "Past me never did this and past me was an idiot"
- **Mid-build plan changes**: Whole sections about pivoting the design
- **Physical artifacts**: Coffee rings on cost breakdowns, tape on notes

---

## Key Design Principles

1. **More rotation everywhere** — Cards tilt 1--2deg. Stamps go 3--6deg. Tags, callouts, table rows, dividers — everything has a slight angle now.
2. **Border chaos** — Section borders range from 1.5px to 4px and some are dashed. Card borders vary per nth-child. It's not random — it's patterned — but it feels random.
3. **Physical artifacts** — Coffee rings, tape, pushpins, dog-ears. These are the things that happen to paper in a real workshop.
4. **Louder handwriting** — Caveat is bigger (1.2--1.5rem depending on context) and more opaque. The human voice is harder to ignore.
5. **Wider warmth range** — 7 warm variants instead of 5. More color temperature variety across cards and panels.
6. **Heavier texture** — Three layers of grain on the body, plus knot marks via radial gradients. The wood is rougher.
7. **Still readable** — Despite all the roughness, the hierarchy is clear. Headings are headings. Body text is body text. The chaos is controlled.

---

## Compatibility

Uses the same class names as `rough-woodworking/` and `woodworking/`. Swap `tokens.css` and the layout stays the same — just rougher. New classes (`.coffee-ring`, `.taped`, etc.) are additive and won't break layouts that don't use them.

---

## Fonts

Same four families as Level 1, loaded via the same Google Fonts import:

- **Bitter** (400, 500, 600, 700) — Headings
- **Caveat** (400, 500, 600, 700) — Handwritten annotations, margin notes, principle numbers
- **Source Sans 3** (300, 400, 500, 600) — Body text, card descriptions
- **IBM Plex Mono** (400, 500, 600) — Labels, measurements, section numbers, code
