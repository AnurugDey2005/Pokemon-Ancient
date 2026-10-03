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
- **Assigned Fix**: Changed `WarpToTruck()` in `src/new_game.c` to warp directly to `MAP_LITTLEROOT_TOWN_PROFESSOR_BIRCHS_LAB` (Camp Ambervale Field Lab) at coords (6, 5). Set `VAR_LITTLEROOT_INTRO_STATE = 7` in `NewGameInitData()` to permanently bypass truck, mom, and clock routines.
- **Status**: RESOLVED & VERIFIED
- **Verification**: Verified in Cloud Build #37154253999 / Release v1.0.0-demo.

---

### BUG-002: Gender Menu vs Dialogue Naming Disconnect
- **Severity**: Medium
- **Area**: `src/main_menu.c`, `src/strings.c`, `src/data/trainers.party`
- **Build/Version**: 0.0.9
- **Steps to Reproduce**: Start New Game. Professor asks "Are you LEO? Or are you MAYA?", but the UI window displays "BOY" / "GIRL".
- **Expected Result**: UI window offers "LEO" and "MAYA", defaulting male to LEO and female to MAYA. Rival adopts opposite name throughout story.
- **Actual Result**: Vanilla gender options and vanilla rival names appeared.
- **Assigned Fix**: Updated `sMenuActions_Gender` in `src/main_menu.c` to display `LEO` and `MAYA`. Set preset names to LEO and MAYA. Updated `gText_ExpandedPlaceholder_Brendan` to `LEO` and `gText_ExpandedPlaceholder_May` to `MAYA` in `src/strings.c`. Updated all 35 rival team names in `src/data/trainers.party`.
- **Status**: RESOLVED & VERIFIED
- **Verification**: Verified in Cloud Build #37154253999 / Release v1.0.0-demo.

---

### BUG-003: Legacy "Emerald Version" Title Screen Banner
- **Severity**: Medium
- **Area**: `graphics/title_screen/emerald_version.png`
- **Build/Version**: 0.0.9
- **Steps to Reproduce**: Boot ROM. Main title screen displays green "Emerald Version" banner descending from top.
- **Expected Result**: Displays "ANCIENT VERSION" matching Pokémon Ancient branding.
- **Actual Result**: Emerald Version banner appeared.
- **Assigned Fix**: Re-authored `graphics/title_screen/emerald_version.png` with metallic amber/gold "ANCIENT VERSION" 128x32 indexed graphic adhering to GBA 4bpp Color 0 transparency.
- **Status**: RESOLVED & VERIFIED
- **Verification**: Verified in Cloud Build #37154253999 / Release v1.0.0-demo.

---

### BUG-004: Placeholder Starter Sprites
- **Severity**: High (Immersion Break)
- **Area**: `src/data/pokemon/species_info/ancient_families.h`
- **Build/Version**: 0.0.9
- **Steps to Reproduce**: Select starter Pokémon in Camp Ambervale. Vanilla Kanto starter sprites appeared.
- **Expected Result**: Authentic prehistoric dinosaur sprites with zero white background boxes.
- **Assigned Fix**: Replaced all starter sprite and palette pointers in `ancient_families.h` with authentic prehistoric dinosaur assets (Shieldon line for Frillsprout, Tyrunt line for Pyroraptor, Amaura line for Plesioling) with verified GBA hardware transparency.
- **Status**: RESOLVED & VERIFIED
- **Verification**: Verified in Cloud Build #37154253999 / Release v1.0.0-demo.

---

### BUG-005: Softlock at Route 101 North Boundary, Two Moving Trucks Outside, and Lab Starter Glitch
- **Severity**: Critical (Hard Softlock & Visual Immersion Break)
- **Area**: `src/battle_setup.c`, `src/new_game.c`, `data/maps/LittlerootTown_ProfessorBirchsLab/scripts.inc`, `data/maps/LittlerootTown/map.json`, `data/maps/Route101/scripts.inc`
- **Build/Version**: 1.0.0-demo
- **Steps to Reproduce**:
  1. Boot game, start in lab. When starter was chosen or talked to, `special ChooseStarter` called `CB2_StartFirstBattle` launching a wild Zigzagoon battle inside the indoor lab.
  2. Leaving the lab revealed two moving trucks parked outside both player and rival houses.
  3. Walking north to Route 101 triggered coordinate events with `VAR_LITTLEROOT_TOWN_STATE` or `VAR_ROUTE101_STATE == 1` which called `applymovement` on displaced/hidden objects (`LOCALID_LITTLEROOT_TWIN`, `LOCALID_ROUTE101_BIRCH`, `LOCALID_ROUTE101_ZIGZAGOON`), causing `waitmovement 0` to hang indefinitely. Player was frozen and unable to move up.
- **Expected Result**:
  1. Professor Cycad immediately addresses player via `OnFrame` script in lab, hands over chosen prehistoric starter smoothly with no wild battle in the lab.
  2. Zero trucks outside (both truck flags permanently hidden).
  3. Player walks freely north onto Route 101 with zero coordinate trigger softlocks or freezes.
- **Assigned Fix**:
  1. Updated `CB2_GiveStarter` in `src/battle_setup.c` to check if player is inside `MAP_LITTLEROOT_TOWN_PROFESSOR_BIRCHS_LAB`. If so, calls `SetMainCallback2(CB2_ReturnToFieldContinueScriptPlayMapMusic)` to return cleanly to the field script without launching a wild battle in the lab.
  2. In `src/new_game.c`, explicitly set `FLAG_HIDE_LITTLEROOT_TOWN_BRENDANS_HOUSE_TRUCK`, `FLAG_HIDE_LITTLEROOT_TOWN_MAYS_HOUSE_TRUCK`, `FLAG_HIDE_LITTLEROOT_TOWN_MOM_OUTSIDE`, `FLAG_SET_WALL_CLOCK`. Cleared `FLAG_HIDE_LITTLEROOT_TOWN_BIRCHS_LAB_BIRCH`.
  3. Initialized `VAR_LITTLEROOT_TOWN_STATE = 4` and `VAR_ROUTE101_STATE = 3` in `NewGameInitData()` and `CompleteStarterGift`, completely bypassing all coordinate triggers on Littleroot Town and Route 101 boundaries.
  4. Added `map_script_2 VAR_BIRCH_LAB_STATE, 0, LittlerootTown_ProfessorBirchsLab_EventScript_FirstMeetingIntro` to `LittlerootTown_ProfessorBirchsLab_OnFrame` so the briefing and starter selection execute smoothly on frame 0.
- **Status**: RESOLVED & PENDING CLOUD BUILD VERIFICATION
- **Verification**: Cloud Build in progress.
