# Relief

Every mob that eats also passes what it can't use. Digestion leaves residue in the bowels, and water the body has no room for fills the bladder, until the body needs to relieve itself. Where it goes matters: a privy keeps waste in a pit, a chamber pot carries it out of the bedroom, and waste on open ground or in a stream fouls the water around it. Waste is also worth keeping, since a dung heap rots it into the manure that feeds the fields. Animals relieve where they stand, so a barn must be mucked out. Vanilla has no relief, so Feudum adds its own.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Every entity type whose diet profile carries a relief block has relief: players, villagers, livestock, and wild animals. [ADR 0011](../../adr/0011-every-mob-that-eats-has-relief.md) records why.
- A diet profile with no relief block has no relief. An entity type with no diet profile has neither hunger, thirst, nor relief.
- A per-world setting sets how harsh relief is for every entity: `off`, `mild` (debuffs only, never an accident), or `harsh` (accidents happen). The default is `harsh`. It is separate from the hunger, thirst, and body temperature settings.
- Relief never kills, so difficulty plays no part.
- Creative and spectator players are exempt.

## Model

- A body carries a bladder and bowels, which the [stomach](hunger.md#model) of Hunger and the [hydration](thirst.md#model) of Thirst fill.
- **Bladder**: fills with the water that passes off once hydration is full, and with the share of the hydration drain that leaves as urine: the base drain and the salt load. Exertion and heat drain leave as sweat and fill nothing, so a body passes little on a hot day of hard work.
- **Bowels**: fill as the stomach digests, by the residue of what digests, as [Food](#food) describes.
- Relieving empties a store. Neither store drains on its own.
- While the body sleeps, the bladder fills at half its rate, so a body that relieved before bed sleeps through the night.
- Relief advances by the Feudum time that passed, so it follows the day length and the sleep speed-up.
- At normal activity in a mild climate, a human needs to pass water four to six times per Feudum day and to empty the bowels once.

## Stages

The stage follows whichever store is fuller, as a share of its capacity. Thresholds come from the diet profile. For a human:

| Stage       | Reached             | Effects                                       |
|:------------|:--------------------|:----------------------------------------------|
| Comfortable | Below 50%           | None.                                         |
| Urge        | 50%                 | Cues only.                                    |
| Pressing    | 75%                 | Slower work, and the body can't fall asleep.  |
| Desperate   | 90%                 | Slower movement and work, no sprinting.       |
| Accident    | 100%, under `harsh` | The full store empties where the body stands. |

- Work covers mining, chopping, and attacking, as in Body temperature.
- A sleeping body that reaches Pressing wakes, so a jug of ale at supper means a trip to the privy before dawn.
- Under `mild`, a store holds at 100% and the body stays Desperate until it relieves.
- Effects apply as Feudum attribute modifiers, never as mob effects, so no icon shows in the inventory.
- Modifiers of the same kind as those of Hunger, Thirst, and Body temperature take the strongest rather than adding up, under a rule that Health owns.

### Accidents

- An accident empties the full store where the body stands, as [Relieving](#relieving) on open ground does, and leaves the body Soiled.
- A Soiled body clears once it is washed, by immersion in water or by pouring a container of water over itself. Immersion adds the waste to the water, as [Waste in water](#waste-in-water) describes, and pouring leaves foul wet ground. An accident also soils the garment on the legs, and a body that wears a soiled garment stays Soiled, as [Clothing](../content/clothing.md#soiling) describes.
- [Washing and bathhouses](https://github.com/NoNamer777/feudum/issues/75) plans washbasins and bathhouses as further ways to wash.
- [Illness](https://github.com/NoNamer777/feudum/issues/37) decides whether a Soiled body or deep dung makes a body sick.

## Relieving

- A player relieves by holding the relieve key for a few seconds: about 3 for the bladder and 8 for the bowels. The body can't move or act until it finishes, and an interruption, such as damage, stops it with the rest still in the store.
- A body can relieve at any stage, and relieving empties both stores, except at a lant tub.
- Where the waste goes depends on where the body relieves:
  - **Privy**: into the privy's pit, as [Privies](#privies) describes.
  - **Chamber pot**: into the pot, which holds a few uses and must be emptied by hand.
  - **Lant tub**: the bladder alone, into the tub, as [Textiles](textiles.md#stale-urine) describes. The bowels stay as they are.
  - **Open ground**: the bowels leave a layer of night soil. Urine soaks in and leaves nothing lasting, but counts as a fouling source for a moment.
  - **In water**: into the water, as [Waste in water](#waste-in-water) describes.
- An emptied chamber pot pours its waste where it is emptied: into a privy, onto a dung heap, onto open ground, or into water.
- [Privy and chamber pot](https://github.com/NoNamer777/feudum/issues/71) owns the blocks and items: how a privy and its pit are built, and how a pot is carried and emptied.

### Privies

- A privy pit has a capacity and fills with each use. A full pit refuses further use until a shovel empties it, which yields night soil.
- A pit is a fouling source for the groundwater under it, which seeps toward nearby wells, as [Fluids](fluids.md#groundwater-quality) describes.
- A privy built over water has no pit and empties straight into the water, as a garderobe over a moat does.
- A privy or chamber pot belongs to the building it sits in, which [Buildings](https://github.com/NoNamer777/feudum/issues/29) decides. A player may use those in the village holding, which are communal, those in the buildings of a manor they are lord of, and those in their own buildings outside any village.
- [Inns and taverns](https://github.com/NoNamer777/feudum/issues/74) decides when a guest may use the privy of the house.

### Standing

Relief decides how relieving moves [standing](villages.md#standing-and-wishes), and Villages owns the scale:

- Each of these lowers a player's standing a little with a village, when it happens inside its territory and in sight of one of its villagers: relieving on open ground or into water, emptying a chamber pot onto open ground or into water, an accident, and using the privy, chamber pot, or lant tub of another household.
- A Soiled player in sight of a village's villagers lowers standing a little once per sighting, not over and over.
- Relieving in the wilderness, or in a privy, chamber pot, or lant tub the player may use, costs nothing.
- The amounts are starting values to tune.

## Waste

- Waste comes in three kinds: **night soil** from humans, **dung** from animals, and **manure**, which a dung heap makes from both.
- Waste on the ground lies as a layer, which stacks up to a full block. A shovel collects a layer as an item, and placing the item lays it down again.
- Each layer is a fouling source for the water within 6 blocks of it, as [Fluids](fluids.md#fouling) describes.
- Waste on open ground dries and fades over about 4 Feudum days, and rain speeds it. Waste on covered ground doesn't fade, so dung builds up in a barn until it is mucked out.

### Waste in water

- Waste that enters water adds foulness to it at once, in proportion to the amount, so a chamber pot emptied into a stream runs foul downstream for a stretch, as a current carries it.
- Night soil and dung that land in water dissolve into it and leave no layer.

### Dung heap

- A dung heap is a block that collects night soil, dung, and straw bedding, and rots them into manure over about one season. Turning the heap with a fork speeds it.
- A dung heap is a fouling source like any other waste, so it belongs downhill of the well.
- [Farming](https://github.com/NoNamer777/feudum/issues/32) decides what manure, and fresh waste spread on a field, do to the soil.
- [Dung and manure](https://github.com/NoNamer777/feudum/issues/72) owns the waste items, the waste layer, and the dung heap block.

## Cues

- Players read their own state from body cues, never from a meter.
- **Urge**: a soft shift of weight in the first-person view, once when the stage is reached.
- **Pressing**: the shift repeats, and standing still makes the view sway a little.
- **Desperate**: a hunched step and a tight breath.
- **Soiled**: flies buzz around the body until it is washed.
- Mobs show their state too: a villager past Urge hurries toward a privy, and animals relieve where they stand without warning.

## Food

- The [food component](hunger.md#food) of Hunger also carries a residue amount: how much of the food passes on to the bowels once digested. Grass, hay, and coarse bread leave much, and meat, milk, and ale little.
- The alcohol amount of a drink, which [Brewing](https://github.com/NoNamer777/feudum/issues/28) owns, speeds the filling of the bladder for a while after it.

## Animals

- Animals share one relieving goal: past Urge, they stop and relieve where they stand, and leave dung there.
- A grazing herd spreads its dung across the pasture, where it fades in the open. Stabled animals pile it on the barn floor.
- Animals walk around dung layers deeper than half a block, and a pen floored in deep dung is a matter for Illness.
- A diet profile can let a species seek a spot instead, so a cat or a trained dog goes outside before it relieves.

## Diet profiles

- The [diet profile](hunger.md#diet-profiles) of Hunger carries an optional relief block, so relief needs no profile or entity type tags of its own.
- The relief block holds the bladder and bowel capacity, the stage thresholds, the kind of waste the species leaves, and whether it seeks a spot or relieves where it stands.
- Villagers use the human diet profile, the same as players.
- The young modifier of a profile also shrinks both capacities.

## Persistence

- A player's relief saves with the player. Logging back in resumes from the saved values, since a player's absence is not simulated.
- A new player starts with both stores empty.
- Respawning empties both stores and clears Soiled.
- Wild mobs in unloaded chunks are not simulated. When their chunk loads, each starts with both stores at a random level below Urge, and leaves no dung for the time it was away.
- An owned animal outside any village territory keeps its saved values while its chunk is unloaded, as a logged-out player does.
- Village simulation brings the villagers and livestock of an unloaded village forward, as [Boundaries](#boundaries) describes.

## Query

- One query returns an entity's bladder and bowel fullness, stage, whether it is Soiled, and the current fill rate of each store with the share of each input.
- A second function returns the waste a layer, a privy pit, or a dung heap holds.
- Other mechanics read relief through these.

## Commands

- `/feudum relief query [entity]` shows the result of the query.
- `/feudum relief set <entity> <bladder|bowels> <value>` sets a value, for testing.
- Every `/feudum relief` command requires operator permission.

## Boundaries

Relief owns the bladder and bowels, how they fill, the stages and their effects, accidents and Soiled, relieving and where waste goes, privy pits and who may use them, how relieving moves standing, waste and its layers, how waste fades and fouls, the dung heap and its rotting, cues, the residue amount of food components, the relief block of diet profiles, and the relieving goal of animals. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Hunger](hunger.md)**: the stomach whose digestion fills the bowels, and the food components and diet profiles that Relief extends.
- **[Thirst](thirst.md)**: hydration, the water that passes off once it is full, and the drain whose share fills the bladder.
- **[Fluids](fluids.md)**: how foulness spreads in water and groundwater, and how it decays.
- **[Villages](villages.md)**: the standing scale.
- **[Health](https://github.com/NoNamer777/feudum/issues/36)**: the rule that modifiers of the same kind take the strongest.
- **[Illness](https://github.com/NoNamer777/feudum/issues/37)**: what a Soiled body, deep dung, and fouled water do to a body.
- **[Farming](https://github.com/NoNamer777/feudum/issues/32)**: what manure and fresh waste do to the soil.
- **[Brewing](https://github.com/NoNamer777/feudum/issues/28)**: the alcohol amount of drinks.
- **[Segmented sleep](https://github.com/NoNamer777/feudum/issues/42)**: the waking hour that a full bladder already brings.
- **[Clothing](../content/clothing.md)**: soiled garments, which keep a body Soiled until they are washed.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: when and where a villager relieves, such as the chamber pot at night and the privy by day.
- **[Gong farmer](https://github.com/NoNamer777/feudum/issues/73)**: the villager who empties privy pits and carries night soil to the dung heap.
- **[Inns and taverns](https://github.com/NoNamer777/feudum/issues/74)**: when a guest may use the privy of the house.
- **[Washing and bathhouses](https://github.com/NoNamer777/feudum/issues/75)**: washbasins, bathhouses, and the wetness that washing leaves.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: filling privy pits and dung heaps abstractly while a village is unloaded.
- **[Buildings](https://github.com/NoNamer777/feudum/issues/29)**: which building a privy belongs to, and privies and barns as parts of a village.
- **[Privy and chamber pot](https://github.com/NoNamer777/feudum/issues/71)** and **[Dung and manure](https://github.com/NoNamer777/feudum/issues/72)**: the blocks and items that hold and carry waste.
- **[Textiles](textiles.md)**: the lant tub, which takes the bladder alone, and the stale urine it ages for fulling and dyeing.
