# Design Decisions

## Architecture
- Single HTML file, no dependencies
- Canvas 2D, imageSmoothingEnabled=false
- Web Audio API synthesized music (EDM/trance style)

## Balance
- Mage AOE range reduced (was 128–168, now 85–120) to prevent dominance
- Mage can earn range back via Weapon Mastery upgrades
- Enemy HP: (base + wave*N) * (1 + wave*0.22)
- Boss HP varies per type (2200-5000 base + wave scaling)

## Boss Design Philosophy
- Each boss has a unique mechanic, not just different projectile patterns
- Reaper: pure melee pressure, teaches kiting
- Lich King: projectile dodging + add management
- Infernal: environmental hazards (lava) + large slow projectiles
- Ice Titan: ground hazards (ice spikes) + circular arena with fall risk
- Kraken: destructible environment + water boss you can't reach directly
- Storm Lord: spinning patterns + focused beams

## Boss System
- 4 phases with 1s invincibility on transition (sequential, no skipping)
- Phase thresholds: P1=spawn, P2=85% (Kraken: 90%), P3=70%, P4=55%
- Secret revive (+50% HP, +40% ATK, +20% speed), Kraken has 0 revives
- Henchmen themed per boss (pirates, golems, skeletons, etc.)
- Infernal: forced attack on phase transition
- Kraken: swims in water, breaks piers, tentacle attacks, pirate ship spawns

## Sea Maps
- Frozen Caverns: circular arena, sea = instant death
- Abyssal Depths: pier/raft network, Kraken destroys walkable tiles
- Enemies use sea-aware AI; Kraken immune to knockback into water

## Targeting
- Click-to-target with crosshair (mobile-friendly for future touch support)
- X key for quick target switch
- Target persists through LOS loss

## Music
- EDM/trance style with Sandstorm/Erlkönig influences
- 5 states: dungeon(126bpm) boss0-3(130/136/150/165bpm)
- 16th-note resolution, detuned sawtooth lead, triplet arpeggios
- DynamicsCompressor prevents clipping
- Phase transitions change patterns seamlessly without restarting
