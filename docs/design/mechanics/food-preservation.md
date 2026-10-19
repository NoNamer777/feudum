# Food preservation

Everything a village grows, hunts, or shears starts to spoil the day it is taken. Fish keeps a couple of days and fresh meat a few more, while grain in a dry granary keeps for years. Warmth and wet speed the rot, so a village slaughters in the cold, keeps its stores in a cellar, and roofs its hay. What it can't eat in time it salts, smokes, dries, pickles, pots under fat, or packs in honey, each at about its historical pace. A winter on salt pork and stockfish still runs short of fruit unless the cellar holds apples. Vanilla food never spoils, so Feudum adds spoilage of its own.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Every organic item spoils: food, fodder, raw hides, raw fleece, cut plant stalks and herbs, seeds, saplings and cuttings, eggs, and carcasses. [ADR 0018](../../adr/0018-every-organic-item-spoils.md) records why.
- Processing that stabilized a material historically, such as tanning, spinning, or seasoning, ends its spoilage. Wood, planks, leather, thread, rope, cloth, felt, bone, horn, feathers, wax, and anything fired or smelted keep forever.
- [Brewing](brewing.md#keeping-and-souring) owns how drinks keep, [Textiles](textiles.md#retting) owns retting and over-retting, and [Tanning](tanning.md) owns curing hides and stops their spoilage once tanning starts.
- A per-world setting sets how fast items spoil: `off`, `slow` (half rate), or `normal`. The default is `normal`.

## Working

- A hand step is done at its block by holding the use key, as in [Brewing](brewing.md#working). Work advances by the Feudum time that passed, and stopping keeps what is done.
- A waiting step is a placed block that keeps its own progress, as [Waiting steps](#waiting-steps) describes.
- Preserving is household work that any villager does, at the same blocks and the same rate as a player. [Villagers](https://github.com/NoNamer777/feudum/issues/46) decides when a household preserves, and the [Larderer](https://github.com/NoNamer777/feudum/issues/137) keeps the larder and cellar of a manor.

## Keeping time

- Every organic item carries a keeping time: how long it lasts at 10 °C and dry before it rots. Its remaining keeping time runs down with Feudum time, at the rate that [Rate](#rate) sets.
- The used share of its keeping time sets its stage. Starting values to tune:

| Stage   | Used share | Effect                                                                     |
|:--------|:-----------|:---------------------------------------------------------------------------|
| Fresh   | 0–50%      | Its full food component.                                                   |
| Stale   | 50–80%     | 75% of its energy and 50% of its group amounts.                            |
| Spoiled | 80–100%    | 50% of its energy and 25% of its group amounts, and a foul load.           |
| Rotten  | Past 100%  | Turns into its rotten version, as [Rotten items](#rotten-items) describes. |

- Eating Spoiled food adds to the [foul load](thirst.md#model) of Thirst, as foul water does. [Illness](illness.md#foul-load) decides what the foul load does.
- For an item that isn't food, Stale and Spoiled lower what it yields: a Stale hide gives less leather, and a Spoiled seed may not sprout. The design that uses the item sets how much, such as Tanning for hides and [Farming](farming.md#sowing) for seeds.
- Two stacks of the same item merge only when their remaining keeping times round to the same Feudum hour, so a field harvested in one go stacks, and food from different days stays apart. The hour is a starting value to tune.
- Food placed as a block, such as a pie or a hay bale, spoils by the same rules, and so does an item dropped on the ground. Crops still growing in the field don't spoil; Farming decides what happens to them.

## Starting keeping times

Starting values to tune, at 10 °C and dry:

| Item                                                                                                            | Keeps          |
|:----------------------------------------------------------------------------------------------------------------|:---------------|
| Fresh fish, milk, raw hides, fresh herbs, soft fruit, leafy greens                                              | About 2 days   |
| Fresh meat, carcasses                                                                                           | About 4 days   |
| Bread, saplings, cuttings, hot-smoked food                                                                      | About 1 week   |
| Eggs                                                                                                            | About 2 weeks  |
| Apples, pears, roots, onions, cabbages, flour, potted meat, smoked herring                                      | About a season |
| Raw fleece, seeds, hay, salted food, pickles, sauerkraut, honey preserves, dried fruit, dried meat, dried herbs | About a year   |
| Grain, dried peas and beans, stockfish                                                                          | Years          |
| Honey                                                                                                           | Forever        |

- Items made by a chain of methods, such as ham and bacon, keep longer than any step alone, as [Chains](#chains) describes.
- [Dairy](https://github.com/NoNamer777/feudum/issues/135) sets the keeping times of butter and cheese.

## Rate

### Temperature

- Spoilage runs at 1× at 10 °C. It doubles with every 10 °C warmer and halves with every 10 °C colder, down to 0 °C. Starting values to tune:

| Temperature | Rate   |
|:------------|:-------|
| Below 0 °C  | Frozen |
| 0 °C        | 0.5×   |
| 10 °C       | 1×     |
| 20 °C       | 2×     |
| 30 °C       | 4×     |

- Below 0 °C food freezes and stops spoiling. Thawed food spoils at the normal rate again, with no penalty.
- The rate reads the temperature where the item sits: the [room temperature](body-temperature.md#shelter-and-heat) of an enclosed space, the [cave temperature](body-temperature.md#felt-temperature) below the surface, and the [local temperature](weather.md#local-temperature) of Weather in the open.
- An item in a body's inventory reads the temperature around that body, never the body's own heat.
- A summer kitchen at 25 °C spoils meat almost three times as fast as a cellar at 10 °C, and winter is the slaughter season.

### Wetness

- A wet item spoils at twice the rate. Grain and hay go moldy, which is why hay needs a roof and grain a dry granary.
- An item gets wet in the rain in the open, in water, or in a container that lets the rain in. It dries again with warmth, sun, and wind.

### Containers

| Container         | Effect                                                     |
|:------------------|:-----------------------------------------------------------|
| Sack              | None.                                                      |
| Basket            | None, and it lets air through, so wet contents dry faster. |
| Barrel            | Sealed.                                                    |
| Earthenware crock | Sealed.                                                    |

- A sealed container keeps out rain, water, and [vermin](https://github.com/NoNamer777/feudum/issues/136). A sack or basket standing in the rain lets the rain in.
- Pickles, potted meat, and honey preserves need a sealed container: taken out, they keep only a few days.
- General storage, such as chests, belongs to [Inventory](https://github.com/NoNamer777/feudum/issues/83), and casks to [Drink containers](https://github.com/NoNamer777/feudum/issues/49).

## Cold storage

- **Cellar**: any enclosed room below the surface. Its room temperature settles toward the cave temperature, so an unheated cellar stays cool in summer and above freezing in winter. A cellar needs no block of its own; [Body temperature](body-temperature.md#shelter-and-heat) owns the rule.
- **Ice house**: an enclosed room holding ice or packed snow, which are cold sources under Body temperature. It holds near freezing well into summer, as long as the ice lasts. [Snow and ice](https://github.com/NoNamer777/feudum/issues/53) decides how fast the ice melts.
- Brewing reads the same room temperature for fermenting and souring, so a cellar keeps ale as well as food.

## Methods

Each method turns a food into a new item with its own food component and keeping time, such as fresh pork into salt pork. [Foods](https://github.com/NoNamer777/feudum/issues/51) lists the preserved foods, and this page sets the rules that make them.

The diagram maps each kind of food to the methods that keep it, and shows the chains that combine two methods. Each arrow stands for one method and is labeled with it, and all three arrows into pickles are pickling in vinegar. Raw foods have a light fill, and preserved foods are bold.

![Each kind of raw food and the preserved foods it becomes. Meat is dry salted into salt meat, dried into dried meat, potted under fat into potted meat, and hot smoked into hot-smoked meat. Salt meat is cold smoked into ham and bacon. Fish is salted or brined into salt fish, cold smoked into smoked herring, dried in cold wind into stockfish, and pickled. Salt fish is cold smoked into red herring. Eggs and vegetables are pickled in vinegar, and vegetables are brined into sauerkraut and salted beans. Fruit is dried into dried fruit and packed in honey into honey preserves. Herbs, peas, and beans are dried.](images/food-preservation-methods.svg)

### Salting

| Step     | What happens                                                               | Takes         |
|:---------|:---------------------------------------------------------------------------|:--------------|
| Dry salt | Layering meat or fish with [salt](../content/salt.md) in a salting barrel. | About ¼ day   |
| Cure     | Leaving the barrel to draw the water out.                                  | About 2 weeks |
| Brine    | Submerging meat, fish, or vegetables in a barrel of brine.                 | About 1 week  |

- Each measure of meat or fish takes a measure of salt, as a starting value.
- Fine white salt cures to a quarter less keeping time than coarse bay salt or rock salt, as the [grades](../content/salt.md#grades) of Salt describe.
- Brine must reach a [salinity](fluids.md#water-quality) of about 3, strong enough to float an egg, as a starting value. Seawater is too weak, so brine comes from salt dissolved in water or from seawater boiled down.
- Brined cabbage becomes sauerkraut, and brined beans salted beans.
- Salted food carries a high salt amount, so it adds to the [salt load](thirst.md#model) of Thirst.
- **Soaking**: steeping salted food in a tub of fresh water for a few Feudum hours halves its salt amount, and uses up a tenth of its keeping time. The salt goes into the water.

### Smoking

| Step       | What happens                                                               | Takes                  |
|:-----------|:---------------------------------------------------------------------------|:-----------------------|
| Cold smoke | Hanging food on a smoking rack in an enclosed room with a smoldering fire. | About 3 days to 1 week |
| Hot smoke  | Hanging food on a smoking rack over an open hearth.                        | A few Feudum hours     |

- Cold smoking gives long keeping: smoked herring keeps about a season, and salted food that is then smoked keeps longer still.
- Hot smoking cooks the food, and adds only about a week of keeping.
- [Fire](fire.md#smoke) decides what smolders, what it burns, and what smoke does to the bodies in the room.

### Drying

- Food dries on a drying rack in the open or under a roof with open sides, as a waiting step.
- It dries faster with a higher [local temperature](weather.md#local-temperature), sun, and a stronger [sheltered wind](weather.md#wind-shelter). Rain wets it and sets it back.
- Drying fully takes days to weeks, depending on the weather. The food keeps spoiling while it dries, so drying has to outrun the rot.
- Dried products are stockfish, dried fruit, dried meat, dried herbs, and dried peas and beans.
- Climate decides what a village dries: a cold, windy coast slows the rot and makes the best stockfish, and a hot, dry summer makes the best raisins.

### Pickling

- Vegetables, eggs, or fish packed in [vinegar](brewing.md#keeping-and-souring) in a sealed crock become pickles after about a week, and keep about a year.
- Sauerkraut comes from brine, not vinegar, as [Salting](#salting) describes.

### Potting

- Cooked meat packed into a crock and sealed under a layer of melted fat keeps about a season.
- Lard, tallow, or butter serve as the fat. [Foods](https://github.com/NoNamer777/feudum/issues/51) supplies lard and tallow, and [Dairy](https://github.com/NoNamer777/feudum/issues/135) butter.

### Honey preserves

- Fruit packed in honey in a sealed crock keeps about a year.
- Honey alone keeps forever. It comes from [Beekeeping](https://github.com/NoNamer777/feudum/issues/128).

### Chains

- Methods apply one after another, and each step makes a new item: salt pork that is then cold smoked becomes ham or bacon, and salt herring becomes red herring.
- A chained item keeps as long as the longest-keeping step, plus a quarter, as a starting value.

## Processed items

- An item made from other items starts at the used share of its most-used input. Stale meat makes salt pork that is already Stale, and a Spoiled turnip makes a Spoiled stew. Preserving can only keep what is still good, so a village preserves while the food is fresh.
- Rotten items can't be processed.
- The rule holds for every design that makes one organic item from another, such as [Cooking](cooking.md) and milling.

## Nutrition

- Preserving keeps the energy and the grain and protein amounts of a food, and halves its fruit and vegetable amounts.
- Sauerkraut and pickled vegetables keep their full vegetable amount.
- A winter on salt pork and stockfish therefore still drifts toward the fruit [deficiency](hunger.md#deficiencies) of Hunger, unless the cellar holds apples and roots.

## Rotten items

- Every organic item has its own rotten version, such as rotten pork, a rotten apple, a rotten hide, or a rotten sapling.
- Rotten items never spoil further.
- Rotten meat and fish feed the carnivores and scavengers whose [diet profile](hunger.md#diet-profiles) allows it. Nothing else eats a rotten item.
- Every rotten item goes on the [dung heap](relief.md#dung-heap) and rots into manure with the rest. Dumped anywhere else, it is a mild [fouling source](fluids.md#fouling).

## Carcasses

- A carcass rots through the same stages, with a keeping time of about 4 days.
- At Rotten, it draws flies, becomes a fouling source, and leaves bones and rotten meat behind.
- Butchering, and what a carcass yields when cut up, belong to [Animal husbandry](animal-husbandry.md#slaughter-and-butchering), and the meat cuts to [Foods](https://github.com/NoNamer777/feudum/issues/51).

## Cues

- Players read freshness from the item, never from a meter: the tooltip shows the stage name, never a timer.
- Spoiled and Rotten items change texture.
- Flies buzz around rotten items, whether dropped, placed, or in a container.
- Spoiled food never shows "Craved" in its tooltip, whatever the body craves.

## Waiting steps

- These steps are placed blocks that keep their own progress: the salting barrel, the brine barrel, the soaking tub, the smoking rack, the drying rack, and the crocks of pickles, potted meat, and honey preserves.
- Each reads its temperature from Body temperature and Weather.
- Each catches up on the elapsed time when its chunk loads, as [Fluids](fluids.md#unloaded-chunks) does.
- Picking one up returns the item with its progress saved.

## Tools and blocks

| Step                           | Block                                   |
|:-------------------------------|:----------------------------------------|
| Dry salt, cure                 | Salting barrel                          |
| Brine                          | Brine barrel                            |
| Soak                           | Soaking tub                             |
| Cold smoke, hot smoke          | Smoking rack                            |
| Dry                            | Drying rack                             |
| Pickle, pot, preserve in honey | Earthenware crock                       |
| Cook before potting            | Hearth, under [Cooking](cooking.md)     |
| Store                          | Sack, basket, barrel, earthenware crock |

- Food preservation owns the sack, basket, barrel, and earthenware crock as food containers.

## Vanilla content

- Vanilla rotten flesh stays hidden; every Feudum item has its own rotten version instead.
- The vanilla smoker stays hidden. Smoking food belongs to the smoking rack, and cooking to [Cooking](cooking.md).
- Vanilla foods never spoil, since [Foods](https://github.com/NoNamer777/feudum/issues/51) hides them.

## Persistence

- Every organic item and block saves its remaining keeping time and the time it last caught up.
- Every waiting-step block saves its progress and the time it last caught up.
- Items in a logged-out player's inventory pause, since a player's absence is not simulated.
- Village simulation brings the food stock of an unloaded village forward, as [Boundaries](#boundaries) describes.

## Query

- One query returns the preservation state of an item or block: its stage, its remaining keeping time, and its current rate with the share of each input: temperature, wetness, and container.
- Other mechanics read spoilage through this query.

## Commands

- `/feudum preservation query <pos|entity slot>` shows the result of the query.
- `/feudum preservation set <pos|entity slot> keeping <value>` sets the remaining keeping time, for testing.
- Every `/feudum preservation` command requires operator permission.

## Boundaries

Food preservation owns keeping times, the stages of spoilage and their effects, the rate and its inputs, rotten items, and how a carcass rots. It also owns salting, smoking, drying, pickling, potting, and honey preserves, the nutrition of preserved food, the rule that processed items inherit spoilage, the food containers, and the blocks of the craft. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Hunger](hunger.md)**: food components, food groups, deficiencies, cravings, and diet profiles.
- **[Thirst](thirst.md)**: the salt load that salted food adds, and the foul load that Spoiled food adds.
- **[Body temperature](body-temperature.md)**: room temperature, cave temperature, cold sources, and the rule that settles a room below the surface toward the cave temperature.
- **[Weather](weather.md)**: local temperature, rain, sun, and the sheltered wind that dries food.
- **[Fluids](fluids.md)**: salinity, brine, and fouling sources.
- **[Relief](relief.md)**: the dung heap that takes rotten items.
- **[Brewing](brewing.md)**: how drinks keep, and the vinegar that pickling uses.
- **[Textiles](textiles.md)**: retting and over-retting.
- **[Time](time.md)**: the calendar that keeping times are measured in.
- **[Animal husbandry](animal-husbandry.md)**: slaughter, butchering, and tallow.
- **[Foods](https://github.com/NoNamer777/feudum/issues/51)**: every food and preserved food item, meat cuts, and lard.
- **[Cooking](cooking.md)**: the hearth, cooked food, and its food component.
- **[Dairy](https://github.com/NoNamer777/feudum/issues/135)**: cheese and butter making, and how long they keep.
- **[Salt](../content/salt.md)**: the salt item, its grades, and salt pans.
- **[Snow and ice](https://github.com/NoNamer777/feudum/issues/53)**: the ice and packed snow of an ice house, and how fast they melt.
- **[Fire](fire.md)**: the smoldering fire of cold smoking, its fuel, and what smoke does to bodies.
- **[Beekeeping](https://github.com/NoNamer777/feudum/issues/128)**: honey.
- **[Farming](farming.md)**: crops in the field, and what a Spoiled seed does.
- **[Tanning](tanning.md)**: curing hides, where their spoilage stops, and what a Stale hide yields.
- **[Illness](illness.md)**: what the foul load of Spoiled food does.
- **[Vermin](https://github.com/NoNamer777/feudum/issues/136)**: rats and mice in the stores, which a sealed container keeps out.
- **[Inventory](https://github.com/NoNamer777/feudum/issues/83)**: chests and general storage.
- **[Drink containers](https://github.com/NoNamer777/feudum/issues/49)**: casks, jugs, and cups.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: when a household preserves.
- **[Larderer](https://github.com/NoNamer777/feudum/issues/137)**: the villager who keeps a manor's larder and cellar.
- **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: the food stock, and any trade that sells preserved food.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: spoilage of the food stock while a village is unloaded.
