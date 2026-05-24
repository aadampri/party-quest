# Framework Design

## Architecture

Party Quest is a **template-based** framework. Each quest instance is a self-contained HTML file that includes:

- Story prompts (theme-specific narrative)
- Game descriptions with rules
- Score tables (dynamically sized per player count)
- A game selector (choose which games to include)
- Print-optimized layout for A4

### Component Model

```
┌─────────────────────────────────────┐
│  UI Panel (screen only)             │
│  - Player count                     │
│  - Name inputs                      │
│  - Game selector                    │
│  - Print button                     │
└─────────────────────────────────────┘
┌─────────────────────────────────────┐
│  Opening (Letter/Story)             │  ← Page 1
└─────────────────────────────────────┘
┌─────────────────────────────────────┐
│  Legend (symbols, rules overview)    │  ← Page 2
├─────────────────────────────────────┤
│  Game Block × N                     │  ← Pages 2–N
│  ┌─ Title                           │
│  ├─ Story prompt (themed)           │
│  ├─ Rules list                      │
│  ├─ Score table (dynamic rows)      │
│  └─ Note (winner → recipient)       │
├─────────────────────────────────────┤
│  Finale (group activity)            │
├─────────────────────────────────────┤
│  Fallback games (hidden if unused)  │
├─────────────────────────────────────┤
│  Material checklist                 │
├─────────────────────────────────────┤
│  Extras (stickers, templates)       │
└─────────────────────────────────────┘
```

## Game Types

Games fall into measurable categories:

| Type | Metric | Example |
|------|--------|---------|
| **Timed** | Fastest wins | Balance race, obstacle course |
| **Accuracy** | Closest to target | Weight guessing, dice prediction |
| **Distance** | Farthest wins | Standing jump, throwing |
| **Accumulation** | Most collected | Catching, sponge soaking |
| **Luck** | Random outcome | Dice roll, card draw |
| **Creative** | Judged/voted | Best disguise, funniest face |

### Energy Levels

Each game has an energy profile:

- 🟢 **Calm** — craft, puzzle, guessing (sitting/standing)
- 🟡 **Medium** — throwing, balancing, precision tasks
- 🔴 **High** — running, racing, obstacle courses

**Recommended arc:** 🟢 → 🟡 → 🟡 → 🔴 → 🟡 → 🔴 → Finale

## Player Scaling

- N players → N-1 games needed (last token goes to the child without one)
- Game selector allows choosing which N-1 games from the full catalog
- Tables dynamically add/remove rows
- Works for 2–9 players (limited by available games: 6 main + 2 fallback = 8 max)

## Print Design

- Target: A4 paper (210×297mm, printable area ~190×277mm)
- Each game block uses `page-break-inside: avoid`
- Background colors print via `print-color-adjust: exact`
- UI panel hidden on print
- All content must be legible in grayscale (printers vary)

## Craft Templates

Optional printable templates (e.g., racket shape) use:
- SVG at 1:1 scale in mm units
- Parameterizable dimensions (slider controls)
- 5cm control measure line (unscaled) for print verification
- Instructions hidden on print, only the template prints
