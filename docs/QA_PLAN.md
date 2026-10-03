# QA PLAN: POKÉMON ANCIENT

## 1. Regression & Release Verification Checklist

### Functional QA
- [ ] New Game boots cleanly without freezing or black screen.
- [ ] Intro dialogue displays Professor Cycad and sets Leo/Maya correctly.
- [ ] Player spawns directly at Camp Ambervale; truck sequence is bypassed.
- [ ] Starter selection screen presents Frillsprout, Pyroraptor, and Plesioling with proper stats and moves.
- [ ] Route 101 Cataclysm battle initiates and concludes with correct rewards.
- [ ] Route 103 Rival battle triggers properly based on player's chosen starter.
- [ ] In-game save and reload function properly without corrupting 128KB Flash save.

### Visual QA
- [ ] Title screen displays "ANCIENT VERSION" without corrupted tiles.
- [ ] Starter Pokémon sprites contain zero opaque white background boxes.
- [ ] Eyes, teeth, and body highlights remain crisp white and do not become transparent.
- [ ] Text boxes do not overflow.

### Audio QA
- [ ] Title theme plays cleanly.
- [ ] Battle music triggers without audio cracking or abrupt cuts.
