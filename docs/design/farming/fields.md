# Fields

How farmland is worked, from breaking the ground to sowing and weeding, and how the ground loses its nutrients and gets them back. [Plants](plants.md) sets how crops grow on the ground they get, [Plant species](plant-species.md) what each crop needs from it, and [Biomes](../world/biomes.md) the soil each biome lies on.

## What counts as a field

This page covers arable fields and gardens: the open fields of grain and pulses, and the small plots dug by hand beside houses for vegetables and herbs. Both follow the same rules; a garden is only smaller and worked by hand. Hay meadow and pasture belong to [Meadow and pasture](https://github.com/NoNamer777/feudum/issues/269), and orchards to [Woodland](https://github.com/NoNamer777/feudum/issues/245).

Players lay out fields however they like: this page sets no rules for their shape or size, or for who holds them. Open-field strips and holdings belong to [Land tenure](https://github.com/NoNamer777/feudum/issues/270).

## Tilled ground

Breaking the ground turns a soil block into tilled ground of the same soil, so tilled loam stays loam and tilled sand stays sand. Rock, shingle, and mud cannot be tilled. Tilled ground left unsown grows weeds, then grass, and turns back into untilled ground over a few seasons, as [Wild plants](plants.md#wild-plants) describes.

How wet tilled ground lies belongs to [Ground wetness](https://github.com/NoNamer777/feudum/issues/255), not to the nearness of water.

Plowing leaves the shape of the land as it is, and shows only in the texture of the tilled soil. Ridge and furrow, which centuries of plowing built across real fields, waits on [Terrain resolution](https://github.com/NoNamer777/feudum/issues/272), since a whole block is too coarse for it.

## Nutrients

Each block of ground holds its own levels of three nutrients, nitrogen, phosphorus, and potassium, and its own acidity. Acidity is not a nutrient, but it decides how well a crop takes the nutrients up.

### Natural levels

Each soil has natural levels, which real soils set. The table gives them for each soil that can be tilled; playtesting tunes the values behind the labels:

| Soil            | Nitrogen | Phosphorus | Potassium | Acidity       |
|:----------------|:---------|:-----------|:----------|:--------------|
| River silt      | High     | High       | High      | Neutral       |
| Loam            | Medium   | Medium     | High      | Neutral       |
| Chalk           | Low      | Low        | Low       | Alkaline      |
| Sand            | Low      | Low        | Low       | Acid          |
| Thin stony soil | Low      | Low        | Medium    | Acid          |
| Peat            | High     | Low        | Low       | Strongly acid |

Peat holds much nitrogen, but bound up and slow to release, so it farms poorly until it is drained and limed. Draining belongs to [Ground wetness](https://github.com/NoNamer777/feudum/issues/255).

Only tilled ground loses nutrients. On wild land, what grows decays where it stands, so the ground stays at its natural levels. Newly cleared land therefore gives rich first harvests, as it did in the period.

### What a crop needs

[Plant species](plant-species.md) lists what each crop and field weed needs of each nutrient, and the acidity it tolerates. Legumes, such as peas, beans, vetches, and clovers, fix their own nitrogen.

A crop grows and yields as well as its scarcest nutrient allows, measured against what it needs, and plenty of the others does not make up for it. Acidity outside the crop's range counts as one more shortage, since the crop then takes up nutrients poorly: acid ground starves a wheat crop even when it holds plenty. These effects come on top of the soil, wetness, and shade of [Ground and shade](plants.md#ground-and-shade).

A surplus does no harm, except that too much nitrogen makes grain grow tall and lodge: wind and rain lay it flat, and part of the harvest is lost.

### Reading the ground

Nothing shows nutrients as a number, a bar, or a label. Players read them from the ground and what grows on it:

- **The crop** shows each shortage as it really does: pale, yellowing leaves for nitrogen, purplish leaves and stunted growth for phosphorus, and leaf edges scorched brown for potassium. How thick and tall it stands, and what it yields, show the rest.
- **The tilled soil** looks darker the more manure has gone into it.
- **The wild plants** hint at acidity, since each grows on the soils [Plant species](plant-species.md) gives it: heather and gorse grow on acid sand, and marjoram on chalk.

## Losing and restoring nutrients

A crop draws nutrients from its block as it grows, and so do the weeds among it. What stays on the field after harvest, such as stubble, roots, and the haulm of peas and beans, returns part of what it took once it rots or is plowed in. Straw carted away takes its share with it.

### Resting ground

Ground left resting, as fallow or untilled, drifts back toward its natural levels, each at its own pace:

- **Nitrogen** returns within a year or two, from rain and from the wild clovers and weeds that grow on fallow.
- **Phosphorus and potassium** return only over decades.
- **Acidity** drifts back over years, so lime wears off.

Fallow therefore restores nitrogen well and the rest poorly.

### Restoring the ground

Players and villagers put nutrients back in these ways, each with its real effect:

| Source           | Nitrogen | Phosphorus | Potassium | Acidity        | Notes                                                               |
|:-----------------|:---------|:-----------|:----------|:---------------|:--------------------------------------------------------------------|
| Manure           | Yes      | Yes        | Yes       | Eases a little | Dung and soiled straw from stalls, as [Manure](#manure) describes   |
| Folding          | Yes      | Yes        | Yes       | Eases a little | Animals penned on fallow or stubble dung it where they stand        |
| Legumes          | Yes      | No         | No        | No             | Their roots and haulm leave nitrogen behind                         |
| Marl and chalk   | No       | No         | No        | Sweetens       | Dug from pits and spread on acid ground                             |
| Wood ash         | No       | Yes        | Yes       | Sweetens       | From burned wood                                                    |
| Seaweed          | Yes      | No         | Yes       | No             | Gathered on coasts                                                  |
| Household refuse | Yes      | Yes        | Yes       | No             | Kitchen waste, ashes, and straw from the midden, mostly for gardens |

Folding needs the livestock of [Animals](https://github.com/NoNamer777/feudum/issues/228). Burnt lime, which needs a kiln, belongs to [Crafts](https://github.com/NoNamer777/feudum/issues/247), and paring and burning turf to [Fire](https://github.com/NoNamer777/feudum/issues/248). Bone meal, a 19th-century practice, has no place.

### Manure

Dung and soiled straw collect in stalls and are carried to a midden, where they rot over months into manure; rotted manure is worth more than fresh. A pitchfork spreads it, and plowing or digging works it into the soil. Manure left lying on top loses most of its nitrogen to the air.

### Flood silt

A flood that leaves silt on the ground brings that ground's nutrients toward the levels of river silt, so flood plains renew themselves, as they did in the period. When and where floods leave silt belongs to [Erosion](https://github.com/NoNamer777/feudum/issues/256).

## Rotation

Nothing enforces a rotation, and a field keeps no record of what grew on it before. The rules make the three-field rotation pay on their own: winter grain must be sown in autumn, as [Winter grains](plants.md#winter-grains) sets, grain draws nitrogen down, legumes put some back, and fallow rests the ground. A player who sows wheat on the same field every year watches its yield fall.

## Working the ground

### Clearing wild land

A plow needs cleared ground. Trees are felled with an axe, and their stumps and roots grubbed out with a mattock, as [Tools](../crafts/tools.md#using-a-tool) sets; then the land can be plowed. A plow refuses ground with roots or stumps in it, but breaks grass turf without help.

### Breaking the ground

Ground is broken in two ways:

- **By hand**, digging with a spade or a hoe, which works any soil that can be tilled, but slowly. It suits gardens and small plots.
- **With a plow** drawn by a team, many times faster, for fields.

Two plows exist, as in the period:

| Plow       | Team     | Work                                                              | Speed                                              |
|:-----------|:---------|:------------------------------------------------------------------|:---------------------------------------------------|
| Ard        | Two oxen | Scratches the soil, and leaves weeds in place                     | Full on light soils; slower and shallower on heavy |
| Heavy plow | Larger   | Turns the soil over with its moldboard, burying weeds and stubble | Full on every soil                                 |

Loam and river silt count as heavy ground; sand, chalk, thin stony soil, and peat as light. The draft animals, and how a team is harnessed, belong to [Animals](https://github.com/NoNamer777/feudum/issues/228).

To plow, a player walks behind the team holding the plow, which tills each block it passes over. The player steers the team and turns it at the end of each row. A villager plows the same way.

A sustained frost freezes the ground, as it does still water in [Seasons](../world/seasons.md#snow-and-ice), and frozen ground cannot be plowed, dug, or hoed. How wet ground works belongs to [Ground wetness](https://github.com/NoNamer777/feudum/issues/255).

### Sowing

Sowing takes one seed item for each block, so the return per seed in [Harvest](plants.md#harvest), about 4 for wheat, is the number of items reaped for each one sown. Seed goes in two ways:

- **Broadcast**: grain, pulses, and flax are scattered by hand over a swath of tilled ground as the player walks.
- **Set one at a time**: garden crops, beans, and sets such as onion bulbs are planted block by block.

### Covering seed

Broadcast seed needs covering. A harrow drawn by a team covers the swath it passes over, as the plow tills, and a rake does the same by hand, more slowly. Harrowing also breaks up the clods a heavy plow leaves. Seed left on the surface, or sown into clods, sprouts less often, and birds take it, as [Plant diseases and pests](https://github.com/NoNamer777/feudum/issues/250) describes.

### Weeds

Field weeds, the species [Plant species](plant-species.md#field-weeds) lists in "Fields", sow themselves into tilled ground. They compete with the crop for nutrients and light, so the crop yields less. Hoeing pulls them out, and the heavy plow buries them; the ard leaves them standing. Their seed is reaped with the crop and sown with it the next year unless the seed is cleaned first, which belongs to [Food](https://github.com/NoNamer777/feudum/issues/246).

### The plow and the harrow

The plowshare and coulter, the iron that cuts the soil, dull and wear like a tool's edge and head, and are mended the same way, as [Wear](../crafts/tools.md#wear) describes. Making the plow and the harrow belongs to [Crafts](https://github.com/NoNamer777/feudum/issues/247).

## Livestock

Grazing animals eat and trample crops, so fields need fences or hedges to keep them out. How animals graze, and which barriers hold which animals, belong to [Animals](https://github.com/NoNamer777/feudum/issues/228); laying a hedge is a job for the billhook in [Tools](../crafts/tools.md#the-tools).

## Villagers

Villagers work fields under the same rules as players. When they work belongs to [Villager schedules](https://github.com/NoNamer777/feudum/issues/214), and how a player directs what gets sown where to [Village orders](https://github.com/NoNamer777/feudum/issues/271).

## Land nobody keeps loaded

When unloaded land loads again, its tilled ground and nutrients jump to the state the missed days imply, as [plants](plants.md#land-nobody-keeps-loaded) do. Village fields follow [Village catch-up](https://github.com/NoNamer777/feudum/issues/216).

## Vanilla farming

Feudum's fields replace vanilla's, so vanilla farmland and tilling with a vanilla hoe are hidden. Tilled ground needs no water within 4 blocks, bone meal grows nothing, and the composter is hidden. Trampling turns no ground back to dirt; it only damages crops, as [Contact](plants.md#contact) describes.
