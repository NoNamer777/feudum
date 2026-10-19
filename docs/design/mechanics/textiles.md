# Textiles

Every thread, rope, and bolt of cloth in Feudum is made the long way. Flax rots in a pond for a week before it can be broken, scutched, and hackled, and a fleece is skirted, scoured, carded, and spun for days before the loom sees it. Woolen cloth is fulled in stale urine and stretched on tenters, and dye comes from woad, madder, and weld boiled in a vat. Clothing a household takes a season of work, so a village needs its spinners, weavers, fullers, and dyers. Vanilla string drops from spiders, and its wool and dyes take a single step, so Feudum replaces them.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Textiles works six fibers: flax, hemp, and nettle (the bast fibers), wool, goat hair, and lime bast.
- It starts where the fiber is gathered. [Farming](https://github.com/NoNamer777/feudum/issues/32) grows flax and hemp, and Textiles takes over at the pulled stalk. [Animal husbandry](animal-husbandry.md) owns sheep and goats, their regrowth, and the natural fleece colors of their breeds; Textiles owns the shears, shearing, and the fleece. Nettle and lime trees grow wild, as [world generation](../world-generation/README.md) places them.
- It ends at thread, twine, rope, cloth, felt, matting, dyes, and dyed items. [Clothing](../content/clothing.md) sews garments from them.
- Every historical step of the craft is its own step here, and each takes about as long as it did, so cloth is scarce and valuable.
- Cloth carries no quality: every cloth of a kind is the same until [Cloth quality](https://github.com/NoNamer777/feudum/issues/105) lands.

## Working

- A hand step is done at its block, or with its handheld tool, by holding the use key. Work advances by the Feudum time that passed, and converts the input a little at a time, so stopping keeps what is done.
- A waiting step is a placed block that keeps its own progress, as [Waiting steps](#waiting-steps) describes.
- Villagers work the same blocks at the same rate. Spinning and flax dressing are household work any villager does. [Weaver](https://github.com/NoNamer777/feudum/issues/107), [Fuller](https://github.com/NoNamer777/feudum/issues/108), and [Dyer](https://github.com/NoNamer777/feudum/issues/109) are trades.
- [Tools and blocks](#tools-and-blocks) lists what each step needs.

## Fibers and products

The diagram maps each fiber to the cloth and cordage it yields, and shows where a chain branches. Each arrow stands for one step and skips the rest, which the tables below list. Arrows into cloth are weaving, and the other arrows name their step. Cordage is tan, and felt and matting, which are neither spun nor woven, are gray.

![Six fibers and what they become. Wool is carded into rolags, which are spun into woolen yarn and woven and fulled into woolen, or felted into felt. Combed wool becomes tops, spun into worsted yarn, which is woven into worsted or plied into thread. Flax is hackled into line and tow, spun into fine and coarse yarn, and woven into linen and coarse linen; fine yarn is also plied into thread, and coarse yarn into twine. Nettle and hemp are scutched and spun, then woven into nettle cloth and hemp cloth or plied into twine, and hemp yarn is also laid into rope. Goat hair is carded and spun, then woven into haircloth or laid into rope. Lime bast is retted and peeled into strips, which are twisted into rope or plaited into matting.](images/textiles-fibers.svg)

## Bast fibers

Flax, hemp, and nettle follow one chain:

| Step   | What happens                                                        | Yields         |
|:-------|:--------------------------------------------------------------------|:---------------|
| Pull   | Farming's harvest of flax and hemp, or gathering wild nettle.       | Stalks         |
| Ripple | Drawing the stalks through a rippling comb to strip the seed heads. | Stalks, seed   |
| Ret    | Rotting the stalks until the fiber loosens from the woody core.     | Retted stalks  |
| Dry    | Standing the retted stalks in sheaves.                              | Dry stalks     |
| Break  | Cracking the woody core at a flax brake.                            | Broken stalks  |
| Scutch | Beating the core away on a scutching board with a scutching knife.  | Fiber, shives  |
| Hackle | Drawing the fiber through the iron teeth of a hackle.               | Line, tow      |
| Spin   | Twisting line into fine yarn, or tow into coarse yarn.              | Yarn           |
| Warp   | Winding yarn into a warp on a warping frame.                        | Warp           |
| Weave  | Weaving weft yarn through the warp at a loom.                       | Cloth          |
| Bleach | Optionally, spreading linen or hemp cloth on grass in the sun.      | Bleached cloth |

- Seed from rippling is replanted under Farming and fed to animals under [Hunger](hunger.md). [Oil pressing](https://github.com/NoNamer777/feudum/issues/106) owns linseed and hempseed oil.
- Nettle is gathered wild in summer and needs no rippling.

### Retting

- **Water retting**: a retting bundle sunk in still or slow water rets in about 1 to 2 Feudum weeks, faster in warmer [water](fluids.md). The bundle is a strong [fouling source](fluids.md#fouling), so a village rets in a pond of its own, never upstream of its well.
- **Dew retting**: stalks spread on grass ret in about 3 to 5 Feudum weeks. Rain and dew speed it, and frost and dry weather slow it. It fouls nothing, and once Cloth quality lands it yields poorer fiber.
- **Over-retting**: stalks left past done for about half as long again rot, and lose fiber the longer they stay. Retting needs checking.
- **Standing**: sinking a retting bundle inside a village's territory, in water that its wells draw on or its villagers drink from, lowers a player's [standing](villages.md#standing-and-wishes) a little, as relieving in water does.

### Line and tow

- Hackling splits the fiber into line, the long fine fiber, and tow, the short coarse fiber, at about two parts line to one of tow.
- Line spins into fine yarn for linen cloth and thread. Tow spins into coarse yarn for sacking, twine, and rough cloth.

### Bleaching

- Undyed linen and hemp cloth spread on grass in the sun bleach in about one Feudum week, from natural to bleached. Rain doesn't hurt it, and cloudy days slow it.
- Bleaching never lightens a dyed item.

## Wool

| Step           | What happens                                                             | Yields            |
|:---------------|:-------------------------------------------------------------------------|:------------------|
| Shear          | Clipping the fleece from a sheep with shears.                            | Fleece            |
| Skirt and sort | Stripping the soiled edges of the fleece.                                | Fleece, skirtings |
| Scour          | Washing the grease out in warm water in a heated cauldron.               | Scoured wool      |
| Card or comb   | Carding into short, fluffy rolls, or combing into long, parallel fiber.  | Rolags, tops      |
| Spin           | Spinning rolags into woolen yarn, or tops into worsted yarn.             | Yarn              |
| Warp and weave | As for the bast fibers.                                                  | Cloth             |
| Full           | Shrinking and thickening woolen cloth, as [Fulling](#fulling) describes. | Fulled cloth      |
| Tenter         | Stretching the wet cloth on a tenter frame to dry square.                | Tentered cloth    |
| Raise and crop | Raising the nap with a teasel frame, then cropping it level with shears. | Woolen cloth      |

- A fleece takes the grime and mud of its sheep at shearing, as [Hygiene](hygiene.md#fleece) describes. Grime raises the share of skirtings, and grime and mud lengthen the scour, so a flock washed in a stream before shearing gives the better fleece.
- Shearing leaves the sheep shorn, which costs it most of its fleece insulation under [Body temperature](body-temperature.md#thermal-profiles) until the wool grows back.
- Skirtings count as dung under [Relief](relief.md#waste).
- Goat hair is sheared the same way, as [Goat hair and lime bast](#goat-hair-and-lime-bast) describes.

### Woolen and worsted

- **Woolen** is spun from carded wool, then fulled, tentered, raised, and cropped. It is warm and soft, and the main wool of garments.
- **Worsted** is spun from combed wool and goes from the loom straight to use, with no fulling. It is smooth and hard-wearing, less warm than woolen and more wind-resistant.

### Fulling

- Cloth is fulled by treading it in a fulling trough of water with a fulling agent: fuller's earth or stale urine.
- Fuller's earth is a clay that world generation places in deposits, which [Terrain](https://github.com/NoNamer777/feudum/issues/60) decides.
- Stale urine comes from a lant tub, as [Stale urine](#stale-urine) describes.
- A fulling mill run by [Watermill](https://github.com/NoNamer777/feudum/issues/67) fulls faster than treading, and needs no one in the trough.

### Felt

- Felt is carded wool laid out on a felting table and matted with hot water and pressure, without spinning or weaving.
- Felt goes into hats and boot linings under Clothing, and into rugs.

## Goat hair and lime bast

- **Goat hair**: sheared or combed from goats, then carded and spun into coarse yarn. It is woven into haircloth for sacks, tents, and kiln cloths, or laid into rope. It is never fulled.
- **Lime bast**: bark stripped from lime trees in spring, retted in water for about 2 to 4 Feudum weeks as a fouling source like any retting bundle, and peeled into strips. The strips are twisted into rope or plaited into matting, without spinning or weaving.

## Spinning

- A **distaff and drop spindle** spins anywhere: while walking or standing, with both hands busy, movement slowed, and no sprinting.
- A **spinning wheel** is a block that spins about three times faster, with the body seated at it.
- Both spin every yarn, fine or coarse, woolen or worsted.

## Weaving

- A warping frame winds yarn into a warp, and the warp goes onto a loom.
- The loom weaves weft yarn through the warp into cloth. A warp sets the kind of cloth, and the weft is yarn of the same fiber.
- The loom weaves cloth and rugs only. Banners belong to [Heraldry](https://github.com/NoNamer777/feudum/issues/103).

## Cordage

Three grades of cordage replace vanilla string:

| Cordage | Made from                                   | How                                 | Serves, for example                          |
|:--------|:--------------------------------------------|:------------------------------------|:---------------------------------------------|
| Thread  | Fine linen yarn or worsted yarn             | Two yarns plied on spindle or wheel | Sewing and mending garments                  |
| Twine   | Tow, hemp, or nettle yarn                   | Two yarns plied on spindle or wheel | Bowstrings, fishing line, wicks, and lashing |
| Rope    | Hemp or goat hair yarn, or lime bast strips | Many yarns laid at a ropewalk       | Leads, rigging, well ropes, and building     |

- A ropewalk is a rope jack block and a traveler block, set apart on a straight run. Rope comes out as long as the run between them.
- The design that owns each use, such as [Weapons](../content/weapons.md), [Fishing](https://github.com/NoNamer777/feudum/issues/64), or [Sailing](https://github.com/NoNamer777/feudum/issues/41), references the cordage it needs.

## Cloth

Each kind of cloth is one stackable item, which carries its color as data. Clothing decides how much cloth each garment takes.

| Cloth        | Fiber       | Serves                                                    |
|:-------------|:------------|:----------------------------------------------------------|
| Linen        | Flax line   | Underlayers, tunics, robes, gambesons, and wall hangings. |
| Coarse linen | Flax tow    | Sacking and rough work.                                   |
| Hemp cloth   | Hemp        | Sacks, sails, tents, and the cover of brigandine.         |
| Nettle cloth | Nettle      | A cheap, rough linen for underlayers and tunics.          |
| Woolen       | Carded wool | Most wool garments, cloaks, and wall hangings.            |
| Worsted      | Combed wool | Hose and tunics that wear hard.                           |
| Felt         | Carded wool | Hats, boot linings, and rugs.                             |
| Haircloth    | Goat hair   | Sacks, tents, and kiln cloths.                            |

- Clothing gives woolen, worsted, nettle, and felt their garment stats. Hemp cloth, coarse linen, and haircloth go into no garment.
- [Armor](../content/armor.md#making-armor) takes the hemp cloth cover of brigandine from here.
- A scoured fleece makes about 2 woolen cloth, enough for a tunic.

## Pace

Starting values for the hand work behind 2 woolen cloth, from a fresh fleece, worked by one body:

| Step            | Distaff and spindle |   Spinning wheel |
|:----------------|--------------------:|-----------------:|
| Skirt and scour |         about ¼ day |      about ¼ day |
| Card            |               1 day |            1 day |
| Spin            |              6 days |           2 days |
| Warp and weave  |             1½ days |          1½ days |
| Full and tenter |               1 day |            1 day |
| Raise and crop  |               ½ day |            ½ day |
| **Total**       |   **about 10 days** | **about 6 days** |

- At the default day length of [Time](time.md), that is about 7 hours of play by spindle, and about 4 by wheel. Waiting steps, such as retting and tentering, come on top.
- The bast fibers take about as long per cloth, with breaking, scutching, and hackling in place of carding.
- Every value is a starting value to tune.

## Dyes

### Dyestuffs

| Dyestuff        | Color  | Mordant | Fastness |
|:----------------|:-------|:-------:|:--------:|
| Woad            | Blue   |  None   |   Fast   |
| Madder          | Red    |  Alum   |   Fast   |
| Weld            | Yellow |  Alum   | Fugitive |
| Walnut hulls    | Brown  |  None   |   Fast   |
| Oak galls       | Black  |  Iron   |   Fast   |
| Lichen (orchil) | Purple |  None   | Fugitive |

- Dye plants grow wild, as world generation places them, and Farming covers them once they are cultivated. Textiles owns the harvested dyestuff.
- **Alum** comes from alunite deposits, which Terrain decides. **Iron** comes from iron liquor: scrap iron left to rust in a vat of water.
- Woad is prepared in a **woad vat**: woad leaves fermented in warm water with stale urine over about 3 Feudum days. An item comes out of it yellow-green and turns blue in the air.
- Expensive dyes, such as kermes, wait for [Social standing of dress](https://github.com/NoNamer777/feudum/issues/82).

### Dyeing

- A dye vat is a block heated by a fire, filled with water, a dyestuff, and its mordant.
- Fiber, yarn, cloth, or a finished garment can be dyed, and the color carries through every later step.
- Each item takes one of three shades: pale, mid, or deep. More dyestuff, or more dips, deepen the shade.
- **Overdyeing** an item mixes the new color with the one it has, as [Palette](#palette) describes. A color only deepens or mixes, and never lightens.
- A spent vat leaves dye water, a fouling source when poured out, as [Waste](#waste) describes.

### Palette

- **Undyed**: natural linen and bleached linen, natural hemp and nettle, and the four fleece colors of wool: white, gray, brown, and black.
- **Base colors**: blue, red, yellow, brown, black, and purple, from the dyestuffs.
- **Mixes**: green (blue over yellow), orange (red over yellow), and violet (blue over red). Pale black is gray.
- Overdyeing with brown or black dulls any color toward it.
- A mix with no name, such as blue over orange, steps to the nearest named color.
- Every color has the three shades, so the palette stays named for [Heraldry](https://github.com/NoNamer777/feudum/issues/103) and Social standing of dress.

### Fading

- A dyed item loses shade from sunlight, while worn or left in the open, and with each wash, which [Hygiene](hygiene.md#fading) counts.
- Its fastness sets the rate: the fastness of the dyestuff times a factor for the stage it was dyed at. The factor is 1 for fiber, about 1¼ for yarn, about 2 for cloth, and about 3 for a garment, so what is dyed in the wool lasts longest.
- A mordant raises fastness wherever the dyestuff takes one.
- Fading steps the shade down toward the undyed color. A faded item can be overdyed again.
- As a starting value, a mid shade of a fast dye on a garment dyed in the wool loses one shade over about a year of daily wear.

## Stale urine

- A **lant tub** is a vessel block that takes water only. Relieving at it empties the bladder and leaves the bowels as they are, an exception to the rule of [Relief](relief.md#relieving) that relieving empties both stores.
- Urine in a closed lant tub ages into stale urine over about one Feudum week. Stale urine fulls cloth and ferments a woad vat.
- A lant tub is a fouling source for the groundwater under it, like a privy pit.
- Who may use a lant tub follows the rule of [Privies](relief.md#privies), and using one costs no standing.
- [Privy and chamber pot](https://github.com/NoNamer777/feudum/issues/71) owns how a lant tub is built and carried.

## Waste

The waste of each step, and how strongly it fouls the water it reaches as a [fouling source](fluids.md#fouling):

| Waste               | From                     | Fouling   | Other use                    |
|:--------------------|:-------------------------|:----------|:-----------------------------|
| Retting bundle      | Water retting            | Strongest | None.                        |
| Spent fulling water | Fulling with stale urine | Strong    | None.                        |
| Spent dye water     | A spent dye or woad vat  | Strong    | None.                        |
| Scouring water      | Scouring                 | Mild      | None.                        |
| Shives              | Scutching                | None      | Bedding and kindling.        |
| Skirtings           | Skirting                 | As dung   | Counts as dung under Relief. |

- Shives bed the dung heap as straw does, and kindle [Fire](https://github.com/NoNamer777/feudum/issues/33).
- Water poured out fouls the water it reaches, as waste in water does under Relief, and fouls wet ground where it lands.
- The fouling rates are starting values to tune.

## Hangings and rugs

- A **wall hanging** is a thin block of woolen cloth, linen, or felt hung on a wall face. It raises the insulation of that face under [Body temperature](body-temperature.md#shelter-and-heat), so a stone wall hung with cloth holds heat about as well as a timber one.
- A **rug** is a thin block of felt or woolen laid on a floor face, which raises its insulation the same way.
- Neither can block an opening.
- Both take the color of their cloth. Tapestries and other fine hangings wait for Social standing of dress.
- Textiles adds no full block of wool or felt: solid wool was never a building material.

## Waiting steps

- These steps are placed blocks that keep their own progress: a retting bundle in water, stalks spread for dew retting, cloth spread for bleaching, cloth on a tenter frame, a lant tub, and a woad vat.
- Each reads its conditions, such as water temperature, rain, sun, and frost, from [Fluids](fluids.md) and [Weather](weather.md).
- Each catches up on the elapsed time when its chunk loads, as Fluids does.
- Picking one up returns the item with its progress saved.

## Tools and blocks

| Step           | Tool or block                                                                    | Kind        |
|:---------------|:---------------------------------------------------------------------------------|:------------|
| Ripple         | Rippling comb                                                                    | Block       |
| Ret            | Retting bundle; spread stalks                                                    | Block       |
| Break          | Flax brake                                                                       | Block       |
| Scutch         | Scutching board, worked with a scutching knife                                   | Block, item |
| Hackle         | Hackle                                                                           | Block       |
| Shear          | Shears                                                                           | Item        |
| Scour          | Heated cauldron, under [Cooking](https://github.com/NoNamer777/feudum/issues/30) | Block       |
| Card           | Hand cards                                                                       | Item        |
| Comb           | Wool combs                                                                       | Item        |
| Spin           | Distaff and drop spindle; spinning wheel                                         | Item, block |
| Warp           | Warping frame                                                                    | Block       |
| Weave          | Loom                                                                             | Block       |
| Full           | Fulling trough; fulling mill                                                     | Block       |
| Tenter         | Tenter frame                                                                     | Block       |
| Raise and crop | Teasel frame and cropping shears                                                 | Item        |
| Felt           | Felting table                                                                    | Block       |
| Bleach         | Spread cloth                                                                     | Block       |
| Dye            | Dye vat; woad vat                                                                | Block       |
| Stale urine    | Lant tub                                                                         | Block       |
| Rope           | Rope jack and traveler                                                           | Block       |

- A teasel frame holds dried teasel heads, from a plant that grows wild and that Farming cultivates.
- [Smithing](https://github.com/NoNamer777/feudum/issues/86) makes the iron parts: the hackle's teeth, the shears, the scutching knife, and the wire of hand cards and wool combs.

## Vanilla content

- Vanilla string, wool blocks, carpets, the 16 dyes, the loom, and the shears stay hidden.
- Spiders and cobwebs drop nothing.
- A sheep can't be dyed alive. Its fleece takes the natural color of its breed.
- Every vanilla recipe that used string, wool, or dye moves to the design that owns its output, and takes Feudum cordage, cloth, and dyes instead.

## Persistence

- Every textile item saves its fiber, step, color, shade, and remaining fastness.
- Every waiting-step block saves its progress and the time it last caught up.

## Query

- One query returns the textile state of an item or block: fiber, step reached, progress of a waiting step, color, shade, and fastness.
- Other mechanics read textiles through it.

## Commands

- `/feudum textiles query <pos|entity slot>` shows the result of the query.
- `/feudum textiles set <pos|entity slot> <progress|shade> <value>` sets a value, for testing.
- Every `/feudum textiles` command requires operator permission.

## Boundaries

Textiles owns the six fibers from gathering to cloth and every step between, felt, matting, cordage and the ropewalk, and the tools and blocks of the craft. It also owns dyestuffs, mordants, dyeing, the palette and fading, the lant tub and stale urine, the waste of each step, and wall hangings and rugs. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Clothing](../content/clothing.md)**: the garments sewn from cloth and thread, their stats, and how much cloth each takes.
- **[Armor](../content/armor.md)**: the brigandine that takes a hemp cloth cover.
- **[Body temperature](body-temperature.md)**: the insulation of wall and floor faces, and the fleece insulation a shorn sheep loses.
- **[Fluids](fluids.md)**: how foulness spreads in water and groundwater, and the water temperature that speeds retting.
- **[Weather](weather.md)**: the rain, sun, and frost that drive dew retting, bleaching, tentering, and fading.
- **[Relief](relief.md)**: relieving, the rule for who may use a privy, and the dung that skirtings count as.
- **[Villages](villages.md)**: the standing scale.
- **[Farming](https://github.com/NoNamer777/feudum/issues/32)**: flax, hemp, teasel, and cultivated dye plants, and replanting seed.
- **[Animal husbandry](animal-husbandry.md)**: sheep and goats, fleece regrowth, and breeds with their natural colors.
- **[Terrain](https://github.com/NoNamer777/feudum/issues/60)**: the deposits of fuller's earth and alunite.
- **[Watermill](https://github.com/NoNamer777/feudum/issues/67)**: the power of the fulling mill.
- **[Cooking](https://github.com/NoNamer777/feudum/issues/30)**: the heated cauldron that scours wool.
- **[Smithing](https://github.com/NoNamer777/feudum/issues/86)**: the iron parts of the tools.
- **[Privy and chamber pot](https://github.com/NoNamer777/feudum/issues/71)**: how a lant tub is built and carried.
- **[Hygiene](hygiene.md)**: the washes that fade dyes, and the dirt a fleece takes from its sheep.
- **[Cloth quality](https://github.com/NoNamer777/feudum/issues/105)**: whether cloth carries a quality, and how the steps and [Skills](https://github.com/NoNamer777/feudum/issues/43) set it.
- **[Oil pressing](https://github.com/NoNamer777/feudum/issues/106)**: linseed and hempseed oil.
- **[Social standing of dress](https://github.com/NoNamer777/feudum/issues/82)**: fine cloth, expensive dyes, and tapestries.
- **[Heraldry](https://github.com/NoNamer777/feudum/issues/103)**: banners, which take their cloth and dyes from here.
- **[Weapons](../content/weapons.md)**, **[Fishing](https://github.com/NoNamer777/feudum/issues/64)**, and **[Sailing](https://github.com/NoNamer777/feudum/issues/41)**: the bowstrings, lines, sails, and rigging made of cordage and cloth.
- **[Weaver](https://github.com/NoNamer777/feudum/issues/107)**, **[Fuller](https://github.com/NoNamer777/feudum/issues/108)**, and **[Dyer](https://github.com/NoNamer777/feudum/issues/109)**: the villagers who weave, full, and dye.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)** and **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: household spinning, and textile work while a village is unloaded.
