# Balance Guide

All stats, formulas, and scaling data for Dungeon's Last Stand.

## Class Stats

| Class | Base HP | Base ATK | Base SPD | Starting Weapon |
|-------|---------|----------|----------|-----------------|
| Knight | 240 | 24 | 1.9 | Broadsword |
| Ranger | 120 | 19 | 3.1 | Shortbow |
| Mage | 85 | 36 | 2.4 | Magic Staff |

## Weapon Stats

### Melee Weapons

| Weapon | ATK | Range | Speed (ms) | Notes |
|--------|-----|-------|------------|-------|
| Broadsword | 22 | 78 | 500 | Knight starter |
| Greataxe | 42 | 85 | 780 | High damage, slow |
| Warhammer | 55 | 70 | 960 | Highest melee ATK |
| Longsword | 32 | 88 | 580 | Longest melee range |
| Flail | 36 | 98 | 640 | Extended reach |
| Dagger | 14 | 46 | 210 | Fastest weapon in game |

### Ranged Weapons

| Weapon | ATK | Range | Speed (ms) | Notes |
|--------|-----|-------|------------|-------|
| Shortbow | 16 | 215 | 360 | Ranger starter |
| Crossbow | 32 | 245 | 580 | High ranged damage |
| Longbow | 28 | 275 | 460 | Longest range (ranged) |
| Throwing Axe | 38 | 168 | 600 | Spinning axe sprite |
| Repeater | 14 | 198 | 185 | Fastest ranged weapon |
| Poison Arrow | 22 | 235 | 420 | Balanced |

### AoE Weapons

| Weapon | ATK | Range | Speed (ms) | Notes |
|--------|-----|-------|------------|-------|
| Magic Staff | 30 | 90 | 700 | Mage starter |
| Fireball | 44 | 105 | 950 | High AoE damage |
| Ice Shard | 24 | 120 | 520 | Fast AoE |
| Chain Lightning | 38 | 120 | 860 | Base 2 chain targets |
| Void Blast | 52 | 85 | 1060 | Highest ATK in game |
| Arcane Bolt | 34 | 145 | 560 | Longest AoE range |

## Weapon Mastery (Wave 5+)

Masteries are offered during upgrade selection for weapons the player currently owns.

| Weapon | Mastery | Rarity | Effect |
|--------|---------|--------|--------|
| Broadsword | Whirlwind Slash | 2 | Spin AoE + hit all in range + visual sweep |
| Broadsword | Blade Fury | 2 | +30% damage |
| Greataxe | Rend | 2 | Bleed: +20 damage over 3s |
| Greataxe | Whirlwind | 2 | Hits all enemies in range |
| Greataxe | Crusher | 3 | +50% damage |
| Warhammer | Concuss | 2 | Stuns enemies for 1.2s |
| Warhammer | Shockwave | 3 | Hits all enemies in range |
| Dagger | Flurry | 3 | 4 hits per attack |
| Dagger | Assassinate | 3 | 40% chance for triple crit |
| Crossbow | Piercing Bolt | 2 | Projectiles pierce all enemies |
| Crossbow | Deadeye | 3 | 30% chance for triple crit |
| Crossbow | Speed Loader | 2 | -30% reload time |
| Longbow | Power Draw | 2 | +40% damage |
| Longbow | Volley | 3 | 3-arrow spread shot |
| Fireball | Twin Inferno | 2 | Fires twice (150ms delay) |
| Fireball | Inferno Radius | 2 | +50 AoE range |
| Fireball | Scorched Earth | 3 | +30% damage |
| Ice Shard | Deep Freeze | 2 | Slows enemies by 60% |
| Ice Shard | Blizzard | 3 | Hits all nearby enemies |
| Chain Lightning | Arc Storm | 2 | Chains to 2 additional targets |
| Chain Lightning | Thunderstrike | 3 | Stuns enemies for 0.8s |
| Void Blast | Singularity | 3 | Pulls enemies toward player |
| Void Blast | Unravel | 2 | +40% damage |
| Void Blast | Event Horizon | 3 | Creates a black hole (120px radius, 2s duration) |

