# Z1 Research Library

A shared technical research project for understanding **The Legend of Zelda (NES)** and **Zelda 1 Randomizer** well enough to support future tools, practice ROM hacks, trackers, analysis software, and community resources.

This repository is intentionally separate from the existing research used by **Z1 Dojo**. The original Z1 Dojo research folder should remain untouched. Useful discoveries may be copied or rewritten here later, but this project starts fresh.

## Purpose

The goal of this project is to collect reliable, reusable technical knowledge about Zelda 1 in one place.

This research may eventually support:

- **Z1 Dojo** — configurable combat and boss practice
- **Z1 Atlas** — autotracking, dungeon reconstruction, run timing, statistics, route analysis, and stream overlays
- **Z1 Tech Lab** — repeatable practice for clips, screen scrolling, KhananaKey, and other advanced techniques
- Future Zelda 1 tools that have not been designed yet

This repository is not one of those applications. It is the technical foundation they can share.

## Status

This project is in its **early foundation stage**.

It currently begins with a README and a CHANGELOG. The structure, findings, templates, scripts, and test assets will be added gradually as the research grows.

## Repository Approach

This project should grow slowly and deliberately.

- Keep the README focused on what the project is and how it works.
- Track project progress and milestone history in `CHANGELOG.md`.
- Add folders and files only when they are actually needed.
- Prefer a small amount of verified research over a large amount of undocumented guesses.

## Research Principles

- **Preserve existing work:** The current Z1 Dojo research remains separate and unchanged.
- **Separate observation from proof:** A value changing once does not make it confirmed.
- **Record reproduction steps:** Findings should be reproducible whenever possible.
- **Prefer reusable documentation:** Write findings so they can help Dojo, Atlas, and Tech Lab.
- **Be honest about confidence:** Mark findings as candidate, observed, repeated, or verified.
- **Prefer read-only tracking research:** Atlas-oriented emulator research should avoid modifying game state unless a test specifically requires it.

## Intended Research Areas

The long-term research areas include:

- Game state and transitions
- Player state and inventory
- Rooms and dungeons
- Enemies and bosses
- Randomizer compatibility
- Emulator integration
- Timing, milestones, and run completion
- Data needed for practice export into Z1 Dojo

## Z1 Atlas Notes

Z1 Atlas is expected to support features such as:

- Current overworld and dungeon position
- Visited-screen and visited-room tracking
- Optional reveal of full dungeon shape after obtaining the Map
- Staircase and passage inference
- Room timing, visit counts, deaths, and damage
- Randomizer-aware automatic splits
- Route replay, heatmaps, and post-run analysis
- Compact layouts suitable for half-screen use beside an emulator
- Optional OBS / YouTube / Twitch overlays

Major assistance features should be individually configurable rather than forced.

## Run Completion Definition

For Z1 Atlas, defeating Ganon is a major milestone but not the end of the run.

The run remains active while the player continues searching Level 9. The official finish occurs when **Zelda is found and rescued**.

## Legal and Community Notes

- This project should not distribute copyrighted Zelda ROM files.
- ROM hacks should be distributed as patches that require the user to supply the appropriate base ROM.
- Autotracking and RAM-reading features may not be permitted in competitive Z1R races.
- Any tool using autotracking should clearly distinguish practice use from manual or race-oriented modes.

## Progress Tracking

For project history, milestone tracking, and ongoing changes, see:

- [`CHANGELOG.md`](./CHANGELOG.md)

## Initial Next Steps

The first technical research targets should be:

1. Current game mode
2. Current overworld screen
3. Current dungeon number
4. Current dungeon room
5. Dungeon Map possession

These findings would unlock the earliest useful Z1 Atlas prototype while also helping Z1 Dojo and Z1 Tech Lab.
