# Underground

What lies below the surface of Feudum's world: its rock, the loose ground over it, its ores, its caves, and the water that runs through them. [Terrain height](terrain-height.md) sets how deep the world reaches, [Biomes](biomes.md) the soil on top, and [Rivers](rivers.md) the streams that rise from springs and sink into limestone. How players dig into the ground and what limits how deep they go belong to [Mining](https://github.com/NoNamer777/feudum/issues/263), and how ore is smelted and worked to [Crafts](https://github.com/NoNamer777/feudum/issues/247).

## Rock

The rock follows the real geology of Western Europe, so it changes across the land with the terrain above it:

- **High ranges and old massifs** expose hard crystalline and metamorphic rock, as Brittany, Cornwall, the Massif Central, and the Harz do.
- **Uplands** stand on older hard sedimentary rock and slate, as the Ardennes and Wales do.
- **Lowland basins** hold younger, softer rock: chalk, clay, sandstone, and limestone, as the Paris and London basins do.

Each kind of stone is a Feudum block:

| Kind                        | Rocks                                                                           |
|:----------------------------|:--------------------------------------------------------------------------------|
| Crystalline and metamorphic | Granite, gneiss, schist, slate, marble                                          |
| Sedimentary                 | Sandstone, limestone, chalk with flint nodules, mudstone or shale, conglomerate |
| Volcanic                    | Basalt                                                                          |
| Evaporites                  | Rock salt, gypsum                                                               |

Basalt comes from extinct volcanic country, such as the Auvergne and the Eifel. Feudum has no lava and no active volcanoes, as Western Europe has none.

### How the layers lie

The sedimentary layers are tilted and folded, so each crops out in bands across the land, as the chalk and limestone escarpments of the Downs and the Cotswolds do. Beneath them lies a crystalline basement, which rises toward the surface under the uplands and ranges and sinks deep under the basins. No rock lies at a fixed y: the depth of each follows the region.

### Loose ground

