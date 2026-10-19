# Tanning

Every scrap of leather and fur in Feudum is made the long way. A cowhide is fleshed on the beam, laid in lime until its hair slips, scraped bare, and softened in a pit of dung before it goes into the tan pits, where it lies in oak-bark ooze for a year. Lighter skins are tawed white with alum in two weeks, oiled into buckskin, or stretched and scraped into parchment, and pelts taken in winter are dressed into fur with the hair left on. The pits need tending, the lime and bate foul the water, and the tanner smells of the trade, so a village keeps its tannery downstream and its hides in the pits at every stage at once. Vanilla leather drops from a cow and needs no work, so Feudum replaces it.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Tanning works five processes: bark tanning, tawing (with fur dressing, its hair-on form), oil tanning, rawhide, and parchment.
- It starts at the hide that [butchering](animal-husbandry.md#slaughter-and-butchering) yields, from livestock and wild animals alike. Tanning owns the hide items. [Wildlife](https://github.com/NoNamer777/feudum/issues/47) decides which wild species give a hide or a pelt.
- It ends at sole and upper leather, white leather, buckskin, fur, rawhide, parchment, and vellum. [Clothing](../content/clothing.md) sews garments from them, and the leatherworker's bench of [Armor](../content/armor.md#making-armor) shapes hardened leather from sole leather.
- Every historical step of the craft is its own step here, and each takes about as long as it did, so leather is scarce and valuable.
- Leather and fur carry no quality: every product of a kind is the same until [Cloth and leather quality](https://github.com/NoNamer777/feudum/issues/105) lands.

## Working

- A hand step is done at its block, or with its handheld tool, by holding the use key, as in [Textiles](textiles.md#working). Work advances by the Feudum time that passed, and stopping keeps what is done.
- A waiting step is a placed block that keeps its own progress, as [Waiting steps](#waiting-steps) describes.
- Villagers work the same blocks at the same rate. Fleshing and scraping are household work any villager does. [Tanner](https://github.com/NoNamer777/feudum/issues/174), [Tawyer](https://github.com/NoNamer777/feudum/issues/175), [Currier](https://github.com/NoNamer777/feudum/issues/176), [Furrier](https://github.com/NoNamer777/feudum/issues/177), and [Parchmenter](https://github.com/NoNamer777/feudum/issues/178) are trades.
- The [Butcher](https://github.com/NoNamer777/feudum/issues/149) skins livestock, and the Furrier skins wild fur-bearers.

## Hides

Every species gives its own hide item, such as a cowhide, a calfskin, or a fox pelt. Each belongs to one of three classes, and the class decides which processes it can go through:

| Class | Species, for example                     | Processes                                             |
|:------|:-----------------------------------------|:------------------------------------------------------|
| Hide  | Cattle, horses, water buffalo, deer      | Bark tanning, oil tanning (deer), rawhide             |
| Skin  | Calves, sheep, goats, pigs               | Bark tanning, tawing, oil tanning, rawhide, parchment |
| Pelt  | Rabbits, and the fur-bearers of Wildlife | Fur dressing                                          |

- A sheepskin can also be dressed with its wool on, as a fur, as [Fur dressing](#fur-dressing) describes.
- Each hide gives a number of units of its product. The animal's size scales that number within its class, so a bear pelt gives more fur than a fox pelt. Clothing decides how many units each garment takes.

Starting yields to tune, for an animal of the example's size:

| Class | Example           | Gives                                                             |
|:------|:------------------|:------------------------------------------------------------------|
| Hide  | Cowhide           | About 4 sole leather, or 4 rawhide                                |
| Skin  | Calf- or goatskin | About 1 upper leather, white leather, or buckskin, or 2 parchment |
| Pelt  | Fox pelt          | About 1 fur                                                       |

## Processes and products

The diagram maps each class of hide through the processes it can go through to the products they make. Each arrow stands for a whole process, whose steps the sections below list. Of the hides, only deer hides are oil-tanned, and the dashed arrow is a woolly sheepskin dressed as fur.

![Three classes of hide and what they become. Hides are bark-tanned into sole leather, made into rawhide, or, for deer, oil-tanned into buckskin. Skins are bark-tanned and curried into upper leather, tawed into white leather, oil-tanned into buckskin, made into rawhide, or made into parchment, and calfskin into vellum. Pelts and woolly sheepskins are dressed into fur.](images/tanning-processes.svg)

| Product       | Process                      | From                 | Serves, for example                                         |
|:--------------|:-----------------------------|:---------------------|:------------------------------------------------------------|
| Sole leather  | Bark tanning                 | Hides                | Hardened leather, soles, belts, harness, and shield facings |
| Upper leather | Bark tanning and currying    | Skins                | Clothing's leather garments                                 |
| White leather | Tawing                       | Skins                | Gloves and fine work                                        |
| Buckskin      | Oil tanning                  | Skins, deer hides    | Jerkins, trousers, and gloves that stay soft when wet       |
| Fur           | Fur dressing                 | Pelts, sheepskins    | Clothing's fur garments                                     |
| Rawhide       | Liming, scraping, and drying | Hides, skins         | Lashings, drumheads, and sieves                             |
| Parchment     | Liming, stretching, scraping | Sheep and goat skins | Books and maps                                              |
| Vellum        | As parchment                 | Calfskins            | Books and maps                                              |

- Each product is one stackable item, and keeps forever.
- The design that owns each use, such as [Clothing](../content/clothing.md), [Armor](../content/armor.md), [Weapons](../content/weapons.md), or [Cartography](https://github.com/NoNamer777/feudum/issues/98), references the product it needs.

## Curing

A raw hide keeps about 2 days under [Food preservation](food-preservation.md#starting-keeping-times). Curing makes it last until the tanner can take it:

| Cure       | How                                                                        | Keeps          | Soaking before work |
|:-----------|:---------------------------------------------------------------------------|:---------------|:--------------------|
| Salting    | Soaking the hide in a pit of brine for about 2 days.                       | About a season | About 1 day         |
| Air-drying | Stretching the hide on a stretching frame to dry stiff, into a flint hide. | About a year   | About 3 days        |

- Brine is salty water under [Fluids](fluids.md#evaporation-and-brine), made from seawater or by dissolving [salt](https://github.com/NoNamer777/feudum/issues/66) in water.
- A cured hide is soaked soft in a pit of water before any process. A fresh hide needs no soaking.
- A hide's [spoilage stage](food-preservation.md#keeping-time) sets its yield: a Stale hide gives about 75%, and a Spoiled hide about 50% and fouls the water of the pit it goes into. A Rotten hide gives nothing.
- A hide's spoilage stops once it enters the lime pit or, for fur, the tawing bath, since both preserve it.

## Preparing the hide

Every process except fur dressing starts with the same steps at the fleshing beam and the lime pit:

| Step   | What happens                                                         | Yields                  |
|:-------|:---------------------------------------------------------------------|:------------------------|
| Flesh  | Scraping the flesh and fat off the inner side with a fleshing knife. | Fleshed hide, fleshings |
| Lime   | Laying the hide in a lime pit until the hair loosens.                | Limed hide              |
| Unhair | Scraping the loosened hair off at the fleshing beam.                 | Unhaired hide, hair     |
| Scud   | Working the last lime, hair, and grease out at the beam.             | Clean hide              |

- [Lime](https://github.com/NoNamer777/feudum/issues/29) comes from the lime kiln of Buildings.
- Fleshings and hair are by-products, as [By-products](#by-products) describes.

## Bark tanning

Bark tanning makes sole leather from hides and upper leather from skins. After preparing the hide:

| Step  | What happens                                                                                    | Yields                         |
|:------|:------------------------------------------------------------------------------------------------|:-------------------------------|
| Bate  | Soaking the clean hide in a bate pit, which draws out the lime and makes it supple.             | Bated hide                     |
| Tan   | Laying the hide in a tan pit between layers of ground bark, as [Tan pits](#tan-pits) describes. | Tanned hide                    |
| Dry   | Hanging the tanned hide on a stretching frame under cover.                                      | Sole leather, or a tanned skin |
| Curry | For skins: shaving, stuffing with dubbin, and slicking at the currier's table.                  | Upper leather                  |

- Bate is dog or poultry dung in water. The dung is gathered as [Relief](relief.md#waste) describes.
- **Dubbin** is tallow melted with fish oil in a [heated cauldron](cooking.md#other-uses-of-the-heated-cauldron). The tallow comes from [rendering](cooking.md#rendering), and the fish oil from cod and ling livers under [Fishing](fishing.md#gutting). Tanning owns dubbin.
- Sole leather is not curried: it goes from the frame to use.

### Tan pits

- A tan pit is a pit of water and ground bark, whose tannin steeps out into ooze.
- A pit's strength falls as its hides take up the tannin. Inspecting a pit shows its strength.
- A pit left untended for about 2 Feudum weeks stalls: its hides stop tanning but don't spoil.
- **Re-layering** the pit with fresh ground bark restarts it. The spent bark comes out as tan.
- So a hide spends a year in the pits and a skin a season, re-layered about every 2 Feudum weeks, and a village keeps pits at several stages at once.

### Bark

| Bark   | Strength | Source                     |
|:-------|:---------|:---------------------------|
| Oak    | Full     | Oak, the main tanning bark |
| Willow | Weaker   | Willow                     |
| Birch  | Weaker   | Birch                      |

- [Forestry](https://github.com/NoNamer777/feudum/issues/165) owns peeling bark from felled or coppiced trees, in spring when the sap rises.
- Peeled bark dries in the open, and dry bark keeps forever.
- A **bark mill** grinds dry bark into ground bark by hand. A bark mill turned by a draft animal under [Animal husbandry](animal-husbandry.md#draft-work), or by a [Watermill](https://github.com/NoNamer777/feudum/issues/67), grinds faster and needs no one at the handle.
- Weaker bark tans more slowly, as a starting value about 1½ times as long as oak.
- **Tan**, the spent bark, burns as fuel under [Fire](fire.md#fuels) and mulches beds and paths.

## Tawing

Tawing makes white leather from skins. After preparing the hide:

| Step  | What happens                                                                | Yields         |
|:------|:----------------------------------------------------------------------------|:---------------|
| Taw   | Soaking the clean skin in a tawing bath of alum, salt, egg yolk, and flour. | Tawed skin     |
| Dry   | Stretching the tawed skin on a stretching frame.                            | Dry tawed skin |
| Stake | Working the dry skin soft over the fleshing beam.                           | White leather  |

- **Alum** comes from alunite deposits, as in [Textiles](textiles.md#dyestuffs). Egg yolk comes from [eggs](animal-husbandry.md#eggs), and flour from [Foods](https://github.com/NoNamer777/feudum/issues/51).
- Soaking washes the alum out of white leather and leaves it stiff, as rawhide. A soaked piece, or a garment of it, works again once it is tawed again.

## Fur dressing

Fur dressing makes fur from pelts and woolly sheepskins, with the hair left on. It skips liming, which would loosen the hair:

| Step  | What happens                                                           | Yields                  |
|:------|:-----------------------------------------------------------------------|:------------------------|
| Flesh | As in [Preparing the hide](#preparing-the-hide).                       | Fleshed pelt, fleshings |
| Taw   | Soaking the pelt in a tawing bath of alum and salt only.               | Tawed pelt              |
| Dry   | Stretching the pelt on a stretching frame, fur side in.                | Dry pelt                |
| Stake | Working the dry pelt soft over the fleshing beam, and combing the fur. | Fur                     |

- A pelt is **prime** from Late Autumn to Early Spring, when the fur is thick. A pelt taken outside its prime gives about half the fur.
- A sheepskin dressed as fur carries the fleece the sheep had at slaughter, so a newly shorn sheep gives a bare skin, which goes to the other processes as a skin.

## Oil tanning

Oil tanning makes buckskin, which stays soft when wet and washed, from skins and deer hides. After preparing the hide:

| Step  | What happens                                                          | Yields     |
|:------|:----------------------------------------------------------------------|:-----------|
| Oil   | Working brains or fish oil into the clean hide at the fleshing beam.  | Oiled hide |
| Stake | Working the hide soft while it dries over the beam.                   | Soft hide  |
| Smoke | Hanging the hide over a smudge pit of smoldering wood, which sets it. | Buckskin   |

- Brains come with the offal of [butchering](animal-husbandry.md#slaughter-and-butchering), and fish oil as for dubbin.
- A smudge pit is a small pit of punky wood kept as a [smoldering fire](fire.md#model), which smokes without flame.

## Rawhide

Rawhide is a hide or skin limed and scraped, then dried with no tanning. After preparing the hide, it dries stiff on a stretching frame.

- Rawhide keeps forever while dry. Left soaked for days, it softens and starts to spoil again, at the rate of a raw hide.
- It serves for lashings, drumheads, and sieves, and its scraps go into hide glue.

## Parchment and vellum

Parchment is made from sheep and goat skins, and vellum from calfskins. After preparing the hide:

| Step    | What happens                                                   | Yields                      |
|:--------|:---------------------------------------------------------------|:----------------------------|
| Stretch | Lacing the clean skin wet onto a stretching frame.             | Laced skin                  |
| Scrape  | Scraping both sides with a lunellum while the skin dries taut. | Parchment or vellum, scraps |

- The scraps go into hide glue.
- [Cartography](https://github.com/NoNamer777/feudum/issues/98) and the designs that make books read parchment and vellum. Neither is designed yet.

## Pits

- A **pit** is one block, dug into the ground and lined with clay or planks, which holds about 4 hides.
- It is filled with water through [Fluids](fluids.md#volume), and its contents decide what it does:

| Contents                                                  | Pit         | Does                                     |
|:----------------------------------------------------------|:------------|:-----------------------------------------|
| Water                                                     | Soaking pit | Soaks cured hides soft                   |
| Brine                                                     | Salting pit | Salts raw hides                          |
| Water and lime                                            | Lime pit    | Loosens the hair                         |
| Water and bate                                            | Bate pit    | Bates limed hides                        |
| Water and ground bark                                     | Tan pit     | Tans, as [Tan pits](#tan-pits) describes |
| Water, alum, and salt, with or without egg yolk and flour | Tawing bath | Taws skins and pelts                     |

- A charge of lime, bate, or tawing liquor is spent after one batch of hides. Emptying a pit gives its waste, as [Waste](#waste) describes.

## Pace

Starting values for the time from a fresh or soaked hide to the product, most of it spent waiting in a pit or on a frame:

| Product              | Time                 |
|:---------------------|:---------------------|
| Sole leather         | About 1 Feudum year  |
| Upper leather        | About a season       |
| White leather        | About 2 Feudum weeks |
| Fur                  | About 2 Feudum weeks |
| Buckskin             | About 2 Feudum weeks |
| Parchment and vellum | About 2 Feudum weeks |
| Rawhide              | About 1 Feudum week  |

- Liming takes about 1 Feudum week of each chain that limes.
- The hand steps (fleshing, unhairing, scudding, staking, scraping, and currying) take about ½ to 1 day each per hide.
- At the default day length of [Time](time.md), a Feudum year is about 64 hours of play.
- Every value is a starting value to tune.

## By-products

| By-product | From                       | Becomes                                                                                                                                                           |
|:-----------|:---------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fleshings  | Fleshing                   | Hide glue, or the dung heap                                                                                                                                       |
| Hair       | Unhairing cattle and goats | Plaster under [Buildings](https://github.com/NoNamer777/feudum/issues/29), and stuffing under [Tack and barding](https://github.com/NoNamer777/feudum/issues/139) |
| Scraps     | Rawhide and parchment      | Hide glue                                                                                                                                                         |
| Tan        | Re-layering a tan pit      | Fuel and mulch                                                                                                                                                    |

- **Hide glue** is fleshings and scraps boiled in a heated cauldron. It sets hard, and keeps forever once dry. The fletcher's bench of [Weapons](../content/weapons.md#making-weapons) uses it.
- Fleshings that aren't boiled spoil as offal under Food preservation, and go to the [dung heap](relief.md#dung-heap).

## Waste

The waste of each step, and how strongly it fouls the water it reaches as a [fouling source](fluids.md#fouling):

| Waste               | From                   | Fouling |
|:--------------------|:-----------------------|:--------|
| Spent lime water    | Emptying a lime pit    | Strong  |
| Spent bate          | Emptying a bate pit    | Strong  |
| Fleshings in water  | Dumping fleshings      | Strong  |
| Spent ooze          | Emptying a tan pit     | Mild    |
| Spent tawing liquor | Emptying a tawing bath | Mild    |

- Water poured out fouls the water it reaches, as waste in water does under [Relief](relief.md#waste-in-water), and fouls wet ground where it lands.
- Pouring lime or bate waste inside a village's territory, into water that its wells draw on or its villagers drink from, lowers a player's [standing](villages.md#standing-and-wishes) a little, as retting does under [Textiles](textiles.md#retting).
- Working the lime pit, the bate pit, and the fleshing beam adds [grime](hygiene.md#grime) to the worker, so a tanner smells of the trade.
- The stench of a tannery's blocks themselves is out of scope, since no design yet reads the smell of a place.
- The fouling rates are starting values to tune.

## Disease

- A raw or cured hide from a sick animal carries its disease, and handling it counts as [touch](illness.md#touch) under Illness.
- Liming or tawing ends the disease on the hide.

## Waiting steps

- These steps are placed blocks that keep their own progress: every pit, a hide on a stretching frame, and a hide over a smudge pit.
- Each reads its conditions, such as water temperature, from [Fluids](fluids.md) and [Weather](weather.md).
- Each catches up on the elapsed time when its chunk loads, as Fluids does.
- Picking a hide out of one returns it with its progress saved.

## Tools and blocks

| Step                             | Tool or block                                       | Kind        |
|:---------------------------------|:----------------------------------------------------|:------------|
| Salt, soak, lime, bate, tan, taw | Pit                                                 | Block       |
| Air-dry, dry, stretch            | Stretching frame                                    | Block       |
| Flesh, unhair, scud, oil, stake  | Fleshing beam, worked with a fleshing knife         | Block, item |
| Grind bark                       | Bark mill                                           | Block       |
| Curry                            | Currier's table, with a shaving knife and a slicker | Block, item |
| Smoke                            | Smudge pit                                          | Block       |
| Scrape parchment                 | Lunellum, at the stretching frame                   | Item        |
| Dubbin and hide glue             | Heated cauldron, under [Cooking](cooking.md)        | Block       |

- [Smithing](https://github.com/NoNamer777/feudum/issues/86) makes the iron blades: the fleshing knife, the shaving knife, and the lunellum.

## Vanilla content

- Vanilla leather, rabbit hide, and the rabbit's foot stay hidden.
- Cows, horses, and rabbits drop nothing on death. Their carcasses give Feudum hides through butchering.
- Every vanilla recipe that used leather moves to the design that owns its output, and takes Feudum leather or parchment instead: books to the designs that make books, saddles and leather horse armor to [Tack and barding](https://github.com/NoNamer777/feudum/issues/139), and item frames and bundles to [Inventory](https://github.com/NoNamer777/feudum/issues/83).
- [Clothing](../content/clothing.md#scope) already replaces leather armor.

## Data

- Hide items, their classes, the species that give them, and their yields are data-driven, so a data pack can add a species.
- The processes, their steps and times, and the barks are data-driven too.

## Persistence

- Every hide saves its species, class, cure, spoilage, the disease it carries, the step reached, and, for a pelt, whether it was prime.
- Every pit saves its contents, their strength, the hides in it with their progress, and the time it last caught up and was last re-layered.
- Every stretching frame and smudge pit saves its hide, its progress, and the time it last caught up.

## Query

- One query returns the tanning state of a hide, product, or block: species, class, cure, step reached, progress of a waiting step, and, for a pit, its contents and strength.
- Other mechanics read tanning through it.

## Commands

- `/feudum tanning query <pos|entity slot>` shows the result of the query.
- `/feudum tanning set <pos|entity slot> <progress|strength> <value>` sets a value, for testing.
- Every `/feudum tanning` command requires operator permission.

## Boundaries

Tanning owns the hide items and their classes, curing, the five processes and every step between, the pit and its contents, tending the tan pits, grinding bark, dubbin, hide glue, hair, tan, and the waste of each step. It also owns the products: sole and upper leather, white leather, buckskin, fur, rawhide, parchment, and vellum. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Animal husbandry](animal-husbandry.md)**: livestock, slaughter, and butchering, which yields the hide, the brains, and the fat; eggs; and draft animals.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: which wild species give a hide or a pelt.
- **[Clothing](../content/clothing.md)**: the garments sewn from leather and fur, their materials and stats, and how many units each takes.
- **[Armor](../content/armor.md)**: the leatherworker's bench and the hardened leather it shapes from sole leather.
- **[Weapons](../content/weapons.md)**: leather shield facings, and the fletcher's bench that uses hide glue.
- **[Food preservation](food-preservation.md)**: the keeping time and spoilage stages of raw hides and fleshings.
- **[Fluids](fluids.md)**: water, brine, and how foulness spreads.
- **[Relief](relief.md)**: the dung that makes bate, and the dung heap.
- **[Cooking](cooking.md)**: the heated cauldron, and rendering tallow and fish oil.
- **[Fishing](fishing.md)**: the livers that render into fish oil.
- **[Fire](fire.md)**: smoldering, and tan as fuel.
- **[Hygiene](hygiene.md)**: grime and smell.
- **[Illness](illness.md)**: diseases and touch.
- **[Villages](villages.md)**: the standing scale.
- **[Textiles](textiles.md)**: alum.
- **[Forestry](https://github.com/NoNamer777/feudum/issues/165)**: peeling bark.
- **[Buildings](https://github.com/NoNamer777/feudum/issues/29)**: the lime kiln, and hair in plaster.
- **[Salt](https://github.com/NoNamer777/feudum/issues/66)**: salt for brine and tawing.
- **[Foods](https://github.com/NoNamer777/feudum/issues/51)**: flour and offal.
- **[Watermill](https://github.com/NoNamer777/feudum/issues/67)**: the power of a bark mill.
- **[Smithing](https://github.com/NoNamer777/feudum/issues/86)**: the iron blades of the tools.
- **[Tack and barding](https://github.com/NoNamer777/feudum/issues/139)**: saddles, harness, and hair stuffing.
- **[Cartography](https://github.com/NoNamer777/feudum/issues/98)**: maps on parchment.
- **[Inventory](https://github.com/NoNamer777/feudum/issues/83)**: item frames and bundles.
- **[Cloth and leather quality](https://github.com/NoNamer777/feudum/issues/105)**: whether leather and fur carry a quality.
- **[Tanner](https://github.com/NoNamer777/feudum/issues/174)**, **[Tawyer](https://github.com/NoNamer777/feudum/issues/175)**, **[Currier](https://github.com/NoNamer777/feudum/issues/176)**, **[Furrier](https://github.com/NoNamer777/feudum/issues/177)**, **[Parchmenter](https://github.com/NoNamer777/feudum/issues/178)**, and **[Butcher](https://github.com/NoNamer777/feudum/issues/149)**: the villagers who skin, tan, taw, curry, dress fur, and make parchment.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)** and **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: household fleshing, and tanning while a village is unloaded.
