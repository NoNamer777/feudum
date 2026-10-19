# Hygiene

A body gets dirty as it lives. Sweat and soot build into grime over days of labor, mud cakes the legs on a wet road, and a butcher ends the day stained with blood. Dirt shows on the body and its clothes, and it smells, so a village keeps its distance from a filthy stranger and a wolf scents a bloodied hunter from downwind. Water washes it off: a sponge bath at a washbasin, a soak in a tub, or a plunge in the river, and soap with hot water does it best. A wash in a winter stream chills a body to the bone, so a heated tub or stone bath is worth its firewood. Garments are laundered on their own and dried on a line or by the hearth. Animals get dirty too: stock in an unmucked barn turns filthy, and pigs wallow to cool off. Vanilla has no dirt and no washing, so Feudum adds its own.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Every entity type whose diet profile carries a dirt block gets dirty: players, villagers, livestock, and wild animals. [ADR 0021](../../adr/0021-every-mob-that-eats-can-get-dirty.md) records why.
- A diet profile with no dirt block never gets dirty. An entity type with no diet profile has no dirt.
- A per-world setting turns dirt `off` or `on` for every entity. The default is `on`. It is separate from the settings of the needs and of Body temperature.
- Dirt never harms a body on its own, so difficulty plays no part.
- Creative and spectator players are exempt.
- [Bathhouse](https://github.com/NoNamer777/feudum/issues/151) owns how a bathhouse is laid out and recognized, with its rows of tubs, private rooms, and furnace room. This page owns the tubs, stone baths, and bath furnaces it holds.

## Model

- A body carries three kinds of dirt, each from clean at 0 to filthy at 1:
  - **Grime**: sweat, dust, and soot.
  - **Mud**: wet soil.
  - **Bloodstain**: blood on the skin, the body's own or another's. It is not the blood of [Health](health.md#blood), which bleeding drains.
- Worn garments carry the same three kinds, as [Garments](#garments) describes.
- **Smell** is derived, never stored. It follows the grime and bloodstain of the body and its worn garments, and the Soiled state of [Relief](relief.md#accidents), so it falls whenever they do.
- Soiled stays a state of its own, which Relief owns.
- Dirt advances by the Feudum time that passed, so it follows the day length and the sleep speed-up.

## Getting dirty

### Grime

- Grime builds slowly with time, and faster with exertion: sprinting, swimming, climbing, mining, chopping, and fighting, the set of [Body temperature](body-temperature.md#felt-temperature).
- Sooty or dusty work, such as smithing, charcoal burning, and mining, builds it fastest.
- An animal lying on the dung layers of [Relief](relief.md#waste) gains grime, so stock in a barn that isn't mucked out turns filthy.
- As starting values, a laboring human reaches Rank in about 2 to 3 Feudum days without washing, and an idle one in about a week.

### Mud

- The [wet ground](fluids.md#volume) of Fluids is muddy where it lies on soil, such as dirt, farmland, or a riverbank.
- Walking on muddy ground muds the feet and legs, and lying or falling on it muds the whole body. Wading in shallows over a soil bed muds the legs up to the waterline.
- Half of fresh mud dries and flakes off over about a Feudum day, and the rest stays until washed.
- Mud has no smell.

### Bloodstain

- A bleeding body stains itself, and [heavy bleeding](health.md#injuries) stains it faster.
- Striking a bleeding target in melee stains the striker.
- [Butchering](animal-husbandry.md#slaughter-and-butchering) a carcass, and gutting fish or game, stain the worker.
- Bloodstain never fades on its own.

## Garments

- Garments carry grime, mud, and bloodstain of their own.
- Mud and bloodstain land on the outermost garment over the region they reach, mostly the feet and legs for mud. They reach the body only where nothing is worn.
- Grime builds on the body and, at the same rate, on the garments of its underlayer, which take its sweat.
- Smell reads the worn garments as well as the body, so a washed body in grimy clothes still smells, and laundry matters.
- Dirt changes no garment stats: insulation, resistance, and wear stay as [Clothing](../content/clothing.md) sets them.

## Smell

Smell is the highest grime or bloodstain of the body or any worn garment, and a Soiled body smells Foul. For a human:

| Stage | Reached   | Effects                                                                 |
|:------|:----------|:------------------------------------------------------------------------|
| Fresh | Below 25% | None.                                                                   |
| Stale | 25%       | None.                                                                   |
| Rank  | 50%       | Standing falls on sighting, and the scent carries farther.              |
| Foul  | 75%       | Standing falls more, the scent carries farther still, and flies gather. |

- Smell puts no modifier on any attribute.

### Standing

Hygiene decides how smell moves [standing](villages.md#standing-and-wishes), and Villages owns the scale:

- A player at Rank or Foul, inside a village's territory and in sight of one of its villagers, lowers standing with that village a little once per sighting, and more at Foul.
- A Soiled player smells Foul, and a sighting costs standing once, not once for Relief and again for smell.
- Visible bloodstain worries villagers, and [Villagers](https://github.com/NoNamer777/feudum/issues/46) decides how they react.
- The amounts are starting values to tune.

### Scent

- Smell and bloodstain together set a body's scent, which carries farther downwind. Bloodstain weighs more, so a bloodied hunter draws predators.
- [Wildlife](https://github.com/NoNamer777/feudum/issues/47) and [Stealth](https://github.com/NoNamer777/feudum/issues/89) decide how animals and villagers sense a scent. Hygiene supplies it through the [query](#query).

### Health

- Grime and mud raise the chance that an [open wound](health.md#injuries) rots, and grime on the hands raises the chance of passing a disease by touch, as [Illness](illness.md#open-wounds) describes. Bloodstain doesn't count, since it is blood, not filth.

## Washing

Water clears dirt by its temperature and whether soap is used:

| Dirt       | Cold water | Hot water or soap |
|:-----------|:-----------|:------------------|
| Mud        | All        | All               |
| Bloodstain | All        | All               |
| Soiled     | Clears     | Clears            |
| Grime      | Half       | All               |

- Water of 30 °C or more counts as hot, as a starting value.
- Soap with hot water washes in half the time.
- Water above half foulness no longer cleans.

### Methods

- **Pouring**: pouring a container of water over oneself clears Soiled, as Relief describes, and half of the mud and bloodstain, but no grime. It leaves the body wet by the water poured.
- **Washbasin**: a sponge bath of about 5 seconds, which draws about 2 liters from the basin. It washes the body by the table, but not its worn garments, and leaves the body damp rather than soaked.
- **Soak**: a body sitting in a tub or a stone bath washes over about 10 seconds. It washes the body and every garment it wears, and leaves both soaked.
- **Open water**: a body under water washes as a soak does, as [Relief](relief.md#accidents) and [Clothing](../content/clothing.md#soiling) already describe for Soiled.
- A body soaking or swimming feels the temperature of the water, under [Body temperature](body-temperature.md#felt-temperature), so a hot bath warms and a winter stream chills.

### Soap

- Using soft soap on oneself lathers the body until its next wash, and using it on a garment in the inventory lathers the garment.
- Using soft soap on a filled tub or washbasin makes its water soapy for several washes.
- A lathered body or garment, or soapy water, washes as soap does in the table.
- A pot of soft soap holds several uses. [Lye and soap](#lye-and-soap) describes how it is made.

### Wash water

- Each wash adds foulness to the water in proportion to the dirt it removes, and soap adds a little more. A Soiled body also adds its waste, as [Waste in water](relief.md#waste-in-water) describes.
- A family can share one tubful, at the cost of its getting fouler with each bather until it no longer cleans.
- Emptying a tub or a washbasin pours its water where it is emptied. Poured-out wash water is a mild [fouling source](fluids.md#fouling).
- Bathing or laundry in a stream fouls it downstream, as waste in water does.

## Vessels

### Washbasin

- A washbasin is a basin on a stand that holds 5 liters. It is filled by pouring from a container and emptied by hand.

### Wooden tub

- A wooden tub is a single block that holds 300 liters, and a soak needs at least 150.
- It is filled by pouring from containers and emptied by tipping it. Filling one by hand takes many trips, which is what a bathhouse and its [Bathkeeper](https://github.com/NoNamer777/feudum/issues/152) are for.

### Stone bath

- A stone bath is a pool of any size and shape, lined with bath stone, a dressed stone block, and filled with the water of [Fluids](fluids.md). Water bounded on every side and below by bath stone counts as a stone bath.
- A bath furnace set against the lining heats the water while it burns fuel.

### Water temperature

- The water of a washbasin, tub, or stone bath carries a temperature. It drifts toward the [room temperature](body-temperature.md#shelter-and-heat) of its enclosed space, or toward the local temperature of [Weather](weather.md#local-temperature) in the open, over about a Feudum hour, and more slowly for a larger volume.
- Water poured in mixes its temperature with the water already there as an average weighted by volume, as Fluids mixes salinity, so hot water from the heated cauldron of [Cooking](cooking.md#boiling-water) warms a tub or washbasin.
- Each bath furnace adds heat to its stone bath while it burns, so a large bath needs several. A bath furnace burns the usual fuels, and it is also a heat source under Body temperature.
- The heat output of a bath furnace is a starting value to tune.

### Access

- A player may use the tubs, stone baths, and washbasins of the village holding, which are communal, those in the buildings of a manor they are lord of, and those in their own buildings outside any village. A public bathhouse is communal.
- Using the tub, stone bath, or washbasin of another household lowers standing, as using its privy does under [Relief](relief.md#standing).
- [Village economy](https://github.com/NoNamer777/feudum/issues/44) decides whether a bathhouse charges a fee.

## Laundry

- A garment off the body is washed by using it on open water, a filled tub, or a filled washbasin for about 5 seconds. It washes by the table of [Washing](#washing), leaves the garment soaked, and fouls the water as bathing does.
- A **battledore**, a wooden laundry bat, halves the time when held in the offhand. It is never required. [Carpentry](https://github.com/NoNamer777/feudum/issues/115) decides where it is made.
- A towel is laundered the same way.
- A [Laundress](https://github.com/NoNamer777/feudum/issues/153) washes and dries the garments of a household or a village.

### Fading

- Laundry, and wearing a garment into a tub or stone bath, count as a wash toward the [fading](textiles.md#fading) of a dyed garment. Swimming, wading, and rain don't.
- Textiles decides how much each wash fades.

## Drying

[Clothing](../content/clothing.md#drying) owns how garments dry while worn, carried, or stored. Hygiene adds fast drying:

- **Clothesline**: a line strung between two posts up to 8 blocks apart, which holds one garment or towel per block of its length. It dries what hangs on it by felt temperature, sun, and sheltered wind, as a worn garment dries, but faster, since the air reaches both sides. Rain wets what hangs on it.
- **Drying rack**: a block that holds four garments or towels and dries them by the heat sources around it, so a rack by the hearth dries a soaked cloak overnight.
- Both show what hangs on them.

### Towel

- A linen towel is sewn from linen cloth of [Textiles](textiles.md) at a tailor's bench.
- Rubbing down with a towel for about 2 seconds takes the body's wetness down to damp, and moves that water into the towel.
- A towel carries wetness as a garment does, and a soaked towel dries nothing until it has dried itself.

## Lye and soap

- Wood ash is left by burning wood on a hearth or a fire, which [Fire](https://github.com/NoNamer777/feudum/issues/33) decides.
- A **lye barrel** is a block filled with wood ash. Water poured through it collects as lye within about a Feudum day, and each fill of ash leaches one batch.
- **Soft soap** is lye boiled with tallow or oil in the heated cauldron of Cooking. The tallow comes from [Animal husbandry](animal-husbandry.md#slaughter-and-butchering), and the oil from [Oil pressing](https://github.com/NoNamer777/feudum/issues/106).
- Lye and soft soap keep indefinitely. Boiling ends the spoilage of the tallow or oil, as [ADR 0018](../../adr/0018-every-organic-item-spoils.md) allows for processing that stabilized a material.

## Animals

- Animals get dirty from the same sources as other bodies, and from lying on dung, as [Grime](#grime) describes. They wear no garments, so their smell follows their own dirt.
- Rain clears half of an animal's mud, and swimming washes it as a soak does. A player washes an animal by pouring water over it.
- A **curry brush** clears an animal's mud and grime, but not its bloodstain, after a few seconds of brushing. The [Groom](https://github.com/NoNamer777/feudum/issues/147) brushes a village's animals.

### Wallowing

- A dirt block can mark a species as wallowing, as pigs are. A wallowing animal seeks muddy ground while Overheated and rolls in it.
- Mud on any body cools it as [wetness](body-temperature.md#wetness) does, and its water dries at half the rate, so a wallow cools for longer.

### Fleece

- A sheep's mud and grime pass to its fleece at shearing. Grime raises the share of skirtings, and mud and grime lengthen the scour, as [Textiles](textiles.md#wool) describes.
- A sheep washed before shearing, by swimming or by pouring water over it, gives a clean fleece, so a flock is driven through a stream or a sheepwash pool in the week before shearing.

## Diet profiles

- The [diet profile](hunger.md#diet-profiles) of Hunger carries an optional dirt block, so dirt needs no profile or entity type tags of its own.
- The dirt block holds the rate of each source, how fast mud flakes off, the smell thresholds, and whether the species wallows.
- Villagers use the human diet profile, the same as players.

## Cues

- Players read their own dirt from their body, never from a meter. Grime darkens the hands and the model, mud cakes the legs, and bloodstain spatters the hands and the model. Each garment shows its own dirt, on the model and in the inventory.
- A player learns their smell from others: from Rank, villagers wrinkle their noses and step back, and animals shy. At Foul, flies gather as they do around a Soiled body.
- A lathered body or garment shows foam, and soapy water shows suds.
- Mobs show their dirt on the model too, so a filthy herd reads at a glance.

## Persistence

- A player's dirt saves with the player. Logging back in resumes from the saved values, since a player's absence is not simulated.
- A new player starts clean, and respawning clears dirt and Soiled.
- A garment or towel saves its dirt with the item.
- Wild mobs in unloaded chunks are not simulated. When their chunk loads, each starts with a random low dirt.
- An owned animal outside any village territory keeps its saved values while its chunk is unloaded, as a logged-out player does.
- Village simulation brings the villagers and livestock of an unloaded village forward, as [Boundaries](#boundaries) describes.
- A washbasin, tub, or stone bath saves the volume, temperature, foulness, and soapiness of its water. A clothesline or drying rack saves what hangs on it.

## Query

- One query returns an entity's grime, mud, and bloodstain, its smell and stage, its scent, whether it is lathered, and the dirt of each worn garment.
- A second function returns the volume, temperature, foulness, and soapiness of the water in a washbasin, tub, or stone bath.
- Other mechanics read hygiene through these.

## Commands

- `/feudum hygiene query [entity]` shows the result of the query.
- `/feudum hygiene set <entity> <grime|mud|bloodstain> <value>` sets a value, for testing.
- Every `/feudum hygiene` command requires operator permission.

## Boundaries

Hygiene owns grime, mud, and bloodstain, how bodies and garments get dirty, smell and its stages, how smell moves standing, and scent. It also owns washing and what clears what, washbasins, wooden tubs, stone baths, and bath furnaces, the water temperature of those vessels, and wash water. Laundry and the battledore, which washes count toward fading, the clothesline, the drying rack, and the towel, lye and soft soap, the curry brush, wallowing, the dirt a fleece takes at shearing, and the dirt block of diet profiles are its own as well. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Relief](relief.md)**: accidents, the Soiled state, and the waste a Soiled body leaves in water.
- **[Clothing](../content/clothing.md)**: garments, their wetness and how they dry while worn, carried, or stored, and soiled garments.
- **[Body temperature](body-temperature.md)**: wetness, felt temperature and how a body feels water, room temperature, and heat sources.
- **[Fluids](fluids.md)**: water, wet ground, foulness, and how water mixes.
- **[Health](health.md)**: bleeding and open wounds.
- **[Hunger](hunger.md)**: the diet profiles that Hygiene extends.
- **[Textiles](textiles.md)**: linen cloth, skirting and scouring, and how much a wash fades a dye.
- **[Animal husbandry](animal-husbandry.md)**: butchering and tallow.
- **[Villages](villages.md)**: the standing scale.
- **[Weather](weather.md)**: the local temperature that open-air water drifts toward.
- **[Bathhouse](https://github.com/NoNamer777/feudum/issues/151)**: how a bathhouse is laid out and recognized, with its private rooms and furnace room.
- **[Bathkeeper](https://github.com/NoNamer777/feudum/issues/152)**: the villager who keeps a bathhouse.
- **[Laundress](https://github.com/NoNamer777/feudum/issues/153)**: the villager who washes and dries garments.
- **[Groom](https://github.com/NoNamer777/feudum/issues/147)**: the villager who brushes a manor's horses.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: when and where villagers wash, and how they react to smell and bloodstain.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)** and **[Stealth](https://github.com/NoNamer777/feudum/issues/89)**: how scent is sensed.
- **[Illness](illness.md)**: what grime and mud in a wound do to a body, and how grime on the hands spreads disease by touch.
- **[Cooking](cooking.md)**: the heated cauldron that heats water and boils soap.
- **[Fire](https://github.com/NoNamer777/feudum/issues/33)**: wood ash.
- **[Oil pressing](https://github.com/NoNamer777/feudum/issues/106)**: the oil for soap.
- **[Carpentry](https://github.com/NoNamer777/feudum/issues/115)**: where the battledore is made.
- **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: bathhouse fees.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: dirt and washing while a village is unloaded.
