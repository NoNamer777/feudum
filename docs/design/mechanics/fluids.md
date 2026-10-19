# Fluids

Water in Feudum is finite: every block holds real liters that flow, level out, evaporate, and soak into the ground. Rivers run along a generated drainage network and swell or dry with the seasons, the ground holds a water table that wells draw down, and every liter carries a salinity and a foulness that move and mix with it. A pen beside a pond fouls it, a privy uphill of a well fouls the well, and seawater dried in a pan leaves salt. Vanilla water is infinite, still, and always clean, so Feudum replaces it from scratch.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Fluids covers water. [Lava](https://github.com/NoNamer777/feudum/issues/63) waits for a design of its own.
- Feudum water is its own fluid, built from scratch: flow, swimming, buoyancy, and everything else water does. Vanilla water stays registered but is never generated, placed, or obtainable, as [Vanilla water](#vanilla-water) describes.
- Water advances by the Feudum time that passed, so it follows the day length and the sleep speed-up.
- One per-world setting, a tick budget for the flow simulation, trades how quickly water settles for server performance. Gameplay stays the same in every world.

## Volume

- Water is finite and volumetric, and no rule creates water from nothing. [ADR 0009](../../adr/0009-water-is-finite-and-volumetric.md) records why.
- A block holds up to 1000 liters. The surface renders at 16 heights, rounded from the volume.
- Water flows down first and then spreads sideways toward lower neighbors until its surface is level.
- **Settling**: water whose surface has leveled out goes still and costs nothing. A change nearby, such as a drawn bucket, a dug channel, rain, or evaporation, wakes the blocks around it until they settle again.
- **Sea level**: ocean water at sea level holds its level as a fixed boundary. Draining a channel into the sea or flooding a pit from it moves real water at the channel, but never spreads a deficit across the ocean.
- **Wet ground**: water below 50 liters doesn't flow or render as water. The block shows as wet ground, and the water evaporates or soaks in. A body lying on wet ground gains [wetness](body-temperature.md#wetness).
- **Waterlogging**: a waterloggable block, such as a fence, a slab, or stairs, holds water up to its open share of the block, which its shape data lists. A fence in a pond doesn't leave a dry hole in it.
- Containers draw and pour real liters, and drinking by hand takes each sip from the block.

## Rivers

- Rivers run along a drainage network that world generation lays out: courses, confluences, catchments, lake basins, and underground channels through karst. [Terrain](https://github.com/NoNamer777/feudum/issues/60) owns the network, and Fluids owns the water in it. [ADR 0010](../../adr/0010-rivers-follow-a-generated-drainage-network.md) records why.
- Each river segment carries a **discharge** in liters per hour, which sets its level. Discharge sums these sources:
  - **Tributaries**: the discharge of every segment that joins it upstream, so mountain streams merge into a river.
  - **Baseflow**: springs where the [water table](#groundwater) meets the channel, which keep a river running through dry spells.
  - **Runoff**: rain over its catchment, delayed by hours to days. Wetlands in the catchment soak up runoff and release it slowly.
  - **Melt**: snow cover in its catchment as it melts, and glaciers where Terrain generates them.
  - **Lake outlets**: lakes upstream that fill past their rim.
  - **Resurgences**: underground rivers that come back to the surface as large springs.
- Evaporation along the segment subtracts from its discharge.
- Discharge follows the season and the weather, so rivers swell in the Wet season and with spring melt and shrink in the Dry season. A stream whose discharge reaches zero runs dry, so seasonal streams need no rule of their own.
- The sea boundary takes each river's water at its mouth.
- **Current**: river water moves in the direction of its course, at a speed that its discharge and channel set. The current pushes swimmers, items, and boats, and carries [quality](#water-quality) downstream.
- **Floods**: when discharge exceeds what a channel holds, the water spills onto the floodplain as real water, and drains back or soaks in as the river falls. [Farming](farming.md#weather-damage) and [Buildings](https://github.com/NoNamer777/feudum/issues/29) own what floodwater does to crops and buildings.

## Water cycle

Water enters and leaves the world through these paths. The diagram shows where water sits and the flows between those stores that this section, [Rivers](#rivers), and [Groundwater](#groundwater) describe. Blue boxes are where water sits, and dashed boxes are where it enters or leaves the world.

![The water cycle. Weather adds snow to snow cover and ice, rain to open water, and rain on land, which soaks into the ground or runs off into rivers. Snow and ice melt into open water and, in the catchment, into rivers, and open water freezes. Open water flows to rivers through lake outlets and floods draining back, and rivers flood onto it. Open water seeps into the ground, which feeds rivers through baseflow and springs. Wells draw from the ground, and containers, troughs, and bodies draw from open water and pour back into it. Rivers reach the sea at their mouths, and open water and rivers lose water to evaporation.](images/fluids-water-cycle.svg)

### In

- **Rain on water**: rain from [Weather](weather.md) adds volume to open water and to open containers, such as the [rain barrel](https://github.com/NoNamer777/feudum/issues/52).
- **Rain on land**: rain soaks into the ground up to its infiltration rate and recharges the water table. Sand soaks up a lot, clay and stone almost nothing, and saturated ground nothing. The excess becomes real water that flows downhill, pools in hollows, and reaches channels.
- **Melt**: snow cover and ice melt into water, in the amounts Weather sets.
- **Springs**: the sources of [Rivers](#rivers), and the water table where it meets the surface.

### Out

- **Evaporation**: open water loses volume faster in heat, wind, and sun, reading the local temperature, wind, and cloud cover of Weather.
- **Seepage**: water in a permeable block, such as dirt, sand, or gravel, soaks into the ground and recharges the water table. A pond dug in sand drains away unless clay lines it.
- **Drawing and drinking**: containers, troughs, and bodies take real liters.
- **The sea**: the sea boundary takes what flows into it.

### Runoff and loaded chunks

- In loaded chunks, rain on land is real water, and it reaches rivers by flowing there.
- The runoff of a river's discharge counts only the rain over the unloaded parts of its catchment, so no rain counts twice.

## Groundwater

- The **water table** of a column is the depth below which its ground is full of water.
- A baseline follows from the world seed, the generated terrain, the climate profile, and recent precipitation, so it can be computed for any column and moment, as the weather can. Terrain must offer it from the seed alone.
- A column that something touches stores its deviation from the baseline. Wells and heavy drawing lower it, and seepage raises it. Deviations spread slowly to neighboring columns and relax back toward the baseline over time.
- Untouched ground stores nothing.
- A well dug below the water table fills at a rate that grows with its depth below it. A Dry season can drop the table below a shallow well. [Buildings](https://github.com/NoNamer777/feudum/issues/29) owns wells and cisterns.
- [Farming](farming.md#moisture) reads the water table and decides how soil moisture follows from it.

## Water quality

- Every liter of water carries a salinity and a foulness, the values that [Thirst](thirst.md#water-quality) reads. Both are continuous.
- **Generation**: ocean water has a salinity of 1, inland water 0, and estuaries a gradient over the last stretch of each river mouth. Generated swamp and marsh water starts foul. Foulness starts at 0 everywhere else.
- **Storage**: each block's quality defaults to what generation gave its water, and its chunk stores only the blocks that differ, so open ocean costs nothing.
- **Mixing**: quality moves with the water. Where water meets, salinity and foulness mix as an average weighted by volume. Still water also diffuses slowly into its neighbors, so fouling at one edge of a pond creeps across it.

### Fouling

- A fouling source adds foulness to the water within 6 blocks of it at a rate. The sources are livestock, the waste of [Relief](relief.md), and carcasses lying in water.
- The starting rates let three livestock foul a still pond within about one Feudum day.
- Foulness decays toward 0, so a fouled pond clears in about two days once its sources leave.
- A current carries foulness downstream and dilutes it. A river beside a pen stays nearly clean, and the stretch just below the pen runs slightly foul.
- Other content can register as a fouling source, such as the retting bundles and spent water of [Textiles](textiles.md#waste).

### Groundwater quality

- Seepage carries foulness into the water table's deviation of a column, so a cesspit or a pen upslope of a well fouls it through the ground.
- The ground filters what passes through it: sand and loam clean water well, and gravel and fractured rock barely at all.
- Untouched groundwater is clean.

### Evaporation and brine

- Evaporation removes water but not what it carries, so salinity and foulness rise as water evaporates.
- Water with a salinity above 1 is brine, up to saturation at about 7.5. Brine dried out leaves [salt](https://github.com/NoNamer777/feudum/issues/66), so a shallow pan of seawater makes salt.
- Foulness rises up to 1, so a shrinking puddle gets fouler.

## Ice

- [Weather](weather.md#snow-and-ice) decides when ice forms and thaws on water. Fluids decides what the ice holds.
- Ice keeps the volume and quality of the water it froze from, and returns them when it melts.
- Seawater freezes at about −2 °C.
- Ice forming from salty water takes a fifth of its salinity and pushes the rest into the water left behind. Melted sea ice is nearly drinkable, and freezing brine in a pan concentrates it toward salt.

## Bodies in water

- **Swimming**: Fluids owns how bodies move in water: swimming, diving, and climbing out.
- **Buoyancy**: a body floats or sinks by the weight it wears and carries, which [Encumbrance](https://github.com/NoNamer777/feudum/issues/65) owns. A swimmer in mail struggles, and one in plate sinks. Items float or sink the same way, and boats float on the same buoyancy.
- **Current**: a current pushes in proportion to its speed. A strong river sweeps swimmers downstream, and fording one means finding a shallow, slow stretch.
- **Breath**: a body under water uses up its breath and then drowns. [Health](health.md#damage-with-no-struck-region) owns the damage.
- **Fire**: water puts out fire and burning entities.
- **Wetness**: immersion soaks a body, which [Body temperature](body-temperature.md#wetness) reads. Body temperature also owns the water temperature a body in water feels.
- **Aquatic mobs**: Fluids owns how mobs move in water. [Wildlife](https://github.com/NoNamer777/feudum/issues/47) owns how they behave.
- **In the world**: Feudum renders its own underwater view and fog, and plays its own water sounds.

## Vanilla water

- Vanilla water is never generated, placed, or obtainable. Everything that would make it, such as melting ice, a filled bucket, or dripstone, makes Feudum water or nothing.
- Bubble columns, conduits, sponges, and the water role of cauldrons are removed with no replacement.
- [Aquatic plants](https://github.com/NoNamer777/feudum/issues/68) replaces kelp and seagrass and adds reeds. Coral and sea pickles go without replacement.
- [Drink containers](https://github.com/NoNamer777/feudum/issues/49) replaces the bucket.

## Unloaded chunks

- Each chunk records when it last caught up on water. A loaded chunk simulates water as Feudum time passes; an unloaded chunk applies it all when it loads.
- Catching up applies the elapsed rain on open water, evaporation, seepage, foulness decay, and the relaxation of water table deviations. River blocks take the level their discharge sets for the current moment.
- Water never flows across a border with an unloaded chunk. The border acts as a wall until both sides are loaded, and flow then resumes.
- Rain on the land of an unloaded chunk counts only as runoff, as [Runoff and loaded chunks](#runoff-and-loaded-chunks) describes.

## Query

- One query returns, for any position, the volume, salinity, foulness, and current of the water there, its depth, and the water table of the column.
- A second function returns the discharge of a river segment at any moment.
- Other mechanics read water through these, such as Thirst for what a body drinks, Farming for soil moisture, Buildings for wells, and Village simulation during each catch-up step.

## Commands

- `/feudum fluids query [pos]` shows the result of the query.
- `/feudum fluids set <pos> <volume|salinity|foulness> <value>` sets a value, for testing.
- `/feudum fluids discharge <river> [value] [duration]` overrides the discharge of a river, to test floods and droughts. Without a value, it shows the current discharge.
- Every `/feudum fluids` command requires operator permission.

## Boundaries

Fluids owns Feudum water: volume, flow, and settling, river discharge and currents, floods, the water cycle, groundwater and the water table, salinity and foulness with fouling, mixing, and brine, what ice holds, and how bodies move and float in water. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Thirst](thirst.md)**: what salinity and foulness do to a body that drinks.
- **[Weather](weather.md)**: rain, snow cover, ice forming and thawing, and the local temperature, wind, and cloud cover that drive evaporation.
- **[Body temperature](body-temperature.md)**: wetness and water temperature.
- **[Terrain](https://github.com/NoNamer777/feudum/issues/60)**: the drainage network and the groundwater baseline, from the seed alone.
- **[Illness](illness.md)**: what foul water does once drunk, and the stronger fouling of a sick body's waste.
- **[Relief](relief.md)**: the waste that fouls water.
- **[Textiles](textiles.md)**: the retting bundles and spent water of the craft, which foul water.
- **[Health](health.md)**: drowning damage.
- **[Encumbrance](https://github.com/NoNamer777/feudum/issues/65)**: the weight that buoyancy reads.
- **[Sailing](https://github.com/NoNamer777/feudum/issues/41)**: hulls, sails, and steering of boats.
- **[Fishing](https://github.com/NoNamer777/feudum/issues/64)**: catching fish.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: how aquatic mobs behave.
- **[Farming](farming.md)**: soil moisture, irrigation, and what floods do to crops.
- **[Buildings](https://github.com/NoNamer777/feudum/issues/29)**: wells and cisterns, and what floods do to buildings.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: what an unloaded village's wells and ponds yield during catch-up.
- **[Watermill](https://github.com/NoNamer777/feudum/issues/67)**: how a water wheel reads the current and falling water.
- **[Fire](fire.md)**: how fire spreads, and how rain and poured water put it out.
- **[Cooking](cooking.md)**: boiling water.
- **[Salt](https://github.com/NoNamer777/feudum/issues/66)**: the salt item and salt pans.
- **[Drink containers](https://github.com/NoNamer777/feudum/issues/49)**, **[Rain barrel](https://github.com/NoNamer777/feudum/issues/52)**, and **[Feed trough and hay](https://github.com/NoNamer777/feudum/issues/50)**: the containers and troughs that hold water.
- **[Snow and ice](https://github.com/NoNamer777/feudum/issues/53)**: the ice block.
- **[Aquatic plants](https://github.com/NoNamer777/feudum/issues/68)**: plants that grow in water.
- **[Lava](https://github.com/NoNamer777/feudum/issues/63)**: the other vanilla fluid.

World generation must offer the drainage network and the groundwater baseline from the seed alone, as [ADR 0010](../../adr/0010-rivers-follow-a-generated-drainage-network.md) records.
