# Architecture

Technical overview of the Dungeon's Last Stand codebase.

## Single File Design

The entire game lives in a single `index.html` file with no external dependencies. This includes:

- HTML structure (home screen, account system, main menu, class selection, HUD, upgrade screen, game over overlay)
- CSS styles (inline `<style>` block)
- JavaScript game engine (inline `<script>` block)
- All game data (weapons, enemies, maps, upgrades, masteries)
- Account system and progress persistence (localStorage-based)

No build tools, bundlers, or package managers are needed. The game runs by opening the HTML file in a browser.

## Screen Flow

The game follows this navigation flow:

```
Home Screen → Account (Login/Register/Guest) → Main Menu → Class Select → Game
                                                  ↑                         ↓
                                                  ← ← ← Game Over ← ← ← ←
```

### Screens

| Screen | ID | Purpose |
|--------|----|---------|
| Home Screen | `#homescreen` | Title screen with PLAY button |
| Account Screen | `#account-screen` | Login, register, or guest access |
| Main Menu | `#main-menu` | Tabbed menu: Play, Shop, Social |
| Class Selection | `#overlay` | Choose class before entering game |
| Game HUD | `#hud` | In-game stats and weapon slots |
| Upgrade Screen | `#upgrade-screen` | Post-wave reward selection |
| Game Over | `#gameover` | Death screen with stats |

## Account System (DLS Object)

The `DLS` global object manages accounts, progress, and friends:

| Method | Description |
|--------|-------------|
| `DLS.register(user, pass)` | Create new account |
| `DLS.login(user, pass)` | Login to existing account |
| `DLS.guest()` | Play without account |
| `DLS.logout()` | End session |
| `DLS.saveProgress(wave, kills, coins)` | Save run results to account |
| `DLS.getProgress()` | Get account stats (bestWave, totalKills, coins, gamesPlayed) |
| `DLS.addFriend(name)` | Add friend by username |
| `DLS.removeFriend(name)` | Remove friend |
| `DLS.restoreSession()` | Auto-login from saved session |

### Storage Structure

Accounts are stored in `localStorage` under key `dls_accounts`:

```json
{
  "username": {
    "pass": "password",
    "progress": {
      "bestWave": 15,
      "totalKills": 342,
      "coins": 50,
      "gamesPlayed": 8
    },
    "friends": ["otheruser"]
  }
}
```

Session persistence uses `dls_session` key. Guest mode falls back to `dls_coins` for coin tracking.

## Global State: The G Object

All runtime game state is stored in a single global object `G`, initialized in `initGame()`:

| Property | Type | Description |
|----------|------|-------------|
| `G.cls` | string | Selected class name |
| `G.wave` | number | Current wave number |
| `G.kills` | number | Total kill count |
| `G.currentMap` | string | Active map name |
| `G.mapConfig` | object | Reference to current MAPS entry |
| `G.player` | object | Player state (position, HP, weapons, etc.) |
| `G.enemies` | array | All active enemies |
| `G.bullets` | array | All active projectiles (player and enemy) |
| `G.particles` | array | Visual particle effects |
| `G.powerups` | array | Dropped items on ground |
| `G.blackHoles` | array | Active black hole effects |
| `G.activeRooms` | Set | Room names the player has entered |
| `G.screenShake` | number | Current shake intensity (decays per frame) |
| `G.paused` | boolean | Game paused (upgrade screen) |
| `G.gameOver` | boolean | Game ended |
| `G.waveActive` | boolean | Enemies still alive in current wave |

## Key Data Constants

| Constant | Description |
|----------|-------------|
| `MAPS` | Map definitions (dungeon, graveyard, hell) with floor/wall colors, furniture, torches, carve regions, rooms |
| `WEAPONS` | All 18 weapons with ATK, range, speed, type |
| `CLASSES` | Knight, Ranger, Mage base stats |
| `CLASS_WEAPONS` | Available weapon pool per class |
| `CLASS_UPGRADES` | Stat/heal/combo upgrades per class |
| `WEAPON_MASTERIES` | Mastery options per weapon |
| `SIZE_VARIANTS` | Small/normal/large multiplier tables |

## Core Systems

### Game Loop

`loop(ts)` runs via `requestAnimationFrame`. Each frame:

1. Process input (WASD/arrows, spacebar, shift)
2. Handle dodge roll movement
3. Apply normal movement with wall clamping
4. Check room activation (player entering new rooms)
5. Handle knockback ability
6. Check hazard damage (lava)
7. Auto-fire weapon (`tryShoot()`)
8. Update bullets (movement, collision, range expiry)
9. Update enemies (AI, movement, attacks, status effects)
10. Filter dead enemies (handle boss revive)
11. Update powerups, black holes, particles
12. Check wave completion
13. Decay invincibility and screen shake
14. Update HUD and call `draw()`

