# Salt

Salt is what lets a village keep its meat through the winter, cure its hides, and season its pottage. On the coast, seawater dries in shallow pans under the summer sun into coarse bay salt, or boils down in an iron pan over a fire into fine white salt. Inland, a few villages sit on a brine spring or a bed of rock salt, and the rest must trade for it. Salt also feeds the body: people, herds, and deer need a little of it, and a deficient herd strays toward a lick. Vanilla has no salt, so Feudum adds its own.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Salt owns the salt item and its grades, the salt that water carries and leaves behind, every way of making salt, salt licks, and the pinch of salt that seasons a dish.
- It starts at seawater, brine, and rock salt. [Fluids](../mechanics/fluids.md#water-quality) owns salinity and how water carries, mixes, and concentrates it.
- It ends at the salt item. Each design that uses salt owns its own step, as [Uses](#uses) lists.
- [Hunger](../mechanics/hunger.md#salt-level) owns the salt level a body needs, and [Thirst](../mechanics/thirst.md#model) the salt load of too much salt.

## Working

- A hand step, such as raking a crust or scraping salt silt, is done at its block, or with its handheld tool, by holding the use key, as in [Textiles](../mechanics/textiles.md#working). Work advances by the Feudum time that passed, and stopping keeps what is done.
- Villagers work the same blocks at the same rate. Making salt is the trade of the [Salter](https://github.com/NoNamer777/feudum/issues/181).

## Salt

- One salt item holds about 1 kg of salt, as a starting value. "A measure of salt" on other pages means one salt item.
- Salt is conserved with the salinity of [Fluids](../mechanics/fluids.md#evaporation-and-brine). A liter of seawater, at salinity 1, carries about 35 g of salt, so salt and salinity convert exactly:
  - Water that dries leaves exactly the salt it carried.
  - Salt dissolved in water raises its salinity by exactly that amount.
- A full block of seawater (1,000 L) holds about 35 salt, and a full block of saturated brine about 260.
- Salt keeps forever. It is not organic, so [Food preservation](../mechanics/food-preservation.md) never spoils it.
- Salt stores in the containers that already exist, such as barrels, sacks, and chests. Feudum adds no container of its own for it.

### Grades

Every salt item has a grade, which the way it was made sets:

| Grade      | Made by                                 | Looks                     | Dry salting       | Taste |
|:-----------|:----------------------------------------|:--------------------------|:------------------|:------|
| Bay salt   | Evaporation, in a salt pan              | Coarse and gray           | Full keeping time | Plain |
| White salt | Boiling, in a boiling pan or a cauldron | Fine and pure             | A quarter less    | Best  |
| Rock salt  | Crushing a rock salt block              | Coarse, gray-pink, gritty | Full keeping time | Worst |

- Coarse salt draws the water out of meat and fish slowly and evenly. Fine white salt crusts the outside and leaves the inside wet, so food dry-salted with it keeps a quarter less than the [Salting](../mechanics/food-preservation.md#salting) time of Food preservation, as a starting value.
- [Food quality](https://github.com/NoNamer777/feudum/issues/161) reads the grade of a seasoning and decides what the taste does. [Dairy](https://github.com/NoNamer777/feudum/issues/135) decides whether butter and cheese ask for white salt, and [Village economy](https://github.com/NoNamer777/feudum/issues/44) prices the grades apart.
- Every grade holds the same 1 kg of salt, for the salt amount, dissolving, and conservation alike.
- Brine carries no grade. Any grade dissolves into plain salinity, and boiling that brine back down always gives white salt, so dissolving and reboiling refines any salt.

### Dissolving

- A salt item in water dissolves into it: the water's salinity rises, and the item is gone. Water stops taking salt at saturation, about salinity 7.5, and salt beyond that stays an item.
- Rain dissolves salt left out under open sky, and the salt runs off with the rain. So a village keeps its salt under a roof or in a closed container, and dry salt keeps forever.
- Dissolving is how a village makes brine without boiling. A pit of preserving brine at salinity 3 (about 1,000 L) takes about 105 salt.

## Sources

The diagram maps each source to the grade of salt it gives. A source with a light fill is found in the world, and the grades are bold. The dashed arrow is salt dissolved back into brine, which then boils into white salt.

![Where salt comes from. The sea gives seawater. Salt silt from the tidal flats is sleeched into brine, brine is drawn from a brine spring, and a rock salt bed is mined into rock salt blocks, which dissolve into brine. Seawater or brine evaporated in a salt pan gives bay salt, and boiled gives white salt. A rock salt block crushed gives rock salt. Salt dissolved again in water becomes brine.](images/salt-sources.svg)

| Source       | Where                               | Gives                      | Made with                                                         |
|:-------------|:------------------------------------|:---------------------------|:------------------------------------------------------------------|
| Seawater     | Every coast                         | Bay salt or white salt     | A salt pan or a boiling pan                                       |
| Salt silt    | Tidal flats bared at low tide       | Brine at about salinity 4  | A shovel and a sleeching pit                                      |
| Brine spring | Some inland regions, over salt beds | Brine at salinity 5 to 7.5 | A container and a boiling pan                                     |
| Rock salt    | Deep beds in some regions           | Rock salt, or brine        | A pick and the quern                                              |
| Trade        | Other villages and merchants        | Any grade                  | [Village economy](https://github.com/NoNamer777/feudum/issues/44) |

- Seawater is weak, so a coastal village makes its salt cheaply in the sun or dearly over a fire.
- Strong brine gives far more salt for each pan of water boiled: a boiling pan of seawater gives about 9 salt, and one of spring brine at salinity 7 about 60. That is why sleeching, springs, and dissolved rock salt are worth the trouble.
- An inland village with no spring or bed must trade for its salt. A salt tax, such as the French gabelle, belongs to [Realm laws](https://github.com/NoNamer777/feudum/issues/102).

### Salt crust

Both pans make salt the same way, as a crust:

- Once the water in a pan reaches saturation, every further liter that dries or boils off leaves its salt as crust on the pan floor, and the water stays at saturation.
- A pan keeps its crust as a continuous amount, so a pan can hold 4.4 salt. Raking yields whole salt items, and the remainder stays in the pan.
- The crust takes its grade from how it formed: salt left while the water boils is white salt, and salt left by evaporation is bay salt. A pan that did both, such as a boiling pan left to dry in the sun, keeps an amount of each and yields both when raked.
- Fresh water or rain that reaches a crust dissolves it back until the water is saturated again, so an uncovered pan loses its crust to a summer storm.

### Salt pans

- A **salt pan** is one clay-lined block, an eighth of a block deep, which holds up to about 125 L of water.
- It is filled by pouring, or by a channel that lets seawater in, through [Fluids](../mechanics/fluids.md#volume).
- It dries by evaporation, which reads the heat, wind, and cloud cover of [Weather](../mechanics/weather.md). Salt pans work in warm, dry weather and stall in cold or rain.
- A full pan of seawater leaves about 4.4 bay salt.
- A row of pans works as concentrating ponds with no extra rule: water moved from one pan to the next carries its salinity, so the last pan holds strong brine and yields the most crust for its volume.

### Boiling pans

- A **boiling pan** is a wide, shallow iron pan, one block, set over a fire, which holds up to about 250 L of water.
- It boils its water away at the pace of boiling under [Cooking](../mechanics/cooking.md#boiling-water), and burns fuel under [Fire](../mechanics/fire.md#fuels) for as long as it boils.
- It makes white salt in any weather and season, at the cost of the fuel.
- The heated cauldron of Cooking can also boil brine dry into white salt, but holds much less.
- [Smithing](https://github.com/NoNamer777/feudum/issues/86) makes the iron pan.

### Brine springs

- A **brine spring** is a spring whose groundwater is strong brine, at salinity 5 to 7.5. Its water flows out under [Fluids](../mechanics/fluids.md#groundwater) like any spring.
- [Terrain](https://github.com/NoNamer777/feudum/issues/60) places brine springs over buried rock salt beds, so a spring hints at rock salt below.
- The wet ground around a spring is a natural salt lick, as [Salt licks](#salt-licks) describes.

### Rock salt

- **Rock salt** is a stone block found in deep beds in some regions, below brine springs. Terrain places the beds.
- It is mined with a pick like other stone, and drops a rock salt block.
- The [quern](https://github.com/NoNamer777/feudum/issues/51) of Foods crushes a rock salt block into about 8 rock salt, as a starting value.
- A rock salt block in water dissolves slowly, as 8 salt, so a flooded mine turns to brine. Rain wears rock salt exposed at the surface slowly, as it does a placed lick.
- Mining rules beyond this belong to whichever design takes up mining.

### Sleeching

- At low tide, sun and wind dry seawater into the silt of the tidal flats, so the bared silt picks up salt. [Tides](https://github.com/NoNamer777/feudum/issues/172) owns the flats and when they lie bare.
- A shovel scrapes the top of a bared flat into **salt silt**, an item that carries the salt it picked up. Rain washes the salt out of salt silt left in the open.
- Washing salt silt with seawater in a **sleeching pit** drains brine at about salinity 4, as a starting value, which is then boiled.
- The washed silt comes out as plain silt and goes back on the flats.
- How much salt bared silt picks up, and how fast, are starting values to tune.

## Seasoning

- Salt seasons a dish by the pinch. A seasoning slot of [Cooking](../mechanics/cooking.md#seasoning) that holds a salt item draws about 10 g of salt for each serving of the batch, as a starting value.
- The rest stays in the slot as a partly used salt item, which shows the weight it has left and seasons the next batch.
- A partly used salt item stacks only with others of the same remaining weight. It seasons and dissolves by the salt it has left.
- Each pinch adds its salt to the salt amount of the dish, which fills the [salt level](../mechanics/hunger.md#salt-level) of Hunger and adds to the [salt load](../mechanics/thirst.md#model) of Thirst.

## Salt licks

People, herds, and deer need salt, as the [salt level](../mechanics/hunger.md#salt-level) of Hunger describes. [ADR 0027](../../adr/0027-salt-is-a-need-as-well-as-a-load.md) records why. A salt-deficient animal seeks a salt lick:

- **Placed lick**: a **salt lick** block pressed from 8 salt of any grade, or a rock salt block set out as it is. A deficient animal walks to it and licks, which fills its salt level and wears the block down by the salt it took.
- Rain wears a placed lick slowly instead of dissolving it at once, as a starting value, so a lick can stand in a pasture.
- **Natural licks**: the wet ground around a brine spring and rock salt exposed at the surface. They draw deficient wild herbivores, so a hunter can wait at one. [Wildlife](https://github.com/NoNamer777/feudum/issues/47) owns how wild animals find and use them.
- A deficient animal with no lick in reach licks salty things nearby instead, as [Hunger](../mechanics/hunger.md#deficiencies) describes. [Animal husbandry](../mechanics/animal-husbandry.md) reads the craving of deficient livestock.

## Uses

Salt and brine serve other designs, and each owns its own step:

| Use               | Takes                       | Owner                                                                              |
|:------------------|:----------------------------|:-----------------------------------------------------------------------------------|
| Dry salting       | Salt                        | [Food preservation](../mechanics/food-preservation.md#salting)                     |
| Brining           | Brine at salinity 3 or more | [Food preservation](../mechanics/food-preservation.md#salting)                     |
| Seasoning         | Salt, by the pinch          | [Cooking](../mechanics/cooking.md#seasoning), as [Seasoning](#seasoning) describes |
| Curing hides      | Brine                       | [Tanning](../mechanics/tanning.md#curing)                                          |
| Tawing            | Salt                        | [Tanning](../mechanics/tanning.md#tawing)                                          |
| Butter and cheese | Salt                        | [Dairy](https://github.com/NoNamer777/feudum/issues/135)                           |
| Quenching steel   | Brine                       | [Smithing](https://github.com/NoNamer777/feudum/issues/86)                         |
| Cleaning wounds   | Brine at salinity 1 or more | [Bandage, splint, and salve](https://github.com/NoNamer777/feudum/issues/125)      |
| Salt glazing      | Salt                        | [Pottery](https://github.com/NoNamer777/feudum/issues/180)                         |

- **Quenching**: brine counts as a quench medium, which cools steel faster and more evenly than plain water. Smithing decides what that does.
- **Cleaning wounds**: brine counts as a mild antiseptic, weaker than the [spirit](../mechanics/brewing.md#distilling) of Brewing. Bandage, splint, and salve decides what it does.
- **Salt glazing**: salt thrown into a stoneware kiln at the peak of the firing fuses with the clay into a thin glaze. Pottery decides the rest.

## Tools and blocks

| Step                | Tool or block                                                        | Kind  |
|:--------------------|:---------------------------------------------------------------------|:------|
| Evaporate           | Salt pan                                                             | Block |
| Boil                | Boiling pan, or the heated cauldron of Cooking                       | Block |
| Rake the crust      | Rake, at a pan, as in [Farming](../mechanics/farming.md)             | Item  |
| Scrape salt silt    | Shovel                                                               | Item  |
| Wash salt silt      | Sleeching pit                                                        | Block |
| Mine rock salt      | Pick                                                                 | Item  |
| Crush rock salt     | Quern, under [Foods](https://github.com/NoNamer777/feudum/issues/51) | Block |
| Feed livestock salt | Salt lick                                                            | Block |

## Vanilla content

- Vanilla has no salt, so there is nothing to hide.

## Data

- The grades, their effect on dry salting, and the salt each item holds are data-driven.
- The pans, the sleeching pit, and the salt lick are data-driven too: their volumes, rates, and yields are starting values to tune.

## Waiting steps

- Salt pans, boiling pans, the sleeching pit, and salt licks are placed blocks that keep their own state.
- Each catches up on the elapsed time when its chunk loads: salt pans through the evaporation of Fluids, boiling pans through the burning of Fire, and salt licks through the rain of Weather.
- The salt that bared silt picks up catches up through the tides of Tides, and the salt level of a body under Hunger.

## Persistence

- Every salt pan, boiling pan, and sleeching pit saves its water through Fluids, its crust amount for each grade, and the time it last caught up.
- Every salt lick saves the salt it has left.
- Every salt silt item saves the salt it carries, and every partly used salt item the salt it has left.

## Query

- One query returns the salt state of a block or item: for a pan or pit, its water volume, salinity, and crust amount for each grade, and for a lick or an item, the salt it holds and its grade.
- Other mechanics read salt through it.

## Commands

- `/feudum salt query [pos]` shows the result of the query.
- `/feudum salt set <pos> <bay|white> <value>` sets the crust amount of a grade, for testing.
- Every `/feudum salt` command requires operator permission.
- The salt level of a body is shown and set through the `/feudum hunger` commands.

## Boundaries

Salt owns the salt item and its grades, how salt converts to and from salinity, dissolving salt, the salt crust, salt pans, boiling pans, brine springs, rock salt, sleeching and salt silt, seasoning by the pinch, and salt licks. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Fluids](../mechanics/fluids.md)**: salinity, brine and saturation, evaporation, groundwater and springs, and how water mixes and flows.
- **[Hunger](../mechanics/hunger.md)**: the salt level, salt deficiency and cramps, and the craving for salt.
- **[Thirst](../mechanics/thirst.md)**: the salt load, and the salt amount of food components.
- **[Weather](../mechanics/weather.md)**: the heat, wind, cloud, and rain that dry and dissolve salt.
- **[Cooking](../mechanics/cooking.md)**: boiling, the heated cauldron, and seasoning slots.
- **[Fire](../mechanics/fire.md)**: the fuel a boiling pan burns.
- **[Food preservation](../mechanics/food-preservation.md)**: dry salting and brining.
- **[Tanning](../mechanics/tanning.md)**: curing hides in brine, and tawing.
- **[Animal husbandry](../mechanics/animal-husbandry.md)**: livestock and their craving at the lick.
- **[Brewing](../mechanics/brewing.md)**: the spirit that cleans wounds better than brine.
- **[Tides](https://github.com/NoNamer777/feudum/issues/172)**: the tidal flats and when they lie bare.
- **[Terrain](https://github.com/NoNamer777/feudum/issues/60)**: where brine springs and rock salt beds generate.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: how wild animals find and use natural licks.
- **[Foods](https://github.com/NoNamer777/feudum/issues/51)**: the quern, and the natural salt amounts of food.
- **[Food quality](https://github.com/NoNamer777/feudum/issues/161)**: what the grade of a seasoning does to taste.
- **[Dairy](https://github.com/NoNamer777/feudum/issues/135)**: salting butter and cheese.
- **[Smithing](https://github.com/NoNamer777/feudum/issues/86)**: the iron boiling pan, and the brine quench.
- **[Bandage, splint, and salve](https://github.com/NoNamer777/feudum/issues/125)**: cleaning wounds with brine.
- **[Pottery](https://github.com/NoNamer777/feudum/issues/180)**: salt glazing.
- **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: trading salt and the price of each grade.
- **[Realm laws](https://github.com/NoNamer777/feudum/issues/102)**: a salt tax.
- **[Inventory](https://github.com/NoNamer777/feudum/issues/83)**: the containers salt is stored in.
- **[Salter](https://github.com/NoNamer777/feudum/issues/181)**: the villager who makes salt.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)** and **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: making salt while a village is unloaded, and drawing salt from its stock.
