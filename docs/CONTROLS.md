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
| (Automatic) | Fire weapon at nearest visible enemy | Weapon speed stat |
| Spacebar | Dodge roll | 800ms |
| Shift | Knockback push | 3s |
| Scroll Wheel | Switch weapon slot | None |

## Auto-Fire Targeting

- The player automatically fires at the nearest enemy in range
- Targeting respects line-of-sight -- enemies behind walls are skipped
- Firing only occurs when the player is not dodge rolling
- No manual aim is required

## Dodge Roll Details

- Press Spacebar to dash in the current movement direction
- If standing still, dashes in the last movement direction
- Grants full invincibility for the 200ms duration
- Leaves a white particle trail
- Blue arc around player shows cooldown status

## Knockback Details

- Press Shift to push all enemies within 120px away from you
- Pushed enemies are stunned for 0.4 seconds
- Push force is stronger the closer the enemy is
- Red arc around player shows cooldown status
- Knockback respects wall collision (enemies will not be pushed into walls)

## Weapon Switching

- Scroll the mouse wheel to swap between Slot 1 and Slot 2
- You start with one weapon; a second slot is gained from upgrade selection
- The active slot is indicated in the HUD with a highlight

## HUD Indicators

| Indicator | Location | Meaning |
|-----------|----------|---------|
| Yellow arc | Around player | Weapon fire cooldown |
| Blue arc | Around player | Dodge roll cooldown |
| Red arc | Around player | Knockback cooldown |
| Golden glow outline | Player sprite | Invincibility active |
| HP bar | Above player | Current health |
| Wave banner | Bottom center | Current wave and enemy count |

## Upgrade Selection

After clearing a wave, a selection screen appears with 3 options. Click an option to choose it. Options may include:

- New weapons (click to equip)
- Stat upgrades (HP, ATK, SPD, shield, range)
- Weapon masteries (wave 5+, for currently owned weapons)
