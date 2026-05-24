# Party Quest — Copilot Instructions

## Project Structure

This is a multilingual project using **language folders at root** (Approach A):

```
party-quest/
├── en/          ← English content
├── de/          ← German content
├── fr/          ← French content
├── templates/   ← Language-neutral templates (shared JS/CSS logic)
└── .github/     ← This file
```

## Multilingual Sync Rules

**CRITICAL:** When modifying content in one language folder, always consider the counterpart:

1. **Structural changes** (HTML layout, CSS, JS logic) → apply identically to ALL language variants
2. **Content changes** (text, stories, instructions) → flag the other language(s) as needing translation
3. **New files** → create a stub/placeholder in all other language folders
4. **Deleted files** → remove from all language folders

### File Parity

Every file in `en/` must have a counterpart in `de/` (and vice versa). Exceptions:
- Theme-specific examples may exist in only one language initially
- `templates/` is shared (language-neutral)

### Naming Convention

- `en/docs/design.md` ↔ `de/docs/design.md` (same filename)
- `en/docs/game-catalog.md` ↔ `de/docs/spielekatalog.md` (translated filename OK)
- HTML files: `gameplan.html` ↔ `spielplan.html` (translated filename OK)

## HTML Game Plans

- Target: A4 paper (210×297mm)
- Use `page-break-inside: avoid` on game blocks
- Use `print-color-adjust: exact` for backgrounds
- UI panels hidden on print via `@media print`
- Player count drives table rows dynamically (N players → N rows)
- Game count = Players - 1

## SVG Templates

- Use mm units for 1:1 printing
- Keep a 5cm unscaled control measure line
- Parameterize via JS sliders (not hardcoded dimensions)
- Instructions/UI hidden on print

## When Asked to Modify a Game Plan

1. Check which language version is being edited
2. If the change is structural (CSS/JS), apply to all language versions
3. If the change is content (German text), only change that file
4. After any change, note if other languages need updating

## Print Considerations

- All colors must be visible on grayscale printers (avoid pure white shapes)
- Use strong strokes (≥1px) on light-colored SVG elements
- Tables need explicit borders in `@media print` (Firefox doesn't inherit)
- Test with both Chrome and Firefox print preview
