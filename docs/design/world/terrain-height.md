# Terrain height

How high and how deep Feudum's world reaches, where sea level lies, and how the height of the land spreads. [Land and sea](land-and-sea.md) sets where each lies, [Biomes](biomes.md) which biomes cover the land, and [Rivers](rivers.md) how rivers run across it.

## Scale

A block is a meter in every direction, so the land has the heights and slopes of real land. A mountain 2,000 blocks high spreads over several kilometers at its foot, as a real one does. [Seasons](seasons.md#height) cools the air with height at the same scale.

## The world's height

The world takes the full height the game allows: 4,064 blocks, from y -2032 to y 2031. Feudum keeps to that limit rather than change how the game stores the world.

Sea level lies at y -1000. The highest ground reaches y 2000, 3,000 blocks above sea level, which leaves 31 blocks above the tallest peaks for snow and whatever is built on them. Below sea level lie 1,032 blocks of sea and rock. The table sums up the levels:

| Level               |       y | Blocks above sea level |
|:--------------------|--------:|-----------------------:|
| Top of the world    |    2031 |                  3,031 |
| Highest ground      |    2000 |                  3,000 |
| Sea level           |   -1000 |                      0 |
| Deepest ocean floor | ~ -1800 |                 ~ -800 |
| Bottom of the world |   -2032 |                 -1,032 |

These heights are chosen for realism. A taller world costs more to generate and keep in memory, though blocks of plain air cost little. If testing shows the cost is too high, the heights come down.

## Mountains

Western Europe's highest summits do not fit under the limit: Mont Blanc rises to 4,808 m and the Pyrenees to 3,404 m. Feudum's tallest ranges stop at 3,000 m, about as high as the Apennines reach. At that height the air is 20 °C colder than at sea level: far inland, on the warmest days the summits average -1 °C, though afternoons reach 5 °C. Whether they keep their snow through summer belongs to [Thaw](https://github.com/NoNamer777/feudum/issues/239).

The height of the land spreads as it does in Western Europe. Most of it is lowland and hills, a few hundred blocks above sea level at most, and uplands rise to about 1,500 blocks. High ranges are rare and far apart, so a range is a landmark to travel to, where vanilla spreads its mountains evenly.

At this scale a mountain shows its shape only from far off: at the game's longest view distance, a player at its foot sees just a slope. How players see distant terrain belongs to [Distant terrain](https://github.com/NoNamer777/feudum/issues/237).

## Seas

Seas keep their real depths where those fit. Shelf seas, such as the North Sea and the Channel, are less than 200 blocks deep. The open ocean drops to about 800 blocks below sea level at most, with rock beneath it, since real ocean depths of 4,000 m and more do not fit.

## Underground

Below the land and the sea floor lies rock, down to the bottom of the world. What fills it, such as stone layers, caves, and ores, and how deep each lies, belongs to [Underground](underground.md).

The bottom 5 blocks of the world are an unbreakable rock of Feudum's own, in place of vanilla's bedrock, so nobody can dig out of the world.
