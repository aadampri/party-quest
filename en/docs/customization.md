# Customization Guide

How to create your own Party Quest theme.

## Step 1: Choose a Theme

A good theme provides:
- A **villain/obstacle** (who hid the treasure / set the traps)
- A **role for the children** (mice, pirates, astronauts, knights)
- A **treasure** (cheese, gold, stars, dragon eggs)
- **Framing for each game** (each game = a "trap" or "challenge" to overcome)

### Theme Examples

| Theme | Villain | Role | Treasure | Trap Framing |
|-------|---------|------|----------|--------------|
| Cats & Mice | House cat | Mice | Cheese | Cat traps |
| Pirates | Sea monster | Pirates | Gold | Island obstacles |
| Space | Alien emperor | Astronauts | Star crystals | Asteroid fields |
| Knights | Dragon | Knights | Dragon eggs | Castle defenses |

## Step 2: Write the Opening

A letter or message from the villain that:
1. Introduces the story
2. Explains what was hidden
3. Warns about the "traps" (games)
4. Motivates the kids to play

## Step 3: Frame Each Game

Take a generic game (e.g., "balance race") and wrap it in theme language:

**Generic:** "Balance an object on a paddle, walk around a marker."

**Cats & Mice:** "Carry the stolen cheese without dropping it! If it falls, the alarm goes off!"

**Pirates:** "Carry the cannon ball across the deck in a storm! Don't let it roll overboard!"

## Step 4: Design Symbols

Each child gets a unique symbol (for marking puzzle pieces and matching to their treasure):
- Must be simple enough for kids to draw/recognize
- Must be distinct from each other
- Should fit the theme (cheese types, pirate flags, planet shapes)

## Step 5: Create the Game Plan HTML

Start from `templates/gameplan-blank.html` and:
1. Set the language (`<html lang="xx">`)
2. Write story prompts for each game
3. Customize the legend with your symbols
4. Adjust the material checklist
5. Design stickers (SVG icons for the symbols)

## Step 6: Test Print

- Verify all games fit on pages (no splits)
- Check that symbols are visible in grayscale
- Measure the 5cm control line
- Test the UI panel (player count, names, game selector)

## Tips

- **Less is more:** 4-6 games is ideal. More causes fatigue.
- **Weather backup:** Have 1-2 indoor alternatives for outdoor games
- **Time budget:** ~10 min per game + transitions. 6 games ≈ 90 min total.
- **Prep the finale:** Hide treasures BEFORE guests arrive
