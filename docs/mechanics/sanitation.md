# Sanitation

Feudum villagers and livestock produce waste, and it has to go somewhere. Chamber pots empty into privies, cesspits fill, barns fill with dung, and the noisome trades foul whatever lies downstream. A village that keeps its waste away from its wells and carts it to the fields gains manure. A village that lets it pile up drinks the flux, feeds the rats, and loses heart.

## Who makes waste

- **Feudum villagers** make waste, as [Human waste](#human-waste) describes.
- **Livestock** makes dung everywhere in the world, as [Livestock waste](#livestock-waste) describes. The [temperature document](temperature.md#livestock) defines which animals count as livestock.
- **Players** make no waste and have no bodily need, but they live with the filth around them: polluted water, smell, and rats.

Vanilla villagers, wild animals, and monsters make no waste.

Waste is physical. It exists as blocks and items in the world, and every effect comes from where they sit, so cleaning up means moving them.

## Human waste

### Privies and chamber pots

- **Chamber pot.** A new potter's block beside the bed, which fills overnight. The household empties it into the privy each morning, and keeps the urine in a urine tub for the [noisome trades](#noisome-trades).
- **Privy.** A new seat block over a cesspit. A privy serves the household whose home it stands by.
- **Communal latrine.** A row of privy seats over a larger pit, which the builder raises near busy workplaces.
- **No privy.** Villagers without a privy go behind the home or at the edge of the village, and leave filth there.

### Cesspits

A cesspit is a pit dug below a privy. A standard pit is 2 by 2 blocks and 2 deep, and fills in about a season for a household of four. A larger pit lasts longer.

- **Filling.** Night soil fills the pit in layers you can see, like snow layers.
- **Overflow.** A full cesspit overflows into the blocks around it as filth, and turns from a moderate into a strong [polluter](#polluters).
- **Infection.** A cesspit that takes the waste of a body with [the flux](disease.md#illnesses) is infected until a few days after the last use, or until it is emptied. Water that an infected cesspit pollutes carries a much higher chance of the flux than other unclean water. This is how the flux spreads through water.

Players make no waste, so a player with the flux does not spread it.

### Privies over water

A privy built over running water, like the garderobes that hung over medieval streams and moats, has no cesspit and never fills. It is a strong polluter, and the river carries its pollution downstream. Medieval towns drew their water upstream for this reason.

### Gong farmer and laystall

- **Gong farmer.** Empties a cesspit at night once it is nearly full. Night soil goes into muck barrels on a handcart, as medieval towns required by law.
- **Laystall.** The gong farmer carts the night soil to a laystall outside the village: a [dung heap](#dung-heap-and-manure) that takes night soil. It rots the night soil into manure over a season. Night soil from an infected cesspit keeps the infection until it has rotted.

The laystall is the strongest polluter a village has, so where it sits decides which water stays clean.

## Livestock waste

Dung builds up in layers on the floor of pens and barns, faster indoors and faster with more animals:

- **Barns.** Dung grows deep enough to harm livestock after about a week without mucking out.
- **Open pens.** It takes about two weeks.
- **Pasture.** Grazing animals on open pasture spread their dung, which never builds up.

Deep dung lowers the resistance of the animals standing in it, and causes **foot rot**, a mild livestock disease of the [disease mechanic](disease.md#livestock).

The herder mucks out the pens and barns, lays fresh **straw** bedding, and carries the dung and the used bedding to the dung heap. Straw is a new item from harvesting wheat, barley, and rye.

## Dung heap and manure

The dung heap is a new block that rots organic waste into **manure**, a new item:

- **Inputs.** Dung, used bedding, rotten food and rotten flesh, kitchen scraps, offal, and street filth. Night soil turns a dung heap into a laystall.
- **Rotting.** Waste rots into manure over a few weeks, and night soil over a season. Warm air speeds this up, and freezing air stops it.
- **Manure.** The soil fertility mechanic describes what manure does for the fields.

A village keeps its dung heap by the barns and fields, away from its wells. The vanilla composter stays as a small household option that turns scraps into bone meal, as [food spoilage](food-spoilage.md#rotten-food) describes.

## Household refuse

Each kind of household refuse goes where medieval households sent it:

- **Kitchen scraps.** A new item. Scraps feed the pigs, or go to the dung heap.
- **Ash.** A new item that fireplaces and braziers leave behind. Ash goes to the fields, or into lye for bleaching, dyeing, and later washing.
- **Bones.** Go to bone meal, as in vanilla.
- **Rubbish.** Broken pots and everything else go to the **midden**, a new heap block behind the home that grows with the household's refuse and needs clearing about once a season.

## Noisome trades

Some trades foul the air and the water as part of their work:

| Trade   | Waste                                                   |
|:--------|:--------------------------------------------------------|
| Tanner  | Lime, bark, and dung pits, and scraps of hide           |
| Butcher | Blood and offal at the shambles, the slaughtering place |
| Fuller  | Urine in the fulling trough                             |
| Dyer    | The woad vat, whose smell dyers were known for          |
| Farmer  | The retting pond, where flax soaks until its stalks rot |

- **Offal.** A new item from butchering. Offal goes to the pigs, the dogs, or the dung heap.
- **Urine.** Households keep urine in a new urine tub block. The tanner, the fuller, and the dyer collect it for their work.
- **Placement.** The builder sites noisome trades at the edge of the village, downstream of wells and homes, as [Siting](#siting) describes.

## Filth

### Polluters

Every waste block is a polluter. Its strength sets the range of everything it does:

| Strength | Range | Polluters                                                                                                            |
|:---------|------:|:---------------------------------------------------------------------------------------------------------------------|
| Weak     |     4 | Midden, urine tub, a pen or barn with shallow dung                                                                   |
| Moderate |     8 | Privy and cesspit, dung heap, deep dung, rotting food, a corpse in water, an unburied body, shambles, fulling trough |
| Strong   |    16 | Laystall, tannery, retting pond, woad vat, an overflowing or infected cesspit, a privy over water                    |

A river carries pollution downstream for four times the range of the polluter. Waste dropped as items, such as dung, night soil, or refuse on the ground near water, pollutes like the block it came from.

### Effects

Within its range, a polluter brings:

- **Unclean water.** Wells, cisterns, and still water turn unclean, as the [thirst document](thirst.md#contamination) describes, and clear a day or two after the polluter is gone.
- **Smell.** Particles and a sound that grow with the strength.
- **Flies.** Swarms over filth in the warm band and above. They are particles and sounds, like the mosquitoes of the [disease mechanic](disease.md#causes), not mobs.
- **Rats.** Filth draws rats to the stores nearby, as the vermin mechanic describes.
- **Miasma.** Villagers believed that bad air caused disease, as medieval people did. Feudum villagers avoid the smell where they can, and their morale drops while filth sits near their home or work.

Filth itself never harms anyone. Its harm comes through unclean water, the flux, rats, and morale, so every consequence has a warning first: a smell, flies, or a villager who walks around it.

Server config scales the pace of waste, the ranges, and the effects, and can turn sanitation off.

### Street filth

Overflowing cesspits, villagers without a privy, and full middens leave filth around the village. The raker clears it by day, and carts it and the refuse of full middens to the laystall.

### Reading filth

Players judge waste by what they can see and hear: cesspit layers, dung depth on the floor, the smell, and flies. There is no meter and no number in a tooltip, as temperature has no thermometer.

## Handling waste

Players handle waste with tools they already have, and one new vessel:

- **Shovel.** Scoops a layer of dung, midden refuse, filth, or night soil as an item.
- **Muck barrel.** A new cooper's barrel that carries night soil and urine without spilling. Night soil can only be scooped into a muck barrel, so it never sits in an ordinary inventory slot.

## Villagers

Feudum villagers manage waste like a medieval village did:

- **Households.** Empty their chamber pots each morning, keep their urine in a tub, feed their scraps to the pigs, carry their ash and rotten food out, and keep their midden behind the home.
- **Herder.** Mucks out the pens and barns, and lays fresh straw.
- **Gong farmer.** Empties the cesspits at night.
- **Raker.** Clears the streets and the full middens by day.
- **Builder.** Raises privies, latrines, dung heaps, and the laystall, and sites them by the rules below.

### Siting

The builder places the village's polluters by these rules, which are configurable:

| Polluter            | Rule                                                          |
|:--------------------|:--------------------------------------------------------------|
| Privy and cesspit   | Outside the pollution range of every well                     |
| Midden              | Behind the home, outside the pollution range of every well    |
| Dung heap           | Next to the barns and fields, outside the range of every well |
| Laystall            | At least 32 blocks from the nearest home, downstream of wells |
| Tannery and retting | At the edge of the village, downstream of wells and homes     |

Downwind joins the rules once the wind mechanic exists. Players can build anywhere, and live with the consequences.

## Seasons and climate

Waste follows the air band, by the same rule as [food spoilage](food-spoilage.md#rate):

- **Heat.** Warm air speeds up rotting, smell, flies, and the ripening of manure, so summer and hot climates need the most care.
- **Winter.** Cesspits and dung heaps freeze in the freezing band. Frozen waste neither smells nor rots, but cesspits still fill.
- **Spring thaw.** Thawing waste releases a burst of smell, and meltwater runoff widens the range of every polluter for a few days.

The Nether and the End have no special rules.

## Related mechanics

Sanitation works together with these mechanics:

- **[Thirst](thirst.md).** Polluters turn nearby water unclean, and rivers carry pollution downstream.
- **[Disease](disease.md).** Infected cesspits spread the flux, and deep dung causes foot rot in livestock.
- **[Food spoilage](food-spoilage.md).** Rotten food goes to the dung heap, and the air band sets the pace of rotting.
- **[Temperature](temperature.md).** Heat speeds up rotting and smell, and freezing stops them.
- **[Seasons](seasons.md).** Winter freezes waste, and the spring thaw releases it.
- **Soil fertility.** Manure, ash, and night soil feed the fields.
- **Hygiene.** Washing and laundry need the lye that household ash gives.
- **Vermin.** Filth draws rats.
- **Morale.** Villagers lose morale while filth sits near their home or work.
- **Wind.** The builder will site polluters downwind.

## Additions and changes

- **Waste.** Feudum villagers and livestock make waste as blocks and items.
- **Privies.** A new chamber pot block, a new privy seat block, and communal latrines, over cesspits that fill in layers and overflow as filth.
- **Infected cesspits.** Cesspits that take the waste of the flux spread it through the water they pollute.
- **Privies over water.** Privies over running water that never fill and pollute downstream.
- **Laystall.** A dung heap that takes night soil and rots it into manure over a season.
- **Livestock dung.** Dung layers that build up in pens and barns, and straw bedding that the herder lays.
- **Foot rot.** A new mild livestock disease of the disease mechanic, caught from deep dung.
- **Dung heap.** A new block that rots dung, bedding, rotten food, scraps, offal, and filth into manure.
- **Items.** New night soil, dung, manure, straw, kitchen scraps, ash, and offal.
- **Midden.** A new heap block behind each home for household rubbish.
- **Noisome trades.** Tanneries, the shambles, fulling troughs, woad vats, and retting ponds, which pollute strongly.
- **Urine tub.** A new block where households keep urine for the tanner, the fuller, and the dyer.
- **Polluters.** Every waste block pollutes within a range set by its strength, carried downstream along rivers.
- **Filth effects.** Smell and fly particles and sounds, rats drawn to filth, and villager miasma.
- **Muck barrel.** A new cooper's barrel that carries night soil and urine. The vanilla shovel scoops waste.
- **Villager behavior.** Feudum villagers empty their chamber pots, keep urine, feed scraps to pigs, avoid the smell, and site polluters away from wells and homes.
- **Configuration.** Server settings for the pace of waste, the polluter ranges, the effects, the siting rules, and turning sanitation off.
