# Fishing

Every fish in Feudum is a real fish in real water. Trout hold in the cold, fast riffles, pike lie in the weed of a still pool, and herring flicker in shoals under the diving gulls. Each species lives where the water suits it, spawns in its season on its own ground, and grows over the years, so a pond fished out in spring takes years to recover. In autumn the salmon run upriver to the spawning gravel and pile up below any weir that leaves them no gap. A village takes its fish with rod and line, nets, traps, weirs, the spear, and the rake, and it keeps carp in a dug pond that it drains to harvest. Vanilla fishing pulls loot from a table wherever a bobber lands, so Feudum replaces it.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Fishing covers finfish, eels, crabs, lobsters, crayfish, and shellfish beds. It owns the fish themselves (their species, where they live, how many there are, and how they breed, grow, and migrate), every way of catching them, fishponds, and gutting the catch.
- [Wildlife](https://github.com/NoNamer777/feudum/issues/47) owns how live fish behave, such as fleeing a shadow, and the herons, otters, and other predators that hunt them. It also owns whales, seals, and the other water mobs, as [Vanilla content](#vanilla-content) describes.
- [Sailing](https://github.com/NoNamer777/feudum/issues/41) owns boats, rowed and under sail. Fishing says only what is done from them.
- [Foods](https://github.com/NoNamer777/feudum/issues/51) owns the food components of fish and roe, and [Food preservation](food-preservation.md) owns how they keep and how they are salted, smoked, dried, and pickled.
- Fishing advances by the Feudum time that passed, so it follows the day length and the sleep speed-up.

## Working

- A hand step, such as netting, gutting, or cutting an ice hole, is done by holding the use key, as in [Brewing](brewing.md#working). Work advances by the Feudum time that passed, and stopping keeps what is done.
- Villagers do the same work at the same rate as a player. The [Fisher](https://github.com/NoNamer777/feudum/issues/171) plans the villager who fishes for a village and keeps its weirs and ponds.

## Fish

- Every fish is a mob that swims in Feudum water. [ADR 0026](../../adr/0026-fish-are-mobs-with-populations-of-their-own.md) records why.
- [Fluids](fluids.md#bodies-in-water) owns how fish move in water, and Wildlife owns how they behave.
- Every span on this page that comes from biology is the real span, scaled to the calendar as [Animal husbandry](animal-husbandry.md#species) scales it. A year has 96 days, so a real month is about 8 days, and a real year is one Feudum year.

### Shoals

- A small schooling species (herring, mackerel, pilchard, roach, and minnow) lives as a **shoal**: one mob that carries a count of fish and their average weight.
- The client renders a shoal as its count of individual fish, up to a cap of about 40, that flock together. They turn as one, scatter from a predator or a splash, and bunch in a net. The server tracks one entity.
- A catch takes fish from a shoal's count. A shoal whose count falls to zero is gone, and two shoals of a species that meet merge.
- The fry of every species hatch as a shoal too, as [Spawning](#spawning) describes.

### Weight and age

- Every fish has a **weight** that grows with its age, toward the size of its species in the [Species](#species) table. A fish that eats poorly grows slowly, and a crowded water body stunts its fish.
- Weight sets the yield when gutted, the line it takes to land the fish, and whether it slips through a net's mesh.
- A fish is adult once it reaches the age its species spawns at.

### Profiles

Fish carry the profiles that the ADRs require of every living mob:

- **Health**: a [body profile](health.md#pools) with a head and a body pool, as for every legless body.
- **Body temperature**: a [thermal profile](body-temperature.md#thermal-profiles) that marks fish as ectotherms. Its comfort band is the water temperature the species lives in. Cold water slows a fish, so it feeds and bites less, and water too warm for the species stresses and then kills it.
- **Hunger**: a [diet profile](hunger.md#diet-profiles) whose appetite drives bites, as [Angling](#angling) describes. A fish fills its stomach from the food of its water body, at a rate that its [carrying capacity](#carrying-capacity) sets, with no foraging behavior.
- **Illness**: an illness block, so fish catch the [fish plagues](illness.md#fish-plagues) of Illness.
- **Exempt**: thirst, relief, and dirt. Fish foul water as [Fouling](#fouling) describes, rather than through relief.

## Habitat

A species lives, feeds, and spawns only where the water suits it. Each species' profile sets its range for every factor below, and its row in the [Species](#species) table summarizes them.

| Factor            | Read from                                                                                           |
|:------------------|:----------------------------------------------------------------------------------------------------|
| Salinity          | [Fluids](fluids.md#water-quality): fresh, brackish, or sea                                          |
| Current           | Fluids: still or running, and how fast                                                              |
| Depth             | Fluids                                                                                              |
| Water temperature | [Body temperature](body-temperature.md#felt-temperature)                                            |
| Foulness          | Fluids                                                                                              |
| Oxygen            | Computed, as [Oxygen](#oxygen) describes                                                            |
| Bottom            | The block under the water: gravel, sand, mud, or stone                                              |
| Cover             | [Aquatic plants](https://github.com/NoNamer777/feudum/issues/68) and submerged roots or logs nearby |
| Access            | Whether a migrating fish can find a path, as [Migration](#migration) describes                      |

- Food stays abstract: it sets a water body's [carrying capacity](#carrying-capacity) rather than being a value of its own.
- A fish outside its range for salinity, temperature, oxygen, or foulness is stressed and then dies, so a sea fish carried into a pond dies, and a trout in a warm, still pool struggles.
- Bottom and cover decide where a species holds and spawns within its water: pike lie in the weed, salmon spawn on clean gravel, and tench root in the mud.

### Oxygen

- The oxygen of water is computed whenever it is read, never stored. It runs from 0 to 1.
- Cold water holds more than warm, running water more than still, and a tumbling stretch over stones the most.
- Foulness lowers it, as rot uses it up.
- Ice cover cuts it off: still water under ice loses oxygen each day the ice holds, faster the shallower it is. A shallow pond under ice through a long frost drops low enough to kill.
- Each species has an oxygen need, from high for trout and salmon to very low for carp, tench, and eels.

## Species

The roster below gives each species its own mob and its own whole fish item. Spawning seasons, weights, and needs are starting values to tune.

| Species   | Lives in                                 | Spawns           | Spawns on               | Adult at | Oxygen   | Grows to     |
|:----------|:-----------------------------------------|:-----------------|:------------------------|:---------|:---------|:-------------|
| Trout     | Cold, running fresh water                | Late Autumn      | Gravel                  | 3 years  | High     | About 2 kg   |
| Grayling  | Cold, running fresh water                | Mid Spring       | Gravel                  | 3 years  | High     | About 1 kg   |
| Barbel    | Cool, running fresh water, deep runs     | Late Spring      | Gravel                  | 4 years  | Medium   | About 5 kg   |
| Gudgeon   | Running fresh water over sand and gravel | Late Spring      | Stones                  | 2 years  | Medium   | About 50 g   |
| Minnow    | Cold, clear, running fresh water         | Late Spring      | Gravel                  | 1 year   | High     | About 10 g   |
| Crayfish  | Cool, running fresh water over stones    | Late Autumn      | Carried by the female   | 3 years  | Medium   | About 100 g  |
| Pike      | Still or slow fresh water, weed          | Early Spring     | Flooded vegetation      | 3 years  | Medium   | About 15 kg  |
| Perch     | Still or slow fresh water, roots, weed   | Mid Spring       | Weed and roots          | 3 years  | Medium   | About 1 kg   |
| Roach     | Still or slow fresh water                | Late Spring      | Weed                    | 3 years  | Low      | About 500 g  |
| Bream     | Still, warm fresh water over mud         | Early Summer     | Weed                    | 4 years  | Low      | About 4 kg   |
| Tench     | Still, warm fresh water over mud, weed   | Mid Summer       | Weed                    | 3 years  | Very low | About 3 kg   |
| Carp      | Still, warm fresh water over mud         | Early Summer     | Weed, above about 18 °C | 4 years  | Very low | About 10 kg  |
| Salmon    | The sea, and rivers to spawn             | Late Autumn      | River gravel            | 4 years  | High     | About 10 kg  |
| Sea trout | The sea, and rivers to spawn             | Mid Autumn       | River gravel            | 3 years  | High     | About 4 kg   |
| Eel       | Fresh water, and the sea to spawn        | Beyond the world | Beyond the world        | 10 years | Very low | About 2 kg   |
| Lamprey   | The sea, and rivers to spawn             | Late Spring      | River gravel            | 6 years  | Medium   | About 1 kg   |
| Sturgeon  | The sea, and large rivers to spawn       | Late Spring      | River gravel and stone  | 12 years | Medium   | About 100 kg |
| Herring   | Cool sea                                 | Early Autumn     | Gravel banks at sea     | 3 years  | Medium   | About 300 g  |
| Mackerel  | The upper sea, inshore in summer         | Late Spring      | Open water              | 2 years  | High     | About 700 g  |
| Pilchard  | Warm sea, inshore in summer              | Mid Spring       | Open water              | 2 years  | Medium   | About 100 g  |
| Cod       | Cold sea                                 | Late Winter      | Open water              | 4 years  | Medium   | About 15 kg  |
| Ling      | Cold, deep sea over rock                 | Late Spring      | Open water              | 6 years  | Medium   | About 20 kg  |
| Hake      | Deep sea                                 | Early Summer     | Open water              | 4 years  | Medium   | About 5 kg   |
| Haddock   | Cold sea                                 | Early Spring     | Open water              | 3 years  | Medium   | About 2 kg   |
| Plaice    | The sea over sand                        | Late Winter      | Open water              | 4 years  | Medium   | About 2 kg   |
| Sole      | Warmer sea over sand or mud              | Mid Spring       | Open water              | 3 years  | Medium   | About 1 kg   |
| Conger    | The sea among rocks                      | Beyond the world | Beyond the world        | 10 years | Low      | About 20 kg  |
| Crab      | The sea among rocks                      | Late Winter      | Carried by the female   | 4 years  | Medium   | About 2 kg   |
| Lobster   | The sea among rocks                      | Mid Summer       | Carried by the female   | 6 years  | Medium   | About 3 kg   |

- Each weight is the size a grown fish reaches. Old fish grow larger, so a rare pike, cod, or sturgeon grows well past it.
- Carp is a pond fish that villages bring in, and world generation places it wild only rarely.
- Sturgeon is rare everywhere.
- [Shellfish beds](#shellfish-beds) hold mussels, oysters, cockles, and whelks.

## Population

### Stocking

- World generation stocks every water body to its carrying capacity, with the species its habitat suits, at a spread of ages.
- A **water body** is a river segment of the [drainage network](fluids.md#rivers), a lake basin, a pond of connected still water, or, at sea, each chunk of sea water.

### Spawning

- Adults of a species spawn in its season on its spawning ground, when at least two of them are in the same water body and in good condition under Hunger.
- Spawning lays a clutch of eggs on the ground. Each chunk stores its clutches as a short list, with the species, the count, and the date laid. Open-water spawners lay theirs in any water of the right salinity and temperature.
- Eggs hatch after about 8 days, and their fry rise as a shoal. Foulness, low oxygen, water falling away from the ground, or trampling kills eggs.
- A fry shoal of a solitary species splits into single fish once its fish reach a size that the species sets.
- Fry die fast: most of a clutch never reaches its first year, and a water body above its carrying capacity loses more.
- Crabs, lobsters, and crayfish carry their eggs until they hatch, so their clutches travel with the female.
- Eels and congers spawn beyond the world. Their young arrive from the open sea each Spring, as [Migration](#migration) describes, at a rate the species sets.

### Carrying capacity

- The **carrying capacity** of a water body is the weight of fish it can feed. Its size, depth, warmth, shallows, and cover set it. A shallow, weedy, warm pond feeds more fish for its size than a deep, bare channel.
- Below capacity, fish eat well and grow, and their fry survive. Above it, fish grow slowly and lose condition, and fry die off, so the water body settles back toward capacity.
- Hungry fish bite more readily, so a stunted, crowded pond is easy to fish.
- [Fishponds](#fishponds) can raise their capacity with feed.

### Deaths

- Fish die of old age, at a lifespan the species sets.
- A share of fry and small fish die each season to predators, larger where pike or other fish eaters live. Wildlife owns the herons, otters, and birds that hunt fish as mobs.
- Fish die of low oxygen, foulness, heat, and the fish plagues of [Illness](illness.md#fish-plagues).
- Fishing takes the rest. A water body fished hard before its spawning season has few spawners left, and takes years to come back.

### Fish kills

- When oxygen falls below the need of a species, or foulness rises above its tolerance, its fish gasp at the surface and then die within hours.
- A dead fish floats belly-up and is a carcass in water, a [fouling source](fluids.md#fouling) of Fluids. A large kill fouls the water further and can kill what is left.

## Migration

Some species live part of their lives in the sea and part in rivers. The diagram shows their runs along a river and what a barrier does to them. The layout of the river is illustrative.

![Two views of a river running from its spawning gravel upstream down to the sea. Past a weir that leaves a gap, salmon and sea trout run up in Autumn, and lampreys and sturgeon in Spring. Young salmon and sea trout go down to the sea, grown eels run down in Autumn and leave the world, and elvers come up in Spring. Below a weir across the whole channel, the upriver runs pile up and none reaches the gravel, while eels cross it over wet ground both ways.](images/fishing-migration.svg)

- **Upriver runs**: salmon and sea trout run up from the sea in Autumn, lampreys and sturgeon in Spring. Each follows the drainage network of Fluids upstream to the spawning gravel of the river it hatched in, which it saves as its home river.
- **Down to the sea**: young salmon and sea trout go down to the sea after about 2 years in the river, and grow there. Lampreys die after spawning. Salmon and sea trout that survive spawning drift back down to the sea.
- **Eels**: grown eels run down to the sea on dark Autumn nights, reach the open sea, and leave the world. Elvers arrive at river mouths each Spring and climb into fresh water.
- **Sea shoals**: herring, mackerel, and pilchard come inshore in their season and go back to deep water after. Cod move to their spawning grounds in Winter.
- **Barriers**: a weir, a mill dam, or any structure across the full width of a river blocks a run, as does a fall higher than the species can leap. Salmon leap falls up to about 3 blocks, and other species leap none. A run that meets a barrier piles up below it, and spawns there on whatever ground it finds or not at all. A gap at least a block wide in the deepest part of the channel lets every run pass.
- Eels cross a barrier over wet ground, so only a dry barrier stops them.
- **In transit**: a migrating fish that reaches the border of an unloaded chunk is stored as in transit, on its river segment or, at sea, on its path. When the chunk ahead loads, the fish is placed where its swimming speed and the time elapsed put it along its route. A barrier stops a fish in transit as it stops one in loaded water.

## Shellfish beds

- Mussels, oysters, cockles, and whelks live as **bed blocks** on the floor of shallow coastal water. Each bed has a species and a density from 0 to 100%.
- Mussels grow on stone, oysters on mud and shell in brackish and sea water, cockles in sand, and whelks on sand and mud below them.
- Gathering takes from the density. Beds regrow each Summer, when spat from the beds nearby settle, faster the denser the beds around them.
- Foulness above a bed's tolerance kills it slowly. Shellfish filter the water they live in, so shellfish from foul water add a [foul load](thirst.md#model) when eaten, as Spoiled food does.
- [Tides](https://github.com/NoNamer777/feudum/issues/172) will move beds onto the flats that the tide bares and floods. Until it is designed, beds sit in shallow water.

## Fouling

- Fish register with Fluids as a [fouling source](fluids.md#fouling), at a rate that scales with the weight of fish per liter of water.
- The rate is low enough that wild water never fouls from its fish. Crowded water does: an overstocked pond, a weir pound, a keepnet, or a fish box fouls, which lowers its oxygen and can end in a fish kill.

## Angling

### Casting

- An angler fishes with a rod, a line, a hook, and bait, and a float or a sinker.
- Holding the use key swings the rod, and releasing it casts. The longer the hold, the farther the cast, up to the length of the line.
- With a float, the bait hangs at the depth the float sets. With a sinker and no float, it lies on the bottom, where eels, barbel, and flatfish feed.

### Bites

- A bite comes from a real fish that finds the bait. A fish notices bait within a few blocks by its scent and movement, and farther downstream where the current carries the scent.
- Its appetite under Hunger decides whether it takes the bait, along with:
  - **Season and water temperature**: fish in cold water are sluggish and bite little.
  - **Time of day**: most species feed at dawn and dusk, and eels at night.
  - **Weather**: overcast skies and water colored by rain bring bites, and a bright, still noon brings few.
  - **Bait**: each species favors some baits, as [Bait](#bait) describes.
  - **Wariness**: a fish that sees the angler close on the bank, or that was hooked and lost, stays wary for a while.

### Striking and playing

- **Bite**: the float dips, or the line twitches. The angler strikes within about a second, or the fish drops the bait.
- **Playing**: a fish heavy for the line fights. Holding the use key pulls, and releasing it gives line. Too much strain breaks the line, and too little lets the fish throw the hook. The fish tires as it is played.
- There is no reel: the line is tied to the rod tip, as on a medieval rod, so a heavy fish is landed only by tiring it.
- A small fish comes straight in after the strike.
- **Landing**: a fish heavier than about 2 kg needs a **landing net**, or it may slip off at the bank.

### Set lines

- A **night line** is a line with a few baited hooks, staked on the bank and left. A **longline** carries many hooks and is set from a boat.
- Fish take the hooks while no one watches. A hooked fish stays alive on its hook for a few hours and then dies, and eels or predators may take it.

## Bait

| Bait           | Made from                                                                                 | Favored by                               |
|:---------------|:------------------------------------------------------------------------------------------|:-----------------------------------------|
| Worms          | Dug with a spade from moist soil, more where [soil moisture](farming.md#moisture) is high | Most fresh-water fish, eels, flatfish    |
| Maggots        | Bred on a carcass or offal left in the open                                               | Roach, bream, perch, grayling            |
| Paste          | Dough from [Cooking](cooking.md), or grain                                                | Carp, tench, bream, roach                |
| Cut fish       | Pieces of a whole fish                                                                    | Eels, cod, ling, conger, crabs, lobsters |
| Live bait      | A small fish, such as a minnow or gudgeon, kept alive                                     | Pike, perch, salmon                      |
| Artificial fly | Tied from feathers and thread                                                             | Trout, grayling, salmon                  |

- Bait spoils under Food preservation. Live bait dies out of water as any fish does, and is kept alive as [The catch](#the-catch) describes.

## Tackle

- **Rod**: a hazel or ash pole, from [Forestry](https://github.com/NoNamer777/feudum/issues/165).
- **Line**: horsehair or [twine](textiles.md#cordage). Horsehair is cut from a horse's tail with shears, under the [ownership](animal-husbandry.md#ownership) rules of Animal husbandry. A line's strength sets the weight of fish it holds without breaking, and plying more hairs makes it stronger.
- **Hook**: iron, from [Smithing](https://github.com/NoNamer777/feudum/issues/86), or bone.
- **Float**: cork or quill. **Sinker**: lead or a stone.
- **Landing net**: a small net on a hoop and pole.

## Nets

### Kinds

- **Cast net**: a round net thrown over shallow water from the bank or a boat. Holding the use key aims it, and it lands as a circle about 3 blocks across, taking the fish under it.
- **Seine**: a long net hauled through shallow water from the shore by two or more workers, sweeping an arc and drawing in what it encloses. A seine takes whole shoals in the shallows.
- **Drift net**: a wall of net set from a boat at sea, which hangs from the surface overnight. Shoal fish swim into it and catch by the gills.

### Mesh

- Every net has a mesh size. Fish lighter than the mesh lets through swim free, so a coarse net spares the young.
- A drift net takes fish near the size of its mesh. Much larger fish bounce off it.

### Making and care

- Nets are knotted from twine with a netting needle and a mesh gauge, a hand step that Fishing owns. The gauge sets the mesh.
- A net has a condition. Snags and heavy fish tear it, and a net stored wet rots. Drying it on poles or a [drying rack](hygiene.md#drying) stops the rot, and mending with twine restores it.

## Traps and weirs

### Traps

- An **eel trap** or **fish basket** is woven from willow withies and set in water. It catches fish that swim into it with the current or toward the bait inside it, up to its capacity.
- A **crab pot** is a baited basket set on the sea floor for crabs and lobsters, often from a boat.
- Fish in a trap stay alive until it is emptied. A fish left more than about a day dies and spoils.

### Weirs

- A **fish weir** is a structure of stakes and wattle in a river, set in a V that steers fish with the current into a trap or a **pound**, an enclosure that holds them alive.
- Fishing recognizes a weir from stakes and wattle fences in water that funnel into a trap or a pound.
- A weir across the whole river blocks migration, as [Migration](#migration) describes, unless it leaves a gap.
- Tidal weirs on the shore wait for [Tides](https://github.com/NoNamer777/feudum/issues/172).

## Spearing

- A **leister** is a spear with several barbed prongs, thrust at a visible fish in shallow water from the bank or while wading. It uses the attack rules of [Weapons](../content/weapons.md).
- Light helps: spearing at night by a torch held over the water draws and shows the fish.

## Gathering

- Shellfish are gathered from their beds by a hand step: mussels pulled from stone, oysters picked up, cockles raked from sand, and whelks picked from the bottom. An oyster dredge towed from a boat reaches deeper beds.
- Crabs and lobsters in shallow water are taken by hand.

## Ice fishing

- A hole cut through ice with an axe or an ice pick, as a hand step, opens the water below to every kind of angling and to set lines.
- The hole refreezes over time, at the rate that [Weather](weather.md#snow-and-ice) sets for ice.
- Fish under ice are cold and sluggish, so they bite slowly.

## Boats

From a boat, an angler fishes as from the bank, and a crew sets longlines, drift nets, and crab pots, and tows the oyster dredge. [Sailing](https://github.com/NoNamer777/feudum/issues/41) owns the boats.

## The catch

- A landed fish is a live item. Out of water it dies within about a minute and becomes a **whole fish** item. Eels, crabs, and lobsters live out of water for about a day if kept damp, and shellfish for a few days.
- A whole fish spoils in about 2 days under [Food preservation](food-preservation.md).
- A **keepnet** on the bank or a **fish box** moored in the water keeps catches alive, as medieval fishmongers kept fish fresh for market.
- A live fish placed in water swims off as a mob. A whole fish dropped in water is a carcass for fouling.

## Gutting

Gutting a whole fish is a hand step with a knife. It stains the worker, as [Hygiene](hygiene.md) describes, and yields by the fish's weight:

| Yield | From                    | Goes to                                                                                                                                                         |
|:------|:------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Flesh | Every fish              | [Foods](https://github.com/NoNamer777/feudum/issues/51)                                                                                                         |
| Offal | Every fish              | Bait, the [dung heap](relief.md#dung-heap), or a fouling source when thrown in water                                                                            |
| Roe   | Fish in spawning season | Foods                                                                                                                                                           |
| Liver | Cod and ling            | Fish oil, rendered in a heated cauldron under [Cooking](cooking.md#rendering), which [Lighting](https://github.com/NoNamer777/feudum/issues/163) burns in lamps |
| Bones | Every fish              | The dung heap                                                                                                                                                   |

- Oysters are opened with a knife, and mussels, cockles, and whelks are boiled. Crabs and lobsters are boiled whole.
- Shells go to the dung heap or to the lime kiln of [Buildings](https://github.com/NoNamer777/feudum/issues/29).

## Fishponds

- A **fishpond** is a still water body that a player or villager dug or dammed. It is a water body of its own, stocked by its keeper instead of by world generation.
- **Stocking**: live fish are carried to the pond in a water-filled container from [Drink containers](https://github.com/NoNamer777/feudum/issues/49), or in a barrel. A fish in a container dies if its water fouls or warms past its range.
- **Feeding**: grain, offal, or kitchen scraps thrown in raise the pond's carrying capacity for a few days. Feed the fish don't eat rots and fouls the water.
- **Draining**: a sluice or a cut channel lets the water out. As the water falls, the fish crowd into the last pools, and once it is gone they are gathered from the mud by hand. The pond then refills from its source.
- **Breeding and fattening**: a keeper breeds young fish in one pond and moves them to another to grow, as separate ponds. Carp breed only in a shallow pond warm enough for them.
- A fishpond meets every rule of this page, so a shallow pond under ice can suffer a winter kill, and an overstocked one fouls.

## Ownership

- Wild fish belong to no one. Who may fish which water, a lord's reserved fishery, poaching, and the sturgeon as a royal fish belong to [Realm laws](https://github.com/NoNamer777/feudum/issues/102) and [Village economy](https://github.com/NoNamer777/feudum/issues/44).
- Fish in a fishpond, a trap, a weir's pound, a keepnet, or a fish box belong to the owner of the pond or gear, and fry hatched in an owned pond belong to its owner.
- Taking them is theft, as [Ownership](animal-husbandry.md#ownership) describes for livestock.

## Cues

- Players read fish from the water, never from a meter or a count.
- Fish rise to insects at dusk, leaving rings on still water.
- Gulls dive over a shoal at sea, and the water darkens and flickers above it.
- Salmon leap at a weir or a fall during their run.
- Bubbles rise over carp and tench feeding in a pond.
- Fish gasp at the surface when oxygen runs low, a warning of a coming kill, and a dead fish floats belly-up after it.
- The float dips or the line twitches at a bite. While playing, the rod bends and the line sings as it nears breaking.
- Inspecting a fish gives an angler's appraisal in words, such as "a heavy, well-fed pike".

## Unloaded chunks

- Each water body records when it last caught up on fish. When a chunk with fish loads, it applies the elapsed spawning, hatching, growth, migration, and deaths to them by the rules of this page.
- Fish in transit are placed as [Migration](#migration) describes.
- Shellfish beds regrow and clutches hatch by the time that passed.
- [Village simulation](https://github.com/NoNamer777/feudum/issues/45) reads the same rules for what an unloaded village's Fisher brings home.

## Vanilla content

- Cod, salmon, pufferfish, tropical fish, and tadpoles never spawn or generate.
- Their items, spawn eggs, and fish buckets stay hidden, along with the vanilla fishing rod.
- The fishing loot tables are empty, and Feudum adds no treasure or junk catches. Every other vanilla source of fish, such as a cat's morning gift, gives nothing.
- The fishing enchantments are already off, with enchanting.
- Wildlife owns squid, glow squid, dolphins, turtles, axolotls, frogs, and guardians, each getting a Feudum version or leaving the game.

## Persistence

- Every fish saves its species, birth date, weight, owner, and, for a migratory species, its home river.
- A shoal saves its count and average weight.
- Each chunk saves its clutches of eggs, and each water body the time it last caught up.
- Fish in transit save their route, position, and the time they entered transit.
- Every shellfish bed saves its density, every net its condition and wetness, and every trap, pound, keepnet, and fish box its contents.

## Query

- One query returns, for any position in water, its oxygen, bottom, cover, and access, the fish of its water body by species with their counts, and its carrying capacity.
- A second returns a fish's species, age, weight, condition, owner, and migration state.
- Other mechanics read fish through these, such as Village simulation and Village economy.

## Commands

- `/feudum fishing query [pos]` shows the result of the first query.
- `/feudum fishing spawn <species> [count] [weight]` spawns fish or a shoal, for testing.
- `/feudum fishing run <species> [start|stop]` starts or stops a migration run, for testing.
- Every `/feudum fishing` command requires operator permission.

## Boundaries

Fishing owns fish and their species, habitat, oxygen, shoals, weight, spawning, carrying capacity, deaths and fish kills, migration and barriers, and fish in transit. It also owns shellfish beds, the fouling of fish, angling, bait, tackle, set lines, nets and netting, traps, weirs, spearing, gathering, ice fishing, the catch and its keeping alive, gutting, fishponds, and the cues of fish. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Fluids](fluids.md)**: water, its salinity, foulness, and current, the drainage network, and how fish move and float.
- **[Body temperature](body-temperature.md)**: thermal profiles and water temperature.
- **[Hunger](hunger.md)**: diet profiles and appetite.
- **[Health](health.md)**: body profiles and pools.
- **[Illness](illness.md)**: the fish plagues and the shared water route.
- **[Weather](weather.md)** and **[Time](time.md)**: ice, the local temperature, cloud, and the seasons.
- **[Food preservation](food-preservation.md)**: how fish, roe, and bait keep, and salt fish, smoked herring, stockfish, and pickled fish.
- **[Cooking](cooking.md)**: cooking fish and shellfish, and rendering liver into oil.
- **[Hygiene](hygiene.md)**: the stains of gutting, and the drying rack.
- **[Relief](relief.md)**: the dung heap that takes offal, bones, and shells.
- **[Farming](farming.md)**: the soil moisture that worms follow.
- **[Animal husbandry](animal-husbandry.md)**: horses, whose tails give horsehair, and the ownership rules.
- **[Textiles](textiles.md)**: twine for lines and nets.
- **[Weapons](../content/weapons.md)**: the attack rules of the leister.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: how fish behave, the predators that hunt them, and the other water mobs.
- **[Sailing](https://github.com/NoNamer777/feudum/issues/41)**: boats.
- **[Tides](https://github.com/NoNamer777/feudum/issues/172)**: tidal flats, and the shellfish beds and tidal weirs on them.
- **[Terrain](https://github.com/NoNamer777/feudum/issues/60)**: the bottom of rivers, lakes, and the sea, from the seed alone.
- **[Aquatic plants](https://github.com/NoNamer777/feudum/issues/68)**: the weed that gives cover.
- **[Foods](https://github.com/NoNamer777/feudum/issues/51)**: the food components of fish, roe, and shellfish.
- **[Parasites](https://github.com/NoNamer777/feudum/issues/157)**: parasites of fish, and those passed to people who eat them raw.
- **[Forestry](https://github.com/NoNamer777/feudum/issues/165)**: rod poles, withies, and stakes.
- **[Smithing](https://github.com/NoNamer777/feudum/issues/86)**: hooks and sinkers.
- **[Lighting](https://github.com/NoNamer777/feudum/issues/163)**: fish oil in lamps, and torches for spearing.
- **[Drink containers](https://github.com/NoNamer777/feudum/issues/49)**: containers for carrying live fish.
- **[Buildings](https://github.com/NoNamer777/feudum/issues/29)**: the lime kiln that burns shells.
- **[Watermill](https://github.com/NoNamer777/feudum/issues/67)**: mill dams, which are barriers to migration.
- **[Encumbrance](https://github.com/NoNamer777/feudum/issues/65)**: the weight of nets and the catch.
- **[Realm laws](https://github.com/NoNamer777/feudum/issues/102)** and **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: fishing rights, reserved fisheries, poaching, royal fish, and selling the catch.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: fishing while a village is unloaded.
- **[Village generation](https://github.com/NoNamer777/feudum/issues/61)**: the weirs and ponds a new village starts with.
- **[Fisher](https://github.com/NoNamer777/feudum/issues/171)**: the villager who fishes.
- **[Skills](https://github.com/NoNamer777/feudum/issues/43)**: whether fishing takes a skill.

World generation must stock every water body with fish, as [ADR 0026](../../adr/0026-fish-are-mobs-with-populations-of-their-own.md) records, and offer the bottom of every water body from the seed alone.
