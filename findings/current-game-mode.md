# Current Game Mode

## Research ID

`STATE-001`

## Status

**Not started**

## Research Question

Which RAM address, variable, or combination of values reliably identifies the game’s current operating state?

Z1 Atlas must eventually distinguish among states such as:

- Title screen
- File-selection screen
- Gameplay startup
- Overworld
- Dungeon
- Cave, cellar, or underground passage
- Inventory menu
- Screen transition
- Death sequence
- Ganon defeated
- Zelda room
- Zelda rescued
- Ending sequence

## Why This Matters

A location value is not meaningful by itself.

For example, a value of `$42` could represent:

- An overworld screen
- A dungeon room
- A temporary underground room
- A transition state
- An unrelated value while the game is not in active gameplay

Before Z1 Atlas can safely track locations, rooms, deaths, timing, or automatic splits, it must know what kind of game state is currently active.

This finding may eventually support:

- **Z1 Atlas**
  - Current-location tracking
  - Overworld and dungeon map switching
  - Run start and finish detection
  - Pause-aware timing
  - Death detection
  - Ganon and Zelda milestones
- **Z1 Dojo**
  - Reliable setup, combat, death, and reset-state detection
- **Z1 Tech Lab**
  - Drill start, attempt, success, and reset detection

## Scope

The first goal is not to identify every possible internal mode perfectly.

The initial goal is to find enough reliable information to distinguish:

1. Overworld
2. Dungeon
3. Cave, cellar, or underground area
4. Inventory menu
5. Screen transition
6. Death
7. Ganon defeated
8. Zelda rescued

Additional states can be documented later.

## Existing Knowledge

No findings have been copied into this project yet.

Useful information from the separate Z1 Dojo research may be referenced or rewritten later, but the original Dojo research files will remain untouched.

## Test Environment

Complete this section before recording results.

| Field | Value |
|---|---|
| Base game | |
| ROM region and revision | |
| ROM SHA-1 | |
| ROM MD5 | |
| Randomizer name | |
| Randomizer version | |
| Seed | |
| Flags | |
| Emulator | FCEUX |
| Emulator version | |
| Lua version or script | |
| Test date | |
| Researcher | |

## Candidate Sources

Possible sources of game-mode information may include:

- A dedicated mode byte
- A primary mode plus a secondary submode
- The active gameplay routine
- Current level or world flags
- Screen-transition state
- Menu state
- Death or ending flags
- A combination of several values rather than one address

No candidate address should be considered confirmed until it has been tested across several states and repeated.

## Planned Tools

- FCEUX RAM Search
- FCEUX Hex Editor
- FCEUX Debugger
- FCEUX Lua
- Save states created specifically for repeatable tests
- Optional frame-by-frame input
- A log file or CSV capture for comparing values

## Planned Test States

Create or prepare repeatable examples of the following:

| Test ID | State | Expected use |
|---|---|---|
| GM-01 | Title screen | Non-gameplay state |
| GM-02 | File selection | Non-gameplay menu |
| GM-03 | Standing on overworld | Active overworld |
| GM-04 | Moving between overworld screens | Transition |
| GM-05 | Inside a normal cave | Interior |
| GM-06 | Inside a dungeon room | Active dungeon |
| GM-07 | Entering an underground staircase | Interior transition |
| GM-08 | Inside an underground passage or item cellar | Underground |
| GM-09 | Inventory menu open | Paused/menu state |
| GM-10 | Taking lethal damage | Death begins |
| GM-11 | Death animation | Death sequence |
| GM-12 | Continuing after death | Gameplay restart |
| GM-13 | Ganon defeated | Major milestone |
| GM-14 | Searching Level 9 after Ganon | Run still active |
| GM-15 | Entering Zelda’s room | Final area |
| GM-16 | Zelda rescued | Official run finish |
| GM-17 | Ending sequence | Post-run state |

## Planned Research Procedure

### Pass 1: Broad RAM Search

1. Start from a save state on the overworld.
2. Search for values that remain stable while Link moves within one screen.
3. Enter a dungeon and filter for changed values.
4. Return to the overworld and verify whether candidates return to their earlier values.
5. Repeat with a cave and the inventory menu.
6. Record all promising addresses without assuming their meaning.

### Pass 2: Controlled State Changes

For each candidate address:

1. Load the exact same starting save state.
2. Enter only one new state.
3. Record the value before, during, and after the transition.
4. Repeat the test at least three times.
5. Test the same state from a different overworld screen or dungeon.
6. Reject candidates that actually describe a location, animation, or temporary counter rather than the game mode.

### Pass 3: Lua Observation

Create a small read-only Lua script that displays or logs:

- Frame number
- Candidate mode values
- Current level value
- Current room or screen value
- Menu state
- Transition state
- Death-related values

Use the script while moving through every planned test state.

### Pass 4: Cross-Seed Verification

After a candidate mode system works on one randomizer seed:

1. Test it on at least two additional seeds.
2. Test more than one dungeon.
3. Test more than one cave type.
4. Test death in both the overworld and a dungeon.
5. Verify Ganon defeat and Zelda rescue separately.
6. Record any flag or randomizer-version differences.

## Candidate Address Log

Add one row for every serious candidate.

| Address | Size | State or routine suspected | Observed values | Evidence | Status |
|---|---:|---|---|---|---|
| | | | | | Candidate |

## State Observation Log

| Test ID | Frame or time | Candidate values | Location values | What happened | Notes |
|---|---:|---|---|---|---|
| | | | | | |

## Findings

No findings recorded yet.

## Proposed Interpretation

No interpretation recorded yet.

A final interpretation may use one value or a combination such as:

```text
PrimaryMode + Submode + LevelState
```

The research should prefer the simplest reliable model, but not force every state into one byte if the game does not work that way.

## Verification Checklist

- [ ] Distinguishes overworld from dungeon
- [ ] Distinguishes gameplay from inventory menu
- [ ] Distinguishes normal rooms from underground areas
- [ ] Identifies screen transitions
- [ ] Identifies death reliably
- [ ] Distinguishes Ganon defeat from Zelda rescue
- [ ] Confirms that the run remains active after Ganon
- [ ] Works across multiple dungeons
- [ ] Works across multiple seeds
- [ ] Works after save-state reloads
- [ ] Has documented limitations
- [ ] Has a reproducible Lua test
- [ ] Has at least one independent re-test

## Confidence

**Not started**

Use one of these confidence levels when research begins:

- Candidate
- Observed once
- Repeated successfully
- Verified across locations
- Verified across seeds
- Verified across supported versions

## Known Limitations

None documented yet.

## Evidence and Artifacts

Add links or relative paths here as evidence is created.

Possible artifacts include:

- Lua scripts
- CSV logs
- Screenshots
- Save-state descriptions
- Memory dumps
- Debugger notes
- Test recordings

Do not commit copyrighted ROM files.

## Used By

- Z1 Atlas
- Z1 Dojo
- Z1 Tech Lab

## Next Action

Create the first read-only FCEUX Lua diagnostic script for observing candidate game-mode values and logging controlled state changes.
