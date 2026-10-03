# CHANGELOG: POKÉMON ANCIENT

All notable changes to the Pokémon Ancient project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0-demo] - 2026-10-04 (Demo V1 Official Release)

### Added
- **Official GitHub Release `v1.0.0-demo`**:
  - Direct 1-Click ROM Download: `PokemonAncient.gba` (33,554,432 bytes)
  - Direct 1-Click ZIP Download: `PokemonAncient-ROM.zip` (17,549,771 bytes)
  - Release URL: `https://github.com/AnurugDey2005/Pokemon-Ancient/releases/tag/v1.0.0-demo`
- **Canonical Project Documentation Suite**:
  - `docs/PROJECT_BIBLE.md`: Complete world, character, gameplay, and art bible.
  - `docs/DECISIONS.md`: Architectural decision records.
  - `docs/CHANGELOG.md`: Full version tracking.
  - `bugs/ACTIVE_BUGS.md`: Active bug tracker and QA remediation log.
- **Camp Ambervale Direct Spawn (`src/new_game.c`)**: Bypasses moving truck entirely and spawns in front of Professor Cycad.
- **Camp Ambervale Starter Gifting (`data/maps/LittlerootTown_ProfessorBirchsLab/scripts.inc`)**:
  - Hands player their choice of Frillsprout, Pyroraptor, or Plesioling.
  - Automatic nickname prompt.
  - Awards Pokédex, 10 gift Poké Balls, and sets `FLAG_SYS_B_DASH` (running shoes).
- **Dedicated Gender Selection Naming (`src/main_menu.c`)**:
  - Options display `LEO` and `MAYA`.
  - Preset names default to LEO and MAYA.
- **Universal Rival Naming & Teams (`src/strings.c`, `src/data/trainers.party`)**:
  - `{RIVAL}` string token dynamically expands to `LEO` or `MAYA`.
  - All 35 rival team party entries updated to `MAYA` and `LEO`.
- **Authentic Prehistoric Dinosaur Sprites (`src/data/pokemon/species_info/ancient_families.h`)**:
  - Frillsprout line: Shieldon -> Bastiodon -> Aggron.
  - Pyroraptor line: Tyrunt -> Aerodactyl -> Tyrantrum.
  - Plesioling line: Amaura -> Lapras -> Aurorus.
  - 100% GBA 4bpp Color 0 hardware transparency, zero white cardboard boxes.
- **Ancient Title Screen Branding (`graphics/title_screen/emerald_version.png`)**:
  - Custom metallic amber/gold "ANCIENT VERSION" title banner.

### Changed
- Replaced Professor Birch intro dialogue with Professor Andrea Cycad's paleontology dispatch.
- Overhauled Route 103 rival battle with custom prehistoric starter dynamics and romantic/competitive dialogue.
- Organized local Desktop workspace into clean `01_PLAYABLE_GAME` and `02_PROJECT_DOCUMENTATION` directories.

### Fixed
- **BUG-001**: Eradicated legacy Emerald truck and clock-setting sequence from New Game start.
- **BUG-002**: Fixed gender menu vs dialogue naming disconnect.
- **BUG-003**: Replaced green Emerald Version title screen banner with Ancient Version logo.
- **BUG-004**: Replaced placeholder starter sprites with authentic prehistoric dinosaur graphics.
