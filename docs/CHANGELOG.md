# Changelog

## [1.3.0] — 2026-04-07

### Boss Reworks
- The Reaper: now melee-only (no ranged attacks), relies on speed + henchmen
- Lich King: soul bolts no longer home, flat 25 damage per bolt
- The Infernal: 3 huge slow fireballs (Phase 2+), 7-projectile fire cone (Phase 3+), forced attacks on phase transition
- Ice Titan: new ice spike ground attack (Phase 2+) with 0.6s warning
- The Kraken: swims in water only, breaks piers in 2x2 blocks, tentacles burst through floor
- Storm Lord: unchanged

### Kraken Boss Fight
- Kraken moves exclusively in water, bypasses LOS checks
- Abyssal Depths reworked: pier/raft network over deadly ocean with wooden plank tiles
- Phase 2+: Kraken smashes adjacent pier tiles (1.5s cooldown, 2x2 blocks)
- Phase 2+: Tentacles erupt through piers near player (1.5s warning, break tile, 20+wave*2 dmg)
- Henchmen are pirates with red bandana, eye patch, cutlass — arrive via pirate ship animation
- Player receives Harpoon weapon (ATK 120, range 800, 2.5x bonus vs Kraken)
- Kraken has 0 revives, Phase 2 triggers at 90% HP, immune to knockback
- Kraken collision radius 40px (larger hitbox)

### Ice Titan Map
- Frozen Caverns reworked: circular ice arena surrounded by deadly sea
- Walk off the edge = death
- Animated wave particles around arena boundary

### All Bosses
- 1 second invincibility on each phase transition (visual shield indicator)
- Sequential phase transitions only (no skipping)
- Phase transition particles now use boss-specific colors
- Revive animation now uses correct boss sprite (was using Reaper for all)
- Henchmen colored to match their boss theme
- Storm Lord henchmen are gold golems; Kraken henchmen are pirates

### Gameplay
- Click-to-target system: click an enemy to lock on, crosshair (Fadenkreuz) displayed
- X key: switch target to nearest enemy
- Target persists until enemy dies or manually switched
- Click weapon slots in HUD to switch weapons
- Harpoon weapon auto-equipped during Kraken fight (removed after)

### Dev Mode
- Dev Mode button on class select screen (code: 939493)
- Keys 1-6 jump to boss waves (5/10/15/20/25/30)
- O key: go back one wave, P key: skip forward one wave
- 10000 HP in dev mode wave jumps

### Audio
- Complete soundtrack rewrite: EDM/trance style inspired by Sandstorm/Erlkönig
- 16th-note detuned sawtooth riff, triplet arpeggios, four-on-the-floor kicks
- Boss phases add layers: P2+ countermelody, P3+ harmony, P4 offbeat fills
- DynamicsCompressor prevents clipping
- Phase transitions no longer restart music (seamless transition)

## [1.2.0] — 2026-04-07
- Boss phase thresholds changed: P2 at 85%, P3 at 70% (was 65%), P4 at 55% (was 40%)
- The Infernal reworked: fireball barrage now starts at Phase 2, fire breath cone at Phase 3
- The Infernal Phase 1 now fires a single fireball instead of a full barrage
- New mechanic: lava pools spawn on the floor during The Infernal's Phase 4
- Lava pools deal 12 HP/s, last 8s, and cannot spawn on walls

## [1.1.0] — 2026-04-06
- Lava pools now only appear in Hell Fortress (removed from frozen/abyss)
- All AOE weapon ranges buffed: Magic Staff 90→120, Fireball 105→140, Ice Shard 120→150, Chain Lightning 120→160, Void Blast 85→120, Arcane Bolt 145→180
- Black hole buffed: radius 120→180px, duration 2→2.5s, DPS 5→8
- Class-specific Q abilities: Knight Shield Bash (cone stun), Ranger Trap (caltrops slow), Mage Blink (teleport)
- Each map has unique dungeon layout (different room shapes and corridors)
- Boss revive particles now match boss color theme (green for Lich, blue for Ice Titan, etc.)
- Enemy skins tinted per biome (goblins/skeletons change color per map)

## [1.0.0] — 2026-04-06
- New map every 5 waves — 6 unique biomes total
- Waves 1-5: Dungeon (The Reaper boss)
- Waves 6-10: Graveyard (Lich King boss)
- Waves 11-15: Hell Fortress (The Infernal boss)
- Waves 16-20: Frozen Caverns — ice blue tiles, frost fog, ice hazards (Ice Titan boss)
- Waves 21-25: Abyssal Depths — dark ocean floor, bioluminescent glow, water hazards (Kraken boss)
- Waves 26+: Sky Fortress — golden stone, bright torches, royal rug (Storm Lord boss)
- Ice Titan: frost barrage + radial ice ring at phase 2+
- Kraken: scattered spray + homing tentacles at phase 2+, random bursts at phase 3+
- Storm Lord: spinning lightning wheel + focused beam at phase 2+
- Each boss has unique HP/ATK scaling and projectile colors