## Enemy Base Stats

### Regular Enemies

| Enemy | Base HP Formula | Base ATK Formula | Base SPD | Appears | Notes |
|-------|----------------|------------------|----------|---------|-------|
| Goblin | (30 + w*8) * hm * sizeM | (6 + w*0.9 * dm) * sizeM | 1.3 + w*0.04 | Wave 1+ | Size variants |
| Skeleton | (70 + w*14) * hm * sizeM | (11 + w*1.2 * dm) * sizeM | 0.9 + w*0.03 | Wave 2+ | Size variants |
| Necromancer | (120 + w*18) * hm | 7 (fixed) | 0.7 | Wave 4+ | Spawns skeletons every 4.5s |
| Orc | (160 + w*22) * hm | (16 + w*1.5 * dm) | 0.8 + w*0.025 | Wave 6+ | Lunge attack at close range |
| Troll | (320 + w*28) * hm | (20 + w*1.8) * dm | 0.55 + w*0.015 | Wave 8+ | Regenerates 2% HP/s after 3s no damage |
| Minion | 60 + w*10 | 15 + w | 1.4 | Boss waves | Spawned by bosses |
| Spawned Skeleton | (50 + w*8) * sizeM | 12 * sizeM | 1.1 | Any | Spawned by necromancers |

### Elite Necromancer (Wave 15+)

- 40% chance to spawn as elite
- 1.8x HP multiplier
- Larger sprite with golden crown
- Spawns large skeletons instead of normal

### Enemy Spawn Counts Per Wave

| Enemy | Count Formula | Effective Multiplier |
|-------|---------------|----------------------|
| Goblin | (3 + w*1.4) * cm * 0.5 | Rounded |
| Skeleton | (1 + w*0.5) * cm * 0.35 | Wave 2+, rounded |
| Necromancer | w / 4 | Wave 4+, rounded |
| Orc | w / 5 | Wave 6+, rounded |
| Troll | w / 8 | Wave 8+, min 1 |

## Size Variant Multipliers

Goblins and skeletons can spawn as small, normal, or large.

| Size | Scale | HP Mult | ATK Mult | Collision Radius Mult |
|------|-------|---------|----------|-----------------------|
| Small | 0.65x | 0.5x | 0.6x | 0.7x |
| Normal | 1.0x | 1.0x | 1.0x | 1.0x |
| Large | 1.5x | 2.0x | 1.5x | 1.4x |

### Size Probability by Wave

- Large chance: min(30%, w * 1.5%)
- Small chance: max(10%, 35% - w * 1%)
- Normal chance: remainder

## Wave Scaling Formulas

| Multiplier | Formula | Purpose |
|------------|---------|---------|
| HP multiplier (hm) | 1 + w * 0.16 | Scales enemy health |
| Count multiplier (cm) | 1 + w * 0.16 | Scales enemy count |
| Damage multiplier (dm) | 1 + w * 0.13 | Scales enemy attack |

Where `w` = current wave number.

## Boss Stats

Bosses appear every 5 waves.

| Boss | Waves | Base HP | HP Scaling | Base ATK | ATK Scaling |
|------|-------|---------|------------|----------|-------------|
| The Reaper | 1-10 | 2200 | +180/wave | 25 | +3/wave |
| Lich King | 11-20 | 2800 | +200/wave | 20 | +2.5/wave |
| The Infernal | 21+ | 3500 | +220/wave | 30 | +3/wave |

### Boss Phase System

Phases trigger at HP thresholds: 85%, 65%, 40%.

| Phase | Henchman Count | Spawn Cooldown | Speed Mult | Attack Cooldown |
|-------|----------------|----------------|------------|-----------------|
| Phase 1 (100-85%) | -- | -- | 1.0x | 1600ms |
| Phase 2 (85-65%) | 2 | 4500ms | 1.4x | 1300ms |
| Phase 3 (65-40%) | 3 | 2800ms | 1.8x | 1000ms |
| Phase 4 (below 40%) | 4 | 1800ms | 2.2x | 700ms |