Loose deposits lie between the soil and the bedrock: gravel and sand along rivers, glacial till in the north and in the mountains, and wind-blown loess. The soil on top belongs to [Biomes](biomes.md) and [Fields](https://github.com/NoNamer777/feudum/issues/244).

### Under the sea

The land's geology carries on under the shelf seas, beneath a cover of sand and mud. The floor of the open ocean is basalt beneath mud, as real ocean crust is, and holds no ores.

## Depth

The surface lies about 1,000 blocks above the bottom of the world under a basin, and up to 4,000 blocks above it under a high range. Most of what a player seeks lies near the top of that rock:

- **Ores** lie within the top few hundred blocks and are richest near the surface, where weathering enriched them.
- **Caves** reach down to the springs their water drains to, as [Caves](#caves) describes.
- **Below them** lies plain rock, and the crystalline basement lies at the bottom everywhere.
- **The bottom 5 blocks**, from y -2032 to y -2028, are a flat layer of unbreakable rock of Feudum's own, in place of vanilla's bedrock.

Medieval miners rarely dug deeper than 100 to 200 m, because water flooded their mines. What makes digging deep hard in Feudum, such as flooding, bad air, and heat, belongs to [Mining](https://github.com/NoNamer777/feudum/issues/263).

## Ores

Feudum's ores and minerals follow the [era rule](../setting/era.md#the-rule): each is something Western Europeans mined between 1000 and 1300. Fantasy minerals belong to [Fantasy](https://github.com/NoNamer777/feudum/issues/220).

### Districts

Ores gather in ore districts, as real ones do, rather than spreading evenly through the rock as in vanilla. A district is tens of kilometers across, a place to seek out and settle near, as the Cornish tin country, the Harz silver mines, and the Erzberg iron mountain were. Each ore forms in the rock and setting where real deposits form, so the districts follow the geology. Iron is the exception: bog iron and ironstone are found everywhere.

The ores run from common to rare. After iron, a large landmass holds several districts each of lead, coal, and salt, and fewer of tin, copper, and silver. Gold and mercury are the rarest, with a mercury district perhaps once across many landmasses. The spacing of districts is tuned in testing. The table sums up each ore:

| Ore     | Where it forms                                                      | Form           | Rarity               |
|:--------|:--------------------------------------------------------------------|:---------------|:---------------------|
| Iron    | Wetlands, and ironstone in sedimentary rock                         | Bog iron, beds | Everywhere           |
| Lead    | Limestone and slate, as in the Mendips and the Harz                 | Veins          | Several per landmass |
| Coal    | Seams at the edges of the basins, as at Liège and in Northumberland | Seams          | Several per landmass |
| Salt    | Beds in the basins, as at Lüneburg, Salins, and Hallstatt           | Beds           | Several per landmass |
| Tin     | Granite and the stream gravels below it, as in Cornwall             | Veins, placers | Fewer                |
| Copper  | Old massifs                                                         | Veins          | Fewer                |
| Silver  | Lead veins in limestone and slate, as in the Harz                   | Veins          | Fewer                |
| Gold    | Old massifs and the stream gravels below them                       | Veins, placers | Rarest               |
| Mercury | Its own district, as at Almadén                                     | Veins          | Rarest               |

Stone and earths come from the rock and the loose ground: building stone from every rock, flint from chalk, gypsum from beds in the basins beside the salt, and clay, sand, and gravel from the sedimentary rock and the loose deposits.

### Forms

Deposits take the forms real ones do, where vanilla scatters clumps of ore:

- **Veins**: thin, steep sheets along cracks in the rock.
- **Seams and beds**: flat layers within the sedimentary rock, such as coal and ironstone.
- **Placers**: tin and gold washed into stream gravels, which can be worked from the surface.
- **Bog iron**: lumps under wetland.

### Signs at the surface

A deposit shows at the surface where a real one does. Veins and seams crop out on slopes and in stream banks, and a rusty cap of weathered rock, a gossan, marks a metal vein. Placer gravels gather in the streams below a district, coal shows black in valley sides, and salt springs rise over salt beds. How players learn to read these signs belongs to [Mining](https://github.com/NoNamer777/feudum/issues/263).

## Caves

Caves form only where real ones do:

- **Karst** in limestone: cave systems, sinkholes, swallow holes where streams sink, and resurgences where they come out again, as in the Causses, the Mendips, and the Jura.
- **Sea caves** in the cliffs of the coast.
- **Small fissures** elsewhere, with no cave networks through granite, clay, or chalk.

Caves are therefore rare outside limestone country. Their passages are a few meters across, with an occasional large chamber, and Feudum has none of vanilla's vast caverns.

A cave system reaches from the surface down to the spring its water drains to, and flooded passages dip up to about 300 blocks below that spring, as at the Fontaine de Vaucluse. Most caves are therefore tens to a few hundred blocks deep, as in the Mendips and the Causses. Where limestone stands high in a range, rare shaft systems drop over 1,000 blocks from a plateau to a spring in a deep valley, as the Gouffre Berger and the Pierre Saint-Martin do. All of them stay within the limestone, above the plain rock below.

Caves hold their real formations, such as stalactites, stalagmites, and flowstone, each a Feudum block, and are fully dark. Creatures that live in caves, such as bats, belong to [Animals](https://github.com/NoNamer777/feudum/issues/228).

## Water underground

Springs, which feed the streams of [Rivers](rivers.md#springs), rise where the geology puts them:

- **Spring lines** run along the foot of chalk and limestone escarpments, where water-bearing rock lies on clay.
- **Karst water** sinks at swallow holes, runs as underground rivers through the caves, and comes out again at resurgences, so a river that sinks into limestone flows on below the ground.
- **Cave passages** below the water table are flooded.
- **Warm springs** rise in a few rare places where deep faults bring heated water up, as at Bath, Aachen, and Dax, all used for bathing in the period. They are the one sign of heat underground.

How much water each spring carries, and how water moves through the ground, belong to [Ground wetness](https://github.com/NoNamer777/feudum/issues/255).
