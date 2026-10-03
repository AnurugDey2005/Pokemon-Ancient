# DECISION LOG: POKÉMON ANCIENT

This file records all architectural, narrative, design, and technical decisions made for Pokémon Ancient.

---

### DATE: 2026-10-04
**DECISION**: Establish canonical documentation suite and eliminate all legacy Pokémon Emerald presentation artifacts for Demo V1.  
**REASON**: Player feedback demonstrated immersion breakage from base-ROM leftovers: moving truck sequence, mom clock event, generic Birch intro dialogue, generic Brendan/May naming mismatches, and placeholder starter sprite mapping.  
**ALTERNATIVES CONSIDERED**:
1. Incrementally patching text while keeping the Emerald intro flow. (Rejected: Fails the "not a base-ROM reskin" non-negotiable standard).
2. Complete immediate scratch rewrite of the intro sequence directly to Camp Ambervale. (Adopted).  
**IMPACT**: The player begins directly at Camp Ambervale field tent, bypassing the truck, clock, and suburban house. Initial starter selection occurs in the field with dedicated species.  
**REVERSIBLE?**: Yes, via git version control.  
**RELATED FILES**: `src/new_game.c`, `src/main_menu.c`, `data/text/birch_speech.inc`, `data/maps/LittlerootTown/scripts.inc`, `docs/PROJECT_BIBLE.md`.

---

### DATE: 2026-10-01
**DECISION**: 4bpp Palette Index 0 Strict Transparency Mandate.  
**REASON**: Eliminate the amateur "pasted white cardboard box" artifact on Pokémon sprites.  
**ALTERNATIVES CONSIDERED**:
1. Color-keying `#FFFFFF` as transparent. (Rejected: Destroys white eye pupils, teeth, and claws).
2. Explicit Color 0 allocation with 16-color indexed palette. (Adopted).  
**IMPACT**: True whites remain crisp; all outer canvas areas render 100% transparently over battle backgrounds and UI.  
**REVERSIBLE?**: No, this is an eternal standard.  
**RELATED FILES**: `src/data/pokemon/species_info/ancient_families.h`, `graphics/pokemon/*`.
