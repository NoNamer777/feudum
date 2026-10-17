# Blocks

The blocks Feudum adds or changes, and the mechanic that describes each. Rooms and structures that the mod detects from ordinary blocks are listed after the blocks. Items are in the [items index](../items/README.md), and crops and plants in the [crops](../crops/README.md) and [plants](../plants/README.md) indexes.

## Heat and building

| Block           | What it is                                        | Mechanic                                                         |
|:----------------|:--------------------------------------------------|:-----------------------------------------------------------------|
| Fireplace       | Burns logs or firewood, and warms its room        | [Temperature](../mechanics/temperature.md#heat-and-cold-sources) |
| Brazier         | A freestanding fire bowl that burns the same fuel | [Temperature](../mechanics/temperature.md#heat-and-cold-sources) |
| Thatch          | A building block with the best insulation         | [Temperature](../mechanics/temperature.md#insulation)            |
| Wattle and daub | A building block with the best insulation         | [Temperature](../mechanics/temperature.md#insulation)            |

## Water

| Block        | What it is                                                  | Mechanic                                      |
|:-------------|:------------------------------------------------------------|:----------------------------------------------|
| Well head    | A stone ring with a windlass and a bucket, over a dug shaft | [Thirst](../mechanics/thirst.md#water-stores) |
| Rain barrel  | Fills with clean water in the rain                          | [Thirst](../mechanics/thirst.md#water-stores) |
| Water trough | Holds water for livestock                                   | [Thirst](../mechanics/thirst.md#livestock)    |
| Kettle       | Boils water clean over a fire                               | [Thirst](../mechanics/thirst.md#purifying)    |
| Salt pan     | Dries salt water into salt in the sun                       | [Thirst](../mechanics/thirst.md#salt)         |

## Food

| Block          | What it is                                                                  | Mechanic                                                                                                   |
|:---------------|:----------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------|
| Salting barrel | A cooper's barrel that cures meat and fish in salt                          | [Food spoilage](../mechanics/food-spoilage.md#preservation)                                                |
| Drying rack    | Dries food and herbs in sun and wind                                        | [Food spoilage](../mechanics/food-spoilage.md#preservation)                                                |
| Crock          | A potter's lidded pot for pickling, fermenting, and preserving, which seals | [Food spoilage](../mechanics/food-spoilage.md#preservation)                                                |
| Butter churn   | Churns milk into butter                                                     | [Food spoilage](../mechanics/food-spoilage.md#preservation)                                                |
| Cheese press   | Presses curds into cheese                                                   | [Food spoilage](../mechanics/food-spoilage.md#preservation)                                                |
| Meat hooks     | Hold meat and fish in the smokehouse                                        | [Food spoilage](../mechanics/food-spoilage.md#preservation)                                                |
| Sealed cask    | A bunged or waxed cask that slows spoilage and keeps rats out               | [Food spoilage](../mechanics/food-spoilage.md#rate), [Vermin](../mechanics/vermin.md#containers-and-sacks) |

## Waste

| Block       | What it is                                                                      | Mechanic                                                          |
|:------------|:--------------------------------------------------------------------------------|:------------------------------------------------------------------|
| Chamber pot | A potter's pot beside the bed, which fills overnight                            | [Sanitation](../mechanics/sanitation.md#privies-and-chamber-pots) |
| Privy seat  | A seat over a cesspit, or over running water                                    | [Sanitation](../mechanics/sanitation.md#privies-and-chamber-pots) |
| Night soil  | Fills a cesspit in visible layers, like snow layers                             | [Sanitation](../mechanics/sanitation.md#cesspits)                 |
| Filth       | Waste left on open ground, and the overflow of a full cesspit                   | [Sanitation](../mechanics/sanitation.md#cesspits)                 |
| Dung        | Builds up in layers on the floor of pens and barns                              | [Sanitation](../mechanics/sanitation.md#livestock-waste)          |
| Dung heap   | Rots organic waste into manure, and becomes a laystall when it takes night soil | [Sanitation](../mechanics/sanitation.md#dung-heap-and-manure)     |
| Midden      | A heap behind the home that grows with household rubbish                        | [Sanitation](../mechanics/sanitation.md#household-refuse)         |
| Urine tub   | Keeps a household's urine for the tanner, the fuller, and the dyer              | [Sanitation](../mechanics/sanitation.md#noisome-trades)           |
| Muck barrel | A cooper's barrel that carries night soil and urine without spilling            | [Sanitation](../mechanics/sanitation.md#handling-waste)           |

## Vermin

| Block        | What it is                                                          | Mechanic                                            |
|:-------------|:--------------------------------------------------------------------|:----------------------------------------------------|
| Nest         | Grows a colony of rats or mice near food                            | [Vermin](../mechanics/vermin.md#nests)              |
| Box trap     | A baited wooden trap that catches one rat or mouse                  | [Vermin](../mechanics/vermin.md#traps-and-ratsbane) |
| Staddle      | Raises a granary out of reach of rats, in wooden and stone versions | [Vermin](../mechanics/vermin.md#the-granary)        |
| Clothes pegs | Hold cloth and clothing on the wall                                 | [Vermin](../mechanics/vermin.md#clothes-moths)      |

## Crafts and trades

| Block           | What it is                                                        | Mechanic                                                                                                      |
|:----------------|:------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------|
| Sewing table    | Sews garments and patches from a list of patterns                 | [Clothing](../mechanics/clothing.md#sewing)                                                                   |
| Pillow mound    | A long, low earthen mound that warren rabbits burrow and breed in | [Clothing](../mechanics/clothing.md#the-warren)                                                               |
| Fulling trough  | Where wool cloth is fulled in urine and fuller's earth            | [Cloth](../mechanics/cloth.md#fulling-and-finishing), [Sanitation](../mechanics/sanitation.md#noisome-trades) |
| Woad vat        | Ferments woad balls into blue dye with urine and lye              | [Cloth](../mechanics/cloth.md#dyeing), [Sanitation](../mechanics/sanitation.md#noisome-trades)                |
| Dye vat         | A heated copper that dyes with madder, weld, and vanilla dyes     | [Cloth](../mechanics/cloth.md#dyeing)                                                                         |
| Flax brake      | Breaks the woody core of retted flax and hemp                     | [Cloth](../mechanics/cloth.md#retting-and-dressing)                                                           |
| Scutching board | Where the scutching knife scrapes the broken core away            | [Cloth](../mechanics/cloth.md#retting-and-dressing)                                                           |
| Heckle          | Combs dressed fiber into line and tow                             | [Cloth](../mechanics/cloth.md#retting-and-dressing)                                                           |
| Spinning wheel  | Spins and plies yarn three times as fast as the spindle           | [Cloth](../mechanics/cloth.md#spinning)                                                                       |
| Tenter frame    | Dries wet fulled wool outdoors, where it is also finished         | [Cloth](../mechanics/cloth.md#fulling-and-finishing)                                                          |
| Fulling mill    | Fulls cloth with water-driven hammers                             | [Cloth](../mechanics/cloth.md#fulling-and-finishing)                                                          |
| Bolt            | Nine lengths of cloth, stored and displayed                       | [Cloth](../mechanics/cloth.md#weaving)                                                                        |
| Felting board   | Where fleece or noils are felted with hot water and lye           | [Cloth](../mechanics/cloth.md#felt-and-waxed-linen)                                                           |
| Silkworm tray   | Where silkworms feed on mulberry leaves                           | [Cloth](../mechanics/cloth.md#silk)                                                                           |
| Silk reel       | Reels boiled cocoons into raw silk                                | [Cloth](../mechanics/cloth.md#silk)                                                                           |
| Straw skep      | The beekeeper's hive, for honey and wax                           | [Thirst](../mechanics/thirst.md#additions-and-changes)                                                        |

## Burial and other blocks

| Block          | What it is                                                           | Mechanic                                                 |
|:---------------|:---------------------------------------------------------------------|:---------------------------------------------------------|
| Grave marker   | Marks a proper grave                                                 | [Disease](../mechanics/disease.md#graves)                |
| Painted cross  | A door decoration that marks a plague house                          | [Disease](../mechanics/disease.md#quarantine)            |
| Sundial        | Shows the date and the season                                        | [Seasons](../mechanics/seasons.md#additions-and-changes) |
| Rope           | Hangs down from the block above it, and can be climbed like a ladder | [Cloth](../mechanics/cloth.md#cordage)                   |
| Fuller's earth | Generates in small patches among clay deposits                       | [Cloth](../mechanics/cloth.md#fulling-and-finishing)     |

## Rooms and structures

| Structure        | What it is                                                                | Mechanic                                                                                                     |
|:-----------------|:--------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------|
| Root cellar      | A room below Y 40, where the air stays mild all year                      | [Food spoilage](../mechanics/food-spoilage.md#storage)                                                       |
| Larder           | A cool room where a household keeps its food                              | [Food spoilage](../mechanics/food-spoilage.md#storage)                                                       |
| Ice house        | A well-insulated room that ice keeps cold                                 | [Food spoilage](../mechanics/food-spoilage.md#storage)                                                       |
| Smokehouse       | A room that a smoldering fire fills with smoke                            | [Food spoilage](../mechanics/food-spoilage.md#preservation)                                                  |
| Granary          | A room raised on staddles, out of reach of rats and mice                  | [Vermin](../mechanics/vermin.md#the-granary)                                                                 |
| Garderobe        | A room with a privy seat, where stored cloth is safe from moths           | [Vermin](../mechanics/vermin.md#clothes-moths)                                                               |
| Greenhouse       | A sheltered, heated room, or a cold frame, where crops grow out of season | [Seasons](../mechanics/seasons.md#additions-and-changes)                                                     |
| Cistern          | An underground store of several blocks that rain or a gutter fills        | [Thirst](../mechanics/thirst.md#water-stores)                                                                |
| Cesspit          | A pit below a privy that fills with night soil                            | [Sanitation](../mechanics/sanitation.md#cesspits)                                                            |
| Communal latrine | A row of privy seats over a larger pit                                    | [Sanitation](../mechanics/sanitation.md#privies-and-chamber-pots)                                            |
| Laystall         | A dung heap outside the village that takes night soil                     | [Sanitation](../mechanics/sanitation.md#gong-farmer-and-laystall)                                            |
| Retting pond     | Where flax and hemp stalks rot loose from their fiber                     | [Cloth](../mechanics/cloth.md#retting-and-dressing), [Sanitation](../mechanics/sanitation.md#noisome-trades) |
| Tannery          | Where the tanner works, at the edge of the village                        | [Sanitation](../mechanics/sanitation.md#noisome-trades)                                                      |
| Shambles         | The butcher's slaughtering place                                          | [Sanitation](../mechanics/sanitation.md#noisome-trades)                                                      |
| Physic garden    | Where the herbalist grows herbs                                           | [Disease](../mechanics/disease.md#medicinal-plants-and-rye)                                                  |
| Dye garden       | Where the dyer grows woad, madder, and weld                               | [Cloth](../mechanics/cloth.md#dyeing)                                                                        |
| Bleaching field  | Grass where linen is laid out to whiten in the sun                        | [Cloth](../mechanics/cloth.md#bleaching)                                                                     |
| Ropewalk         | A long, straight path where rope is laid                                  | [Cloth](../mechanics/cloth.md#cordage)                                                                       |
| Pest house       | A home at least 32 blocks from the others, for pox and plague             | [Disease](../mechanics/disease.md#quarantine)                                                                |
| Burial ground    | Walled or fenced ground for proper graves                                 | [Disease](../mechanics/disease.md#graves)                                                                    |
| Plague pit       | Where bodies go during a plague epidemic                                  | [Disease](../mechanics/disease.md#bodies)                                                                    |

## Changed vanilla blocks

| Block                       | Change                                                                                                           | Mechanic                                                                                                                                 |
|:----------------------------|:-----------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------|
| Every block                 | Gets an insulation class                                                                                         | [Temperature](../mechanics/temperature.md#insulation)                                                                                    |
| Water                       | Is clean, unclean, or salt, and ocean water is salt                                                              | [Thirst](../mechanics/thirst.md#purity)                                                                                                  |
| Water, ice, and snow        | Freeze and melt by the air temperature                                                                           | [Temperature](../mechanics/temperature.md#world-effects)                                                                                 |
| Campfire, furnace, and lava | Warm the room they stand in                                                                                      | [Temperature](../mechanics/temperature.md#heat-and-cold-sources)                                                                         |
| Cauldron                    | Boils water clean over a heat source, washes off soiled, waxes linen, and holds lye and buttermilk for bleaching | [Thirst](../mechanics/thirst.md#purifying), [Sanitation](../mechanics/sanitation.md#accidents), [Cloth](../mechanics/cloth.md#bleaching) |
| Loom                        | Becomes the treadle loom, which weaves cloth and keeps its banner patterns                                       | [Cloth](../mechanics/cloth.md#weaving)                                                                                                   |
| Wool block                  | Crafted from four raw fleece                                                                                     | [Cloth](../mechanics/cloth.md#vanilla-wool)                                                                                              |
| Banner                      | Sewn from six lengths of wool cloth and a stick                                                                  | [Cloth](../mechanics/cloth.md#vanilla-wool)                                                                                              |
| Composter                   | Takes rotten food                                                                                                | [Food spoilage](../mechanics/food-spoilage.md#rotten-food)                                                                               |
| Bed                         | A player can lie in it by day to rest                                                                            | [Disease](../mechanics/disease.md#care)                                                                                                  |
