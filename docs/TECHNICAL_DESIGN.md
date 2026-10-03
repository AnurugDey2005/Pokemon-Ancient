# TECHNICAL DESIGN: POKÉMON ANCIENT

## 1. Engine & Toolchain
- **Base**: `pokeemerald-expansion` (custom fork).
- **Toolchain**: arm-none-eabi-gcc 10+, binutils, gbagfx, preproc, scaninc.
- **Build Target**: GitHub Actions Ubuntu Linux cloud runner.
- **Binary**: Clean 32MB standard GBA ROM (`PokemonAncient.gba`).

## 2. Memory & Hardware Architecture
- **ROM Size**: 32MB (exact 33,554,432 bytes).
- **VRAM OBJs**: 32KB sprite character tile budget, 4bpp palettes.
- **Save Format**: 128KB Flash memory (standard GBA battery save).
- **Antivirus Immunity**: Zero native execution of third-party emulators, compilers, or untrusted executables on the host Windows machine.