Delta time is capped at 50ms to prevent physics jumps on tab switch.

### Rendering (`draw()`)

Rendering uses a camera offset system:

1. Calculate camera position (centered on player, clamped to world bounds)
2. Apply screen shake offset
3. `ctx.translate(-camX, -camY)` for world-space rendering
4. Draw background (pre-rendered to offscreen canvas `bgC`)
5. Draw torches, furniture, map overlays, hazard glow
6. Restore transform for screen-space vignette
7. Re-apply transform for world-space entities
8. Draw black holes, powerups, particles, bullets, enemies, player
9. Draw HUD arcs (weapon cooldown, dodge, knockback)
10. Draw wave banner (screen-space)

### Camera System

- Viewport: 960x640 pixels (`VW`, `VH`)
- World: 1600x1000 pixels (`W`, `H`)
- Camera follows player, clamped so edges do not show void
- Screen shake adds random offset to camera position

### Collision System

The world uses a tile-based collision map (`colMap[row][col]`).

- `isBlocked(x, y)`: checks if a pixel position is inside a wall tile
- `boxFree(x, y)`: checks 4 corners of a 20px box around a point
- `clampMove(ox, oy, nx, ny)`: tries full move, then axis-separated, then stays put
- `hasLOS(x1, y1, x2, y2)`: raycasts in 8px steps between two points

If an entity gets stuck in a wall, a spiral search finds the nearest free tile.

### Map System

Maps are defined in the `MAPS` constant with these properties:

| Property | Description |
|----------|-------------|
| `floorCols` | Array of 4 floor tile color variants |
| `wallBase`, `wallBricks`, `wallMort` | Wall rendering colors |
| `furniture` | Array of decorative objects (barrels, chests, gravestones, etc.) |
| `torches` | Torch positions with per-biome flame colors |
| `overlay` | Optional per-frame visual effect function (fog, heat haze) |
| `hazards` | Lava pools (hell only) with damage zones |
| `carve` | Array of `[col, row, width, height]` rectangles to carve as walkable |
| `rooms` | Named room definitions with pixel-space bounds |

`buildMap(name)` performs:
1. Initialize collision map (all walls)
2. Carve walkable rectangles from `carve` array
3. Render floor/wall tiles to offscreen background canvas
4. Render hazards, rugs, wall shadows
5. Set up torch positions and furniture references

### Room Activation

- Each room has a name and pixel bounds
- Enemies spawn assigned to a room via `pickRoom()`
- Non-main-room enemies start dormant (35% opacity, no AI)
- When the player's position enters a room's bounds, all its enemies activate
- Screen shake and sound play on room activation
- Wave only completes when all rooms are cleared

### Audio System

Procedural music using Web Audio API:

- 5 states: dungeon (88 BPM), boss phases 0-3 (100/120/140/160 BPM)
- Natural minor and Phrygian scales
- No audio files -- all sounds are synthesized
- `sfxShoot()`, `sfxHit()`, `sfxDie()`, `sfxBossPhase()`, `sfxDodge()`, `sfxKnockback()`, `sfxHeal()`, `sfxPickup()`, `sfxLevelup()`, `sfxRevive()`

### Enemy AI Patterns

| Enemy | Behavior |
|-------|----------|
| Goblin | Moves directly toward player; reduced speed without LOS |
| Skeleton | Moves directly toward player; reduced speed without LOS |
| Necromancer | Maintains distance (~110px); retreats if too close; spawns skeletons every 4.5s |
| Orc | Chases player; lunges forward when within 90px (3.5s cooldown) |
| Troll | Chases player (slow); regenerates 2% HP/s if not hit for 3s |
| Minion | Chases player directly; spawned by bosses |
| Boss | Chases player with phase-scaled speed; ranged attacks with phase-scaled patterns; spawns henchmen |

All enemies:
- Separate from each other when overlapping (22px threshold)
- Are clamped to world bounds
- Take lava damage in hell hazard zones
- Get unstuck from walls via spiral search

### Weapon System

Three weapon types with different attack mechanics:

- **Melee**: Hits enemies within range; chainHit mastery hits all in range; burstCount for multi-hit
- **Ranged**: Fires projectile with velocity toward target; pierce, spread, chain options
- **AoE**: Instant effect on target(s) within range; chain targets, pull, black hole effects

Damage formula: `(player.atk + random(0-9)) * masteryDmgMult`

Critical hits (from mastery): 3x damage multiplier.

### Upgrade System

After each wave clear:
1. `showUpgrades()` pauses the game
2. Builds option pool: up to 2 new weapons + up to 2 masteries + up to 5 stat upgrades
3. Shuffles and picks 3 options to display
4. Player clicks to choose; game resumes with next wave

Weapon upgrades use weighted random sampling where rarity and pick history affect probability.
