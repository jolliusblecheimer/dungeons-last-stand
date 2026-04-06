# Roadmap

Future planned features and ideas for Dungeon's Last Stand.

## Map Expansion (Map 4+)

| Map | Waves | Theme | Notes |
|-----|-------|-------|-------|
| Frozen Caverns | 31-40 | Ice caves, slippery floors, frozen pillars | Sliding mechanic on ice tiles, cracked ice hazards |
| Abyssal Depths | 41-50 | Underwater ruins, bioluminescent flora | Bubble currents pushing player, deep-sea enemies |
| Sky Fortress | 51+ | Floating platforms, wind gusts, lightning | Gaps between platforms, wind knockback hazard |

### Map Feature Ideas

- Environmental puzzles (pressure plates, locked doors)
- Secret rooms with rare weapon drops
- Trap tiles (spikes, dart walls, collapsing floors)
- Dynamic weather per biome (rain in graveyard, ash in hell)

## New Enemy Types

| Enemy | Concept | Mechanics |
|-------|---------|-----------|
| Wraith | Ghostly, partially transparent | Phases through walls, immune to melee |
| Spider | Fast, wall-climbing | Shoots webs that slow player, spawns in packs |
| Golem | Massive stone construct | Very slow, very high HP, ground slam AoE |
| Assassin | Stealthy rogue enemy | Cloaks when far from player, backstab bonus |
| Dragon Whelp | Small flying dragon | Ranged fire breath, hovers over hazards |
| Mimic | Disguised as chest/barrel | Surprise attack when player approaches furniture |
| Shaman | Support caster | Buffs nearby enemies with speed/damage aura |

## Class-Specific Abilities (Beyond Weapon Mastery)

### Knight
- **Shield Bash**: Active ability, stuns and damages enemies in a cone
- **Taunt**: Forces nearby enemies to target the knight for 3 seconds
- **Fortified Stance**: Stand still to gain damage reduction, lose on movement

### Ranger
- **Trap Placement**: Drop caltrops or snares on the ground
- **Shadow Step**: Short-range teleport behind nearest enemy
- **Mark Target**: Tagged enemy takes bonus damage from all sources

### Mage
- **Blink**: Teleport a short distance (separate from dodge roll)
- **Mana Barrier**: Absorb damage using a mana resource pool
- **Arcane Nova**: Channeled AoE that grows in radius over time

## Multiplayer / Co-op

- WebSocket-based 2-player co-op (stretch goal)
- Shared screen with split camera or zoomed-out view
- Revive mechanic for downed partner
- Shared upgrade pool or alternating picks
- Boss HP scaled to player count

### Challenges
- Synchronizing game state over network
- Camera system for two players in different rooms
- Balancing enemy count and HP for co-op

## Mobile Controls (Planned)

Touch controls for mobile browser play:

- Virtual joystick for movement (left thumb)
- Auto-aim with tap-to-switch-target
- Swipe gestures for dodge roll and knockback
- Touch-friendly upgrade selection screen
- Responsive canvas scaling for mobile viewports

### Approach
- Virtual joystick (left thumb) for movement
- Ability buttons (right side) for dodge, knockback
- Auto-fire handles targeting automatically
- Responsive canvas scaling
- Can be wrapped in Capacitor/Cordova for app store listing

## UI Improvements

### Minimap
- Small overlay in corner showing room layout
- Player dot, enemy dots, cleared/uncleared room indicators
- Toggle with M key or always visible

### Inventory / Loadout
- Pre-game weapon selection screen
- Weapon unlock progression across runs
- Persistent stats (best wave, total kills, class playtime)

### HUD Enhancements
- Damage numbers floating above enemies on hit
- Kill feed / combo counter
- Boss HP bar at top of screen (dedicated, larger)
- Cooldown timers with icons instead of arc indicators
- DPS meter (optional toggle)

### Quality of Life
- Settings menu (volume sliders, particle toggle, screen shake toggle)
- Pause menu with resume/restart/quit
- Death recap showing damage sources
- Wave preview showing upcoming enemy types
- Tutorial overlay for first-time players

## Audio

- Per-biome ambient sound layers (dripping water, wind, lava bubbles)
- Unique boss music per boss type (currently shares phase system)
- Sound effect variety (multiple hit/shoot sounds, randomized)
- Volume sliders for music, SFX, master

## Performance

- Web Worker for collision calculations on high enemy counts
- Object pooling for bullets and particles
- Offscreen canvas caching for static enemy sprites
- RequestAnimationFrame throttling option for low-end devices
