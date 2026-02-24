# Rough Woodworking — Style Guide

A less-polished variant of the Woodworking theme. Same warm wood palette and workshop components, but with intentional imperfections: varied card warmth, handwritten annotations, slight rotations, and personal voice in the content.

---

## What's Different from `woodworking/`

| Aspect | Polished | Rough |
|--------|----------|-------|
| Card backgrounds | All `--surface` | 5 `--warm-N` variants via nth-child |
| Hero alignment | Centered | Left-aligned |
| Section borders | All 2px | Alternating 2px / 3px |
| Section padding | 5rem / 5rem | 4rem / 4.5rem (mismatched) |
| Container width | 900px | 880px |
| Animations | Fade-up on hero | None |
| Stamps rotation | 2 fixed angles | Each nth-child unique |
| Principle numbers | Bitter serif | Caveat handwritten |
| Callouts | Straight | Rotated -0.3deg |
| Tags | Straight | Alternating rotation |
| New elements | — | `.scrawl`, `.margin-note`, `.struck`, `.amended` |
| Font families | 3 (Bitter, Source Sans 3, IBM Plex Mono) | 4 (+ Caveat) |
| Content voice | Corporate/technical | Personal/opinionated |

---

## Additional CSS Tokens

```
--warm-1: #f0e4ce    Lightest warm (used on odd cards)
--warm-2: #ecdcc4
--warm-3: #e8d6bc
--warm-4: #e4d0b6    Deepest warm
--warm-5: #f2e6d0    Alternate light
```

---

## New Utility Classes

### `.scrawl`
Inline handwritten text in Caveat. Use for annotations within paragraphs.

### `.margin-note`
Block-level annotation with walnut left border, Caveat font, slight rotation. Use for asides and personal commentary.

### `.struck`
Strikethrough with reduced opacity. Combine with `.amended` for corrections.

### `.amended`
Accent-colored bold text. Place after `.struck` for a "crossed out and corrected" pattern.

### `.faded`
Applied to `.lumber-stamp` for a partially-worn stamp look (55% opacity).

---

## Key Design Principles

1. **Varied warmth** — `--warm-1` through `--warm-5` assigned via `nth-child` so no two adjacent cards match.
2. **Handwritten layer** — Caveat for margin notes, principle numbers, and inline scrawl. The human voice on top of the structure.
3. **Slight rotations** — Callouts (-0.3°), stamps (each unique via nth-child), tags (alternating ±0.8°), swatches (alternating).
4. **Imperfect spacing** — Section padding doesn't match. Container is 880px. Some borders are thicker.
5. **Personal content** — The template reads like real build notes. Opinions, mistakes, amendments, references to real products and techniques.
6. **No animation** — Things just appear. No smooth fade-ups or transitions on load.
7. **Heavier texture** — Wood grain on body and hero is more visible. Blueprint grids are coarser.

---

## Compatibility

The rough version uses the same class names as the polished `woodworking/` theme, so they're interchangeable. Swap `tokens.css` and the layout stays the same — just rougher.