### Boss Attack Patterns

| Boss | Pattern | Phase 2+ Bonus |
|------|---------|----------------|
| The Reaper | 3 + phase*3 projectiles in spread | Phase 3+: 3 rear-facing projectiles (0.7x ATK) |
| Lich King | 2 + phase*2 homing soul bolts | Phase 2+: 40% chance to summon 2+ skeletons |
| The Infernal | 4 + phase*3 fireball spread | Phase 2+: 3 fire breath projectiles (0.5x ATK) |

### Secret Revive Mechanic

- No UI hint given to the player
- Boss explodes on death, then revives after 4 seconds
- Revive grants: +50% max HP, +40% ATK, +20% speed
- Lives: wave 5-9 = 1 revive, wave 10+ = 2 revives
- Boss resets to Phase 1 after revive

## Class Upgrade Values

### Knight Upgrades

| Upgrade | Rarity | Effect |
|---------|--------|--------|
| Ration | 1 | +25 HP (heal) |
| Holy Prayer | 2 | +60 HP (heal) |
| Fortify | 1 | +25 Max HP |
| Sharpen | 1 | +8 ATK |
| Whetstone | 2 | +20 ATK |
| Guard | 1 | Absorb 50 damage |
| Iron Wall | 2 | Absorb 100 damage |
| March | 2 | +0.2 SPD |
| Battle Fury | 3 | +14 ATK, +35 HP, Absorb 50 |
| War Rite | 3 | +12 ATK, Heal 45 |

### Ranger Upgrades

| Upgrade | Rarity | Effect |
|---------|--------|--------|
| Herbs | 1 | +22 HP (heal) |
| Nature Gift | 2 | +50 HP (heal) |
| Endurance | 1 | +18 Max HP |
| Precision | 1 | +9 ATK |
| Eagle Eye | 2 | +16 ATK, +25 range |
| Swift | 1 | +0.35 SPD |
| Far Shot | 2 | +35 range |
| Cloak | 1 | Absorb 35 damage |
| Ambush | 3 | +12 ATK, +0.4 SPD, +25 range |

### Mage Upgrades

| Upgrade | Rarity | Effect |
|---------|--------|--------|
| Mana Sip | 1 | +18 HP (heal) |
| Elixir | 2 | +45 HP (heal) |
| Vitality | 1 | +18 Max HP |
| Arcane Power | 1 | +12 ATK |
| Spell Surge | 2 | +26 ATK |
| Mana Shield | 1 | Absorb 60 damage |
| Expand | 2 | +35 AoE range |
| Arcane Burst | 3 | +18 ATK, +25 AoE, Absorb 40 |

### Upgrade Weighting

Upgrades use weighted random selection. Base weights by rarity:
- Rarity 1: weight 10
- Rarity 2: weight 5
- Rarity 3: weight 2

Each time an upgrade is taken, its weight decreases by 3 (minimum 1).

## Powerup Drops

20% drop chance on enemy kill. Equally weighted between:

| Powerup | Effect |
|---------|--------|
| HP | +35 HP |
| ATK | +5 ATK (permanent) |
| Shield | +40 shield |

Powerups despawn after 700 frames.

## Dodge Roll

| Stat | Value |
|------|-------|
| Speed multiplier | 2.2x player speed |
| Duration | 200ms |
| Cooldown | 800ms |
| Invincibility | Full duration (200ms) |

## Knockback (Shift)

| Stat | Value |
|------|-------|
| Radius | 120px |
| Stun duration | 0.4s |
| Cooldown | 3s |
| Force | 18 * (1 - distance/120) |

## Invincibility

- 2 seconds at wave start
- 750ms after taking melee damage
- 650ms after taking projectile damage
- 200ms during dodge roll

## Lava Hazards (Hell Fortress)

| Target | Damage |
|--------|--------|
| Player | 8 HP/s |
| Enemies | 4 HP/s |