## [0.10.0] — 2026-04-06
- Camera system: viewport (960x640) follows player across larger world (1600x1000)
- Maps are now much bigger — open rooms connected by wide corridors, no internal walls
- Dungeon: main hall + east wing + south corridor
- Graveyard: main grounds + eastern crypt + southern tombs
- Hell Fortress: main chamber + demon pit + lower depths
- Dormant room enemies visible at 35% opacity, activate when player enters the room area
- Player spawns in main room, must explore to find and clear all enemies
- Vignette and wave banner render in screen-space, world renders with camera offset
- Fixed wall-stuck glitch with larger boundary margins

## [0.9.0] — 2026-04-06
- Fixed wall-stuck glitch: increased boundary margin, improved recovery to find nearest walkable tile
- Multi-room dungeon layouts for all 3 maps:
  - Dungeon: main hall + east side room (doorway at rows 9-10)
  - Graveyard: north grounds + southern crypt (doorway at cols 14-15)
  - Hell Fortress: main chamber + demon pit (doorway at rows 8-9, 12-13), lava rivers in doorway walls
- Room activation system: enemies in side rooms are dormant (35% opacity, no AI) until player enters
- Entering a room triggers all its enemies with screen shake + sound
- Must clear all rooms to complete a wave (exploration required)
- Enemies spawn distributed across rooms via pickRoom()

## [0.8.2] — 2026-04-06
- 2-second invincibility shield at wave start (flicker effect while active)
- Knockback ability (Shift key): pushes nearby enemies away + 0.4s stun, 3s cooldown, red HUD arc
- Reduced mob counts per wave (~30% fewer enemies, shorter waves)
- Goblin formula: (3+w×1.4)×0.5 (was (4+w×2)×0.55)
- Necromancer: w/4 (was w/3), Orc: w/5 (was w/4), Troll: w/8 (was w/6)

## [0.8.1] — 2026-04-05
- Line-of-sight system: enemies slow down and stop attacking when player is behind walls
- Player auto-targeting now skips enemies behind walls
- Boss ranged attacks blocked by walls
- Internal walls rendered with stronger contrast (darker shadow, edge highlights)
- Throwing Axe projectile now renders as a spinning axe sprite instead of a dot

## [0.8.0] — 2026-04-05
- Bigger maps: canvas enlarged from 700x520 to 960x640
- Collision map system: internal walls create corridors and rooms per biome
- Dungeon: open arena with pillar obstacles
- Graveyard: L-shaped corridors with open grave areas
- Hell Fortress: multi-room layout with lava rivers between areas
- Dodge roll nerfed: 2.2x speed (was 3.5x), 200ms duration (was 300ms)
- Mage: Event Horizon mastery for Void Blast — creates black holes that pull and damage enemies
- Knight: Whirlwind Slash mastery for Broadsword — spinning AoE attack with visual sweep
- Knight: Blade Fury mastery for Broadsword — +30% damage
- New enemy: Troll (wave 8+) — very high HP, regenerates 2% HP/s when not hit for 3s
- Unique bosses per biome: The Reaper (dungeon), Lich King (graveyard), The Infernal (hell)
- Lich King: homing soul bolts, summons skeleton waves, green/purple theme
- The Infernal: fireball barrage, fire breath cone, red/orange theme

## [0.7.0] — 2026-04-05
- Map system: dynamic map switching based on wave progression
- Graveyard map (waves 11-20): grey-green stone, fog overlay, gravestones, dead trees, green torches
- Hell Fortress map (waves 21+): obsidian walls, lava hazard pools (damage players & enemies), fire braziers, pillars, altars, skull piles
- Dodge roll (Spacebar): 300ms dash with invincibility, 800ms cooldown, particle trail, blue cooldown HUD arc
- Enemy size variants: small/normal/large goblins and skeletons with scaled HP, ATK, sprites, and collision
- Elite Necromancer (wave 15+): larger sprite, golden crown, brighter aura, spawns large skeletons

## [0.6.0] — 2026-04-05
- Mage AOE nerfed, difficulty rebalanced
- Boss redrawn, more henchmen per phase
- Secret revive: no UI hint, boss explodes back stronger

## [0.5.0]
- Weapon Mastery system (wave 5+)
- Pierce, chain, DOT, slow, stun, pull mechanics

## [0.4.0]
- Full stats HUD
- Epic 5-state music engine (88–160 BPM)
- Boss 4-phase system

## [0.3.0]
- Class-specific upgrades, combo/heal tags, weighted randomisation

## [0.2.0]
- Docker + nginx, docs added

## [0.1.0]
- Initial release
