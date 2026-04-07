# Controls

All keybindings and input mechanics for Dungeon's Last Stand.

## Movement

| Key | Action |
|-----|--------|
| W / Up Arrow | Move up |
| A / Left Arrow | Move left |
| S / Down Arrow | Move down |
| D / Right Arrow | Move right |

Diagonal movement is normalized (0.707x multiplier) so you do not move faster diagonally.

## Combat

| Key | Action | Cooldown |
|-----|--------|----------|
| (Automatic) | Fire weapon at locked/nearest enemy | Weapon speed stat |
| Click Enemy | Lock target (crosshair displayed) | None |
| X | Switch target to nearest enemy | None |
| Spacebar | Dodge roll | 800ms |
| Shift | Knockback push | 3s |
| Scroll Wheel | Cycle weapon slots | None |
| Click Weapon Slot | Switch to that weapon | None |
| Q | Class ability (Shield Bash / Trap / Blink) | 5s |

## Target Lock System

- Click an enemy to lock onto it — a red crosshair (Fadenkreuz) is displayed
- All attacks focus the locked target regardless of line-of-sight
- Target persists until the enemy dies or you manually switch
- Press X to switch to the nearest enemy
- Click a different enemy to manually switch
- When locked target dies, auto-locks nearest visible enemy
- Crosshair has rotating arc rings (larger for bosses)

## Auto-Fire Targeting

- If no target is locked, auto-targets the nearest visible enemy
- Firing only occurs when the player is not dodge rolling
- Kraken boss bypasses LOS checks (always targetable from water)

## Dodge Roll Details

- Press Spacebar to dash in the current movement direction
- If standing still, dashes in the last movement direction
- Grants full invincibility for the 200ms duration
- Leaves a white particle trail
- Blue arc around player shows cooldown status
- On sea maps: dodge can send you into the water (death!)

## Knockback Details

- Press Shift to push all enemies within 120px away from you
- Pushed enemies are stunned for 0.4 seconds
- Push force is stronger the closer the enemy is
- Red arc around player shows cooldown status
- On sea maps: enemies knocked into water die instantly
- Kraken is immune to knockback

## Weapon Switching

- Scroll the mouse wheel to cycle through weapon slots
- Click a weapon slot in the HUD to switch directly
- You start with one weapon; a second slot is gained from upgrade selection
- During Kraken fight: Harpoon is auto-equipped as 3rd slot
- The active slot is indicated in the HUD with a highlight

## Sea Maps (Frozen Caverns, Abyssal Depths)

- Walking off the platform into the water = instant death
- No wall collision — you walk freely off the edge
- Enemies use sea-aware AI to avoid walking off piers
- Mage blink ability checks target position to prevent landing in water

## HUD Indicators

| Indicator | Location | Meaning |
|-----------|----------|---------|
| Yellow arc | Around player | Weapon fire cooldown |
| Blue arc | Around player | Dodge roll cooldown |
| Red arc | Around player | Knockback cooldown |
| Purple arc | Around player | Q ability cooldown |
| Golden glow outline | Player sprite | Invincibility active |
| Red crosshair | On enemy | Target lock active |
| White flashing box | On boss | Boss phase invincibility |
| HP bar | Above player | Current health |
| Wave banner | Bottom center | Current wave and enemy count |

## Upgrade Selection

After clearing a wave, a selection screen appears with 3 options. Click an option to choose it. Options may include:

- New weapons (click to equip)
- Stat upgrades (HP, ATK, SPD, shield, range)
- Weapon masteries (wave 5+, for currently owned weapons)

## Dev Mode

Accessible from the class select screen via the DEV MODE button (code: 939493).

| Key | Action |
|-----|--------|
| 1 | Jump to wave 5 (The Reaper) |
| 2 | Jump to wave 10 (Lich King) |
| 3 | Jump to wave 15 (The Infernal) |
| 4 | Jump to wave 20 (Ice Titan) |
| 5 | Jump to wave 25 (The Kraken) |
| 6 | Jump to wave 30 (Storm Lord) |
| O | Go back one wave |
| P | Skip forward one wave |

Dev mode grants 10000 HP on wave jumps.
