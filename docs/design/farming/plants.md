# Plants

Which plants grow in Feudum, how they grow through the year, what kills them, how they set fruit and seed, and what they yield. [Seasons](../world/seasons.md#plants) sets the temperature and daylight plants grow by, and [Biomes](../world/biomes.md) the ground they grow on. [Plant species](plant-species.md) lists every species with its values.

## What counts as a plant

This page covers trees, shrubs, crops, and wild plants, along with fungi, seaweeds, mosses, and lichens, which players gather the same way. Those four follow the same rules, with the exceptions [below](#fungi-seaweed-moss-and-lichen).

Each Feudum plant is one real species. A wild form with a habitat of its own, such as sea beet or wild cabbage, keeps its own entry. Varieties bred within a species, such as named apples, belong to [Cultivars](https://github.com/NoNamer777/feudum/issues/249), and magical plants to [Fantasy](https://github.com/NoNamer777/feudum/issues/220).

### Which species

The roster holds every real species with a use in the period or a habitat in one of the biomes, field weeds, wildflowers, and mosses included. A crop follows the rule of [Era](../setting/era.md#the-rule): it is in when it was established in regular cultivation in Western Europe by 1300. Western Europe means Latin Christendom there, so Italy, Provence, Christian Iberia, and Norman Sicily count.

Climate keeps no crop out of the roster. The frost and warmth rules decide where it survives, so an olive may live on a mild coast and die inland. Crops from the New World are out, as are wild plants of habitats no Feudum biome holds, such as Mediterranean scrub, and crops grown only in the crusader states, such as sugar cane. [Regions beyond Western Europe](https://github.com/NoNamer777/feudum/issues/231) may bring them back.

## Growth

### Warmth and daylight

A plant grows by gathering warmth, counted in degree-days: each day adds as much as the daily mean temperature stands above 5 °C. Below 5 °C a plant gathers nothing and stays dormant. It moves on through its stages, and ripens, once it has gathered the warmth its species needs, which [Plant species](plant-species.md) gives for each one. Growth therefore follows the climate rather than the calendar: the same crop ripens weeks later in the uplands than on the coast. How plants high in the mountains gather warmth belongs to [Growth on high ground](https://github.com/NoNamer777/feudum/issues/252).

Each species' warmth holds at the daylight of the season it usually grows in, since real figures are measured there. Longer days than that make a day's warmth count for more, and shorter days for less.

Each game day counts for the real days it stands for, so a crop takes the share of the year it really does, whatever the days-per-month [setting](../world/time.md#settings). Wheat sown in autumn ripens in late summer, and warmth needs keep their real values.

Only daylight under open sky grows plants. Torches and other block light do not, so nothing grows underground or indoors.

### Ground and shade

Each species has the soils it grows on and a range of ground wetness it accepts. How wet the ground lies belongs to [Ground wetness](https://github.com/NoNamer777/feudum/issues/255). Players and villagers can water plants by hand, as [Water behavior](../world/water-behavior.md#buckets) describes, but drought and wet years come from [Weather](https://github.com/NoNamer777/feudum/issues/215). Each species also has a shade tolerance, read from the sky light that reaches it.

On poor ground, the wrong wetness, or in shade, a plant grows more slowly and yields less. Where the ground or the shade is beyond what it can stand, it dies. How farmed ground loses its fertility and gets it back belongs to [Fields](https://github.com/NoNamer777/feudum/issues/244).

Parasites grow only on their host: mistletoe on trees, dodder on flax, and yellow rattle on the roots of grasses and clovers. The bird's-nest orchid has no chlorophyll and feeds through the fungi at its roots rather than on light, so it grows in deep shade wherever they live.

### Life cycles and stages

Each species keeps its real life cycle. Annuals such as grains and peas die after one season. Biennials such as cabbage, turnip, onion, and parsnip set seed only in their second year, so growers leave some in the ground over winter for seed. Perennials, such as trees, bushes, grasses, and most herbs, live for years and grow again each spring.

A plant shows the stages it really goes through, so their number differs by species: sprouting, leafing, flowering, fruiting or ripening, and dying back or going dormant. Deciduous trees bud, leaf, turn, and stand bare, as [Seasons](../world/seasons.md#how-seasons-look) sets.

### Winter grains

Winter grains, such as wheat, rye, and spelt, flower only after weeks of cold. Sown in autumn, they come through winter and ripen in summer. Sown in spring, they grow leaves but never ripen. That gives the sowing seasons of the three-field rotation a rule of their own. Spring forms of wheat and rye, which need no cold, belong to [Cultivars](https://github.com/NoNamer777/feudum/issues/249).

### Ripening

Plants of the same species sown on the same day ripen a few days apart, by a fixed offset for each block, so a field ripens unevenly, as a real one does. A ripe plant stays ripe for a while and then goes the way it really would. Grain sheds its seed after about two weeks and sows itself again, fruit falls and rots, and roots and biennials keep in the ground over winter.

## Trees

Trees grow at their real pace in years: hazel is ready to cut after about 7 years, and oak takes about 80 to reach timber size. A tree grows visibly through the stages of its life, from seedling to sapling, pole, mature tree, and veteran. A veteran at last dies and falls, leaving deadwood where fungi grow.

The generated wildwood holds trees of every age, old giants and fallen trunks included, so its timber takes generations to replace. Coppicing and other ways of managing woods belong to [Woodland](https://github.com/NoNamer777/feudum/issues/245).

## Frost

Each species has a kill temperature, and frost colder than that kills it. Hardened rye survives about -25 °C and wheat about -15 °C, while beans in flower die near -2 °C. Seedlings and blossom are more tender than the grown plant, so a late frost can kill a fruit tree's blossom, and that year's fruit, while the tree lives on.

Snow shelters what lies under it. A plant under snow meets the temperature beneath the snow, which stays near 0 °C, rather than the air. A snowy winter therefore treats winter grain more kindly than a bare, freezing one. [Seasons](../world/seasons.md#snow-and-ice) sets where snow lies, and [Thaw](https://github.com/NoNamer777/feudum/issues/239) how it melts.

## Pollination

Pollination decides whether a flower sets fruit, how many seeds form, and how large fleshy fruit grows: a poorly pollinated apple stays small and lopsided. It never affects a plant's growth or survival. Crops harvested for their leaves or roots, such as cabbage and turnip, need it only to set seed.

Each species is pollinated the way it really is:

- **Insects**: the plant needs pollinators while it flowers. Wild ones live in flower-rich land, such as meadows, woodland edges, heath, and hedges, so the more of it lies near a plant, the better it sets. Hives a village keeps add more. Pollinators fly only when it is warmer than about 10 °C and dry, so a cold, wet spell in blossom time costs that year's fruit.
- **Wind**: the plant needs others of its species nearby and dry weather while it flowers, since rain washes the pollen from the air. A rye field sets full ears, and a lone rye plant few.
- **Self**: the plant sets seed alone, and the weather barely affects it. Wheat, barley, oats, and peas pollinate themselves.

A few species use two modes: sweet chestnut and the willows take pollen from both insects and wind, and field beans pollinate themselves but set more when insects visit. The common fig sets fruit without pollination, saffron is sterile and spreads only by its corms, eelgrass sheds its pollen into the water, and plants that spread by spores have no pollination at all. Bees and the other insects belong to [Animals](https://github.com/NoNamer777/feudum/issues/228).

### Partners

Some species need a partner: a compatible plant nearby, usually of their own species. Apple, pear, and sweet cherry cannot be fertilized by their own pollen, so a lone tree bears almost nothing; a wild crab apple can serve as an apple's partner. Species with separate male and female plants, such as holly, yew, and hop, need a plant of the other sex nearby, and only the female bears fruit or seed.

## Fungi, seaweed, moss, and lichen

These four follow the rules above, with these exceptions:

- **Fungi** feed on rotting wood, rich soil, or living trees rather than light: some decay wood or litter, some live as parasites on trees, and some partner the roots of living trees. Each grows only near the food or host [Plant species](plant-species.md#fungi) lists, in shade or darkness, and fruits in damp, mild weather, mostly in autumn.
- **Seaweed** grows underwater, in the light that filters through shallow water, so it thins out with depth.
- **Moss and lichen** grow slowly, and frost does not kill them.

## Wild plants

Wild plants spread from seed on their own. Cleared land left alone turns back into scrub and then woodland over the years, unless grazing or mowing keeps it open. Pioneers that need open sky, such as birch and pine, take a clearing first, and trees that bear shade, such as beech, grow up beneath them and take over. The wild herds of [Animals](https://github.com/NoNamer777/feudum/issues/228) keep the [wooded grassland](../world/biomes.md#lowland) open this way.

Foraging leaves the plant in place: picking berries, nuts, fruit, leaves, or mushrooms does not kill it, so it lives out its life cycle, and a perennial yields again next season. Digging a wild plant up gives a seedling or cutting that a player can plant in a garden. Grafting fruit trees belongs to [Cultivars](https://github.com/NoNamer777/feudum/issues/249).

## Starting a plant

A plant starts from a seed, a set such as an onion or garlic bulb, or a seedling or cutting, on ground it accepts. A crop's seed is what it yields: seed grain is grain held back from the harvest, so every sack sown comes out of the food supply. Plowing, sowing, and planting belong to [Fields](https://github.com/NoNamer777/feudum/issues/244).

Crops with no wild form in Western Europe, such as wheat, peas, and flax, come only from villages: from [Generated villages](https://github.com/NoNamer777/feudum/issues/240) and through trade. [Plant species](plant-species.md) lists their only biome as "Cultivated". Crops that also grow wild can be taken from the wild, such as sweet cherry from the wildwood. Where a crop's wild form has its own entry, such as wild cabbage beside cabbage, the wild form grows true in a garden and the crop comes only from villages. Breeding one into the other belongs to [Cultivars](https://github.com/NoNamer777/feudum/issues/249).

## Harvest

A crop returns what it really did in the period. English manors, whose accounts record the seed sown and the grain reaped, got about 4 grains back for each one sown of wheat and barley, and about 2.5 of oats. A village therefore keeps a large share of each harvest as next year's seed and needs a lot of land. Soil moves the return up or down.

A harvest yields every part the period used: grain and straw from a cereal, stalks and linseed from flax, and fruit with stones that grow new trees. Every tree or shrub felled with an axe gives timber or poles, bark, and brushwood, and [Plant species](plant-species.md) lists what else each one yields. Using these belongs to [Food](https://github.com/NoNamer777/feudum/issues/246) and [Crafts](https://github.com/NoNamer777/feudum/issues/247).

Each plant is harvested the way it was: grain reaped and soft shoots cut with a sickle, hay mown with a scythe, roots lifted with a spade, fruit picked by hand, woody shoots and withies cut with a billhook, and trees felled with an axe. Harvesting without the right tool yields less. The tools themselves belong to [Tools](../crafts/tools.md).

Diseases such as ergot on rye and rust on wheat, and pests such as birds and rabbits in the fields, belong to [Plant diseases and pests](https://github.com/NoNamer777/feudum/issues/250).

## Contact

Nettles sting, and brambles, gorse, and hawthorn scratch the players, villagers, and animals who push into them. Dense undergrowth slows anyone moving through it. Poisonous plants, such as hemlock and deadly nightshade, harm only when eaten, which belongs to [Food](https://github.com/NoNamer777/feudum/issues/246).

Walking over crops and seedlings damages them, as a path trodden across a field does. Grown grass and established plants take no harm.

Dry plants burn readily, above all dry grass, heather, gorse, and reed. How fire spreads, and burning to manage land, belong to [Fire](https://github.com/NoNamer777/feudum/issues/248).

## Land nobody keeps loaded

When land outside villages loads again, its wild plants jump to the state the date and temperature imply, as [snow](../world/seasons.md#land-nobody-keeps-loaded) does, rather than replaying the missed days. The jump counts the warmth and frost of the missed days from the yearly temperature curve, so it comes close to what the plants would have done. How the missed days' weather counts belongs to [Weather](https://github.com/NoNamer777/feudum/issues/215). The plants of villages follow [Village catch-up](https://github.com/NoNamer777/feudum/issues/216).
