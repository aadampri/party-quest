# Party Quest

A framework for designing structured kids' party games with a quest narrative arc.

## Concept

**Core idea:** A series of mini-games connected by a story, where each game winner advances a shared objective (puzzle pieces, map fragments, keys) that leads to a final group reward.

### Core Loop

```
Game → Winner → Winner picks recipient → Recipient claims token → Repeat
```

After all tokens are distributed, the group assembles them together to unlock the finale (find the treasure, open the chest, solve the riddle).

### Complexity Levels

| Level | Token System | Best For |
|-------|-------------|----------|
| **Simple** | Stickers placed on a pre-made map | Ages 3–5 |
| **Medium** | Puzzle pieces earned through games | Ages 5–7 |
| **Advanced** | Puzzle pieces + assembly reveals hidden location | Ages 7+ |

## Framework Parameters

| Parameter | Description | Range |
|-----------|-------------|-------|
| Players | Number of children | 2–9 |
| Games | Number of mini-games (= players - 1) | 1–8 |
| Complexity | Simple / Medium / Advanced | — |
| Theme | Story wrapper (cats/mice, pirates, space...) | Any |

## How It Works

1. **Choose a theme** — provides the narrative framing for each game
2. **Set player count** — determines how many games are needed
3. **Select games** from the catalog — mix physical, mental, creative, luck-based
4. **Print the game plan** — interactive HTML with editable tables
5. **Run the party** — read story prompts, play games, fill in results

## Structure

```
en/          ← You are here (English)
de/          ← German version
templates/   ← Language-neutral starter templates
```

## Examples

- [Cats & Mice](examples/cats-and-mice/) — House cat is on vacation, mice hunt for hidden cheese

## Game Design Principles

1. **Every child wins something** — the puzzle mechanic ensures everyone gets a piece
2. **Winner chooses recipient** — social element, no child is "last"
3. **Mix game types** — alternate physical/mental/luck to give different kids a chance
4. **Energy arc** — start calm (craft), build up (physical), peak (race), finale (group)
5. **Fallback games** — always have 2+ spare games ready
6. **Scalable** — same framework works for 3 kids or 9 kids

## License

MIT
