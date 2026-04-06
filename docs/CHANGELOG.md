# Changelog

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
