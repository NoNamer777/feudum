# Farming

A village eats what its fields give. Wheat and rye go in after the autumn ploughing and stand through the winter, while barley and oats wait for spring. An ox team breaks the heavy clay, and a spade turns the garden behind the house. Every crop grows by the warmth, the rain, the daylight, and the soil it stands in, so a cold spring sets the harvest back and a wet August sprouts the grain in the stook. Each harvest draws its own nutrients from the ground, so a village rotates its crops, rests its fields, and carts out the dung heap to keep them fertile. At harvest the grain is reaped, bound, stooked, carted, threshed, and winnowed before it reaches the granary, and the straw thatches the roofs. Vanilla crops grow on random ticks in any light, wherever there is water nearby, so Feudum replaces them.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Farming covers field crops, garden crops, orchards and vines, and the grass of meadows and pastures. It owns the soil they grow in, how they grow, the work from breaking ground to the threshed harvest, and haymaking up to dry hay.
- [Forestry](https://github.com/NoNamer777/feudum/issues/165) owns timber trees and woodland, and [Wild plants](https://github.com/NoNamer777/feudum/issues/166) the plants that grow without a farmer. Farming takes seed and rootstock from them.
- [Feed trough and hay](https://github.com/NoNamer777/feudum/issues/50) owns the hay item, the hay bale, and the trough, and [Beekeeping](https://github.com/NoNamer777/feudum/issues/128) owns bees.
- [Crop diseases](https://github.com/NoNamer777/feudum/issues/167) owns blights such as rust, smut, and ergot. A crop can carry a blight that lowers its yield or taints its harvest, and Crop diseases decides how.
- [Foods](https://github.com/NoNamer777/feudum/issues/51) owns the food components of the produce, [Textiles](textiles.md) takes over flax and hemp at the pulled stalk, and [Brewing](brewing.md) takes over grain, fruit, and hops for its drinks.

## Working

- A hand step, such as digging, weeding, reaping, or threshing, is done with its tool or at its block by holding the use key, as in [Textiles](textiles.md#working). Work advances by the Feudum time that passed, and stopping keeps what is done.
- A draft step, such as ploughing or harrowing, is done by leading a draft animal or team along the line of work, as [Draft work](animal-husbandry.md#draft-work) describes.
- Farming has no skill: every body works the fields at the same rate, and [Skills](https://github.com/NoNamer777/feudum/issues/43) decides whether that changes.
- Villagers work the same blocks with the same tools at the same rate. Reaping, binding, threshing, winnowing, and haymaking are household work any villager does. [Ploughman](https://github.com/NoNamer777/feudum/issues/168) and [Gardener](https://github.com/NoNamer777/feudum/issues/169) plan the villagers who plough the fields and keep the gardens, the [Reeve](https://github.com/NoNamer777/feudum/issues/58) oversees the work, and the [Hayward](https://github.com/NoNamer777/feudum/issues/57) guards the crops.
- [Village economy](https://github.com/NoNamer777/feudum/issues/44) owns the duty side of the work: the week work and boon days owed on the lord's demesne, and hired mowers and threshers.
- [Tools and blocks](#tools-and-blocks) lists what each step needs.

## Model

A crop grows by the conditions at its block, and the tilled soil under it carries three nutrients and an acidity. [ADR 0025](../../adr/0025-crops-grow-by-the-conditions-at-their-block.md) records why.

- A crop is a block. It stores its growth progress, its damage, and the time it last caught up.
- Each crop follows a **crop profile**: its growth stages, the ranges of temperature, soil moisture, and acidity it grows in, its frost tolerance, its demand for each nutrient, its seed rate, and its yield. Crop profiles are data-driven, so a data pack can add crops.
- Growth progress builds up with Feudum time, at a rate the [growth conditions](#growth-conditions) set. Random ticks play no part.
- A crop catches up when its chunk loads, by sampling the [Weather](weather.md#query) query over the time that passed. It steps one hour at a time over the last 7 days and one day at a time before that, as catch-up does under [Time](time.md#unloaded-villages).
- Every span in a crop profile is a share of the year, as in [Animal husbandry](animal-husbandry.md#species). A year has 96 days at the default calendar, so a real month is about 8 days. Changing the days per sub-season stretches every crop with it, so the farming year holds. Farming adds no per-world setting of its own.

### Growth conditions

- **Temperature**: the local temperature of [Weather](weather.md#local-temperature). Growth is fastest inside the crop's range and slows toward its edges.
- **Soil moisture**: as [Moisture](#moisture) describes. Growth is fastest inside the crop's band.
- **Nutrients and acidity**: the scarcest nutrient, measured against the crop's demand, caps the growth rate, as [Nutrients](#nutrients) describes.
- **Daylight**: the daylight curve of [Time](time.md#seasons-and-climate). Crops grow only under open sky. Torchlight and covered blocks grow nothing, so there is no farming underground or indoors.

Sowing seasons follow from these conditions, not from fixed windows. A seed can be sown at any time, and whether it comes up and lives depends on the temperature, its frost tolerance, and the moisture. The player learns the farming calendar from the crops themselves.

### Stages

- Each crop profile names its growth stages, from Sown to **Ripe**. A crop that stays in the field past Ripe turns **Overripe**:
  - Overripe grain sheds its grain, and its yield falls each day.
  - Overripe fruit drops as windfalls, which spoil.
  - Roots left in the ground keep for a while, then rot.
- A crop reaped before Ripe gives a low yield, and seed saved from it doesn't sprout.
- Winter-sown crops, such as wheat and rye, sprout in autumn and go **dormant** through the cold. A dormant crop doesn't grow and survives hard frost.
- Frost tolerance has three labels. Starting values to tune:

| Frost tolerance | Survives                  |
|:----------------|:--------------------------|
| Tender          | No frost                  |
| Hardy           | Light frost               |
| Winter-hardy    | Hard frost, while dormant |

### Stress

- Outside its ranges, short of its limits, a crop grows more slowly.
- Past a limit, it takes damage: frost below its tolerance, heat beyond its range, and Parched or Waterlogged soil for days on end.
- Damage lowers the yield at harvest. Past a threshold, it kills the crop, which turns into dead stalks.
- [Weather damage](#weather-damage) adds lodging, sprouting, floods, and fire.

## Soil

### Texture

Every column carries a **soil texture**, which [Terrain](https://github.com/NoNamer777/feudum/issues/60) generates from the seed alone. Starting values to tune:

| Texture | Drainage              | Nutrient baseline | Acidity | Workability                            |
|:--------|:----------------------|:------------------|:--------|:---------------------------------------|
| Sand    | Fast: dries out first | Low               | Neutral | Light: any tool                        |
| Loam    | Moderate              | High              | Neutral | Light: any tool                        |
| Clay    | Slow: waterlogs first | High              | Neutral | Heavy: the heavy plough or a hand tool |
| Peat    | Slow: holds water     | Low               | Sour    | Light, but waterlogs                   |

- Where a village sits decides what its fields can grow, and what work they take.

### Moisture

Soil moisture is computed from the place and the recent weather, as the [dryness](fire.md#dryness) of Fire is, and never stored. It follows from:

- Recent precipitation.
- Evaporation, by the local temperature, the wind, and the cloud cover of [Weather](weather.md#query).
- The drainage of the soil texture.
- The depth of the [water table](fluids.md#groundwater) of Fluids. A shallow table keeps the soil moist through a dry spell.
- Open water nearby.

Soil moisture has five labels. Each crop profile sets its preferred band, which for most crops is Moist:

| Moisture    | Ground                        |
|:------------|:------------------------------|
| Waterlogged | Standing wet, and roots drown |
| Wet         | Soaked after rain             |
| Moist       | Damp to the touch             |
| Dry         | Dusty on top                  |
| Parched     | Cracked                       |

- An **irrigation ditch** of real [Fluids](fluids.md#volume) water raises the moisture of tilled soil within about 3 blocks by one label, as a starting value. It draws a slow volume from the ditch, so a ditch fed by a stream keeps a field watered through a Dry season, and a ditch fed by nothing runs dry.

### Nutrients

Tilled soil carries three **nutrients**: nitrogen, phosphorus, and potassium.

- Each crop profile sets a demand for each nutrient. Harvesting a crop removes its demand from the soil it grew in.
- The scarcest nutrient, measured against the crop's demand, caps its growth rate and its yield. Plenty of one nutrient doesn't make up for a lack of another.
- Grain draws hardest on nitrogen, roots on potassium, and legumes take almost no nitrogen.

Sources and losses, as starting values to tune:

| Source or loss                      | Nitrogen        | Phosphorus      | Potassium       |
|:------------------------------------|:----------------|:----------------|:----------------|
| Manure                              | Raises          | Raises          | Raises          |
| Fresh dung and night soil           | Raises most     | Raises some     | Raises some     |
| Legume roots left in the ground     | Raises          | None            | None            |
| Wood ash, burnt stubble             | None            | Raises some     | Raises most     |
| Crushed bone                        | None            | Raises most     | None            |
| Stubble and weeds ploughed in       | Raises a little | Raises a little | Raises a little |
| Rain on bare soil                   | Lowers          | None            | None            |
| Fallow, toward the texture baseline | Slowly          | Slowly          | Slowly          |

- Manure is spread from the [dung heap](relief.md#dung-heap) of Relief, and fresh dung and night soil from wherever [Relief](relief.md#waste) leaves them.
- Rain on bare soil **leaches** nitrogen. Sand leaches fastest, and clay slowest.
- A fallow field recovers toward the nutrient baseline of its texture. Livestock grazing it speeds that up through the dung it leaves.
- Rotating crops and resting fields follow from these rules, with no rotation rule of their own. A village that grows wheat on the same strip every year watches its yield fall.

### Acidity

Tilled soil also carries an **acidity**, which sets how much of each nutrient a crop can draw. It has three labels: Sour, Neutral, and Sweet.

- Soil texture sets the starting acidity: peat is Sour, and the rest Neutral.
- Each crop profile carries an acidity range. Soil outside it cuts how much of every nutrient the crop can draw, so manure on a Sour field helps a barley crop little.
- **Marl**, **lime**, and wood ash sweeten the soil over years. Rain and harvests slowly sour it again.
- Rye and oats tolerate Sour soil, while barley and the legumes need Neutral or Sweet ground.
- Terrain places marl, which is dug from marl pits. Lime is burned in a lime kiln, which [Buildings](https://github.com/NoNamer777/feudum/issues/29) owns with lime mortar.

### Reading the soil

Players read the soil from the crops and the ground, never from a meter:

- A crop short of nitrogen yellows.
- A crop short of phosphorus purples and stays stunted.
- A crop short of potassium browns at the leaf edges.
- A crop on soil outside its acidity range shows the same signs, and manure doesn't cure them.
- Moist soil looks dark, Dry soil pale, and Parched soil cracked.
- Yield shows the rest, and a field's history is the only record of what it was given.

### Tilled soil

- Each block of tilled soil stores its three nutrient levels and its acidity.
- Untouched ground stores nothing: its levels come from the baseline of its texture.
- Tilled soil left unworked for about a year reverts to grass and stops storing anything, as a starting value.

## Breaking ground

Tilled soil comes from four tools. Starting values to tune:

| Tool         | Pulled by      | Suits                                | Speed   |
|:-------------|:---------------|:-------------------------------------|:--------|
| Spade        | A body         | Any soil, in small plots and gardens | Slow    |
| Mattock      | A body         | Any soil, in new or stony ground     | Slowest |
| Ard          | A draft animal | Sand, loam, and peat                 | Fast    |
| Heavy plough | A team of oxen | Any soil, clay included              | Fastest |

- A plough cuts a straight strip, one block wide, along its line of draft, and turns at the **headland** at the end of the strip.
- An ard only scratches clay, so the soil stays poorly tilled and crops sown on it come up thin.
- Ploughing grass breaks the sward and turns it into tilled soil. Ploughing tilled soil again buries weeds and stubble, which feeds the soil, as [Nutrients](#nutrients) describes.
- A **harrow**, drawn by a draft animal, breaks the clods and covers sown seed.
- A **garden** is no separate mechanic. It is tilled soil worked by hand, usually fenced and near a house, under the same rules as a field: it is dug with the spade and set with the dibber, where a field is ploughed and broadcast.

## Sowing

- Grain, flax, and hemp are **broadcast**: throwing seed from a seed basket sows a patch of tilled blocks in front of the sower, each at the seed rate of its crop.
- Garden crops, legumes, saplings, and cuttings are **set** one block at a time, with a dibber or by hand.
- Birds take part of the seed left uncovered on the surface. Harrowing after sowing covers it.
- A seed sprouts by its spoilage stage under [Food preservation](food-preservation.md#keeping-time). Starting values to tune:

| Seed stage | Sprouts    |
|:-----------|:-----------|
| Fresh      | All        |
| Stale      | About half |
| Spoiled    | None       |

### Seed

- Grain and pulses are their own seed, so a household eats and sows from one store, and seed grain keeps as long as grain does.
- The biennials set seed only when left in the ground through winter to flower in their 2nd year, so a garden keeps a few plants back for seed.
- Flax and hemp seed come from rippling, as [Textiles](textiles.md#bast-fibers) describes.
- Herbs and annual vegetables set seed when left to run past Ripe.
- Seed also comes from [Wild plants](https://github.com/NoNamer777/feudum/issues/166) and from trade under [Village economy](https://github.com/NoNamer777/feudum/issues/44).
- Grain yields about 4 measures for each one sown, in a good year on good ground, and 2 or less in a bad one. Starting values to tune.

## Crops

Farming grows the crops of the medieval Old World. No New World crop grows in Feudum: no potato, maize, pumpkin, tomato, or cocoa. The tables give the starting set as starting values to tune, for the temperate climate profile at the default calendar. The growth conditions shift every span.

### Field crops

| Crop        | Group   | Sown         | Ripe         | Frost        | Acidity       | Draws most |
|:------------|:--------|:-------------|:-------------|:-------------|:--------------|:-----------|
| Wheat       | Grain   | Mid Autumn   | Late Summer  | Winter-hardy | Neutral       | Nitrogen   |
| Rye         | Grain   | Early Autumn | Mid Summer   | Winter-hardy | Sour–Neutral  | Nitrogen   |
| Barley      | Grain   | Mid Spring   | Late Summer  | Hardy        | Neutral–Sweet | Nitrogen   |
| Oats        | Grain   | Early Spring | Late Summer  | Hardy        | Sour–Neutral  | Nitrogen   |
| Millet      | Grain   | Late Spring  | Late Summer  | Tender       | Neutral       | Nitrogen   |
| Peas        | Legume  | Early Spring | Mid Summer   | Hardy        | Neutral–Sweet | Phosphorus |
| Broad beans | Legume  | Early Spring | Mid Summer   | Hardy        | Neutral–Sweet | Potassium  |
| Lentils     | Legume  | Mid Spring   | Late Summer  | Hardy        | Neutral–Sweet | Phosphorus |
| Vetch       | Legume  | Early Spring | Early Summer | Hardy        | Neutral       | Phosphorus |
| Flax        | Fiber   | Mid Spring   | Mid Summer   | Hardy        | Neutral       | Potassium  |
| Hemp        | Fiber   | Late Spring  | Early Autumn | Tender       | Neutral       | Nitrogen   |
| Hops        | Brewing | Perennial    | Early Autumn | Winter-hardy | Neutral       | Nitrogen   |

- Millet suits warm, dry climates, where the other grains struggle.
- Vetch is grown as fodder for livestock.
- Flax and hemp are pulled, not reaped, and [Textiles](textiles.md#bast-fibers) takes them from the pulled stalk.

### Garden crops

| Crop    | Life      | Sown         | Harvested    | Frost        | Draws most |
|:--------|:----------|:-------------|:-------------|:-------------|:-----------|
| Cabbage | Biennial  | Mid Spring   | Early Autumn | Hardy        | Nitrogen   |
| Onion   | Biennial  | Early Spring | Late Summer  | Hardy        | Potassium  |
| Leek    | Biennial  | Mid Spring   | Into winter  | Winter-hardy | Nitrogen   |
| Garlic  | Annual    | Mid Autumn   | Mid Summer   | Winter-hardy | Potassium  |
| Turnip  | Biennial  | Early Summer | Mid Autumn   | Hardy        | Potassium  |
| Parsnip | Biennial  | Early Spring | Late Autumn  | Winter-hardy | Potassium  |
| Carrot  | Biennial  | Mid Spring   | Early Autumn | Hardy        | Potassium  |
| Beet    | Biennial  | Mid Spring   | Early Autumn | Hardy        | Potassium  |
| Lettuce | Annual    | Early Spring | Late Spring  | Hardy        | Nitrogen   |
| Skirret | Perennial | Early Spring | Mid Autumn   | Winter-hardy | Potassium  |

- Garden crops grow in Neutral soil, and the cabbages and beets in Sweet soil too.
- Leeks and parsnips stand in the ground through winter and are lifted as they are needed.

### Herbs, dye plants, and teasel

| Crop    | Life      | Harvested part                   | Use                                                                     |
|:--------|:----------|:---------------------------------|:------------------------------------------------------------------------|
| Parsley | Biennial  | Leaves                           | Cooking                                                                 |
| Sage    | Perennial | Leaves                           | Cooking and [remedies](https://github.com/NoNamer777/feudum/issues/155) |
| Thyme   | Perennial | Leaves                           | Cooking and remedies                                                    |
| Mint    | Perennial | Leaves                           | Cooking and remedies; spreads into neighboring blocks                   |
| Fennel  | Perennial | Leaves and seed                  | Cooking and remedies                                                    |
| Dill    | Annual    | Leaves and seed                  | Cooking                                                                 |
| Mustard | Annual    | Seed                             | Cooking                                                                 |
| Woad    | Biennial  | Leaves, in its 1st year          | Blue dye, under [Textiles](textiles.md#dyes)                            |
| Madder  | Perennial | Roots, from its 2nd year         | Red dye; the longer it stays, the more it gives                         |
| Weld    | Biennial  | The whole plant, in its 2nd year | Yellow dye                                                              |
| Teasel  | Biennial  | Heads, in its 2nd year           | The teasel frame of [Textiles](textiles.md#tools-and-blocks)            |

### Perennials

- A perennial lives for years in its block. It goes dormant over winter and grows again each spring.
- Hops grow from a **crown** that sends up **bines** each spring. The bines climb hop poles, and are cut at harvest while the crown lives on.

## Weeds

- Weeds spread onto tilled soil from the grass and the weeds around it, and grow by a profile of their own.
- A weed takes nutrients and moisture from the crops around it, so an unweeded field yields far less.
- Weeding with a hoe or a weeding hook removes weeds. Weeds left to seed spread to the blocks around them.
- Ploughing buries the weeds of a field, as [Breaking ground](#breaking-ground) describes.

## Trampling

- A body that moves through a standing crop damages it, more the larger it is: a cow does more harm than a child, and a cart or a plough team more than a cow.
- A body that sneaks through does no harm.
- Paths and headlands between the strips keep a field whole.
- Livestock that wanders into crops is a stray, which the Hayward impounds, as [Strays](animal-husbandry.md#strays) describes.
- Tilled soil never turns back to dirt when a body jumps on it.

## Weather damage

- **Frost and heat**: as [Stress](#stress) describes.
- **Lodging**: from Gale up, ripe or nearly ripe grain is flattened. A lodged crop is slower to reap and loses part of its yield.
- **Sprouting**: rain for days on ripe grain, or on sheaves in the stook, sprouts the grain in the ear. Sprouted grain is spoiled for seed and for malt.
- **Floods**: a crop under the standing water of a [flood](fluids.md#rivers) drowns after about a day.
- **Snow**: snow cover shelters winter crops from frost.
- **Fire**: a burning crop turns to air, with the crop lost, as [Burnt forms](fire.md#burnt-forms) describes. Ripe grain and stooks in a dry summer catch readily.
- Hail and other extreme events wait for [Extreme weather](https://github.com/NoNamer777/feudum/issues/31).

## Harvest

- Grain is reaped with a sickle, or mown with a scythe, which is faster and loses more grain.
- Peas, beans, and lentils dry on the plant, and are cut and threshed like grain.
- Roots are lifted with a spade, and vegetables, herbs, and fruit are picked by hand.

### Grain

Grain follows this chain from the field to the granary:

1. **Bind**: the reaped stalks are bound into sheaves.
2. **Stook**: the sheaves are stood in stooks in the field to dry, which takes about 2 Feudum days of dry weather.
3. **Cart**: the dry sheaves are carted to the barn, under [Carts and wagons](https://github.com/NoNamer777/feudum/issues/141).
4. **Thresh**: the sheaves are beaten with a flail on a threshing floor, which gives grain, straw, and chaff.
5. **Winnow**: the grain is tossed in the draft between two open barn doors, or with a winnowing fan, which carries the chaff away.

Threshing fills the winter in the barn, since the sheaves keep until they are threshed. [Food preservation](food-preservation.md) owns how grain keeps, and Buildings the barn and the granary.

### By-products

| By-product | From      | Use                                                                                             |
|:-----------|:----------|:------------------------------------------------------------------------------------------------|
| Straw      | Threshing | Thatch, bedding for the [dung heap](relief.md#dung-heap), fodder, and [kindling](fire.md#fuels) |
| Chaff      | Winnowing | Fodder                                                                                          |
| Stubble    | Reaping   | Grazing, burning, or ploughing in                                                               |

- Burning stubble returns potassium to the soil, and risks spreading, as [Fire](fire.md#spread) describes.

## Pasture and hay

- Each grass block carries a **sward height**. Grazing lowers it, as the feeding goal of [Hunger](hunger.md#animals) describes.
- The sward regrows by the season curve: fast in spring, slow in high summer and autumn, and not at all in winter or under snow.
- A sward grazed down to bare earth is slow to recover.
- A **meadow** mown with a scythe gives cut grass, which dries on the ground into hay over about 2 dry Feudum days. Turning it with a rake speeds the drying.
- Rain on curing hay soaks it, so it takes longer to dry and loses part of its food value.
- Dry hay becomes the hay item of [Feed trough and hay](https://github.com/NoNamer777/feudum/issues/50).

## Orchards and vines

- Fruit trees are **grafted**: a **scion** cut from a tree of a known variety is joined onto a **rootstock** with a grafting knife, and the tree bears the scion's variety. Rootstock comes from wild seedlings, such as a crab apple, from [Wild plants](https://github.com/NoNamer777/feudum/issues/166), or from pips raised in the garden.
- A tree grown from seed gives wild fruit.
- A tree or a vine bears from about its 2nd Feudum year, and reaches full yield in about its 5th, as starting values. At the default day length, a 2-year wait is about 128 hours of play.
- Blossom in spring is frost-sensitive, so a late frost loses the year's fruit.
- Fruit ripens through late summer and autumn. It is picked by hand, or shaken down onto a cloth.
- Pruning with a pruning hook in winter raises the next year's yield. An unpruned tree or vine bears less each year.
- Vines grow from rooted cuttings, need a stake to climb, and are pruned in winter like trees.
- Grapes grow only where the climate profile of [Time](time.md#seasons-and-climate) is warm enough.
- Fruit trees and vines bear without bees. [Beekeeping](https://github.com/NoNamer777/feudum/issues/128) may add a yield bonus near hives.

| Fruit  | Blossom      | Ripe         |
|:-------|:-------------|:-------------|
| Cherry | Early Spring | Early Summer |
| Plum   | Early Spring | Late Summer  |
| Pear   | Early Spring | Early Autumn |
| Apple  | Mid Spring   | Early Autumn |
| Quince | Mid Spring   | Mid Autumn   |
| Medlar | Late Spring  | Late Autumn  |
| Grape  | Late Spring  | Early Autumn |

## Pests

- Birds take seed left uncovered on sown ground, as [Sowing](#sowing) describes.
- [Vermin](https://github.com/NoNamer777/feudum/issues/136) owns everything else that eats crops: rats and mice in the stores, rabbits and pigeons in the field, and scarecrows and the other deterrents.
- [Wildlife](https://github.com/NoNamer777/feudum/issues/47) owns deer and boar in the fields.

## Cues

- Players read a crop from the world, never from a meter or a timer.
- A crop shows its stage in its block, and turns its ripe color at Ripe.
- A crop shows its nutrient shortages, as [Reading the soil](#reading-the-soil) describes.
- A crop short of water wilts, and a frost-damaged crop blackens at the leaves.
- A lodged crop lies flat, and sprouted grain shows green shoots in the ear.
- The tooltip of seed shows its spoilage stage, as Food preservation does for every organic item.

## Unloaded chunks

- Crops, weeds, the sward, and the nutrients of tilled soil catch up when their chunk loads, as [Model](#model) describes.
- [Village simulation](https://github.com/NoNamer777/feudum/issues/45) decides how villagers work the fields of an unloaded village during each catch-up step.

## Tools and blocks

| Use                    | Tool or block                | Made of                                                                             |
|:-----------------------|:-----------------------------|:------------------------------------------------------------------------------------|
| Break ground           | Spade, mattock               | Wood and iron, from [Smithing](https://github.com/NoNamer777/feudum/issues/86)      |
| Plough                 | Ard, heavy plough            | Wood, from [Carpentry](https://github.com/NoNamer777/feudum/issues/115); iron share |
| Harrow                 | Harrow                       | Wood, from Carpentry                                                                |
| Sow                    | Seed basket, dibber          | Wicker; wood                                                                        |
| Weed                   | Hoe, weeding hook            | Wood and iron                                                                       |
| Reap and mow           | Sickle, scythe               | Wood and iron                                                                       |
| Turn hay, lift sheaves | Rake, pitchfork              | Wood; wood and iron                                                                 |
| Dry sheaves            | Stook                        | Sheaves stood in the field                                                          |
| Thresh                 | Flail, threshing floor       | Wood and leather; packed earth or planks                                            |
| Winnow                 | Winnowing fan                | Wicker                                                                              |
| Prune and graft        | Pruning hook, grafting knife | Wood and iron                                                                       |
| Support climbers       | Hop pole, vine stake         | Wood, from [Forestry](https://github.com/NoNamer777/feudum/issues/165)              |
| Water fields           | Irrigation ditch             | A trench holding water                                                              |
| Feed the soil          | Crushed bone, marl, lime     | Bone; marl from Terrain; lime from a lime kiln                                      |

- [Tack and barding](https://github.com/NoNamer777/feudum/issues/139) owns the harness that hitches a draft animal to the ard, the plough, and the harrow.
- Farm tools override their default attack profile from [Weapons](../content/weapons.md#attack-profiles). All of them stay weak against armor, and the scythe is clumsy as a weapon, unlike a war scythe:

| Tool           | Damage kind |
|:---------------|:------------|
| Sickle, scythe | Cut         |
| Pitchfork      | Pierce      |
| Flail, mattock | Blunt       |

## Vanilla content

- Wheat, carrots, potatoes, beetroot, melons, pumpkins, sugar cane, cocoa, sweet berries, glow berries, the torchflower, and the pitcher plant stay hidden, with their seeds and their foods.
- Farmland and the vanilla hoes stay hidden, and Feudum's tilled soil and tools replace them.
- The composter stays hidden; waste goes on the [dung heap](relief.md#dung-heap) of Relief.
- Bone meal no longer makes anything grow. Crushed bone replaces it and adds phosphorus to the soil.
- Vanilla trees and saplings stay hidden, under [Forestry](https://github.com/NoNamer777/feudum/issues/165). Farming grows its own fruit trees and vines.

## Persistence

- Every crop saves its crop profile, growth progress, stage, damage, age for a perennial or a biennial, and the time it last caught up.
- Every block of tilled soil saves its three nutrient levels, its acidity, its weeds, and the time it was last worked.
- A grass block that has been grazed or mown saves its sward height and the time it last caught up. Untouched grass saves nothing.
- Stooks and curing hay save their drying progress.
- Fruit trees and vines save their variety, age, and pruning.
- Soil moisture is computed from the weather, so it is never saved.

## Query

- One query returns the soil state at a position: its texture, moisture, three nutrient levels, and acidity, and any crop there with its stage and damage.
- Other mechanics read farming through this query.

## Commands

- `/feudum farm soil <pos>` shows the soil state at a position.
- `/feudum farm grow <pos> <stage>` sets the stage of a crop, to test harvests.
- `/feudum farm moisture <pos> [label] [duration]` overrides the soil moisture at a position, to test droughts and waterlogging. Without a label, it shows the current moisture.
- Every `/feudum farm` command requires operator permission.

## Boundaries

Farming owns crops, crop profiles, growth and its conditions, stages, dormancy, frost tolerance, and stress, soil texture as it is farmed, soil moisture and irrigation, nutrients, acidity, and tilled soil. It also owns breaking ground, the ard, the heavy plough, and the harrow, sowing and seed, the crop roster, perennials, weeds, trampling, and weather damage to crops. Harvest, the grain chain, straw, chaff, and stubble, the sward and haymaking up to dry hay, orchards, vines, and grafting, and the cues of crops are its own as well. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Time](time.md)**: the calendar, the season curves, daylight, and climate profiles.
- **[Weather](weather.md)**: the local temperature, precipitation, wind, snow cover, and lightning.
- **[Fluids](fluids.md)**: the water table, irrigation water, and floods.
- **[Fire](fire.md)**: fire in the fields, and burnt stubble.
- **[Relief](relief.md)**: dung, night soil, and the dung heap that makes manure.
- **[Food preservation](food-preservation.md)**: how seed, grain, and produce keep.
- **[Hunger](hunger.md)**: the feeding goal that grazes the sward, and the food groups of fodder.
- **[Animal husbandry](animal-husbandry.md)**: draft animals, grazing livestock, and strays.
- **[Brewing](brewing.md)**: malting grain, pressing fruit, and hopping beer.
- **[Textiles](textiles.md)**: flax and hemp from the pulled stalk, dyestuffs, and the teasel frame.
- **[Cooking](cooking.md)**: what grain, pulses, and vegetables become in the kitchen.
- **[Weapons](../content/weapons.md)**: the default attack profiles that farm tools override.
- **[Terrain](https://github.com/NoNamer777/feudum/issues/60)**: soil texture and marl, from the seed alone.
- **[Forestry](https://github.com/NoNamer777/feudum/issues/165)**: timber trees, woodland, and the wood of poles and stakes.
- **[Wild plants](https://github.com/NoNamer777/feudum/issues/166)**: wild seed and rootstock.
- **[Crop diseases](https://github.com/NoNamer777/feudum/issues/167)**: rust, smut, ergot, and other blights.
- **[Foods](https://github.com/NoNamer777/feudum/issues/51)**: the food components of the produce.
- **[Herbal remedies](https://github.com/NoNamer777/feudum/issues/155)**: what herbs do as remedies.
- **[Feed trough and hay](https://github.com/NoNamer777/feudum/issues/50)**: the hay item, the hay bale, and the trough.
- **[Dung and manure](https://github.com/NoNamer777/feudum/issues/72)**: the waste items that are spread on fields.
- **[Buildings](https://github.com/NoNamer777/feudum/issues/29)**: the barn, the granary, thatch, and the lime kiln.
- **[Carts and wagons](https://github.com/NoNamer777/feudum/issues/141)**: carting the harvest.
- **[Tack and barding](https://github.com/NoNamer777/feudum/issues/139)**: the harness of draft animals.
- **[Smithing](https://github.com/NoNamer777/feudum/issues/86)** and **[Carpentry](https://github.com/NoNamer777/feudum/issues/115)**: the iron and wooden parts of tools.
- **[Vermin](https://github.com/NoNamer777/feudum/issues/136)** and **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: the animals that eat crops.
- **[Beekeeping](https://github.com/NoNamer777/feudum/issues/128)**: any yield bonus from bees.
- **[Extreme weather](https://github.com/NoNamer777/feudum/issues/31)**: hail and other extreme events.
- **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: labor services, hired labor, seed trade, and who holds which strip.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: farm work in an unloaded village.
- **[Ploughman](https://github.com/NoNamer777/feudum/issues/168)**, **[Gardener](https://github.com/NoNamer777/feudum/issues/169)**, **[Reeve](https://github.com/NoNamer777/feudum/issues/58)**, and **[Hayward](https://github.com/NoNamer777/feudum/issues/57)**: the villagers who farm and guard the fields.
- **[Skills](https://github.com/NoNamer777/feudum/issues/43)**: whether farming takes a skill.

World generation must offer soil texture from the seed alone, as [ADR 0025](../../adr/0025-crops-grow-by-the-conditions-at-their-block.md) records.
