# Temperature

Players, Feudum villagers, and livestock feel the heat and the cold. The world sets the air temperature, and each body drifts toward it unless clothing, shelter, or fire hold it back. Temperature makes winter something a village plans for: firewood to burn, warm clothing to sew, and closed barns for the herds.

## Air and body

Temperature works in two layers:

- **Air temperature** belongs to a position. The climate, season, time of day, altitude, weather, wind, and nearby blocks set it.
- **Body temperature** belongs to each player, villager, and livestock animal. It drifts toward the air temperature, and clothing, wetness, food, and exertion shift it. Effects come from body temperature, so a short walk in the cold does no harm, and a fire takes time to warm someone back up.

Both use seven bands, from coldest to hottest: freezing, cold, cool, mild, warm, hot, and scorching. The bands sit on an internal number, but the design speaks in bands.

## Who feels it

- **Players** feel temperature everywhere in the world, vanilla villages included.
- **Feudum villagers** feel it, as [Villagers](#villagers) describes.
- **Livestock** feels it, as [Livestock](#livestock) describes.

Vanilla villagers, wild animals, and monsters ignore temperature.

## Air temperature

### Climate and season

In the open and in clear weather, the climate of the biome and the season set the air temperature, by day and by night:

| Climate   | Spring          | Summer           | Autumn          | Winter              |
|:----------|:----------------|:-----------------|:----------------|:--------------------|
| Temperate | Mild / cool     | Warm / mild      | Cool / cool     | Cold / freezing     |
| Cold      | Cold / freezing | Cool / cold      | Cold / freezing | Freezing / freezing |
| Arid      | Warm / cold     | Scorching / cool | Warm / cold     | Mild / cold         |
| Tropical  | Hot / warm      | Hot / warm       | Warm / warm     | Warm / mild         |

Each sub-season blends toward the neighboring season, so early spring sits close to winter and late spring close to summer. The [climate table](seasons.md#climate-by-biome) in the seasons document lists the vanilla biomes of each climate.

### Modifiers

- **Weather.** Rain or snow makes the air one band colder.
- **Altitude.** The air gets one band colder per 40 blocks above Y 80. Below Y 40, the air is mild all year.
- **Sun.** Shade takes away the heat of the sun, so the air in shade is cooler by day than in the open.
- **Wind chill.** Wind makes the air feel colder, in proportion to the strength of the wind and how exposed a body is: under open sky, at altitude, or out in a storm. Walls and windproof clothing block it. The wind mechanic sets the strength of the wind.
- **Heat and cold sources.** Fires warm the air and ice cools it, as [Heat and cold sources](#heat-and-cold-sources) describes.

All the bands and modifiers are configurable.

### The Nether and the End

The Nether and the End have no seasons, but they have a temperature. The Nether is hot everywhere and scorching near lava. The End is cool and still.

## Shelter and rooms

A body under a roof, with no sky above it, is sheltered: weather and wind no longer reach it, and the swing between day and night shrinks.

A room goes further. The mod detects the enclosed space around a body, bounded by walls, floor, roof, closed doors, and windows. Heat sources warm the room they stand in rather than a fixed radius, so a fireplace heats a home, an open door lets the heat out, and a large hall needs more fires.

- **Separation.** Closed doors and trapdoors separate rooms. An open one joins the room to whatever lies beyond it, and a room open to the outside leaks heat for as long as it stays open.
- **Size.** A room holds at most 1,000 blocks of air, configurable. A larger enclosed space only counts as sheltered and cannot be heated as a room.
- **Updates.** The mod rechecks a room when a block on its boundary changes.

### Insulation

Every block has an insulation value, in one of four classes:

| Class | Blocks                                                 |
|:------|:-------------------------------------------------------|
| Poor  | Glass, glass panes, iron bars, metal blocks, leaves    |
| Fair  | Planks, logs, and other wooden blocks                  |
| Good  | Stone, bricks, sandstone, mud bricks, packed mud, dirt |
| Best  | Wool, hay bales, thatch, wattle and daub               |

A room's insulation is the average over the blocks of its walls, floor, and roof, so windows and other poor blocks are weak spots. Higher insulation does two things. Heat from sources leaks away more slowly, and the room follows the outside air more slowly, which evens out the swing between hot days and cold nights. Each climate gets a fitting way to build: mud brick in the desert, and timber with thatch in the north. Block tags define the classes, so a datapack can change them.

### Heat and cold sources

- **Fireplace.** A new block that burns logs or firewood, with firewood lasting longer. It warms its room by a set amount, so a bigger or poorly insulated room needs more fireplaces. In winter, one fireplace burns about a stack of firewood a week.
- **Brazier.** A new freestanding fire bowl that burns the same fuel.
- **Other heat.** Campfires, lit furnaces, and lava add heat. Torches add almost none. Outside a room, a heat source only warms the air right next to it.
- **Cold.** Ice, packed ice, and snow blocks cool the room around them. Rooms below ground stay cool, since the air below Y 40 is mild.

## Body temperature

Body temperature drifts toward the air temperature a body feels, and faster the further apart the two are. These shift it further:

- **Clothing and armor**, as [Protection](#protection) describes.
- **Wetness.** Rain, swimming, and wading make a body wet. Being wet cools it, which is dangerous in the cold and welcome in the heat. A body dries off over time, faster in warm air or next to a fire.
- **Food and drink.** Hot stews and mulled cider or wine warm the body for a few minutes. [Cool water](thirst.md#water-temperature) and melon cool it.
- **Exertion.** Sprinting, fighting, and mining warm the body slightly.

Food, drink, and exertion are small and temporary. They nudge body temperature, but never replace clothing or shelter.

### Protection

Clothing and armor are two layers that stack:

- **Clothing** has seven slots of its own, separate from the armor slots: underclothes, head, body, legs, feet, cloak, and hands. It gives most of the warmth and cooling. Each garment has a warmth value, a cooling value, and a windproof value. Garments include wool clothing, a fur cloak, a waxed coat, and a wide straw hat. The [clothing mechanic](clothing.md) describes the slots and garments in full.
- **Armor** gives protection. Metal armor heats up in the sun and chills in frost unless it has a lining.
- **Linings** can be added to armor: wool or fur for warmth, and linen for cooling. A knight in plate armor survives winter with a fur lining.

Fire resistance protects against heat as well as fire.

### Effects

| Band      | Effects                                                                                                |
|:----------|:-------------------------------------------------------------------------------------------------------|
| Freezing  | Frost overlay, strong slowness, damage over time like vanilla powder snow, and no natural regeneration |
| Cold      | Shivering: hunger drains faster and mining slows                                                       |
| Cool      | None                                                                                                   |
| Mild      | None                                                                                                   |
| Warm      | [Thirst](thirst.md) rises faster                                                                       |
| Hot       | Thirst rises much faster, and hunger regeneration slows                                                |
| Scorching | Heat haze, weakness, nausea flashes, and damage over time                                              |

Effects build over minutes, with warnings first. A dry player without protection, out on a winter night in a cold climate, slides from mild to freezing in about three real minutes. Damage starts only after time spent in the freezing band. Long spells in the freezing band cause a chill, and long spells in the scorching band cause heatstroke. Both are illnesses of the [disease mechanic](disease.md#illnesses), which describes how they progress and heal.

Server config scales how strong the effects are and how fast they build, and can turn temperature off for players.

### Display

- **Gauge.** A small HUD gauge shows the player's body temperature band, with an arrow when it is rising or falling. A wet indicator sits next to it. Config can hide the gauge.
- **Cues.** There is no thermometer. Players read the air from cues instead: breath steams in cold air, and the air shimmers near heat.
- **Screen effects.** The vanilla powder snow frost overlay shows in the freezing band. A heat haze with a reddish vignette shows in the scorching band.

## Villagers

Feudum villagers share the body temperature of players and react to it:

- **Cold band.** They head home and work slower.
- **Freezing band.** A villager who stays in it catches a chill. A sick villager stays in bed and does not work, recovers once warm and fed, and dies if kept freezing.
- **Hot band.** They stop work at midday and rest in shade or indoors.
- **Scorching band.** Heatstroke is rare, and works like a chill.

Each villager home is a room that a fireplace heats, with firewood from the woodcutter. The tailor supplies winter and summer clothing, and villagers change into it as the season turns. A villager without winter clothing chills faster outside. A village that runs out of firewood or clothing in winter loses its villagers to the cold, as the [seasons document](seasons.md#village-effects) describes.

## Livestock

An animal becomes livestock once a player or a villager breeds it, feeds it, or leashes it, and its offspring are livestock from birth. Livestock has a body temperature, catches illnesses like villagers do, and can die from exposure:

- **Barns.** A closed barn keeps cattle and pigs through a temperate winter without heat. In a cold climate, or for chickens, the barn needs a heat source.
- **Wool.** Sheep with wool resist the cold, so a sheep sheared in autumn is at risk.
- **Heat.** Animals left without shade in arid or tropical heat suffer heat stress.

Feeding animals through winter belongs to the herder role, not to temperature.

## World effects

The world reacts to the air temperature, so one rule explains frost, greenhouses, cellars, and ice houses:

- **Crops.** Every crop grows within a range of air temperatures at its block. Frost kills crops that are not frost-hardy, and a greenhouse works because it is a sheltered, heated room.
- **Food storage.** Food [spoils](food-spoilage.md) at a rate set by the air temperature of the room it sits in. A root cellar works because the air below ground stays cool, and an ice house because its ice cools the room.
- **Snow and ice.** In the freezing band, water freezes and snow settles. From the mild band up, ice and snow melt. A heated room melts the snow around its fireplace, and an ice house keeps its ice only while it stays cold enough.

## Related mechanics

Temperature works together with these mechanics:

- **[Seasons](seasons.md).** The season and the climate of the biome set the base air temperature.
- **[Thirst](thirst.md).** Thirst rises faster in the warm, hot, and scorching bands.
- **[Food spoilage](food-spoilage.md).** Cold air slows rot.
- **Wind.** The strength of the wind sets the wind chill.
- **[Disease](disease.md).** Long spells in the freezing or scorching band cause illness.
- **[Clothing](clothing.md).** Garments give warmth, cooling, and windproofing.
- **[Cloth](cloth.md).** Shorn sheep feel the cold, and the silkworm tray needs mild to warm air.

## Additions and changes

- **Air temperature.** Every position gets an air temperature from its climate, season, time of day, altitude, weather, wind, and nearby blocks, which replaces the fixed temperature of vanilla biomes.
- **Body temperature.** Players, Feudum villagers, and livestock get a body temperature that drifts toward the air temperature.
- **Room detection.** Enclosed spaces of up to 1,000 blocks of air count as rooms that heat sources warm.
- **Block insulation.** Block tags sort every block into four insulation classes.
- **Fireplace and brazier.** New heat sources that burn logs or firewood.
- **Firewood.** A new fuel item that burns longer than logs, which the woodcutter supplies.
- **Insulating blocks.** Thatch and wattle and daub, new building blocks with the best insulation.
- **Linings.** Wool, fur, and linen linings for armor. Linen comes from flax, a new crop of the [cloth mechanic](cloth.md#flax-and-hemp).
- **Hot and cool food and drink.** Vanilla stews warm the body, and new mulled cider and wine warm it further. Cool water and melon cool it.
- **Temperature display.** A HUD gauge with a trend arrow and a wet indicator, breath vapor, heat shimmer, and a heat haze, alongside the vanilla frost overlay.
- **Freezing and melting.** Water freezes, snow settles, and both melt by the air temperature instead of the vanilla biome temperature.
- **Crop temperatures.** Crops grow within a range of air temperatures, and frost kills those that are not frost-hardy.
- **Livestock.** Animals that a player or villager breeds, feeds, or leashes become livestock, which feels temperature and can fall ill and die.
- **Villager behavior.** Feudum villagers head home in the cold, rest at midday in the heat, and change into seasonal clothing.
- **Configuration.** Server settings for the bands, the modifiers, the strength and pace of the effects, the room size limit, and the gauge.
