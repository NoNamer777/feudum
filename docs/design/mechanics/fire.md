# Fire

A village lives by fire and fears it. The hearth burns from dawn to curfew, banked under its ash at night and raked back to life in the morning. Firewood is cut a season ahead so it burns clean, and a household that burns green wood sits in its smoke. A fire takes as long to burn something as the fuel in it allows, so thatch flares up and is gone while a timber hall burns for hours. Fire runs downwind, faster in a dry summer and in a gale, throwing embers over a lane onto the next roof. Rain puts it out, and so do buckets, a shovel of earth, or a wet sack. Smoke fills a room without a louver or a chimney, cures the bacon hanging in it, and chokes the people below. Vanilla fire burns for a random time and treats a log like a leaf, so Feudum replaces it.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Fire covers how blocks catch, burn, and burn out, how dry they are, how fire starts, spreads, and is put out, and the bodies and items it burns. It owns the fuels and their burn times, heat, smoke, and ash, the charcoal clamp, the fireplace, the open fire, banking, the ash pit, room smoke and its exits, and the light a fire gives.
- The fire under each craft block is Fire's, and what the heat does belongs to the craft. [Cooking](cooking.md) owns the hearth and bake oven, [Brewing](brewing.md) the malt kiln and the alembic, [Hygiene](hygiene.md) the bath furnace, and [Textiles](textiles.md) the dye vat.
- [Lava](https://github.com/NoNamer777/feudum/issues/63) owns lava, [Lighting](https://github.com/NoNamer777/feudum/issues/163) torches, candles, rushlights, and lamps, and [Smithing](https://github.com/NoNamer777/feudum/issues/86) the furnace and forge. Fire owns only the risk that their flames set things alight.
- A per-world setting sets how far fire reaches: `on`, `contained`, or `off`. The default is `on`.
  - `on`: everything on this page.
  - `contained`: fire never spreads to blocks and never burns them. Contained fires, burning bodies, and items in fire still work.
  - `off`: fire deals no damage at all. Contained fires still burn their fuel and give heat, smoke, and light, so cooking and the crafts work.
- Fire has no skill: every body lights, feeds, and fights a fire at the same rate, and [Skills](https://github.com/NoNamer777/feudum/issues/43) decides whether that changes.

## Model

A fire draws on the fuel load of the block it burns, and each flammable block burns into a burnt form of its own. [ADR 0024](../../adr/0024-flammable-blocks-carry-a-fuel-load.md) records why.

- A fire is a block in the air next to its fuel, or on top of it.
- Each flammable block carries a **fuel load**, which sets how long it feeds a fire, and an **ignition threshold**, which sets how easily it catches. Both are data-driven: block tags map a block to its values, as heat sources do under [Body temperature](body-temperature.md#shelter-and-heat).
- A fire burns down the fuel load of the block it feeds on. When the load runs out, the block turns into its burnt form and the fire moves on or dies.
- A fire burns at one of three **fire sizes**: Small, Medium, or Large. A larger fire burns hotter and faster. A laid fire takes its size from the fuel laid on it, and a spreading fire from the fuel load of the blocks it burns, so a grass fire stays Small and a burning timber wall is Large.
- A **smoldering fire** gives much smoke and little heat. A fire smolders on green or damp fuel, on sawdust, under a cover of earth, and when it is banked.

### Burnt forms

| Block                             | Burnt form                                                            |
|:----------------------------------|:----------------------------------------------------------------------|
| Thatch, leaves, planks, wool, hay | Air                                                                   |
| Logs, timber beams                | Charred timber, which still stands but breaks fast and drops charcoal |
| Grass, and dirt with plants       | Burnt ground, which greens again over a few weeks                     |
| Crops                             | Air, with the crop lost                                               |
| Stone, metal                      | Unchanged                                                             |

- Wood-based fuel leaves a thin ash layer where it burned, which can be gathered as wood ash.

## Dryness

How easily a block catches depends on its **dryness**. Dryness is computed from the recent weather at a place, not stored on each block:

- Days since the last precipitation, the local temperature, and the wind dry blocks out, and precipitation soaks them. [Weather](weather.md) supplies each value for any place and moment.
- A covered block, under no open sky, is never soaked, so a roof keeps the timber below it dry.
- Dryness has four labels. Starting values to tune:

| Dryness | Catches                   |
|:--------|:--------------------------|
| Soaked  | Only next to a Large fire |
| Damp    | Slowly, and smolders      |
| Dry     | At its ignition threshold |
| Parched | Readily, and spreads fast |

- A thatch roof soaked by a week of rain resists sparks, and grassland in a dry summer goes up fast.

### Seasoned firewood

- Wood cut from a tree is **green**. Green wood burns at a lower heat and gives much more smoke than seasoned wood.
- Firewood seasons over about a season while it is stored under cover. Wood left in the rain doesn't season.
- Seasoning applies to firewood items only. Logs placed in the world follow the dryness of their place.

## Ignition

Fire starts from:

- **Lightning**, which strikes high points during storms under [Weather](weather.md#in-the-world). A struck block catches by its dryness. Lightning is the only source of wildfire: no fire starts on its own in hot weather.
- **A fire steel** struck on flint over tinder, as [Lighting a fire](#lighting-a-fire) describes.
- **A brand or taper** lit at an existing fire and carried to the next.
- **Embers** carried downwind, as [Spread](#spread) describes.
- **Sparks** from an open fire, as [Sparks](#sparks) describes.
- **A burning body**, which sets the blocks it stands in alight by their dryness.

### Lighting a fire

- Striking a fire steel on flint over tinder lights the tinder, and the tinder kindles a fire on the fuel it is laid in. Dry fuel catches, and green or damp fuel kindles into a smoldering fire.
- The tinders are char cloth, tinder fungus, dry grass, and [shives](textiles.md#waste). Char cloth is linen charred in a closed tin in a fire.
- Each strike uses up its tinder. The fire steel wears slowly, and the flint chips away.
- [Smithing](https://github.com/NoNamer777/feudum/issues/86) makes the fire steel. Flint comes from the world, as it does for [Weapons](../content/weapons.md).

## Spread

- A fire reaches into the flammable blocks around it. Starting values to tune: in calm air, it reaches a neighboring block every few seconds, by the block's dryness and ignition threshold.
- Spread follows the sheltered wind of [Weather](weather.md#wind-shelter), gusts included. Fire spreads faster and farther downwind, and upwind at about a quarter of its calm speed.
- From Breeze up, **embers** jump gaps downwind and land on blocks that catch by their dryness. Starting values to tune:

| Wind label   |     Ember reach |
|:-------------|----------------:|
| Calm         |            None |
| Light breeze |            None |
| Breeze       |  About 3 blocks |
| Strong wind  |  About 8 blocks |
| Gale         | About 16 blocks |
| Tempest      | About 24 blocks |

- A firebreak has to be wider than the ember reach of the wind, so a lane that stops a fire on a calm day doesn't stop it in a gale.

### Sparks

- An open hearth, a fireplace, and an open fire throw sparks onto flammable blocks within 2 blocks, at a low chance that grows with the fire size and the dryness of those blocks. Floor rushes and a low thatch roof can catch.
- A hearthstone under the fire or a fireguard in front of it stops its sparks, and so does a clear radius of 2 blocks.
- Fires built in stone, such as the bake oven, the malt kiln, and the bath furnace, never throw sparks.

## Putting fire out

- **Precipitation** puts out fires under open sky in proportion to its intensity. Light rain slows spread, heavy rain puts fires out within a Feudum hour, and falling snow acts as light rain. Covered fires are untouched.
- **Water** puts out fire in proportion to the volume poured, so each bucket puts out about as much as it holds. The water is the finite water of [Fluids](fluids.md#volume).
- **Sand or dirt** shoveled onto a fire smothers it.
- **Beating** a Small fire with a wet sack or a green branch puts it out.
- A fire with no fuel left dies.
- [Villagers](https://github.com/NoNamer777/feudum/issues/46) decides how villagers raise the alarm and form a bucket line.

## Fuels

Fuels are data-driven: a data pack gives each fuel a burn time, a heat output, a smoke amount, and an ash yield. The starting set, as relative values to tune:

| Fuel                     | Burn time  | Heat   | Smoke       | Ash             |
|:-------------------------|:-----------|:-------|:------------|:----------------|
| Straw, shives, dry grass | Very short | Low    | Little      | Little wood ash |
| Planks                   | Short      | Medium | Little      | Some wood ash   |
| Firewood, seasoned       | Medium     | Medium | Little      | Wood ash        |
| Logs                     | Long       | Medium | Little      | Wood ash        |
| Charcoal                 | Long       | High   | Almost none | Little wood ash |
| Peat                     | Long       | Low    | Heavy       | Ash             |
| Dried dung cakes         | Medium     | Low    | Heavy       | Ash             |
| Sea coal                 | Very long  | High   | Heavy       | Ash             |

- Straw, shives, and dry grass are kindling: they catch fast and burn out fast, so they light larger fuel.
- Green wood burns as its seasoned form does, but at a lower heat and with heavy smoke.
- Only wood and charcoal leave wood ash, which [Hygiene](hygiene.md#lye-and-soap) leaches into lye. Peat, dung, and sea coal leave ash that makes no lye.
- [Smithing](https://github.com/NoNamer777/feudum/issues/86) reads charcoal and sea coal as the fuels of the forge and furnace.

### Charcoal clamp

- A **charcoal clamp** is wood stacked and covered on every face with turf or earth, then lit. Under its cover it smolders, and over about 3 to 5 Feudum days it chars the wood into charcoal.
- It yields about a quarter of the wood's volume as charcoal, as a starting value.
- A clamp has to be tended. Where it isn't, flame breaks through its cover at a spot. Packing turf or earth over the spot seals it again.
- Each spot left open burns away part of the yield, and a clamp left alone long enough burns through to ash.
- Charcoal burning is sooty work that builds [grime](hygiene.md#grime) fastest.

## Contained fires

A contained fire burns in a block made for it: the hearth, the fireplace, the open fire, the bake oven, the malt kiln, the bath furnace, and the fires under the dye vat and the alembic.

- Fuel is laid into the block, and the fire takes its size from the fuel laid on it. It burns down unless it is fed.
- Its heat output follows its size, and it is a heat source under [Body temperature](body-temperature.md#shelter-and-heat). A burning building is a strong heat source too.
- A contained fire burns down its fuel during catch-up under [Time](time.md#unloaded-villages), so a hearth left unfed in an unloaded village goes out.

### Fireplace

- A **fireplace** is a hearth set into a wall, which Cooking treats as a [hearth](cooking.md#heat), with its spit, pot hook, trivet, and griddle.
- It carries its smoke up a [chimney](#smoke-exits). The open central hearth of Cooking vents through a smoke louver instead.
- It throws sparks as an open hearth does, as [Sparks](#sparks) describes.

### Open fire

- An **open fire** is laid on the ground from fuel, and replaces the vanilla campfire.
- It burns down unless it is fed, and a heated cauldron can sit over it, as [Cooking](cooking.md#heat) allows.

### Banking

- Any open fire, hearth, or fireplace can be **banked**: covered with ash at night to keep its embers.
- A banked fire smolders until morning with little heat and a dim glow.
- Adding kindling to a banked fire revives it, with no need to strike a light.

### Ash pit

- Burning wood leaves wood ash in the **ash pit** of its hearth, fireplace, or open fire, in proportion to the fuel burned. A shovel takes it out.
- A full ash pit starves the fire of air, so it burns at most at Medium until the ash is cleared.
- The bake oven is raked out after every firing, as [Cooking](cooking.md#bake-oven) describes, so it never fills.
- Banking draws on the ash in the pit, and [Hygiene](hygiene.md#lye-and-soap) leaches the rest into lye.

## Smoke

- Every fire gives smoke by its fuel and its size, and a smoldering fire gives the most.
- Each enclosed space, as [Body temperature](body-temperature.md#shelter-and-heat) defines it, holds a **room smoke** level. Its fires feed it, and its openings and smoke exits drain it.
- Room smoke is cached and recomputed as room temperature is, and drops when the chunks unload.

### Smoke stages

Each stage carries the effects of the stages before it:

| Stage   | Effect                                                                                              |
|:--------|:----------------------------------------------------------------------------------------------------|
| Hazy    | Soot grime builds on bodies, and food on a smoking rack cures.                                      |
| Smoky   | Watering eyes blur the edges of the view, and bodies cough.                                         |
| Choking | Damage to the chest pool, as drowning deals under [Health](health.md#damage-with-no-struck-region). |

- Soot grime is the grime of [Hygiene](hygiene.md#grime).
- Cold smoking under [Food preservation](food-preservation.md#smoking) needs a Hazy room over a smoldering fire.
- Smoke never causes a lasting illness.
- Outdoors, smoke rises as a column and drifts downwind, so a fire shows from afar.

### Smoke exits

- A **smoke louver** is a roof block that drains smoke and loses heat as half an opening does.
- A **chimney** is a stone flue that runs from a fireplace to open sky. It drains smoke well and loses little heat. It costs more stone and labor than a louver, as it did historically.
- Doors and other openings drain some smoke too.

## Burning bodies

- A body catches fire by standing in fire, from a burning attacker or arrow, and from embers that land on it.
- It burns for a time set by the outer garments it wears. Starting values to tune:

| Outer garments     |        Burns for |
|:-------------------|-----------------:|
| Wool               |  About 2 seconds |
| Plain clothes      |  About 4 seconds |
| Dry linen or straw | About 10 seconds |

- Rolling, by sneaking on the ground while standing still, puts the fire out in about 2 seconds. Rain and water put it out too.
- Burning wears the garments it burns, under [Clothing](../content/clothing.md).
- [Health](health.md#damage-with-no-struck-region) owns the damage and the [burns](health.md#injuries): the legs for a body standing in fire, and every pool for a burning body.
- Animals flee fire, and [Wildlife](https://github.com/NoNamer777/feudum/issues/47) decides how.
- Creative and spectator players are exempt.

## Items in fire

- A flammable item dropped in fire burns after about 5 seconds, so it can be snatched back. Other items survive.
- A burning container keeps its contents until its own fuel load runs out, which takes about 30 seconds for a chest.
- A few seconds after a container catches, its flammable stacks start burning one at a time.
- While it burns, a body can still open it and pull items out, but each second spent at it risks catching fire.
- When it burns out, its flammable contents are lost and the rest spill.

## Light

- A fire gives light that grows with its size.
- A smoldering or banked fire gives only a dim glow.
- [Lighting](https://github.com/NoNamer777/feudum/issues/163) owns torches, candles, rushlights, and lamps.

## Cues

- Players read a fire from the world and the item, never from a meter or a timer.
- A fire crackles, and the crackle grows into a roar with its size.
- Smoke particles thicken with green or damp fuel.
- Charred timber glows while it cools.
- The tooltip of firewood shows Green or Seasoned.
- The ash fill shows in the hearth.

## Unloaded chunks

- A spreading fire freezes when its chunk unloads and resumes when the chunk loads again.
- Contained fires burn down their fuel during catch-up, as [Contained fires](#contained-fires) describes.

## Tools and blocks

| Use                          | Tool or block             | Made of                                                                       |
|:-----------------------------|:--------------------------|:------------------------------------------------------------------------------|
| Light a fire                 | Fire steel, flint, tinder | Steel, from [Smithing](https://github.com/NoNamer777/feudum/issues/86); flint |
| Make char cloth              | Closed tin                | Tin or iron, from Smithing                                                    |
| Carry fire                   | Brand, taper              | A stick; a rush or wax taper                                                  |
| Burn indoors, with a chimney | Fireplace, chimney        | Stone                                                                         |
| Burn in the open             | Open fire                 | Fuel laid on the ground                                                       |
| Stop sparks                  | Hearthstone, fireguard    | Stone; iron, from Smithing                                                    |
| Drain smoke                  | Smoke louver              | Wood, from [Carpentry](https://github.com/NoNamer777/feudum/issues/115)       |
| Clear ash, smother fire      | Shovel                    | Wood or iron                                                                  |
| Beat out fire                | Wet sack, green branch    | Cloth; a branch                                                               |
| Make charcoal                | Charcoal clamp            | Stacked wood under turf or earth                                              |

## Vanilla content

- The vanilla fire and soul fire stay hidden, and Feudum's own fire replaces them.
- Flint and steel stays hidden, and the fire steel replaces it.
- The fire charge stays hidden.
- The campfire and the soul campfire stay hidden, and the open fire replaces them.
- The vanilla flammability of blocks is off, so only Feudum's fuel loads and ignition thresholds decide what burns.
- The fire enchantments and the fire resistance potions are already off, with enchanting and [Brewing](brewing.md#vanilla-content).

## Persistence

- Every burning block saves its remaining fuel load and its fire size.
- Every contained fire saves its fuel, size, ash fill, banked state, and the time it last caught up.
- Every charcoal clamp saves its progress, its open spots, and the time it last caught up.
- Firewood saves its seasoning.
- Dryness is computed from the weather, so it is never saved. Room smoke is cached, as [Smoke](#smoke) describes.

## Query

- One query returns the fire state at a position: its dryness, the fire size of any fire there, and the room smoke of the space it belongs to.
- Other mechanics read fire through this query.

## Commands

- `/feudum fire dryness <pos> [label] [duration]` overrides the dryness at a position, to test wildfires and soaked roofs. Without a label, it shows the current dryness.
- `/feudum fire smoke <pos>` shows the smoke stage of the room at a position.
- Every `/feudum fire` command requires operator permission.

## Boundaries

Fire owns fire blocks, fuel loads, ignition thresholds, burnt forms, fire sizes, and smoldering, dryness and the seasoning of firewood, ignition, the fire steel, tinder and char cloth, spread, embers and sparks, and how fire is put out. It also owns the fuels and their burn times, heat, smoke, and ash, the charcoal clamp, contained fires, the fireplace, the open fire, banking, and the ash pit. Room smoke with its stages and exits, burning bodies, items and containers in fire, the light of a fire, and its cues are its own as well. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Weather](weather.md)**: precipitation, the local temperature, the wind and wind shelter, and lightning.
- **[Fluids](fluids.md)**: the finite water that puts fire out.
- **[Body temperature](body-temperature.md)**: heat sources, enclosed spaces, openings, and room temperature.
- **[Health](health.md)**: the damage fire deals and the burns it leaves.
- **[Clothing](../content/clothing.md)**: garments and how they wear.
- **[Cooking](cooking.md)**: the hearth, the heated cauldron, the bake oven, and what their heat cooks.
- **[Brewing](brewing.md)**: the malt kiln and the alembic.
- **[Food preservation](food-preservation.md)**: the smoking rack and smoked food.
- **[Hygiene](hygiene.md)**: grime, the bath furnace, and lye.
- **[Textiles](textiles.md)**: shives, linen, and the dye vat.
- **[Time](time.md)**: catch-up.
- **[Weapons](../content/weapons.md)**: flint.
- **[Lava](https://github.com/NoNamer777/feudum/issues/63)**: lava, and the fire it starts.
- **[Lighting](https://github.com/NoNamer777/feudum/issues/163)**: torches, candles, rushlights, and lamps.
- **[Smithing](https://github.com/NoNamer777/feudum/issues/86)**: the fire steel, the fireguard, the furnace, and the forge.
- **[Carpentry](https://github.com/NoNamer777/feudum/issues/115)**: the smoke louver.
- **[Farming](farming.md)**: the crops that fire destroys, and burning stubble.
- **[Buildings](https://github.com/NoNamer777/feudum/issues/29)**: how houses are built with hearths, fireplaces, chimneys, and louvers.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: how animals flee fire.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: when villagers tend, bank, and fight fire.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: fire in a village while it is unloaded.
- **[Skills](https://github.com/NoNamer777/feudum/issues/43)**: whether fire takes a skill.
