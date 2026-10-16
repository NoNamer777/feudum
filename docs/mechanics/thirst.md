# Thirst

Players, Feudum villagers, and livestock need to drink. Water is everywhere, but clean water is not: a village draws it from wells, keeps it from going stale, and brews small ale so there is always something safe to drink. Heat makes everyone thirsty faster, so summer and arid climates put the water supply to the test.

## Who feels it

- **Players** feel thirst everywhere in the world, vanilla villages included. Players in Creative or Spectator mode have no thirst.
- **Feudum villagers** feel it, as [Villagers](#villagers) describes.
- **Livestock** feels it, as [Livestock](#livestock) describes. The [temperature document](temperature.md#livestock) defines which animals count as livestock.

Vanilla villagers, wild animals, and monsters ignore thirst.

## Thirst bar

Thirst works alongside hunger and the same way:

- **Thirst bar.** 20 points, shown as 10 droplets. A full bar means no thirst, and the bar empties as thirst rises.
- **Quenched buffer.** A hidden reserve, like vanilla saturation. Drinks fill it in proportion to their quench, and it drains before the bar does.

The bar is independent of hunger: drinking never feeds and eating never quenches, except for the foods and drinks under [Drinks](#drinks) that do both. Thirst resets to full on respawn, and refills on its own on Peaceful, as hunger does.

### Drain

Thirst has its own exhaustion pool, like hunger: a slow passive drain, plus extra from sprinting, jumping, fighting, and mining. A full bar lasts about one in-game day of normal activity, roughly twice as fast as hunger drains. Body temperature multiplies the drain:

| Body temperature band | Drain |
|:----------------------|------:|
| Freezing to mild      |    ×1 |
| Warm                  |  ×1.5 |
| Hot                   |    ×2 |
| Scorching             |    ×3 |

Swimming does not quench; only drinking does.

### Effects

| Thirst              | Effects                                                                             |
|:--------------------|:------------------------------------------------------------------------------------|
| 7 droplets or more  | None                                                                                |
| 6 droplets or fewer | A dry-mouth sound and a faint screen tint as a warning, and no natural regeneration |
| 3 droplets or fewer | Parched: no sprinting, and mining slows                                             |
| 0 droplets          | Dehydrated: weakness, nausea flashes, and damage over time                          |

Natural regeneration needs both the hunger bar and the thirst bar high enough, so a fed but thirsty player does not heal. Dehydration damage follows the vanilla starvation limits: it stops at 5 hearts on Easy and at half a heart on Normal, and can kill on Hard.

Server config scales the drain and the strength of the effects, and can turn thirst off for players.

### Display

- **Bar.** The droplet bar sits above the hunger bar and shakes when parched, as the hunger bar does. The quenched buffer stays hidden. Config can hide the bar.
- **Unclean water.** The droplets turn greenish while the player drinks unclean water, as a hint.
- **Tooltips.** A drink's tooltip shows its purity, its temperature when it is cool or hot, and the sips left in its container.

## Water

### Purity

All water has one of three purities:

| Purity  | Sources                                                        | When drunk                                                                  |
|:--------|:---------------------------------------------------------------|:----------------------------------------------------------------------------|
| Clean   | Rain, springs, wells, melted snow and ice, and boiled water    | Quenches safely                                                             |
| Unclean | Rivers, lakes, ponds, swamps, and water gone stale or polluted | Quenches, with a small chance of the flux, higher for swamp and still water |
| Salt    | Oceans and beaches                                             | Makes thirst worse and causes nausea                                        |

The flux, the medieval name for dysentery, is an illness of the [disease mechanic](disease.md#illnesses). It causes nausea, faster thirst drain, and weakness, and the disease mechanic describes how it progresses and heals. Unclean water gives villagers the flux the same way it does players.

### Contamination

Clean water turns unclean in two ways:

- **Stagnation.** Water in an open container, such as a bucket, cup, barrel, or cistern, turns unclean after a few in-game days. It turns faster in warm air and slower in cool rooms, by the same rule that [food spoilage](food-spoilage.md#rate) uses. Sealed containers, such as a waterskin, a stoppered jug, or a bottle, keep water clean much longer.
- **Pollution.** A polluter within a few blocks of a well, a cistern, or still water makes that water unclean. Polluters are livestock pens, dung heaps, latrines, tanneries, rotting food, and corpses of mobs that died in the water. A river carries pollution a set distance downstream, so the water upstream of a village is cleaner than the water below it.

Once the polluter is gone, the water clears over a day or two. Rain falling straight into a container is always clean. The sanitation mechanic describes the polluters themselves.

### Purifying

Boiling makes water clean: a vanilla cauldron or a new kettle over a campfire, fireplace, or brazier boils its water in about a minute. Melting snow or ice in a pot also gives clean water. Brewing gives a clean drink, since the boil kills what is in the water. There are no filters, since medieval villages did not filter their water.

### Salt

Salt water never quenches. Boiling it in a pot over a fire, or leaving it in a new salt pan block in the sun, gives salt and no water. The salting barrel of [food spoilage](food-spoilage.md#preservation) uses that salt, and the salter sells the surplus to inland villages.

### Water temperature

Water takes the air band of where it comes from or is stored. Water drawn fresh from a well, a spring, or a stream in cool air is cool, and water stored in a cellar or an ice house stays cool. Carried into warm air, it warms up within a few minutes. Boiled water comes out hot and cools to the air band over a few minutes.

Cool water cools the body, and hot water warms it slightly, as the [temperature document](temperature.md#body-temperature) describes. Purity and temperature are independent, so cool water can still be unclean.

### Drinking by hand

Crouching and using an empty hand on water takes a sip of one droplet, with the purity of that water. Looking up into the rain with an empty hand also gives a sip, so rain is a clean source wherever it falls. Containers are the efficient way to drink, and drinking by hand is the fallback in the wild.

Eating snow by hand gives a sip but cools the body. Frozen water has to be broken or melted before drinking.

## Containers

| Container              | Sips | Notes                                                                           |
|:-----------------------|-----:|:--------------------------------------------------------------------------------|
| Glass bottle (vanilla) |    3 | Shatters when dropped from a height. Glass is rare in a medieval village.       |
| Waterskin              |    8 | Leather, filled from water or a bucket. The everyday carry for travelers.       |
| Clay jug               |    6 | Fired clay. Keeps a drink cool longer, and holds ale, cider, or wine.           |
| Wooden cup             |    1 | Cheap, and can be placed on a table for villagers to drink from.                |
| Tankard                |    1 | Cheap, and can be placed on a table for villagers to drink from.                |
| Bucket (vanilla)       | None | Fills the other containers and carries water in bulk, but cannot be drunk from. |

Each sip gives the quench of the drink it holds. A container remembers the purity and the temperature of what it holds, and mixing clean and unclean water makes the whole container unclean.

The leatherworker makes waterskins, the potter makes clay jugs and cups, and the cooper makes wooden cups, tankards, and buckets.

## Drinks

Quench is in points, and a droplet is 2 points:

| Drink                 | Quench | Alcohol  | Also                                                                               |
|:----------------------|-------:|:---------|:-----------------------------------------------------------------------------------|
| Water                 |      2 | None     | Cool water cools the body, and boiled water warms it slightly                      |
| Milk (vanilla)        |      3 | None     | Feeds a little. No longer clears all effects; [theriac](disease.md#remedies) does. |
| Small ale             |      4 | Weak     | Feeds a little. The everyday safe drink.                                           |
| Ale                   |      4 | Moderate | Feeds a little. Sours within days.                                                 |
| Beer                  |      4 | Moderate | Feeds a little. Hops keep it for weeks.                                            |
| Cider and perry       |      4 | Moderate | None                                                                               |
| Mead                  |      3 | Strong   | None                                                                               |
| Wine                  |      3 | Moderate | None                                                                               |
| Mulled cider and wine |      3 | Moderate | Warms the body                                                                     |
| Herbal tea            |      4 | None     | Warms the body. The herbalist's teas add mild remedy effects.                      |

Every clean drink is safe, and only water can be unclean. The intoxication mechanic describes what alcohol does.

- **Brewer.** Malts barley and brews small ale, ale, beer, and mead. Ale has no hops and takes its flavor from gruit, a herb mix from the herbalist. Beer is ale brewed with hops. Mead uses honey from the beekeeper.
- **Orchardist.** Presses apples into cider and pears into perry.
- **Vintner.** Presses grapes into wine.
- **Mulled drinks.** Cider or wine, warmed over a fire with honey and local herbs. Imported spices wait for the trade mechanic.
- **Herbalist.** Makes herbal teas.
- **Herder.** Milks the village's cows.

Vanilla foods and drinks quench as follows:

- **Water bottle.** Counts as water, with the purity of its source.
- **Stews and soups.** Mushroom, rabbit, beetroot, and suspicious stew quench 2 alongside their food value.
- **Honey bottle, melon slice, and sweet berries.** Each quenches 1. Melon also cools the body.
- **Potions.** Quench nothing beyond the water bottle they are made from.

## Water stores

- **Well.** A new well head block, a stone ring with a windlass and a bucket, on top of a dug shaft. The bottom of the shaft has to hold a water source below the groundwater depth: Y 50 by default, and Y 30 in arid climates. A well never runs dry and draws clean, cool water, as long as no polluter sits near it. The builder digs the village's wells.
- **Rain barrel.** A new block that fills with clean water during rain, about one bucket per rainy in-game hour.
- **Cistern.** An underground store of several blocks that rain or a gutter fills, holding many buckets. It stays cool, so its water stagnates slowly.
- **Water trough.** A new block for livestock, as [Livestock](#livestock) describes.

## Villagers

Feudum villagers drink like medieval villagers did: mostly small ale with meals, and water when there is no ale.

- **Home stores.** Each home keeps a water barrel and an ale cask. Villagers refill the barrel at the village well and the cask from the brewer.
- **Drinking.** A villager drinks from the home stores at meals, and from a waterskin at work.
- **Thirst.** A thirsty villager heads home or to the well and works slower. A villager kept dehydrated falls ill.

A village needs at least one well, a brewer to keep the casks full, and a cooper and a potter for the vessels. A village whose well goes foul drinks unclean water, and its villagers catch the flux.

## Livestock

Livestock drinks from a new water trough within reach of its pen or barn, or from any open water it can reach.

- **Filling.** Rain fills a trough slowly, and a bucket fills it at once. A trough is an open container, so its water stagnates.
- **Thirst.** Thirsty livestock stops breeding and gives less milk and wool. Dehydrated livestock falls ill and can die.

Keeping the troughs full is the herder's work.

## Seasons and climate

Water blocks never dry up, so the vanilla world stays intact. Seasons and climate act through the systems above instead:

- **Rain.** Arid climates and the tropical dry season fill rain barrels and cisterns rarely, so villages there depend on wells.
- **Stagnation.** Warm air speeds it up, so still water and stored water turn unclean faster in summer.
- **Winter.** Frozen water has to be broken or melted before drinking, and snow melted in a pot gives clean water.
- **Heat.** Warm, hot, and scorching weather drains thirst faster, through body temperature.

The Nether and the End have no special rules. The Nether is hot or scorching, so thirst drains two to three times as fast there, and water cannot be placed in it, as in vanilla. The End is cool and has no water. Players carry their water into both.

## Related mechanics

Thirst works together with these mechanics:

- **[Temperature](temperature.md).** Body temperature speeds up thirst in the warm, hot, and scorching bands. Cool water cools the body, and hot drinks warm it.
- **[Seasons](seasons.md).** The season and climate set how often rain fills the water stores, and winter freezes water.
- **[Disease](disease.md).** Unclean water causes the flux, and theriac takes over the effect clearing of vanilla milk.
- **[Food spoilage](food-spoilage.md).** Stored water stagnates by the same rule that food rots, ale sours, and the salting barrel uses salt from salt water.
- **Sanitation.** Latrines, dung heaps, tanneries, and livestock pens pollute nearby water.
- **Intoxication.** Ale, beer, cider, perry, mead, and wine are alcoholic.
- **Trade.** Salt goes to inland villages, and spices for mulled drinks come from abroad.

## Additions and changes

- **Thirst bar.** Players, Feudum villagers, and livestock get a 20-point thirst bar with a hidden quenched buffer, drained by a thirst exhaustion pool that body temperature multiplies.
- **Thirst effects.** A warning, no regeneration, the parched state, and dehydration damage, by thirst level.
- **Water purity.** Every water block and every container of water is clean, unclean, or salt, which replaces the always-safe water of vanilla. Ocean and beach water becomes salt.
- **Contamination.** Stored water stagnates, and polluters near wells, cisterns, and still water make them unclean, carried downstream along rivers.
- **Drinking by hand.** A sip from a water block or from the rain with an empty hand, and from snow.
- **Boiling.** A vanilla cauldron or a new kettle over a heat source boils water clean.
- **Salt.** A new salt item from boiled or sun-dried salt water, and a new salt pan block.
- **Water temperature.** Water and drinks carry a temperature from the air where they were drawn or stored.
- **Containers.** New waterskins, clay jugs, wooden cups, and tankards. The vanilla glass bottle holds 3 sips, and the vanilla bucket fills the other containers.
- **Drinks.** New small ale, ale, beer, cider, perry, mead, wine, mulled cider and wine, and herbal tea.
- **Drink ingredients.** Barley, hops, malt, gruit, orchard apple and pear trees, pears, grapevines, and honey from straw skeps, which the brewer, orchardist, vintner, and beekeeper roles describe.
- **Vanilla food and drink.** Water bottles, milk, stews and soups, honey bottles, melon slices, and sweet berries quench. Milk no longer clears all effects.
- **Water stores.** New well head, rain barrel, cistern, and water trough blocks.
- **Villager behavior.** Feudum villagers keep water and ale at home, drink at meals and at work, and seek water when thirsty.
- **Livestock.** Livestock drinks from troughs and open water, and breeds less, yields less, and falls ill when thirsty.
- **The flux.** A new illness of the disease mechanic, caught from unclean water.
- **Thirst display.** A droplet bar above the hunger bar, greenish droplets for unclean water, and tooltips with purity, temperature, and sips.
- **Configuration.** Server settings for the drain, the strength of the effects, the groundwater depth, the pollution range, and the bar.
