# Cloth

Wool, flax, hemp, cotton, and silk become yarn and thread, and then cloth, through spinning, weaving, fulling, dyeing, and bleaching. Every step is work that players can do by hand with the same blocks the roles use, while a village's spinners, weavers, and finishers do it in bulk. A village that wants to be warm in winter shears its flocks and pulls its flax long before the tailor sews the winter clothes.

Cloth ends where [clothing](clothing.md) begins: the tailor sews finished cloth into garments, blankets, and patches.

## Who it affects

- **Players** make cloth everywhere in the world, vanilla villages included. Cloth-making is work rather than a hazard, so nothing changes in Creative, Spectator, or Peaceful.
- **Feudum villagers** spin, weave, and finish cloth, as [Villagers](#villagers) describes. Vanilla villagers keep their vanilla trades.
- **Sheep** grow a fleece once a year, as [Wool](#wool) describes.

## Fibers

| Fiber  | Source                                               | Climate                                       | Gives                         |
|:-------|:-----------------------------------------------------|:----------------------------------------------|:------------------------------|
| Wool   | Sheep, shorn in late spring                          | Wherever sheep live                           | Wool cloth, fulled wool, felt |
| Flax   | A crop, sown in early spring, pulled in early summer | Temperate and cold                            | Linen, linen thread, tow      |
| Hemp   | A crop, sown in late spring, cut in late summer      | Temperate and cold                            | Canvas, twine, rope, tow      |
| Cotton | A crop, sown in spring, picked in autumn             | Savannas, and deserts and badlands near water | Fustian, cotton wadding       |
| Silk   | Silkworms fed on mulberry leaves                     | Cherry groves                                 | Silk thread, silk cloth       |

Cotton and silk are regional: only villages in their biomes produce them, and other villages buy them, as the planned [trade mechanic](README.md#planned) describes. Medieval Europe wore wool and linen, and bought most of its cotton and silk from the south and the east.

### Wool

- **Shearing.** Vanilla shears take a sheep's fleece as **raw fleece**, a new item in the color of the sheep, instead of wool blocks. The fleece regrows once a year and is ready from late spring, so a sheep sheared in autumn faces the winter bare, as the [temperature document](temperature.md#livestock) warns.
- **Slaughter.** A sheep killed unshorn drops a sheepskin, as [clothing](clothing.md#fur) describes, and a shorn sheep drops only mutton.
- **Washing.** Raw fleece is greasy and dirty. Washing it in water gives clean fleece, and so does washing the sheep in a stream before shearing, as medieval shepherds did.
- **Combing.** A pair of **wool combs** combs one washed fleece into two **combed wool**, ready to spin. Combing leaves short fibers called **noils** now and then, which go to felt.

### Flax and hemp

- **Flax.** A new crop that ripens in about a season. It is pulled up by the roots to keep the full length of the fiber, and gives flax stalks and flaxseed for sowing. Linseed oil stays a future input outside this mechanic.
- **Hemp.** A new crop that grows two blocks tall and is cut rather than pulled. It gives hemp stalks and hempseed, and coarser fiber than flax.

Both have to be retted and dressed before they can be spun, as [Retting and dressing](#retting-and-dressing) describes.

### Cotton

Cotton is a new crop of hot climates, which grows in savannas, and in deserts and badlands within reach of water. It is sown in spring and its bolls are picked in autumn. The seeds are rolled out on a **roller gin**, and the fiber is beaten loose with a **cotton bow**, ready to spin.

### Silk

- **Mulberry.** The white mulberry is a new tree that grows wild only in cherry groves. It gives mulberry leaves, and mulberries, a fruit that keeps 4 days, like berries.
- **Silkworms.** Wild mulberry trees sometimes carry silkworm cocoons, which hatch into the first silkworms. Silkworms live in a new **silkworm tray**, which needs fresh mulberry leaves in spring and early summer and works only in mild to warm air.
- **Reeling.** Cocoons are boiled in the [kettle](thirst.md#purifying) and reeled into raw silk on a new **silk reel** block.
- **Throwing.** Raw silk is thrown, or twisted, into silk thread on the spindle or the spinning wheel.

## Retting and dressing

Retting rots the stalks of flax and hemp loose from their fiber, in one of two ways:

- **Pond retting.** Stalks bundled into water ret in a few in-game days. The retting pond is a strong [polluter](sanitation.md#polluters), sited at the edge of the village and downstream of wells and homes.
- **Dew retting.** Stalks laid out on grass, as a layer that shows on the ground, ret in about twice the time. Dew retting pollutes nothing, but it needs dew or rain, and frost stops it.

Stalks turn from green to gray as they ret. Stalks left too long are over-retted: their fiber rots, and they dress into tow only. Retted stalks dry on the [drying rack](food-spoilage.md#preservation) before they are dressed.

Dressing takes three steps:

1. **Breaking.** The **flax brake**, a new block, crushes the woody core of the stalks.
2. **Scutching.** A **scutching knife** scrapes the broken core away on a scutching board.
3. **Heckling.** The **heckle**, a new block of iron teeth, combs the fiber into long **line** and short, coarse **tow**.

Hemp is retted and dressed the same way, and its line is coarser than flax line.

## Spinning

Fiber is spun into yarn in one of two ways:

- **Distaff and spindle.** The distaff goes in the off hand, loaded with combed wool, line, tow, or cotton, and the spindle goes in the main hand. Holding use spins one yarn every few seconds, at walking speed, as medieval women spun on the move.
- **Spinning wheel.** A block that the carpenter builds. It spins about three times as fast, but only while the spinner sits at it. The spinning wheel reached Europe in the 13th century.

Yarn spun on the wheel is as good as yarn spun on the spindle.

### Yarn and thread

| Yarn or thread | From                    | Use                                            |
|:---------------|:------------------------|:-----------------------------------------------|
| Wool yarn      | Combed wool             | Wool cloth                                     |
| Linen yarn     | Flax line               | Linen, and the warp of fustian                 |
| Hemp yarn      | Hemp line               | Canvas and twine                               |
| Tow yarn       | Flax or hemp tow        | Sackcloth                                      |
| Cotton yarn    | Ginned and bowed cotton | The weft of fustian                            |
| Linen thread   | Two linen yarns, plied  | Sews every garment                             |
| Wool thread    | Two wool yarns, plied   | Sews wool garments, blankets, and patches only |
| Silk thread    | Raw silk, thrown        | Sews every garment                             |
| Twine          | Two hemp yarns, plied   | Works wherever vanilla string does             |

Yarns are plied on the spindle or the wheel. Cotton yarn is never thread. Medieval tailors sewed mostly with linen thread, and wool garments were also sewn with wool thread, which matched the cloth but snapped more easily.

## Weaving

The vanilla loom becomes the **treadle loom**, the loom of the period, which the carpenter builds. It weaves yarn into cloth, and keeps its banner patterns, since banners are cloth.

- **Lengths.** Each kind of cloth is a stackable item, a **length**. Two yarns weave one length.
- **Bolts.** Nine lengths make a **bolt**, a placeable block for storing and displaying cloth, as hay bales store wheat.
- **Time.** A player holds use for a few seconds per length. A villager takes a working day per bolt, as the tailor takes a working day per garment.

### Kinds of cloth

| Cloth          | From                                           | Use                                                           |
|:---------------|:-----------------------------------------------|:--------------------------------------------------------------|
| Wool cloth     | Wool yarn                                      | Tunics, hose, hoods, mittens, and banners                     |
| Fulled wool    | Wool cloth, fulled                             | Cloaks and blankets                                           |
| Linen          | Linen yarn, in its natural gray                | Shirts and every linen garment                                |
| Bleached linen | Linen, bleached                                | The same garments in white, and the only linen that takes dye |
| Canvas         | Hemp yarn                                      | Sails, tents, and awnings, for later mechanics                |
| Sackcloth      | Tow yarn                                       | Sacks, and patches for sacks                                  |
| Fustian        | A warp of linen yarn and a weft of cotton yarn | Tunics and hose, between wool and linen                       |
| Silk cloth     | Silk thread                                    | Silk shirts, coifs, tunics, and hose                          |
| Felt           | Fleece or noils, felted                        | Hats, and the lining of fur hats                              |
| Waxed linen    | Linen and beeswax                              | The waxed coat                                                |

Felt and waxed linen are not woven, as [Felt and waxed linen](#felt-and-waxed-linen) describes. [Clothing](clothing.md#garments) lists the garments each cloth makes.

## Fulling and finishing

Woven wool is loose and thin until it is fulled:

- **Fulling.** Wool cloth soaks in the **fulling trough** with urine from the [urine tub](sanitation.md#noisome-trades) and fuller's earth, and a player or the fuller treads it underfoot. The fuller's old English name, "walker", comes from this work. The fulling trough is a moderate polluter.
- **Tentering.** Cloth comes out of the trough as wet fulled wool, and has to dry on a **tenter frame** outdoors. It dries in dry weather and stops in rain. Wet fulled wool left to dry anywhere else shrinks back into wool cloth.
- **Fulling mill.** A mill whose water-driven hammers full cloth faster, and without treading. The builder raises it on a water wheel, like the miller's mill.

**Fuller's earth** is a kind of clay. It is a new block that generates in small patches among vanilla clay deposits, in rivers, swamps, and lush caves, and drops fuller's earth when dug with a shovel.

### Finishing

Fulled wool can be finished on the tenter frame, once it has dried:

- **Raising.** A **teasel handle**, a tool that holds dried teasel heads, brushes up the nap of the cloth.
- **Shearing.** Vanilla shears crop the raised nap smooth.

Finishing is optional. **Finished cloth** looks smoother, and garments sewn from it last one season longer before they wear. The planned ranks mechanic may reserve finished cloth for the higher estates.

The **fuller's teasel** is a new crop of temperate climates that flowers in its second summer. Its seed heads are dried for the teasel handle.

## Dyeing

Three new plants grow in the dyer's dye garden:

| Plant  | Part                       | Color  | Climate   |
|:-------|:---------------------------|:-------|:----------|
| Woad   | Leaves                     | Blue   | Temperate |
| Madder | Roots, dug after two years | Red    | Temperate |
| Weld   | Whole plant                | Yellow | Temperate |

Cloth takes the 16 vanilla colors. Vanilla dye items stay for blocks, and also work as dyestuffs in the vats.

- **The dye vat.** A heated copper over a fire, which the smith makes. Madder, weld, and vanilla dyes need **alum** to bind to the fiber. Alum comes from alunite in badlands, or from the merchant, as [clothing](clothing.md#fur) describes.
- **The woad vat.** Woad needs no alum. Its leaves are crushed and rolled by hand into **woad balls**, which dry on the drying rack and then ferment in the woad vat with urine and [lye](sanitation.md#household-refuse). The woad vat is a strong polluter, and dyers were known for its smell.
- **Mixing.** Dyeing one color over another mixes them by the vanilla dye recipes, as medieval dyers did: woad over weld gives green, and woad over madder gives purple.
- **When to dye.** Fleece, yarn, cloth, and garments can all be dyed. Fleece or yarn dyed before weaving fades more slowly, so a garment sewn from it keeps its color one wear stage longer. This is the origin of the phrase "dyed in the wool".

Garments take the color of their cloth, and a garment can be re-dyed at the dye vat, as [clothing](clothing.md#garments) describes. Dyeing wool blocks keeps its vanilla crafting recipe.

## Bleaching

Linen is gray when it comes off the loom. The whitster bleaches it white in three steps:

1. **Bucking.** Soaking the linen in a cauldron of lye, made from household ash.
2. **Souring.** Soaking it in a cauldron of buttermilk from the dairymaid.
3. **Crofting.** Laying it out in the sun on a **bleaching field** of grass, as a layer that shows on the ground.

The cycle repeats a few times over several days. It works only in spring and summer, and only in dry weather, so rain stops a bleaching field.

## Felt and waxed linen

- **Felt.** The hatter works fleece or noils into felt with hot water and lye, on a **felting board** beside a kettle, as medieval hatters did. Dyed fleece gives colored felt.
- **Waxed linen.** Linen dipped into beeswax melted in a vanilla cauldron over a fire. Anyone can wax linen, and the tailor waxes it for the village's waxed coats.

## Cordage

Hemp also gives twine and rope:

- **Twine.** Two hemp yarns plied together. Twine works wherever vanilla string does: bows, crossbows, fishing rods, scaffolding, tripwire, and the [box trap](vermin.md#traps-and-ratsbane). Spiders and cobwebs still drop vanilla string.
- **Rope.** Laid from twine on a **ropewalk**, a long, straight path where the roper twists strands of twine together. Leads are crafted from rope, with no slime ball, and the windlass of the [well head](thirst.md#water-stores) needs rope.
- **Rope block.** A new block of rope that hangs down from the block above it, and can be climbed like a ladder.

## Vanilla wool

Shearing no longer drops wool blocks, so the vanilla blocks made from wool change:

- **Wool blocks.** Crafted from four raw fleece, in the color of the fleece. They keep the best [insulation](temperature.md#insulation), and moths eat them.
- **Beds and carpets.** Keep their wool block recipes.
- **Banners.** Sewn at the [sewing table](clothing.md#sewing) from six lengths of wool cloth and a stick, and patterned at the loom.
- **String.** The recipe that turns string into wool is hidden.

## Storage and moths

[Clothes moths](vermin.md#clothes-moths) eat wool, silk, and fur. Stored raw fleece, combed wool, noils, wool yarn, wool thread, wool cloth, fulled wool, felt, raw silk, silk thread, silk cloth, and bolts of any of them can turn moth-eaten. Linen, cotton, hemp, canvas, and sackcloth are safe. The defenses of the vermin mechanic, such as herb sachets, airing, and the garderobe, protect cloth as they protect clothing, and clothes pegs hold cloth on the wall.

## Quantities

| Step     | Ratio                                                           |
|:---------|:----------------------------------------------------------------|
| Combing  | One washed fleece gives two combed wool, and now and then noils |
| Spinning | One combed wool, line, tow, or cotton spins one yarn            |
| Weaving  | Two yarns weave one length                                      |

Garments take these lengths:

| Lengths | Garments                                      |
|--------:|:----------------------------------------------|
|       1 | Hood, coif, mittens                           |
|       2 | Shirt, hose                                   |
|       3 | Tunic                                         |
|       4 | Cloak, mantle, waxed coat, blankets, gambeson |

A villager's yearly wardrobe takes the fleece of about three sheep and the flax of about twenty blocks of field, close to what medieval flocks and fields yielded. Server config scales every ratio.

## Reading cloth

Players judge every step by what they see and hear, with no bar and no number:

- Stalks turn gray as they ret, and darker once over-retted.
- Cloth on the tenter frame darkens while wet and lightens as it dries.
- Linen on the bleaching field whitens with each cycle.
- Tooltips name the stage in words, such as "half-retted", "over-retted", "wet", "finished", or "dyed in the wool".

Server config scales how long the natural steps take: retting, drying, tentering, and bleaching.

## Villagers

Feudum villagers make cloth like a medieval village did:

- **Households.** Every adult spins with the distaff in the evenings by the fire and in idle hours, so a village has a steady trickle of yarn. Households spin, but never weave, so a village needs at least one loom.
- **Roles.** Each step of the work belongs to a role, as the table below shows.
- **Rhythm.** The work follows the year, as [Seasons and climate](#seasons-and-climate) describes.

These roles make what the village needs:

| Item                                                                                                                                       | Maker     | Materials                                              |
|:-------------------------------------------------------------------------------------------------------------------------------------------|:----------|:-------------------------------------------------------|
| Flax, hemp, cotton, teasels, retted stalks                                                                                                 | Farmer    | Seed, and the retting pond or a dew-retting field      |
| Raw fleece                                                                                                                                 | Herder    | Washed sheep, shorn in late spring                     |
| Line and tow                                                                                                                               | Heckler   | Retted, dried flax and hemp stalks                     |
| Combed wool, noils, ginned cotton                                                                                                          | Spinner   | Washed fleece and cotton bolls                         |
| Yarn, linen thread, wool thread                                                                                                            | Spinner   | Combed wool, line, tow, and cotton                     |
| Twine and rope                                                                                                                             | Roper     | Hemp yarn                                              |
| Raw silk, silk thread, silk cloth, ribbons                                                                                                 | Silkwoman | Silkworms and mulberry leaves                          |
| Wool cloth, linen, canvas, sackcloth, fustian                                                                                              | Weaver    | Yarn                                                   |
| Fulled wool                                                                                                                                | Fuller    | Wool cloth, urine, and fuller's earth                  |
| Finished cloth                                                                                                                             | Shearman  | Fulled wool and teasels                                |
| Dyed fleece, yarn, cloth, and garments                                                                                                     | Dyer      | Woad, madder, weld, vanilla dyes, alum, urine, and lye |
| Bleached linen                                                                                                                             | Whitster  | Linen, lye, and buttermilk                             |
| Felt                                                                                                                                       | Hatter    | Fleece or noils, and lye                               |
| Waxed linen                                                                                                                                | Tailor    | Linen and beeswax                                      |
| Treadle loom, spinning wheel, tenter frame                                                                                                 | Carpenter | Planks and sticks                                      |
| Distaff and spindle, flax brake, scutching knife and board, felting board, teasel handle, roller gin, cotton bow, silkworm tray, silk reel | Carpenter | Planks and sticks                                      |
| Wool combs and heckle                                                                                                                      | Smith     | Iron and planks                                        |
| Dye vat                                                                                                                                    | Smith     | Copper                                                 |
| Fulling trough and woad vat                                                                                                                | Cooper    | Planks and barrel hoops                                |
| Fulling mill                                                                                                                               | Builder   | A water wheel, planks, and stone                       |

The heckler, the shearman, and the roper were trades of their own in medieval towns, and the silkwomen of medieval London reeled and threw silk and wove ribbons.

## Seasons and climate

The work follows the year:

- **Late spring.** Sheep are washed and shorn.
- **Summer.** Flax is pulled, hemp is cut, woad and weld are harvested, and pond retting is done.
- **Late summer and autumn.** Dew retting and dressing, cotton picking in hot climates, and every second autumn, digging madder roots.
- **Winter.** Spinning and weaving peak indoors, and households spin by the fire.
- **Spring and summer.** Fulling, tentering, and bleaching, which all need dry weather.

Climate sets which fibers a village grows:

- **Temperate and cold climates.** Wool, flax, and hemp. Woad, madder, weld, and teasels grow in temperate climates only.
- **Arid and tropical climates.** Wool and cotton, with flax and hemp bought from cooler villages.
- **Cherry groves.** Silk.

Frost stops dew retting, and rain stops tentering and bleaching.

## Related mechanics

Cloth works together with these mechanics:

- **[Clothing](clothing.md).** Garments, blankets, and patches are sewn from cloth and thread, and are dyed at the dye vat.
- **[Vermin](vermin.md).** Moths eat wool, silk, and fur in every form, and sacks are sewn from sackcloth.
- **[Sanitation](sanitation.md).** The retting pond, the fulling trough, and the woad vat are noisome trades. They draw on the urine tub, and ash gives lye.
- **[Temperature](temperature.md).** Sheared sheep feel the cold, wool blocks insulate, and the silkworm tray needs mild to warm air.
- **[Seasons](seasons.md).** Every step has its season, and weather stops retting, tentering, and bleaching.
- **[Thirst](thirst.md).** The kettle boils cocoons, and the well head needs rope.
- **[Food spoilage](food-spoilage.md).** The drying rack dries retted stalks and woad balls, and mulberries spoil like berries.
- **Trade.** Cotton, silk, and alum come from their own regions, and villages elsewhere buy them.
- **Ranks.** Will reserve silk and finished cloth for the higher estates.
- **Skills.** Will make spinning, weaving, and dyeing faster or finer for the skilled, though no step needs a skill.

## Additions and changes

- **Fibers.** New raw fleece, washed fleece, combed wool, noils, flax and hemp stalks, line, tow, cotton bolls, ginned cotton, raw silk, and cocoons.
- **Crops.** New flax, hemp, cotton, teasel, woad, madder, and weld crops.
- **Mulberry.** A new white mulberry tree in cherry groves, with mulberry leaves, mulberries, and wild silkworm cocoons.
- **Silkworms.** A new silkworm tray and silk reel, and silk reeled from cocoons boiled in the kettle.
- **Retting.** Pond retting and dew retting, with over-retting.
- **Dressing.** A new flax brake, scutching knife and board, and heckle.
- **Wool preparation.** Washing fleece and sheep, and new wool combs.
- **Cotton preparation.** A new roller gin and cotton bow.
- **Spinning.** A new distaff and spindle, and a new spinning wheel block.
- **Yarn and thread.** New wool, linen, hemp, tow, and cotton yarn, and new linen, wool, and silk thread.
- **Weaving.** The vanilla loom becomes the treadle loom, which weaves cloth and keeps its banner patterns.
- **Cloth.** New lengths of wool cloth, fulled wool, linen, bleached linen, canvas, sackcloth, fustian, silk cloth, felt, waxed linen, and finished cloth, and a new bolt block that holds nine lengths.
- **Fulling.** A new fulling trough, tenter frame, and fulling mill, and a new fuller's earth block among clay deposits.
- **Finishing.** A new teasel handle, and finished cloth whose garments last a season longer.
- **Dyeing.** A new dye vat and woad vat, woad balls, mixing colors by overdyeing, and colors dyed in the wool that fade more slowly.
- **Bleaching.** Bucking, souring, and crofting on a bleaching field.
- **Felt and waxed linen.** A new felting board, and linen waxed in a vanilla cauldron.
- **Cordage.** New twine that works wherever vanilla string does, rope laid on a ropewalk, leads crafted from rope, and a new climbable rope block.
- **Sheep.** Shearing drops raw fleece instead of wool blocks, the fleece regrows once a year, and a shorn sheep drops only mutton.
- **Vanilla wool.** Wool blocks are crafted from raw fleece, banners are sewn from wool cloth, and the string-to-wool recipe is hidden.
- **Moths.** Moths eat raw fleece, combed wool, noils, wool yarn and thread, raw silk, silk thread, wool and silk cloth, felt, and bolts.
- **Display.** Retting, drying, and bleaching show by look, and tooltips name each stage in words.
- **Villager behavior.** Feudum households spin in the evenings, and each role works its step of the year.
- **Roles.** New heckler, shearman, roper, and silkwoman roles, and new cloth work for the farmer, herder, spinner, weaver, fuller, dyer, whitster, hatter, tailor, carpenter, smith, cooper, and builder.
- **Configuration.** Server settings for the length of the natural steps and the ratios of every step.
