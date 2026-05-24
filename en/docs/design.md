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

## Token Binding Mechanics

The **core loop** is: Game → Winner → Winner picks Recipient → Recipient claims Token → Repeat. But *how* the token connects a child to the finale reward is a design choice with several variants:

### Binding Strategies

| Strategy | When Binding Happens | Treasure Preparation | Best For |
|----------|---------------------|---------------------|----------|
| **Bind-on-receive** | Recipient marks token with their personal symbol at receive time | Treasures are unmarked; match symbols at the end | Flexible — no prep needed per child |
| **Pre-bound tokens** | Tokens are pre-marked with symbols *before* the party | Each treasure is pre-labeled with a matching symbol | Less work during the party; surprise element |
| **Positional** | Token = puzzle piece; position on assembled map points to treasure | Treasures hidden at locations the assembled map reveals | Most immersive; requires spatial puzzle |

### How It Works (detailed)

```
┌─────────────────────────────────────────────────────────────┐
│                    BIND-ON-RECEIVE                          │
│                                                             │
│  1. Child receives blank puzzle piece                       │
│  2. Child marks it with their personal symbol (sticker/draw)│
│  3. At finale: assembled puzzle shows location              │
│  4. Each child finds treasure tagged with their symbol      │
│                                                             │
│  Symbol assignment: done at party start (pick from set)     │
│  Treasure prep: wrap N identical treasures, label at end    │
│                  OR pre-label and match during assembly     │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                    PRE-BOUND TOKENS                         │
│                                                             │
│  1. Before party: mark each puzzle piece with a symbol      │
│  2. Before party: mark each treasure with matching symbol   │
│  3. Recipient gets a random piece (symbol is fate)          │
│  4. At finale: child matches their piece's symbol to a      │
│     treasure — "which treasure is YOURS?"                   │
│                                                             │
│  Pro: Zero work during party, surprise which symbol you get │
│  Con: Must prepare N distinct treasures in advance          │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                    POSITIONAL                               │
│                                                             │
│  1. Assembled pieces form a map/image                       │
│  2. Map reveals ONE shared location                         │
│  3. Group goes together to find ALL treasures there         │
│  4. Individual binding via name tags or symbol stickers     │
│     on each treasure at the location                        │
│                                                             │
│  Pro: Most dramatic reveal, strongest group moment          │
│  Con: All treasures must be at one spot                     │
└─────────────────────────────────────────────────────────────┘
```

### Symbols vs. Colors

Use **thematic symbols** rather than colors for personal markers:
- Colors feel arbitrary and can trigger "I wanted blue!" conflicts
- Themed symbols are part of the story (cheese types, animal paw prints, planet icons)
- Symbols work in grayscale (important for printed materials)
- Children feel ownership of "their" symbol throughout the party

### Example Instances

| Theme | Symbols | Binding Strategy |
|-------|---------|-----------------|
| Cats & Mice | Cheese types (Swiss, Gouda, Brie…) | Bind-on-receive (sticker on puzzle piece) |
| Pirates | Skull variants (hat, eyepatch, parrot…) | Pre-bound (coins pre-stamped) |
| Space | Planet icons (Saturn, Mars, Moon…) | Positional (star map reveals coordinates) |

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
