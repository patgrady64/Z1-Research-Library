# Z1 Research Library

A shared technical research project for understanding **The Legend of Zelda (NES)** and **Zelda 1 Randomizer** well enough to support future tools, practice ROM hacks, trackers, analysis software, and community resources.

This repository is separate from the existing research used by **Z1 Dojo**. Nothing in the Z1 Dojo research folder should be moved, renamed, or deleted. Useful discoveries may be copied or rewritten here later, but the original Dojo research remains untouched.

## Purpose

The goal of this project is to collect reliable, reusable technical knowledge about Zelda 1 in one place.

The research may eventually support:

- **Z1 Dojo** — configurable combat and boss practice
- **Z1 Atlas** — autotracking, dungeon reconstruction, run timing, statistics, route analysis, and stream overlays
- **Z1 Tech Lab** — repeatable practice for clips, screen scrolling, KhananaKey, and other advanced techniques
- Future Zelda 1 tools that have not been designed yet

This repository is not one of those applications. It is the technical foundation they can share.

## Project Status

**Early foundation stage**

The project currently begins with this README only. Research files, indexes, templates, scripts, recordings, and folder structure will be added gradually as they are needed.

The priority is to document findings carefully rather than create a large empty folder structure before we know what belongs in it.

## Research Goals

The long-term research areas include:

### Game State

- Current game mode
- Current overworld screen
- Current dungeon
- Current dungeon room
- Current underground or cellar state
- Pause, transition, death, victory, and ending states

### Player State

- Position and movement
- Health and damage
- Inventory
- Sword, ring, bombs, keys, and equipment
- Triforce pieces
- Temporary effects and status values

### Rooms and Dungeons

- Room IDs and coordinates
- Room geometry and tile layouts
- Dungeon shape and Map data
- Visited-room state
- Doors, shutters, locked doors, and bombable walls
- Staircase and underground passage connections
- Dungeon entrances, exits, and transitions
- Level 9, Ganon, and Zelda completion behavior

### Enemies and Bosses

- Enemy and boss IDs
- Object slots
- Spawn behavior
- Position and movement
- Projectiles
- Damage sources
- Defeat and room-clear state
- Graphics and CHR data

### Randomizer Support

- Supported Zelda 1 Randomizer versions
- ROM hashes and build identification
- Memory-layout differences
- Flag-dependent behavior
- Dungeon generation data
- Compatibility limitations

### Emulator Integration

- FCEUX Lua memory access
- Local communication with external applications
- Mesen support
- BizHawk support
- A shared protocol that allows multiple emulator bridges to communicate with Z1 Atlas

## Research Principles

### Preserve Existing Work

The current Z1 Dojo research library is not part of this repository and should remain unchanged.

When a Dojo discovery is useful here, it should be copied or rewritten with its original source clearly noted.

### Separate Observation from Proof

A value changing once does not make it confirmed.

Research should distinguish between:

- Candidate
- Observed
- Repeated
- Verified across rooms
- Verified across seeds
- Verified across supported versions

### Record Reproduction Steps

A finding is more valuable when another person can reproduce it.

Whenever practical, documentation should include:

- ROM or randomizer version
- Emulator and version
- Starting state
- Exact test steps
- Expected values
- Actual values
- Save state, recording, screenshot, memory dump, or code reference
- Known exceptions

### Prefer Read-Only Research

Tools used for Z1 Atlas should read game state without modifying it.

ROM hacks such as Z1 Dojo and Z1 Tech Lab will intentionally modify game behavior, but emulator bridges and autotracking research should remain read-only unless a test specifically requires otherwise.

### Be Honest About Confidence

The project should never present an inference as a confirmed fact.

For example, returning from an underground area to a different dungeon room is strong evidence of a connecting passage staircase. It may still be stored as an inference until the relevant transition data is fully understood.

### Keep Research Reusable

A finding should not be documented only in terms of one feature.

Instead of writing:

> This is the byte Atlas uses to color a room.

Prefer:

> This byte appears to contain the current dungeon room ID. It may be used by Atlas for room tracking, by Dojo for encounter setup, and by Tech Lab for drill validation.

## Intended Z1 Atlas Research

Z1 Atlas is expected to require research that can support:

- Current overworld and dungeon position
- Visited-screen and visited-room tracking
- Different display states for:
  - Current room
  - Visited room
  - Known but unvisited room
  - Unknown room
- Optional full dungeon-shape reveal after obtaining the Map
- Dungeon staircase and passage inference
- Room-entry and room-exit timing
- Visit counts for rooms, dungeons, and overworld screens
- Damage and death locations
- Likely cause of death
- Enemy combinations present during difficult rooms
- Run start, Ganon defeat, and Zelda rescue milestones
- Randomizer-aware automatic splits
- Route replay, heatmaps, and post-run analysis
- Exporting difficult encounters into Z1 Dojo
- Compact layouts suitable for using Atlas beside an emulator on one monitor
- Optional OBS, YouTube, and Twitch overlays

Not every feature is guaranteed to be equally detectable. Research should identify what is confirmed, what is inferred, and what may remain unavailable.

## Intended Z1 Dojo Research

Z1 Dojo research may include:

- Regular enemy setup
- Up to eight active enemies
- Safe randomized spawn positions
- Arena geometry
- Door configuration
- Player loadouts
- Boss initialization
- Single and triple Dodongo encounters
- Reliable reset and retry behavior
- Encounter import from Z1 Atlas
- Later setup sharing, advanced statistics, extra arenas, and visible-Ganon options

## Intended Z1 Tech Lab Research

Z1 Tech Lab research may include:

- Block clips
- Ladder clips
- Screen scrolling and wrapping
- One-frame directional inputs
- Pixel alignment
- KhananaKey
- Bomb placement
- Door and key techniques
- Ganon positioning
- Other repeatable Zelda 1 execution techniques

## Run Completion Definition

For Z1 Atlas, defeating Ganon is a major milestone but not the end of the run.

The run remains active while the player continues searching Level 9. The official finish occurs when **Zelda is found and rescued**.

This distinction should be preserved in timing, splits, statistics, and post-run analysis.

## Optional Features

Major Z1 Atlas assistance and analysis features should be individually configurable.

Examples include:

- Reveal full dungeon shape after obtaining the Map
- Show current room
- Show visit counts
- Show room timers
- Automatic location marking
- Automatic splits
- Damage-source inference
- Route suggestions
- Practice recommendations
- Stream overlay modules

Users should be able to keep the interface minimal or enable deeper analysis.

## Legal and Community Considerations

This project should not distribute copyrighted Zelda ROM files.

ROM hacks should be distributed as patches that require the user to supply an appropriate legally obtained base ROM.

Autotracking and RAM-reading features may not be permitted in competitive Z1R races. Any application using those features should clearly distinguish practice use from manual or race-oriented modes and should not claim race legality without approval from the relevant community organizers.

## First Research Priorities

The first technical targets should be small and foundational:

1. Current game mode
2. Current overworld screen
3. Current dungeon number
4. Current dungeon room
5. Dungeon Map possession
6. Dungeon layout representation
7. Underground transition behavior
8. Death state
9. Health and damage events
10. Enemy object slots

These discoveries would unlock the earliest useful Z1 Atlas prototype while also benefiting Z1 Dojo and Z1 Tech Lab.

## Repository Philosophy

This project should grow slowly and deliberately.

A small number of verified findings is more useful than a large collection of undocumented addresses, guesses, and temporary files.

The guiding rule is:

> Discover it, reproduce it, document it, verify it, and preserve it for every future Z1 project.
