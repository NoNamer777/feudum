# Body temperature

Every living mob, players included, has a body temperature that drifts toward how warm or cold its surroundings feel, and a wetness that makes the cold bite harder and the heat easier to bear. Shelter, fire, clothing, food, and work keep a body comfortable; a winter night in the open, a plunge through the ice, or a midday march across the desert can kill it. Vanilla has no body temperature beyond the freezing of powder snow, so Feudum adds its own.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Every living mob has a body temperature: players, villagers, animals, and the rest. [ADR 0005](../../adr/0005-every-living-mob-has-a-body-temperature.md) records why.
- An entity type with no thermal profile has no body temperature, for things such as constructs or spirits.
- A per-world setting sets how harsh body temperature is for every entity: `off`, `mild` (debuffs only, never lethal), or `harsh` (lethal at the last stage). The default is `harsh`.
- Creative and spectator players are exempt.

## Model

- An entity carries two values: its body temperature, in degrees Celsius like the local temperature, and its wetness, from dry to soaked.
- Body temperature drifts toward an equilibrium set by the felt temperature. Inside the comfort band, the equilibrium is the normal temperature of the species. Outside it, the equilibrium falls or rises in proportion to how far the felt temperature lies past the edge of the band.
- The drift rate comes from the thermal profile, so a small mammal cools fast and a large one slowly. Insulation slows it further.
- Body temperature and wetness advance by the Feudum time that passed, so they follow the day length and the sleep speed-up. Sleeping rough through a winter night can freeze a player; a bed under a roof protects them.
- Players update every second, and mobs on a staggered cycle of a few seconds. Inputs such as the enclosure check and the Weather query are cached.

## Thermal profiles

- Each entity type has a data-driven thermal profile: JSON in a data pack, assigned through entity type tags, as climate profiles are assigned through biome tags.
- A profile holds the normal temperature, the comfort band, the natural insulation, the drift rate, and the stage thresholds. A human's comfort band is about 12 to 26 °C of felt temperature.
- A profile can mark a species as ectothermic. An ectotherm's body temperature tracks the felt temperature closely, and its cold stages make it sluggish rather than hurt it, so a lizard slows on a cold morning and basks in the sun. Its heat stages still hurt it.
- A profile can carry a young modifier, with a narrower comfort band and faster drift, so lambs in a winter field are at risk before the flock is.
- A profile declares which states change natural insulation. A shorn sheep loses most of its fleece insulation until the wool grows back, which makes shearing in late autumn a real decision.

## Felt temperature

