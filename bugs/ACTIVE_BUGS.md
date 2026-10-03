# ACTIVE BUG TRACKER: POKÉMON ANCIENT

This file tracks all identified defects, visual anomalies, softlocks, and regressions in accordance with Section 10 QA specifications.

---

### BUG-001: Legacy Moving Truck & Suburban Clock Intro on New Game
- **Severity**: High (Atmospheric & Narrative Break)
- **Area**: `src/new_game.c`, `data/maps/InsideOfTruck/scripts.inc`, `data/maps/LittlerootTown/scripts.inc`
- **Build/Version**: 0.0.9
- **Steps to Reproduce**: Launch a New Game. After character speech, player spawns inside the moving truck in Littleroot Town.
- **Expected Result**: Player awakens directly at Camp Ambervale research expedition site.
- **Actual Result**: Classic Emerald truck scene plays with mom and clock setting.
- **Assigned Fix**: Change `WarpToTruck()` in `src/new_game.c` to warp directly to `MAP_LITTLEROOT_TOWN` (Camp Ambervale) and set initial flags to bypass truck events.
- **Status**: IN PROGRESS
- **Verification**: Pending build test.

---

### BUG-002: Gender Menu vs Dialogue Naming Disconnect
- **Severity**: Medium
- **Area**: `src/main_menu.c`, `data/text/birch_speech.inc`
- **Build/Version**: 0.0.9
- **Steps to Reproduce**: Start New Game. Professor asks "Are you LEO? Or are you MAYA?", but the UI window displays "BOY" / "GIRL".
- **Expected Result**: UI window offers "LEO" and "MAYA", or dialogue asks "Are you a boy? Or are you a girl?", defaulting male to LEO and female to MAYA.
- **Assigned Fix**: Harmonize dialogue and preset names in `src/main_menu.c` and `data/text/birch_speech.inc`.
- **Status**: IN PROGRESS
- **Verification**: Pending build test.

---

### BUG-003: Legacy "Emerald Version" Title Screen Banner
- **Severity**: Medium
- **Area**: `src/title_screen.c`, `graphics/title_screen/emerald_version.png`
- **Build/Version**: 0.0.9
- **Steps to Reproduce**: Boot ROM. Main title screen displays green "Emerald Version" banner descending from top.
- **Expected Result**: Displays "ANCIENT VERSION" or clean title presentation matching Pokémon Ancient.
- **Assigned Fix**: Update title screen graphics and text handling in `src/title_screen.c`.
- **Status**: IN PROGRESS
- **Verification**: Pending build test.
