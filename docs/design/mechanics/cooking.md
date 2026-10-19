# Cooking

A village eats what it cooks. A pot of pottage simmers on the hearth from morning to night, thickened with peas and whatever the garden gave, and topped up as the household eats from it. Bread rises overnight on barm from the brewhouse and bakes in an oven fired with wood and raked out. Meat turns on the spit for hours, and a pie keeps its filling for a week inside its crust. Cooking makes food safe and worth eating: raw meat brings the flux, and raw grain gives a body almost nothing. A dish carries what went into it, so a pottage of beans and cabbage feeds protein and vegetables, and a hot bowl warms a body in winter. Vanilla cooking is one step in a furnace, so Feudum replaces it.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Cooking covers roasting, boiling, stewing, frying, and baking, dishes combined from several ingredients, dough and bread, boiling water, and rendering fat. It owns the hearth, the heated cauldron, the bake oven, the kneading trough, the table, and the bowls and trenchers that dishes are served in.
- It starts at a raw ingredient. [Foods](https://github.com/NoNamer777/feudum/issues/51) owns the food items and the quern that grinds flour, [Dairy](https://github.com/NoNamer777/feudum/issues/135) cheese and butter, [Food preservation](food-preservation.md) preserved food, [Brewing](brewing.md) drinks, and [Salt](https://github.com/NoNamer777/feudum/issues/66) salt pans.
- It ends at the dish a body eats. [Hunger](hunger.md) owns what the food component does inside the body.
- Dishes carry no quality: every dish of the same template and ingredients is the same until [Food quality](https://github.com/NoNamer777/feudum/issues/161) lands.
- Cooking has no skill: every cook works at the same rate with the same result, and [Skills](https://github.com/NoNamer777/feudum/issues/43) decides whether that changes.

## Working

- A hand step is done at its block by holding the use key, as in [Brewing](brewing.md#working). Work advances by the Feudum time that passed, and stopping keeps what is done.
- A waiting step is a placed block that keeps its own progress, as [Waiting steps](#waiting-steps) describes.
- Cooking is household work that any villager does, at the same blocks and the same rate as a player. [Villagers](https://github.com/NoNamer777/feudum/issues/46) decides when a household cooks, and the [Cook](https://github.com/NoNamer777/feudum/issues/160) runs the kitchen of a manor.
- [Tools and blocks](#tools-and-blocks) lists what each step needs.

## Raw food

- [Foods](https://github.com/NoNamer777/feudum/issues/51) gives each ingredient a raw and a cooked food component. Cooking turns the raw one into the cooked one, and [Methods](#methods) adjusts it.
- Raw meat and fish add to the [foul load](thirst.md#model) of Thirst as much as Spoiled food does, and raw eggs add half that. [Illness](illness.md#foul-load) decides what the foul load does.
- Raw grain and dried peas and beans give a tenth of their cooked energy, but fill the stomach fully.
- Fruit, most vegetables, herbs, and milk are as good raw as cooked.
- Cooking clears the foul load of raw food, but not the foul load of [Spoiled](food-preservation.md#keeping-time) food. Cooking can't rescue meat that has turned.
- The foul load of raw food applies only to a species whose diet profile needs cooked food, as [Diet profiles](#diet-profiles) describes. Carnivores and scavengers eat raw meat with no risk, and dogs and pigs eat kitchen scraps.

## Heat

- Every cooking block takes its heat from a fire: the hearth burns its own, the heated cauldron sits over a hearth or a fire, and the bake oven stores the heat of its firing. [Fire](fire.md#fuels) decides what burns, how long, and the heat output it gives.
- The heat output sets how fast a block cooks. Below a minimum heat, it doesn't cook at all.
- A hearth is also a heat source under [Body temperature](body-temperature.md#shelter-and-heat), so the kitchen fire warms the room.

## Doneness

- Food on the heat runs through three stages: Raw, Cooked, and Burnt. It turns Cooked once its cooking time is done.
- Each method takes about its historical time, as starting values to tune: a pottage simmers for most of a day, a joint roasts for a few Feudum hours, bread bakes for about a Feudum hour, and an egg or a fritter fries in minutes.
- A dish cooked in liquid never burns while liquid remains, but the liquid boils off. Left dry, it burns.
- A roast on the spit has to be turned, a hand step like turning the couch in [Brewing](brewing.md#malt). An unturned roast burns before it is done.
- Frying and baking burn once they pass done by about a quarter of their cooking time, as a starting value.
- Burnt food keeps half the energy and half the group amounts of its cooked food component.

## Methods

Starting values to tune:

| Method         | Block                 | Effect on the cooked food component                       |
|:---------------|:----------------------|:----------------------------------------------------------|
| Boil in a dish | Heated cauldron       | None, since the broth is eaten with it.                   |
| Boil and drain | Heated cauldron       | Halves the fruit and vegetable amounts.                   |
| Roast          | Spit on the hearth    | Lowers the stomach fill by a quarter, as water cooks out. |
| Bake           | Bake oven             | Lowers the stomach fill by a quarter, as water cooks out. |
| Fry            | Griddle on the hearth | Adds the energy of the fat used.                          |

- Boiled and drained food loses its fruit and vegetable amounts to the water, as boiled greens and boiled meat do.
- The frying fat is lard, tallow, butter from [Dairy](https://github.com/NoNamer777/feudum/issues/135), or oil from [Oil pressing](https://github.com/NoNamer777/feudum/issues/106).
- A single raw item cooked on its own, such as a roast joint, a fried egg, or boiled greens, becomes a plain cooked item that [Foods](https://github.com/NoNamer777/feudum/issues/51) lists, and so do bread and oatcakes. Only combined dishes use [templates](#dishes).

## Dishes

A dish is cooked from a template that takes its ingredients from item tags. Its food component is computed from what went in, so its food groups follow its ingredients. [ADR 0023](../../adr/0023-dishes-compute-their-food-component-from-their-ingredients.md) records why.

### Templates

The starting set:

| Template           | Base                     | Additions                  | Liquid                     | Cooked                          |
|:-------------------|:-------------------------|:---------------------------|:---------------------------|:--------------------------------|
| Pottage            | Grain, or peas and beans | Vegetables, herbs, meat    | Water, milk, ale, or broth | Simmered in the heated cauldron |
| Porridge or gruel  | Grain                    | None                       | Water, milk, or ale        | Simmered in the heated cauldron |
| Stew or broth      | Meat or fish             | Vegetables, herbs          | Water, milk, ale, or broth | Simmered in the heated cauldron |
| Pie                | Dough for the crust      | Meat, fish, fruit, or eggs | None                       | Baked in the bake oven          |
| Fritter            | Batter                   | Fruit or vegetables        | None                       | Fried on the griddle            |
| Pudding or sausage | Offal or blood           | Grain, fat                 | None                       | Boiled in the heated cauldron   |

- Templates are data-driven: JSON in a data pack, each naming its slots as item tags and its method, so a data pack can add dishes.
- Each template has slots: a required **base**, up to four **additions**, a **liquid** where its method needs one, and up to two **seasonings**, as [Seasoning](#seasoning) describes.
- The crust of a pie is its coffin, and a pie needs at least one filling. Batter is flour, egg, and milk. A pudding or sausage is filled into a casing of gut, which Foods supplies.

### Starting a dish

The block works out the template from what goes in, so there is no recipe menu:

- **Heated cauldron**: grain or peas and beans with a liquid make pottage, and grain with a liquid and nothing else makes porridge. Meat or fish with a liquid makes a stew.
- **Table**: dough wrapped around a filling makes a pie, and offal or blood with grain and fat, filled into a casing, makes a pudding or sausage. Each then goes to the bake oven or the heated cauldron.
- **Griddle**: batter with an addition makes a fritter.
- Contents that fit no template cook as their separate items.

### Servings

- A batch's food component is the sum of its ingredients' components after the [method](#methods) effects.
- The liquid carries its water amount, and any foulness that boiling didn't clear, into the dish, as the [water amount](thirst.md#food-and-drink) of Thirst. Broth and pottage hydrate a little, and the liquid adds to the stomach fill.
- A batch splits into servings of about one good meal each, so a cauldron of pottage feeds a household and a single pie serves a few.

### Names and stacking

- A dish is named for its template and its one or two largest ingredients, as in "pottage of peas and onions".
- Two servings stack only when they share a template and the same ingredients in the same rounded amounts, and their remaining keeping times round to the same Feudum hour, as [Food preservation](food-preservation.md#keeping-time) requires.

## Seasoning

- Seasonings are salt, herbs, spices, [verjuice](brewing.md#wine), [vinegar](brewing.md#keeping-and-souring), and honey.
- A seasoning counts only through its own food component: salt adds its salt amount to the [salt load](thirst.md#model), and honey adds its energy.
- Spices come from trade, under [Village economy](https://github.com/NoNamer777/feudum/issues/44).

## Bread

The diagram traces the path from grain to bread. Arrows are labeled with their step, and the three arrows into dough are one step: kneading flour with water and a leaven. Ingredients have a light fill, dough is plain, and the breads are bold. The dashed arrow is the piece of dough kept back as the next sourdough starter.

![The path from grain to bread. Grain is milled on the quern into flour. Flour mixed with water makes unleavened dough, which is baked on the griddle into flatbread and oatcakes. Flour kneaded with water and a leaven makes dough. The leaven is barm, from Brewing, or a sourdough starter. The dough rises, and the risen dough is baked in the oven into bread. A piece of the dough is kept back as the next sourdough starter.](images/cooking-bread.svg)

- Flour comes from grain ground on the quern of [Foods](https://github.com/NoNamer777/feudum/issues/51), a [Watermill](https://github.com/NoNamer777/feudum/issues/67), or a [Windmill](https://github.com/NoNamer777/feudum/issues/56).
- Flour, water, and a leaven are kneaded in the kneading trough, a hand step. The dough then rises in the trough as a waiting step, over a few Feudum hours as a starting value, and faster in a warm room.
- The leaven is either [barm](brewing.md#yeast) from Brewing or a sourdough starter: a piece of dough kept back from the last batch. A starter has to be fed with flour every few Feudum days, as a starting value, or it goes stale as barm does.
- Unleavened dough needs no rising, and bakes on the griddle into flatbread and oatcakes.
- The kind of bread follows the flour: manchet from white wheat flour, maslin from wheat and rye, rye bread, barley bread, and horse bread from peas and beans, which feeds horses and the poor.

### Bake oven

- The oven is fired with wood for about a Feudum hour, a waiting step, then raked out by hand. It bakes on its stored heat, which falls over the next Feudum hours.
- Bread goes in first, while the heat is high, then pies, and anything to dry goes in at the last low heat.
- Each firing bakes one batch of about a dozen loaves, as a starting value.
- [Village economy](https://github.com/NoNamer777/feudum/issues/44) and [Realm laws](https://github.com/NoNamer777/feudum/issues/102) decide whether a lord can require villagers to bake in the manor's oven, the medieval ban.

## Boiling water

- The water in a heated cauldron warms toward boiling at a rate set by the heat output below it. Hot water poured out mixes its temperature into a tub or washbasin, as [Hygiene](hygiene.md#water-temperature) describes.
- Water held at a boil for about a Feudum quarter hour, a starting value, loses all its [foulness](fluids.md#water-quality), so a village can make foul water safe to drink.
- Boiling evaporates water and leaves its salt behind, so the [salinity](fluids.md#evaporation-and-brine) rises as the volume falls. That is how seawater boils down to brine.
- The heated cauldron holds its water as a volume under [Fluids](fluids.md#volume).

## Rendering

- Fat from [butchering](animal-husbandry.md#slaughter-and-butchering) melts in the heated cauldron into tallow from cattle and sheep, or lard from pigs. The cracklings left behind are a food.
- Rendering ends the spoilage of the fat, as [ADR 0018](../../adr/0018-every-organic-item-spoils.md) allows for processing that stabilized a material. [Foods](https://github.com/NoNamer777/feudum/issues/51) owns the tallow and lard items.

## Other uses of the heated cauldron

Cooking owns the heated cauldron, its heat, and boiling water. Each process that uses it belongs to its own page:

- The hopped boil to [Brewing](brewing.md#ale-and-beer).
- Soft soap to [Hygiene](hygiene.md#lye-and-soap).
- Scouring wool to [Textiles](textiles.md).
- Clearing a container of disease to [Illness](illness.md#shared-things).

## Warmth

- A cooked dish carries a temperature. It comes off the heat Hot and cools toward the temperature around it, the same temperature that [Food preservation](food-preservation.md#temperature) reads. It goes from Hot to Cold in about a Feudum hour as a starting value, and more slowly for a cauldron's worth than for a bowl.
- A dish eaten Hot or Warm gives its eater the thermal offset of [Body temperature](body-temperature.md#felt-temperature), so a hot pottage in winter is worth the fire. A Cold dish gives none.

## Keeping

Cooked food spoils under [Food preservation](food-preservation.md), and starts at the used share of its most-used ingredient, as [Processed items](food-preservation.md#processed-items) requires. Starting keeping times, at 10 °C and dry:

| Dish                    | Keeps        |
|:------------------------|:-------------|
| Pottage, porridge, stew | About 2 days |
| Fritter                 | About 2 days |
| Roast meat              | About 4 days |
| Pie, pudding, sausage   | About 1 week |

- A pie keeps its filling longer than the filling would keep alone, since the crust seals it.
- Food preservation already sets bread at about 1 week.
- A dish held at a simmer over the fire doesn't spoil, so a pot that never leaves the hearth works.
- Topping up a simmering pot mixes the new ingredients into the batch under the same rule, so the pot takes the used share of its most-used input.

## Serving

- Pottage, porridge, and stew are served in a wooden bowl. Eating a serving gives the bowl back.
- A shared bowl is a [shared thing](illness.md#shared-things) under Illness, and boiling clears it.
- Roast meat can be served on a trencher, a thick slice of stale bread that soaks up the juices. A trencher is eaten with the meal, or given to the poor or the dogs.

## Cues

- Players read a dish from the item and the block, never from a meter or a timer.
- The tooltip shows the doneness (Raw, Cooked, or Burnt), the warmth (Hot, Warm, or Cold), and the ingredients.
- Raw, Cooked, and Burnt food each have their own texture.
- A boiling cauldron steams, a griddle sizzles, and burning food smokes.
- A cooking dish gives off a scent that carries downwind, as the [scent](hygiene.md#scent) of a body does under Hygiene, so a cooking fire can draw a hungry wolf. [Wildlife](https://github.com/NoNamer777/feudum/issues/47) decides how animals sense it.

## Diet profiles

- The [diet profile](hunger.md#diet-profiles) of Hunger carries a needs-cooked-food flag. A species with the flag takes the foul load of raw meat, fish, and eggs, as [Raw food](#raw-food) describes.
- The human diet profile has the flag, so players and villagers do. Animal profiles leave it off.

## Waiting steps

- These steps are placed blocks that keep their own progress: the heated cauldron while it simmers, boils, or renders, the kneading trough while dough rises, and the bake oven while it fires and bakes.
- Each catches up on the elapsed time when its chunk loads, as [Fluids](fluids.md#unloaded-chunks) does.
- Picking one up returns the item with its progress saved.

## Tools and blocks

Each is a single block, not a structure of several:

| Step                       | Block                                                | Made of                                                                                           |
|:---------------------------|:-----------------------------------------------------|:--------------------------------------------------------------------------------------------------|
| Roast, fry, bake flatbread | Hearth, with its spit, pot hook, trivet, and griddle | Stone or clay, with iron fixtures from [Smithing](https://github.com/NoNamer777/feudum/issues/86) |
| Simmer, boil, render       | Heated cauldron, on the pot hook or trivet           | Iron, copper, or brass, from Smithing                                                             |
| Bake bread and pies        | Bake oven                                            | Stone or clay                                                                                     |
| Knead, rise                | Kneading trough                                      | Wood, from [Carpentry](https://github.com/NoNamer777/feudum/issues/115)                           |
| Assemble pies and puddings | Table                                                | Wood, from Carpentry                                                                              |
| Serve                      | Wooden bowl, trencher                                | Wood, from Carpentry; stale bread                                                                 |

## Vanilla content

- Cooking food in the furnace and on the campfire stays off. [Smithing](https://github.com/NoNamer777/feudum/issues/86) decides the furnace, and [Fire](fire.md#open-fire) replaces the campfire with the open fire.
- The vanilla cauldron and its uses stay hidden, and the heated cauldron replaces them.
- The vanilla bowl stays hidden, and the wooden bowl replaces it.
- The recipes for cake, cookies, pumpkin pie, and the vanilla stews and soups stay hidden. [Foods](https://github.com/NoNamer777/feudum/issues/51) hides the items themselves.
- Food preservation already hides the vanilla smoker.

## Persistence

- Every dish item and block saves its template, ingredients, doneness, warmth, and progress, and the time it last caught up.
- Every waiting-step block saves its progress and the time it last caught up.
- Village simulation brings the cooking of an unloaded village forward, as [Boundaries](#boundaries) describes.

## Query

- One query returns the cooking state of an item or block: its template, ingredients, food component, doneness, warmth, and progress.
- Other mechanics read cooking through this query.

## Commands

- `/feudum cooking query <pos|entity slot>` shows the result of the query.
- `/feudum cooking set <pos|entity slot> <progress|temperature> <value>` sets the state of a dish or block, for testing.
- Every `/feudum cooking` command requires operator permission.

## Boundaries

Cooking owns how raw food becomes cooked food, the foul load that raw food adds, heat at the cooking blocks, doneness, and the methods and their effects. It also owns dish templates and how they set a food component, servings, names and stacking, seasoning, dough, leavening, bread, and the firing of the bake oven. Boiling water, rendering, the warmth of dishes, the keeping times of cooked dishes, bowls and trenchers, the needs-cooked-food flag of diet profiles, and the blocks of the craft are its own as well. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Hunger](hunger.md)**: food components, food groups, the stomach, and diet profiles.
- **[Thirst](thirst.md)**: the foul load that raw food adds to, and the water and salt amounts of dishes.
- **[Illness](illness.md)**: what the foul load does, and the shared things that a bowl joins.
- **[Body temperature](body-temperature.md)**: heat sources, room temperature, and the thermal offset of a warm dish.
- **[Food preservation](food-preservation.md)**: keeping times, spoilage, the rule that processed items inherit it, and preserved food.
- **[Fluids](fluids.md)**: water volume, foulness, salinity, and evaporation.
- **[Brewing](brewing.md)**: barm, verjuice, vinegar, and the hopped boil.
- **[Hygiene](hygiene.md)**: the water temperature of tubs and washbasins, soft soap, and scent.
- **[Textiles](textiles.md)**: scouring wool.
- **[Animal husbandry](animal-husbandry.md)**: the fat that rendering melts down.
- **[Foods](https://github.com/NoNamer777/feudum/issues/51)**: every ingredient and cooked item with its raw and cooked food components, flour, the quern, casings, tallow, and lard.
- **[Fire](fire.md)**: the fire in the hearth and the oven, its fuel, heat output, smoke, and ash, the fireplace, and the open fire.
- **[Dairy](https://github.com/NoNamer777/feudum/issues/135)**: milk products, and the butter used for frying.
- **[Oil pressing](https://github.com/NoNamer777/feudum/issues/106)**: the oil used for frying.
- **[Salt](https://github.com/NoNamer777/feudum/issues/66)**: the salt item and salt pans.
- **[Watermill](https://github.com/NoNamer777/feudum/issues/67)** and **[Windmill](https://github.com/NoNamer777/feudum/issues/56)**: milling flour.
- **[Smithing](https://github.com/NoNamer777/feudum/issues/86)**: making the iron fixtures of the hearth and the heated cauldron, and the furnace.
- **[Carpentry](https://github.com/NoNamer777/feudum/issues/115)**: making the kneading trough, the table, and the wooden bowl.
- **[Food quality](https://github.com/NoNamer777/feudum/issues/161)**: whether dishes carry a quality.
- **[Skills](https://github.com/NoNamer777/feudum/issues/43)**: whether cooking takes a skill.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: how animals sense the scent of cooking.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: when and what a household cooks, and its meals.
- **[Cook](https://github.com/NoNamer777/feudum/issues/160)**: the villager who runs the kitchen of a manor.
- **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: spices from trade, and the food stock.
- **[Realm laws](https://github.com/NoNamer777/feudum/issues/102)**: whether a lord can require villagers to bake in the manor's oven.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: cooking while a village is unloaded.
