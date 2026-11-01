# Rivers

How rivers rise, find their way down, grow, and end. [Terrain height](terrain-height.md) sets the land they run across, and [Water behavior](water-behavior.md) how their water flows, freezes, and carries salt.

## Drainage

Rivers come from the land's drainage. The generator traces where rain would run downhill across a coarse version of the terrain. A river forms where enough land drains together, and it cuts its bed into the land so the bed always falls toward the river's end. Every river therefore has a catchment, whose rain the [water network](water-behavior.md#two-layers) keeps feeding it.

A river is not a biome, as it is in vanilla: it runs across the biomes it passes, and its banks take the biome around them. Its flood plains grow riverside woodland, as [Biomes](biomes.md) sets.

## Where rivers rise

A stream begins where its catchment reaches about 1 km², enough to keep water running for most of the year in a land as wet as Western Europe. That gives about 1 to 2 km of stream for every square kilometer of land. A stream's upper reach can run dry in summer, as [Water behavior](water-behavior.md#seas-lakes-and-rivers) allows.

Lakes begin rivers too, where their water spills out, as [Lakes](#lakes) describes. Snow and ice on high ground feed the rivers below them as they melt, at the rate [Thaw](https://github.com/NoNamer777/feudum/issues/239) sets.

### Springs

A stream's head is a spring, where water comes out of the ground. Water is finite, so a spring releases the rain its catchment soaked up, delayed and evened out: it keeps running between rains and weakens in a long drought. How that water moves through the ground belongs to [Ground wetness](https://github.com/NoNamer777/feudum/issues/255).

## Where rivers end

Every river ends at the sea, in a lake, or in a larger river, and its water reaches the sea in the end. Feudum has no closed basins, where water gathers in a low point and leaves only by evaporating, since Western Europe is wet enough that every hollow fills and spills over. Rivers that sink into limestone belong to [Underground](https://github.com/NoNamer777/feudum/issues/236).

A river grows as long as its land allows, with no cap of its own. [Land and sea](land-and-sea.md#landmasses) puts no land more than about 300 km from the sea, so the longest rivers run about 1,000 km.

### Mouths

A river meets the sea in a funnel-shaped estuary with a muddy bed, lined with salt marsh, as the Thames, Seine, and Loire do. A large river flowing into a shallow, sheltered sea drops more silt than the sea carries away, and builds a delta instead, as the Rhine and Meuse do. Salt water reaches up the mouth as [Water behavior](water-behavior.md#where-salt-water-meets-fresh) describes.

## Lakes

Tracing the drainage turns up closed hollows in the terrain. The generator keeps some as lakes and cuts the river's way through the rest. Lakes are common in the high ranges, in hollows scoured by old glaciers, and rare in the lowland, as in Western Europe. A lake fills up to its lowest rim, as [Water behavior](water-behavior.md#seas-lakes-and-rivers) sets, and its outflow runs on from there as a river.

## Width and depth

A river's channel grows with its flow, as a real river's does: its width with about the square root of the flow, and its depth a little more slowly. The channel holds the bankfull flow, the high water a river reaches every year or two, and a larger flood spills onto its flood plain. The table shows illustrative sizes this gives:

| River              | Flow (m³/s) | Width (blocks) | Depth (blocks) |
|:-------------------|------------:|---------------:|---------------:|
| Brook              |      ~ 0.05 |         1 to 2 |          < 0.5 |
| Stream             |         ~ 1 |         3 to 5 |            ~ 1 |
| Thames-sized river |        ~ 65 |       40 to 60 |         2 to 4 |
| Seine-sized river  |       ~ 500 |     120 to 150 |         4 to 6 |
| Rhine-sized river  |     ~ 2,300 |     300 to 400 |        5 to 10 |

## From source to mouth

The generator carves each river's valley as if the river had worn it down over ages, wider the larger the river. A river's course, valley, and bed follow its slope:

- **Steep stretches** run straight, with rapids and step pools, and fall over waterfalls where the bed drops over a ledge of hard rock. Their valleys are narrow and steep-sided, and their beds bare rock and boulders.
- **Below the high ranges**, rivers carrying heavy gravel split into many braided threads across a gravel bed, as Alpine rivers do, and their valleys open out.
- **In the lowland**, rivers meander over beds of sand and silt across broad flood plains and leave oxbow lakes where a bend was cut off.

The bed is made of Feudum's own blocks, and the banks take the ground of the biome around them. The table sums up a river from source to mouth:

| Stretch | Course                                                                 | Valley                 | Bed               |
|:--------|:-----------------------------------------------------------------------|:-----------------------|:------------------|
| Steep   | Straight, rapids, step pools, falls                                    | Narrow and steep-sided | Rock and boulders |
| Upland  | Braided below high ranges                                              | Opening out            | Gravel            |
| Lowland | Meanders, oxbow lakes                                                  | Broad flood plain      | Sand and silt     |
| Mouth   | Estuary, or a delta where a large river meets a shallow, sheltered sea | Salt marsh             | Mud               |

How rivers wear their valleys during play, such as cutting their banks and shifting their bends, belongs to [Erosion](https://github.com/NoNamer777/feudum/issues/256).

## A new world

Every river, lake, and spring generates already running, at the average flow for the season and date the world starts on.

## Cost

Tracing drainage across hundreds of kilometers costs more than vanilla's rivers. If testing shows the cost is too high, the grid the drainage is traced over grows coarser first, so the smallest streams start further downhill. Every river still runs downhill and reaches the sea.
