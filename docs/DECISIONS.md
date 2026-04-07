# Design Decisions

## Architecture
- Single HTML file, no dependencies
- Canvas 2D, imageSmoothingEnabled=false
- Web Audio API procedural music

## Balance
- Mage AOE range reduced (was 128–168, now 85–120) to prevent dominance
- Mage can earn range back via Weapon Mastery upgrades
- Enemy HP: (base + wave*N) * (1 + wave*0.22)
- Boss: 2200 + wave*180 HP, phases at 85/70/55%

## Boss
- 4 phases, secret revive (+50% HP, +40% ATK on revive)
- Phase thresholds: P1=spawn, P2=85%, P3=70%, P4=55%
- Henchmen: P2=2/4.5s, P3=3/2.8s, P4=4/1.8s
- The Infernal: fireball barrage P2+, fire cone P3+, lava pools P4

## Music
- 5 states: dungeon(88bpm) boss0-3(100/120/140/160bpm)
- Natural minor + Phrygian scales
