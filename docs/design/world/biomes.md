# Biomes

Which biomes cover Feudum's overworld, where each grows, what it holds, and how it shapes the temperature. Feudum's biomes replace vanilla's, which never generate. [Terrain height](terrain-height.md) shapes the land the biomes cover, and [Seasons](seasons.md) sets the temperature they adjust.

## What a biome sets

A biome sets a temperature offset, its ground and soil, its water and wetness, the kind of vegetation that grows in it, and the tint of its grass and foliage. It names the kind of habitat it offers without listing species: which plants and animals exist belongs to [Plants](https://github.com/NoNamer777/feudum/issues/226) and [Animals](https://github.com/NoNamer777/feudum/issues/228).

Other designs cover the rest of the land. What lies below the surface belongs to [Underground](https://github.com/NoNamer777/feudum/issues/236), how rivers run to [Rivers](https://github.com/NoNamer777/feudum/issues/235), and whether rain or snow falls, in any biome, to [Weather](https://github.com/NoNamer777/feudum/issues/215).

## Real landscapes

Every biome is a real landscape of Western Europe at about 50° north, the region whose seasons the whole world follows. Landscapes of folklore and magic belong to [Fantasy](https://github.com/NoNamer777/feudum/issues/220), and lands beyond Western Europe to [Regions beyond Western Europe](https://github.com/NoNamer777/feudum/issues/231).

The world generates as wilderness, before anyone cleared it: fields, pasture, and managed woods come from villages. The one exception is the land of the villages that already stand in the world, which belongs to [Generated villages](https://github.com/NoNamer777/feudum/issues/240).

## Where biomes grow

The terrain decides which biome grows where: its height, its slope, its distance to the sea, and how wet the ground lies. Noise varies the land only within those rules, so a biome always fits the ground it stands on, where vanilla scatters its biomes by noise alone.

Biomes keep a real scale. Small ones, such as a fen or a stretch of dunes, span a few hundred blocks, and forests and moors span several kilometers.

Neighboring biomes blend over a band of some dozens of blocks. Their ground, vegetation, grass and foliage tint, and temperature offset all mix across it.

## The biomes

Feudum has 17 biomes in five zones: the sea, the coast, the lowland, the upland, and the high ground. The tree species named below are examples; which species exist belongs to [Plants](https://github.com/NoNamer777/feudum/issues/226).

### Sea

- **Open ocean**: deep water over a floor of sand and rock, beyond the shelf, where the sea is deeper than 200 blocks.
- **Shelf sea**: shallower water over sand and gravel, with seaweed beds, off every coast where the sea is less than 200 blocks deep.

### Coast

- **Dunes**: a sand beach backed by dunes of marram grass, on gentle, open coasts.
- **Salt marsh**: mud cut by creeks and covered in salt-tolerant grass, on sheltered coasts and at river mouths.
- **Sea cliffs**: rock cliffs with shingle coves below and grass on top, on steep coasts.

### Lowland

The lowland reaches from sea level to 600 blocks.

- **Oak wildwood**: oak, lime, ash, and hazel on loam. It is the most common biome, covering most of the lowland and hills.
- **Beech forest**: tall beech with little undergrowth, on thin soil over chalk and on well-drained hills.
- **Wooded grassland**: open grass with scattered oaks and thorn scrub on loam, kept open by wild herds. It grows in patches within the wildwood and on river plains.
- **Heath**: heather and gorse with scattered birch and pine, on sandy, poor ground.
- **Riverside woodland**: alder and willow on wet river silt, on the flood plains along rivers.
- **Fen**: reeds, sedge, and alder thickets around standing water, on peat where groundwater stands, such as at lake edges.
- **Raised bog**: domes of peat and bog moss with few trees, on flat, wet lowland.

### Upland

The upland reaches from 600 blocks to the tree line at 1,350 blocks, where the warmest days inland average 10 °C.

- **Mountain forest**: beech, fir, and spruce on thin, stony soil, on slopes from 600 to 1,100 blocks.
- **Moor**: heather and grass moor with blanket bog on peat, on wet, rounded uplands from 300 blocks up.
- **Subalpine forest**: spruce, larch, and stone pine on thin, stony soil, thinning out from 1,100 blocks to the tree line.

### High ground

- **Alpine meadow**: grass, flowers, and dwarf shrubs on thin turf over rock, on gentler ground from the tree line to about 2,100 blocks.
- **Scree and rock**: bare rock, loose stone, and lichen, on steep ground above the tree line and on all ground above about 2,100 blocks.

### Summary

The table sums up each biome's zone, soil, and where it grows:

| Zone       | Biome              | Soil                  | Where it grows                                     |
|:-----------|:-------------------|:----------------------|:---------------------------------------------------|
| Sea        | Open ocean         | Sand and rock         | Beyond the shelf, deeper than 200 blocks           |
| Sea        | Shelf sea          | Sand and gravel       | Off every coast, under 200 blocks deep             |
| Coast      | Dunes              | Sand                  | Gentle, open coasts                                |
| Coast      | Salt marsh         | Mud                   | Sheltered coasts and river mouths                  |
| Coast      | Sea cliffs         | Rock and shingle      | Steep coasts                                       |
| Lowland    | Oak wildwood       | Loam                  | Most lowland and hills                             |
| Lowland    | Beech forest       | Thin soil over chalk  | Well-drained hills and chalk                       |
| Lowland    | Wooded grassland   | Loam                  | Patches within the wildwood, river plains          |
| Lowland    | Heath              | Sand                  | Sandy, poor ground                                 |
| Lowland    | Riverside woodland | River silt            | Flood plains along rivers                          |
| Lowland    | Fen                | Peat                  | Low ground where groundwater stands, lake edges    |
| Lowland    | Raised bog         | Peat                  | Flat, wet lowland                                  |
| Upland     | Mountain forest    | Thin, stony soil      | Slopes from 600 to 1,100 blocks                    |
| Upland     | Moor               | Peat                  | Wet, rounded uplands from 300 blocks up            |
| Upland     | Subalpine forest   | Thin, stony soil      | From 1,100 blocks to the tree line at 1,350        |
| High       | Alpine meadow      | Thin turf over rock   | Gentler ground from the tree line to about 2,100   |
| High       | Scree and rock     | Rock and loose stone  | Steep ground above the tree line, all above 2,100  |

How each soil affects what grows on it belongs to [Plants](https://github.com/NoNamer777/feudum/issues/226).

## Climate

[Seasons](seasons.md#temperature) sets the temperature from the season, the height, and the time of day. Biomes adjust it in two ways: the land near the sea has a milder climate, and each biome has an offset of its own. How the shape of the land changes the temperature locally, such as slopes facing south running warmer and cold air pooling in hollows, belongs to [Microclimate](https://github.com/NoNamer777/feudum/issues/241).

### Distance from the sea

The sea keeps the land near it mild: its winters are warmer and its summers cooler than inland. At the shore, the yearly mean is 2 °C warmer than inland, and the swing between the seasons is 0.55 times as wide. Both fade smoothly to the inland curve of [Seasons](seasons.md#through-the-year-and-the-day) by 20,000 blocks from the sea. Over the sea itself, the shore's climate holds.

Every sea biome counts as the sea for this distance; lakes do not. The narrower swing applies to the year only: each day still swings 4 °C either side of its mean, as Seasons sets.

The table compares the shore with the land far inland, both in a biome with no offset and at sea level. The shore matches Brest, on the Breton coast, and the land far inland matches Frankfurt:

| Place                      | Coldest daily mean | Warmest daily mean |
|:---------------------------|-------------------:|-------------------:|
| At the shore               |               7 °C |              17 °C |
| 20,000 blocks from the sea |               1 °C |              19 °C |

### Offsets

Height and distance from the sea cover most of the climate, so a biome has an offset only where the land itself makes the air colder. The moor runs 1 °C colder, as an exposed, clouded, and windswept upland. Every other biome has an offset of 0 °C. Mountain biomes take their cold from height alone, and fens and bogs leave the cold of low ground to [Microclimate](https://github.com/NoNamer777/feudum/issues/241).

### Snow all year

No biome is cold enough through its offset to keep snow all year, and Feudum has no glacier biome. Only the highest summits come close, and whether they keep their snow through summer belongs to [Thaw](https://github.com/NoNamer777/feudum/issues/239).

## How biomes look

Each biome tints its grass and foliage: lush green in the wildwood and riverside woodland, darker in the beech forest, browner on heath and moor, and gray-green at the coast. The season shifts every tint, as [Seasons](seasons.md#how-seasons-look) sets, and the tints blend across the borders between biomes.
