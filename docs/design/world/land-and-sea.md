# Land and sea

Where land and sea lie across Feudum's world: how landmasses form, how far they reach, how their coasts run, and how the sea floor falls away from them. [Terrain height](terrain-height.md) sets how high the land rises and how deep the sea falls, [Rivers](rivers.md) how water runs from the land to the sea, and [Biomes](biomes.md) what covers both.

## The world's extent

The generator invents the geography from the world's seed rather than copying a real map. The world runs on with no edge of its own design, as vanilla's does, up to the limit the game sets 30 million blocks from its center.

About 60% of the surface is land and 40% sea. That is more land than Earth's 29%, about as much as Western Europe holds, and it leaves room for villages.

## How the land forms

The generator lays out the land with a coarse model of drifting plates. High ranges rise where plates meet, and ocean opens where they part, so ranges, coasts, and ocean basins lie where they would on real land. That keeps high ranges rare and far apart, as [Terrain height](terrain-height.md#mountains) sets. Noise then adds the detail within that layout.

## Landmasses

Landmasses come in every size, from islets to continents. The largest span a few hundred kilometers, so no land lies more than about 300,000 blocks from the sea, as in the heart of France or Germany. The longest rivers run about 1,000 km, as the Loire and the Rhine do.

The sea's mild climate fades over the first 20,000 blocks inland, as [Biomes](biomes.md#distance-from-the-sea) sets. On a large landmass, most land therefore has the inland climate, and only a band along the coast is mild.

## Coasts

The coastline has detail at every scale, from bays kilometers across down to coves and rocks. Its shape follows the land behind it:

- **Hard rock and upland** meet the sea in cliffs and headlands, cut by rias, river valleys the sea has drowned, as in Brittany and Cornwall.
- **Gentle lowland** meets it in long sandy bays backed by dunes.
- **Sheltered inlets** fill with mudflats and salt marsh.

These match the coast biomes of [Biomes](biomes.md#coast). Feudum has no fjords, since they need glaciers and coasts farther north than 50°. How the sea wears coasts away and builds them up during play belongs to [Erosion](https://github.com/NoNamer777/feudum/issues/256), and how the sea rises and falls along them to [Tides](https://github.com/NoNamer777/feudum/issues/254).

## Islands

Most islands rise from the shelf, cut off from the mainland by shallow straits. They range from bare rocks and skerries to islands the size of Britain. In the open ocean, islands are rare: small, rocky, and far apart. Feudum has no volcanic islands, such as the Azores or the Canaries, since they lie beyond Western Europe; those belong to [Regions beyond Western Europe](https://github.com/NoNamer777/feudum/issues/231).

## Seas

Every sea joins every other, so the world has one connected ocean. Feudum has no landlocked salt lakes, which fits the rule of [Rivers](rivers.md#where-rivers-end) that every river reaches the sea.

### From the coast to the open ocean

Shelf sea, up to 200 blocks deep, reaches tens to hundreds of kilometers out from the coast, as the Atlantic shelf off Brittany and the North Sea do. Narrow seas between landmasses lie on the shelf throughout. Beyond the shelf's edge, the floor drops over a continental slope to the open ocean.

The floor of the open ocean is a broad plain 600 to 800 blocks below sea level. A low ridge rises along it where plates part, as the Mid-Atlantic Ridge does. It has no trenches, since those would fall deeper than the 800 blocks [Terrain height](terrain-height.md#seas) allows. Open ocean spans at most about 500 km between landmasses, about as wide as the largest of them, rather than the 5,000 km of the Atlantic.

The table sums up the sea from the coast outward:

| Zone              | Depth (blocks) | Reach                                 |
|:------------------|:---------------|:--------------------------------------|
| Shelf sea         | Up to 200      | Tens to hundreds of km from the coast |
| Continental slope | 200 to ~ 600   | Edge of the shelf                     |
| Open ocean        | 600 to 800     | Up to ~ 500 km between landmasses     |

### Inland seas

Inland seas are shelf seas almost enclosed by land, reached from the ocean through a narrow strait, as the Baltic and the Mediterranean are. They are as salty as the ocean. Salt in the sea is the same everywhere, apart from the brackish water at river mouths that [Water behavior](water-behavior.md#where-salt-water-meets-fresh) describes.

## Where players start

The world spawn always lies on the lowland of a large landmass, within a few kilometers of the coast. A new player then has the mild coast and the inland both within reach.

## Crossing the sea

The sea parts the land into separate landmasses. Most crossings run over shelf seas and straits a few to a few dozen kilometers wide, and the longest over up to 500 km of open ocean. How players and villagers cross the sea belongs to [Sea travel](https://github.com/NoNamer777/feudum/issues/261).

## Cost

Laying out plates across the whole world costs more than vanilla's continent noise. If testing shows the cost is too high, plain continent noise replaces the plate model, and ranges are placed independently of the coast.
