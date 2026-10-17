# Food spoilage

Food rots over time unless it is kept cold, sealed, or preserved. Most fresh food lasts days, so a village that wants to eat through winter salts, smokes, dries, and pickles its harvest in autumn and keeps it in cool rooms. Drinks follow the same rule: water stagnates, ale sours, and wine turns to vinegar.

## Where food spoils

Spoilage belongs to the food, not to whoever holds it. Food spoils in every inventory and container in the world, vanilla villages and structures included. Food in a loot chest starts fresh when its loot is generated.

Feudum villagers store, rotate, and preserve their food, as [Villagers](#villagers) describes. Vanilla villagers get no new behavior.

## Freshness

### Shelf life

Every food and drink has a shelf life: the in-game days it takes to rot in mild air outside a sealed vessel. [Foods](#foods), [Drinks](#drinks), and [Preservation](#preservation) list them, and a datapack can change the shelf life of any item.

Each stack stores the world time at which it rots. When the stack moves somewhere that spoils faster or slower, the mod recalculates that time from the shelf life left. Food in an unloaded chunk keeps the rate it had when the chunk unloaded, so stores keep spoiling while nobody is near.

### Stages

| Stage   | Shelf life used | Nourishment     | Risk                                           |
|:--------|:----------------|:----------------|:-----------------------------------------------|
| Fresh   | 0 to 50%        | 100%            | None                                           |
| Stale   | 50 to 75%       | 75%             | None                                           |
| Spoiled | 75 to 100%      | 50%             | Food poisoning, more likely from meat and fish |
| Rotten  | Past 100%       | Cannot be eaten | None                                           |

Nourishment covers both hunger and saturation. Food poisoning is an illness of the [disease mechanic](disease.md#illnesses): nausea and faster hunger drain for a while. [Rotten food](#rotten-food) describes what rotten food turns into.

### Rate

The air band where food sits sets how fast it spoils. Food in an inventory uses the air around whoever carries it, and food in a container uses the air of its room.

| Band      |  Rate |
|:----------|------:|
| Freezing  |    ×0 |
| Cold      | ×0.25 |
| Cool      |  ×0.5 |
| Mild      |    ×1 |
| Warm      |  ×1.5 |
| Hot       |    ×2 |
| Scorching |    ×3 |

Freezing stops spoilage, so winter cold and an ice house keep meat for months. Below Y 40 the air stays mild all year, so a cellar spoils food at two thirds of the rate of warm summer air above ground. The [temperature document](temperature.md#air-temperature) sets the air bands.

Three conditions multiply the rate further:

- **Sealed vessels.** Drinks and moist food spoil at ×0.25 in a sealed vessel: a stoppered jug, a waterskin, a bunged or waxed cask, or a crock. Moist food means pickles, preserves, and potted meat; fresh meat and bread gain nothing from sealing. Open vessels and chests are neutral.
- **Wetness.** Food dropped in water or rain, and food on a drying rack in the rain, spoils at ×2.
- **Rot.** Food in a container that holds a rotten item spoils at ×1.5 until the rotten item is taken out.

A shulker box or a bundle uses the air where it sits or is carried. The contents of an ender chest have no place in the world, so they spoil at ×1.

### Frost

Freezing harms produce. Root vegetables, fruit, and eggs that freeze drop one stage when they thaw, so a cellar earns its place in winter by keeping them from freezing. Meat, fish, grain, and preserved food freeze without harm. Frozen drinks have to thaw before anyone can drink them, as the [thirst document](thirst.md#seasons-and-climate) describes.

### Stacks and processing

- **Merging.** Stacks of the same stage merge, and the merged stack takes the earlier rot time. Stacks of different stages never merge, so a spoiled item cannot hide in a fresh stack.
- **Processing.** Cooking, baking, and crafting pass freshness on: the output has used the same share of its shelf life as its input, so stale raw meat cooks into stale cooked meat. With several inputs, the oldest one decides.
- **Preserving.** The blocks under [Preservation](#preservation) accept only fresh or stale food.

### Display

A food's tooltip names its stage. Stale food looks duller, and spoiled food takes a greenish tint. There is no timer: players judge their stores by stage, as they judge the air by cues rather than a thermometer.

Server config scales the rates and the strength of the effects, and can turn spoilage off.

## Foods

Shelf lives in mild air:

| Class      | Days | Foods                                                                                                                          |
|:-----------|-----:|:-------------------------------------------------------------------------------------------------------------------------------|
| Very short |    2 | Raw meat and fish, milk                                                                                                        |
| Short      |    4 | Cooked meat and fish, bread, stews and soups, berries, melon slices, cake, pumpkin pie                                         |
| Medium     |   12 | Eggs, mushrooms, butter, soft cheese                                                                                           |
| Long       |   48 | Potatoes, carrots, beetroots, apples, pears, pumpkins                                                                          |
| Very long  |   96 | Grain, flour, dried beans, hard cheese, dried kelp, cookies                                                                    |
| Never      | None | Salt, honey, sugar, golden apples, golden carrots, glistering melon slices, rotten flesh, spider eyes, chorus fruit, hay bales |

Fresh meat lasts two days in mild air, while roots and apples in a cool cellar last 96 days, a full year by default, which carries them to the next harvest. Poisonous potatoes and suspicious stew keep their vanilla effects on top of spoilage.

## Drinks

Drinks pass through the same stages, with quench in place of nourishment:

| Drink                     | Days | Past its shelf life               |
|:--------------------------|-----:|:----------------------------------|
| Water                     |    3 | Stays unclean                     |
| Milk                      |    2 | Sours, and can only be poured out |
| Small ale, ale            |    4 | Turns to alegar                   |
| Beer                      |   24 | Turns to alegar                   |
| Cider, perry              |   48 | Turns to vinegar                  |
| Wine, mead                |   96 | Turns to vinegar                  |
| Mulled drinks, herbal tea |    4 | Can only be poured out            |

Spoiled water is unclean and risks the flux, as the [thirst document](thirst.md#purity) describes; its stagnation is this rule applied to water. Every other drink stays safe, as thirst promises: it quenches less as it turns, and sours once its shelf life runs out. Alegar and vinegar are not drinks; they go into pickling.

## Preservation

Preserving turns fresh or stale food into food that keeps far longer:

| Food                                     | Method                         | Block                         | Days |
|:-----------------------------------------|:-------------------------------|:------------------------------|-----:|
| Salt meat and fish                       | Curing in salt                 | Salting barrel                |   96 |
| Smoked meat and fish                     | Smoking                        | Smokehouse                    |   48 |
| Ham, bacon, and kippers                  | Salting, then smoking          | Salting barrel and smokehouse |  192 |
| Dried fruit, beans, herbs, and stockfish | Drying                         | Drying rack                   |   96 |
| Pickles                                  | Pickling in vinegar or alegar  | Crock                         |   96 |
| Sauerkraut                               | Fermenting cabbage with salt   | Crock                         |   48 |
| Fruit in honey                           | Preserving in honey            | Crock                         |   96 |
| Potted meat                              | Sealing cooked meat under lard | Crock                         |   48 |
| Salted butter                            | Churning with salt             | Butter churn                  |   48 |
| Hard cheese                              | Pressing and ripening          | Cheese press                  |   96 |

Shelf lives are for mild air outside a sealed vessel, and are configurable. A crock is a sealed vessel, so what it holds keeps four times as long.

- **Salting barrel.** A cooper's barrel that cures meat or fish with salt over a few days.
- **Smokehouse.** A room rather than a single block, detected like the heated rooms of the [temperature document](temperature.md#shelter-and-rooms). A smoldering fire fills it with smoke, and meat and fish on its hooks smoke over a few days.
- **Drying rack.** Dries food in sun and wind, faster in warm air. It stalls in the rain.
- **Crock.** A potter's lidded pot for pickling, fermenting, preserving in honey, and potting.
- **Butter churn and cheese press.** The churn turns milk into butter, and the press turns curds into cheese, which then ripens on a shelf.

The salter supplies salt, the brewer alegar, the vintner and orchardist vinegar, the beekeeper honey, the herder milk, and the butcher lard.

## Rotten food

- **Items.** Rotten meat and fish become vanilla rotten flesh, and other rotten food becomes a new rotten food item. [Drinks](#drinks) lists what each drink turns into.
- **Uses.** Both compost in the vanilla composter, and the [dung heap](sanitation.md#dung-heap-and-manure) of the sanitation mechanic rots them into manure for the fields.
- **Pollution.** Rotten food near a well, a cistern, or still water pollutes it, as the [thirst document](thirst.md#contamination) describes.

## Storage

Cool storage needs no new block. Storage places are rooms under the room rules of the [temperature document](temperature.md#shelter-and-rooms):

- **Root cellar.** A room below Y 40, where the air stays mild all year. It keeps produce from freezing in winter and slows spoilage in summer.
- **Larder.** A cool room in a home where the household keeps its food.
- **Ice house.** A well-insulated room that ice or packed ice keeps cold. It keeps its ice only while it stays cold enough, so it needs fresh ice every winter.

The [granary](vermin.md#the-granary) keeps grain from vermin and damp, and crocks and sealed casks keep rats and mice out, as the [vermin mechanic](vermin.md#containers-and-sacks) describes.

## Villagers

Feudum villagers manage their food like a medieval village did:

- **Larder.** Each home keeps a few days of food in a larder chest, ideally in a cool room, and refills it from the village stores.
- **Eating.** Villagers eat the oldest food first, and refuse spoiled food unless they are starving.
- **Clearing out.** Once a week a villager clears rotten food out of the home and village stores, and carries it to the dung heap or a composter.
- **Household preserving.** In autumn, each home pickles, ferments, preserves fruit in honey, and pots meat in its crocks.
- **Winter stockpile.** Before winter, the village weighs its stored food against the days of winter ahead. When it falls short, homes preserve more, the butcher culls more livestock, and the merchant buys food. Surplus that will not keep goes to the harvest festival.
- **Ice.** In winter, the builder cuts ice from frozen water and stores it in the ice house. A dedicated ice cutter role may take this work over later.

These roles do the rest of the work:

- **Butcher.** Slaughters livestock in the autumn cull, and salts and smokes the meat.
- **Fisher.** Catches fish, and salts and dries the catch.
- **Dairymaid.** Churns butter and makes cheese.
- **Miller.** Grinds grain into flour, so the village stores grain, which keeps, and mills it as needed.
- **Baker.** Bakes bread every few days, since bread keeps only four.

A village whose stores rot before spring starves, as the [seasons document](seasons.md#village-effects) describes.

## Livestock

Animals accept feed at any stage except rotten, both for breeding and for the herder's winter feeding, so stale grain still has a use.

## Seasons and climate

- **Autumn.** The harvest, the cull, and household preserving fill the stores for winter.
- **Winter.** Freezing air stops spoilage outdoors, but frost harms produce left unprotected.
- **Summer and hot climates.** Warm and hot air speeds spoilage, so cellars, ice houses, and preserving matter most in arid and tropical villages.

The Nether is hot or scorching, so food spoils two to three times as fast there. The End is cool, so food spoils at half the rate.

## Related mechanics

Food spoilage works together with these mechanics:

- **[Temperature](temperature.md).** The air band sets the spoilage rate, and rooms make cellars, larders, smokehouses, and ice houses.
- **[Seasons](seasons.md).** The village stores food for winter, frost harms produce, and the harvest festival uses up what will not keep.
- **[Thirst](thirst.md).** Water stagnates and drinks sour by the same rule, and boiling salt water gives the salt for salting.
- **[Disease](disease.md).** Spoiled food causes food poisoning, and spoiled water causes the flux.
- **[Sanitation](sanitation.md).** Rotten food becomes manure, and pollutes nearby water.
- **[Vermin](vermin.md).** Rats, mice, and weevils raid the stores, and the granary keeps them out.
- **Trade.** Fresh food does not survive a journey, so villages trade preserved food such as salt fish, cheese, and ham, and inland villages buy salt to preserve at all.

## Additions and changes

- **Freshness.** Every food and drink gets a shelf life, and each stack a rot time, which replaces vanilla food that never spoils.
- **Stages.** Fresh, stale, spoiled, and rotten, with less nourishment and quench as food ages, and food poisoning from spoiled food.
- **Spoilage rate.** The air band sets the rate, and sealed vessels, wetness, and rotten neighbors multiply it. Frost harms produce when it thaws.
- **Stacks and processing.** Stacks merge only within a stage, and cooking, baking, and crafting pass freshness on.
- **Shelf lives.** Every vanilla food gets a shelf life, configurable per item through a datapack.
- **Souring.** Ale and beer sour into alegar, and cider, perry, wine, and mead into vinegar. Milk, mulled drinks, and herbal tea go off and are poured out.
- **Preserved foods.** New salt meat and fish, smoked meat and fish, ham, bacon, kippers, dried fruit and beans, dried herbs, stockfish, pickles, sauerkraut, fruit in honey, potted meat, salted butter, and soft and hard cheese.
- **Preserving blocks.** A new salting barrel, drying rack, crock, butter churn, and cheese press, and the smokehouse as a room with a smoldering fire and meat hooks.
- **Ingredients.** New cabbage and bean crops, butter, lard, curds, alegar, and vinegar.
- **Rotten food.** A new rotten food item, and rotten meat and fish become vanilla rotten flesh. The vanilla composter and the dung heap take both.
- **Food poisoning.** A new illness of the disease mechanic, caught from spoiled food.
- **Spoilage display.** Tooltips name the stage, and stale and spoiled food get a tint.
- **Villager behavior.** Feudum villagers keep larders, eat the oldest food first, clear out rotten food, preserve in autumn, stockpile for winter, and fill the ice house.
- **Livestock feed.** Animals accept feed at any stage except rotten.
- **Configuration.** Server settings for the rates, the stage effects, and turning spoilage off.
