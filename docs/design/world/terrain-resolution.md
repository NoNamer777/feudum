# Terrain resolution

How finely Feudum shapes its terrain: the pieces a block splits into, and how generation, digging, building, water, and rendering work with them. [Terrain height](terrain-height.md#scale) makes a block a meter in every direction, which is too coarse for gentle shapes such as low banks, sunken lanes, and the ridge and furrow of old fields. How plowing builds ridge and furrow belongs to [Ridge and furrow](https://github.com/NoNamer777/feudum/issues/274).

## Pieces

A block splits 8 ways in each direction, into 512 pieces of 12.5 cm. Each piece carries its own material, so one block can hold several, such as topsoil over clay or snow on a sloping bank. A block stays whole until something splits it, and only a split block keeps its pieces. The table compares a piece with a block and a [spadeful](#digging), what one stroke of a digging tool takes:

| Unit     |    Size | Pieces | Liters |
|:---------|--------:|-------:|-------:|
| Block    |     1 m |    512 |  1,000 |
| Spadeful |   25 cm |      8 |   15.6 |
| Piece    | 12.5 cm |      1 |   1.95 |

A piece is as high as one of the 8 steps a water surface shows in, so the surfaces of terrain and water line up. It is also low enough to walk up, as [Moving over pieces](#moving-over-pieces) describes.

## How pieces look

A piece shows the part of its material's texture that falls at its place in the world. Split ground therefore reads as the same material as whole ground, at the same pixel scale, stepped at 12.5 cm. The world keeps its pixelated look: it has no slopes or smooth surfaces, only finer steps. How far from the player pieces keep showing, before distant terrain draws them coarser, belongs to [Distant terrain](https://github.com/NoNamer777/feudum/issues/237).

## Generation

World generation shapes every surface it makes to the piece: the land, the sea floor, river beds and banks, and cave walls. Gentle land rises in low steps, and a surface steps a whole block only where it is that steep. Fine and coarse terrain never meet at a seam, such as at a cave mouth or along a coast.

## Natural and worked blocks

Natural ground splits as it is dug: soil, sand, gravel, clay, snow, and rock. Worked blocks, such as planks and dressed stone, stay whole: breaking one takes it whole, and only a craftsman's tool cuts it into pieces. Which tool cuts which block belongs to [Crafts](https://github.com/NoNamer777/feudum/issues/247).

A slab, a stair, or a wall end is a worked block cut to that shape, so Feudum has no slab or stair blocks of their own. Blocks that are not cubes, such as doors, fences, and plants, never split.

## Digging

Each stroke of a digging tool takes a spadeful: 2×2×2 pieces at the spot struck. The spadeful snaps to the grid of pieces rather than to a coarser one, so a careful player can cut a bank or a ditch to the piece. The spade digs soil, sand, gravel, clay, and snow, the mattock hard ground, and the pick rock, as [Tools](../crafts/tools.md#using-a-tool) sets. A second-best tool takes the same amount, more slowly. Bare hands take a single piece, where Tools lets them dig at all.

A stroke takes about a second at best, with a keen spade in loose soil, so a block of soil takes 64 strokes, about a minute. Harder ground, a [duller edge](../crafts/tools.md#the-edge), and [fatigue](../needs/fatigue.md#effects) slow it. A real laborer moved about a cubic meter of soil an hour, so the pace runs faster than real, but large earthworks such as a moat or a mill race still take many villagers. Testing tunes the pace.

Dug ground comes away loose: one item of loose material per spadeful, such as loose loam or loose sand, 64 to a block. What broken rock yields belongs to [Mining](https://github.com/NoNamer777/feudum/issues/263), and what cutting a worked block leaves, such as offcuts and cut pieces, to [Crafts](https://github.com/NoNamer777/feudum/issues/247). How much a player carries, and in what, belongs to [Carrying](https://github.com/NoNamer777/feudum/issues/275).

## Placing

A player places loose material a spadeful at a time, at the spot aimed at, snapped to the grid of pieces. A worked block is placed whole, and a cut piece as it was cut. Whether placed ground packs down over time, as backfill settles, belongs to [Erosion](https://github.com/NoNamer777/feudum/issues/256).

## Settling

Sand, gravel, soil, and snow fall when nothing holds them up, and slump when piled steeper than their angle of repose, the steepest slope they hold: about 34° for dry sand. World generation lays them no steeper. Rock, clay, and worked blocks hold whatever shape they are cut to. How water wears the ground away belongs to [Erosion](https://github.com/NoNamer777/feudum/issues/256).

## Thin layers

Snow builds up a piece at a time as it falls, as [Seasons](seasons.md#snow-and-ice) sets. Less than a piece shows as a dusting on the surface rather than as pieces, as less than a step of water wets a block rather than standing on it. Silt left by a flood lies the same way.

## Water

Water stays one pool per block, kept by the liter as [Water behavior](water-behavior.md#volume) sets. A split block holds water only in its open pieces, about 1.95 liters each, and the water surface rests at the piece steps. A step of water shows once it fills the open pieces at that height, however few: a hollow a spadeful in size holds standing water at 15.6 liters. Water passes from block to block only through the open pieces of the face the two blocks share. A wall of pieces through the middle of a block therefore holds nothing back: a dam holds only where it closes the faces between blocks.

## What stays per block

Only shape and material are kept per piece. Wetness, nutrients, tilled state, temperature, and light stay per block, for three reasons:

- **Cost.** These values spread from block to block across the loaded world. Kept per piece, each would have 512 times as many cells, and so would separate pockets of water within a block.
- **Scale.** What they model changes over a meter or more. A crop's roots reach through more than a block, and air temperature differs over meters.
- **Nothing reads them finer.** A plant stands in a whole block, and smooth lighting already blends light between blocks.

A plant stands on the top of the pieces beneath it, so a crop follows the rise and fall of the ground. A split block lets light through its open space.

## Moving over pieces

Players, villagers, and animals walk up a rise of up to 4 pieces, 50 cm, without jumping. A higher rise takes a jump or a climb, which belongs to [Climbing](https://github.com/NoNamer777/feudum/issues/276).

## Cost

Only split blocks store their pieces, and whole blocks cost what they do now. Shaping every generated surface still splits many blocks. If testing shows the cost is too high, surfaces nobody sees up close, such as cave walls and the deep sea floor, go back to whole blocks first. The piece grows to 25 cm only after that.