Felt temperature starts from the local temperature of the [Weather](weather.md#local-temperature) query, which already accounts for season, climate profile, altitude, and the time of day. Environmental inputs add offsets in °C to it, and insulation reshapes the comfort band.

- **Sun**: open sky adds a sun offset that grows with the height of the sun and shrinks with cloud cover. Midday in a clear desert is brutal; shade or overcast takes the edge off.
- **Wind chill**: wind lowers the felt temperature in proportion to the mean speed of the [sheltered wind](weather.md#wind-shelter), and more when wet. Wind-resistant clothing cuts it further.
- **Wetness**: wetness always cools. In the cold it also cancels much of the natural insulation, and a wet garment loses its own, as [Clothing](../content/clothing.md#wetness) describes. In the heat it brings relief, so a swim cools a summer day.
- **Exertion**: sprinting, swimming, climbing, mining, chopping, and fighting build a warming offset that decays over about a minute of rest.
- **Heat sources**: see [Shelter and heat](#shelter-and-heat).
- **Food and drink**: a consumable can carry a thermal component, an offset in °C and a duration, so a hot stew warms for a while and cold water cools. [Hunger](hunger.md) and [Thirst](thirst.md) own the nourishment.
- **Depth**: below the surface, by heightmap and without sky access, felt temperature blends toward the cave temperature, the yearly average of the local temperature there. Caves feel cool in summer and mild in winter, and the deepest levels warm again with geothermal heat.
- **Water**: a body in water feels the water temperature instead of the air. Deep water stays near the yearly average, shallows follow the air, and water under ice never drops below 0 °C. A body in water drifts several times faster than in air, so falling through winter ice kills within a minute or two.
- **Insulation**: clothing and natural insulation, such as fur or fleece, widen the comfort band toward the cold and narrow it toward the heat, and slow the drift. A fur coat makes winter safe and summer worse.

## Wetness

- Wetness rises with precipitation intensity while uncovered, to full when submerged, and by depth when wading.
- Exertion while Overheated adds sweat, so a hard worker cools in the heat but chills once they stop in the cold.
- Snow falling on an uncovered body melts into wetness while the felt temperature is above freezing.
- Garments carry wetness of their own, and precipitation reaches the body only through them, slowed by their water resistance, as [Clothing](../content/clothing.md#wetness) describes.
- Wetness dries faster with higher felt temperature, sun, sheltered wind, and nearby heat sources.

## Shelter and heat

- A body under no open sky is covered: rain and sun no longer reach it.
- Wind shelter, not cover, decides how much wind reaches a body, so a roof with open sides keeps off the rain but not the wind, and a wall with no roof breaks the wind.
- A body inside an enclosed space feels the room temperature of that space instead of the outside air.
- The enclosure check flood-fills the air around a body up to a volume cap. Wall blocks bound the space, and so do door-like blocks, such as doors, trapdoors, gates, and panes, whether open or closed. The fill also stops at outdoor cells, air with open sky above, and each face it shares with one counts as an opening.
- A space past the volume cap is covered, not enclosed.
- Each enclosed space stores a room temperature, which drifts toward the balance between the heat its heat sources put in and the heat it loses. Each wall face loses heat by the insulation of its block, so wool holds heat better than stone. Each opening loses much more: an open door or trapdoor more than a closed one, and a missing block most of all.
- A well-heated room with one hole stays fairly warm, an open barn stays barely above the outside temperature, and an unheated room settles to the outside temperature.
- Room temperatures are cached and recomputed when a block of the space changes. They are dropped when the chunks unload, and the space starts from its balance when they load again.
- Heat sources are data-driven: block tags map a block to a heat output in °C. In the open, the output falls off over a radius. In an enclosed space, the full output goes into the room temperature.
- Cold sources, such as ice and packed snow, carry negative outputs.
- Living entities are weak heat sources, so a herd warms its barn, a crowd warms a hall, and huddling works.
- Enclosure belongs to body temperature. Buildings can reuse the check.

## Clothing

- Every wearable carries thermal stats as data: insulation, wind resistance, water resistance, and sun heating. Metal armor bakes in the sun and chills in the frost.
- Bodies wear clothing in three layers, and [Clothing](../content/clothing.md) owns the slots and how the stats of worn garments combine.

## Stages

Each side of normal has three stages, with thresholds from the thermal profile. For a human:

| Stage           | Threshold | Effects                                                             |
|:----------------|----------:|:--------------------------------------------------------------------|
| Chilled         |   < 36 °C | Cues only; hunger drains faster.                                    |
| Hypothermic     |   < 34 °C | Slower movement and work, no sprinting; hunger drains faster still. |
| Freezing        |   < 31 °C | Heavy slowness; periodic damage.                                    |
| Overheated      |   > 38 °C | Cues only; thirst drains faster.                                    |
| Heat exhaustion | > 39.5 °C | Slower movement and work, no sprinting; thirst drains faster still. |
| Heatstroke      |   > 41 °C | Blurred and swaying vision for players; periodic damage.            |

- Work covers mining, chopping, and attacking.
- Under `mild`, Freezing and Heatstroke keep their slowness and deal no damage.
- Effects apply as Feudum attribute modifiers, never as mob effects, so no icon shows in the inventory.
- Modifiers of the same kind as those of Hunger and Thirst take the strongest rather than adding up, under a rule that Health owns. Damage from each mechanic still applies on its own.
- Feudum's own hypothermia and heatstroke damage types carry their own death messages.
- Feudum replaces the vanilla freezing mechanic: the frozen-ticks counter and its screen overlay never trigger, and vanilla freeze damage never applies.

## Cues

- Players read their own state from body cues, never from a meter, and cues grow with the stage.
- Cold shows as visible breath, a frost vignette, shivering hands and a slight camera shake, and chattering teeth.
- Heat shows as heat shimmer, a sweat-blurred edge to the view, and heavy breathing.
- Wetness shows as dripping and a damp tint on the hands.
- Mobs show their state too, so a player can read a herd at a glance: cold mobs breathe visibly, shiver, and huddle, and hot ones pant and droop.

## Behavior

- Body temperature owns the stages and their effects for every mob.
- Animals share one comfort-seeking goal: when outside their comfort band, they move toward shelter, shade, or warmth, and huddle together.
- Villagers decide their own reactions, such as seeking shelter or falling ill.

## Persistence

- A player's body temperature and wetness save with the player. Logging back in resumes from the saved values, since a player's absence is not simulated.
- Respawning resets a player to normal temperature and dry.
- Mobs in unloaded chunks are not simulated. When their chunk loads, each mob starts at the equilibrium for the current conditions, capped short of the damaging stage, so a loaded chunk never reveals a herd that froze while no one was near.

## Query

- One query returns an entity's body temperature, its felt temperature with the offset of each input, its wetness, and its stage. It also returns each worn garment, as [Clothing](../content/clothing.md#query) describes.
- Other mechanics read body temperature through this query.

## Commands

- `/feudum body query [entity]` shows the result of the query.
- `/feudum body set <entity> <temperature|wetness> <value>` sets either value, for testing.
- Every `/feudum body` command requires operator permission.

## Boundaries

Body temperature owns thermal profiles, felt temperature and its inputs, the wetness of the body, enclosure and room temperature, heat sources, the thermal stats of wearables and consumables, the stages and their effects, cues, and the comfort-seeking goal of animals. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **Weather**: local temperature, precipitation, snow cover, wind, and wind shelter. Body temperature reads the sheltered wind for wind chill and drying.
- **[Hunger](hunger.md)**: nourishment, how faster drain plays out, and the vegetable deficiency that narrows the comfort band.
- **[Thirst](thirst.md)**: drinking, and how faster drain plays out.
- **[Fluids](fluids.md)**: the water a body swims in and the wet ground it lies on, both of which add wetness.
- **[Health](https://github.com/NoNamer777/feudum/issues/36)**: the rule that modifiers of the same kind take the strongest.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: how villagers react to their body temperature.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: abstract losses while a village is unloaded, such as livestock lost in a hard winter, read from the Weather query for each catch-up step.
- **[Fire](https://github.com/NoNamer777/feudum/issues/33)**: how fire catches and spreads. Its heat output is a heat source like any other.
- **[Buildings](https://github.com/NoNamer777/feudum/issues/29)**: whether a building reuses the enclosure check.
- **[Clothing](../content/clothing.md)**: the slots, how the stats of worn garments combine, and the wetness and drying of garments.
