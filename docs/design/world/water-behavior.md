# Water behavior

How water behaves in Feudum: what it carries, how it flows and pools, where it comes from and where it goes, and how it freezes. [Terrain height](terrain-height.md) sets sea level and the depth of the seas, and [Rivers](rivers.md) where rivers rise and run.

## One water

Feudum's water replaces vanilla's, which never generates and cannot be placed. Fresh water, brackish water, salt water, and brine are the same water: each block of it carries a salinity, kept in grams of salt per liter, as the temperature is kept in degrees Celsius. Nothing on screen shows it; players taste it, or see it in what lives there. Four bands name it, and salt lowers the temperature at which it freezes:

| Band     | Salinity (g/L) | Freezes at       |
|:---------|---------------:|:-----------------|
| Fresh    |      Below 0.5 | 0 °C             |
| Brackish |      0.5 to 30 | 0 °C to -1.6 °C  |
| Salt     |       30 to 50 | -1.6 °C to -3 °C |
| Brine    |       Above 50 | -3 °C to -21 °C  |

The sea holds about 35 g/L and freezes at -1.9 °C. Over the sea the coldest nights fall to about 3 °C, as [Biomes](biomes.md#distance-from-the-sea) sets, so the sea never freezes, while sheltered fresh water inland does.

### Where salt water meets fresh

Salt travels with the water that carries it. Water flowing into a block mixes with the water already there, by the amount of each, and neighboring still water evens out slowly, as salt diffuses.

The world generates with the mix in place: salt water in the sea biomes, fresh water inland, and a brackish gradient up river mouths and salt marsh creeks, longer the larger the river. The river's flow carries that salt back out to sea, so what keeps the gradient in place, the flood tide pushing salt water upstream, belongs to [Tides](https://github.com/NoNamer777/feudum/issues/254). Inland, [salt springs](underground.md#water-underground) generate salt water or brine by the strength of each spring.

## Finite water

Water is finite everywhere: it is never created or destroyed, only moved, as [Where water comes from](#where-water-comes-from) describes. Two sources side by side never make a third, as they do in vanilla.

### Volume

A block holds 1,000 liters of water, and water is kept by the liter. Its surface shows in 8 steps of 125 liters. Less than a step on a block does not show as water: it wets the block, then soaks in or evaporates.

Connected still water pools as one body with a single level, so a bucket taken from a lake lowers the whole lake by a sliver, rather than one block by a step.

### Flow

Water falls, then spreads to its neighbors by the difference in their levels, and keeps its momentum as it moves. Currents come from the slope: water runs faster where its surface drops more steeply, and settles flat where nothing drains it. This is the "virtual pipes" model of water simulation.

### Two layers

Rivers run for kilometers, mostly through land no player keeps loaded, so water is simulated in two layers:

- **In loaded land**, block by block: every block holds its water, which falls, spreads, and flows as this page describes.
- **Across the whole world**, as a network: every sea, lake, river reach, pond, and channel is a body with a volume, a level, and the flow it passes downstream. The network runs whether or not its land is loaded, on a slower step than the blocks.

Where loaded land ends, the two layers hand water to each other. A river therefore carries its water from source to sea, loaded or not. A dam in a loaded reach backs water up behind it, and every reach below it gets less.

## Where water comes from

Every liter has a real source and a real sink:

- **Sources**: springs, which belong to [Underground](underground.md#water-underground) and [Rivers](rivers.md#springs), rain over each river's catchment, and melting snow and ice, whose rate belongs to [Thaw](https://github.com/NoNamer777/feudum/issues/239).
- **Sinks**: the sea, evaporation, and soaking into the ground.

Rain falls into water and vessels open to the sky, and a long rain fills the hollows it falls into. Water open to the sky evaporates in warm, dry weather. Evaporating salt or brackish water leaves its salt behind, as in the salterns of the era. How much rain falls and how dry the air is belong to [Weather](https://github.com/NoNamer777/feudum/issues/215).

Water soaks into soil: fast into sand, slowly into loam, very slowly into clay, and not at all into stone. What it does in the ground, such as how wet it keeps the soil and how high it raises the water table, belongs to [Ground wetness](https://github.com/NoNamer777/feudum/issues/255).

### Rates in real time

Every rate of water runs per real second, as in the real world: how fast water flows, rain falls, water evaporates, and water soaks in. Each process keeps its real ratio to the others, so a river carries as much water per second as a real river of its size and its catchment keeps it fed.

What changes is the total per in-game day. A day lasts 40 real minutes by default, as [Time](time.md) sets, so a day of steady rain lays 1/36 of the water a real day of rain would. A real day's rain in each game day would flood every valley, since rivers drain at real speed.

## Seas, lakes, and rivers

The sea is finite too, but so large that nothing changes its level. It holds at sea level, y -1000, until [Tides](https://github.com/NoNamer777/feudum/issues/254) are designed.

A lake forms wherever the terrain leaves a closed hollow, and fills it with fresh water up to its lowest rim, where the water spills out. Its outflow runs on as a river, as [Rivers](rivers.md#lakes) describes.

Rivers follow their sources. They swell after rain and in the spring melt and shrink in summer, and small streams can run dry. A river in flood spills over its banks onto its flood plain, and the water it leaves there drains back, soaks in, or evaporates.

## Currents

A current adds its speed to everything in the water: swimmers, creatures, boats, and items. A swimmer or boat makes headway upstream only by moving faster than the current. How fast players and creatures swim belongs to [Swimming](https://github.com/NoNamer777/feudum/issues/258).

## Ice

[Seasons](seasons.md#snow-and-ice) freezes still water and never flowing water. A block of water counts as still while its current is slower than 0.5 m/s, so ponds, backwaters, and the slow edges of a river freeze in a hard frost, while the main current stays open. Water freezes at the temperature its salinity sets, as [One water](#one-water) shows. Ice keeps the volume of the water it froze from and gives it back as it melts.

## Blocks and water

A block with open space, such as a fence, a slab, or a grate, holds water in that space and lets it pass through, as an empty block does. Solid blocks, closed doors, and closed sluice gates stop it.

Water seeps slowly through sand and gravel, so a dam or pond bank built of them leaks. Clay, stone, and worked blocks hold it.

Whether and how water wears down the ground, such as rivers cutting their banks or floods washing soil away, belongs to [Erosion](https://github.com/NoNamer777/feudum/issues/256).

## Buckets

A bucket holds 12 liters, as a medieval stave bucket does, and fills from the pool or flow it is dipped in. Poured out, it fills a vessel or trough, or wets the ground beneath it rather than leaving standing water there. Moving water in bulk takes channels, as it did in the era. Whether buckets exist and what they are made of belongs to [Tools](https://github.com/NoNamer777/feudum/issues/243).

Poured water wets the soil, so players and villagers can water plants by hand, as [Plants](../farming/plants.md#ground-and-shade) describes.

## How water looks

Water takes its tint from the biome it lies in: clear in most, and brown with peat in the fen, the raised bog, and the moor. It turns bluer and greener as it grows salty, and murky while a river runs in flood.

## Cost

Simulating every liter costs more than vanilla's water. If testing shows the cost is too high, the network's step grows coarser first, before the block-by-block layer gives way.
