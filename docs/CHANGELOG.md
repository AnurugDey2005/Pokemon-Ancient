# CHANGELOG: POKÉMON ANCIENT

All notable changes to the Pokémon Ancient project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [0.1.0-alpha] - 2026-10-04 (Demo V1 Overhaul)

### Added
- Canonical Project Documentation Suite:
  - `docs/PROJECT_BIBLE.md`: Complete world, character, gameplay, and art bible.
  - `docs/DECISIONS.md`: Architectural decision records.
  - `docs/CHANGELOG.md`: Full version tracking.
  - `bugs/ACTIVE_BUGS.md`: Active bug tracker and QA remediation log.
- Camp Ambervale direct spawn in `src/new_game.c`: Bypasses moving truck entirely.
- Dedicated gender selection naming: Leo (male protagonist/rival) and Maya (female protagonist/rival).
- Reusable TMs (`I_REUSABLE_TMS TRUE`) and Bag Evolution items.
- Early Running Shoes granted immediately at Camp Ambervale.

### Changed
- Replaced Professor Birch intro dialogue with Professor Andrea Cycad's paleontology dispatch.
- Overhauled Route 103 rival battle with custom prehistoric starter dynamics and romantic/competitive dialogue.
- Organized local Desktop workspace into clean `01_PLAYABLE_GAME` and `02_PROJECT_DOCUMENTATION` directories.

### Fixed
- Eradicated legacy Emerald truck and clock-setting sequence from New Game start.
- Fixed Unicode em-dash compile failure in GBA `charmap.txt`.
- Guaranteed 100% GBA PPU Color 0 transparency across all starter assets.
