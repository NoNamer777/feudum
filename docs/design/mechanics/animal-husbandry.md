# Animal husbandry

A village lives off its livestock: oxen pull the plough, sheep give wool, cows give milk, hens give eggs, and every beast ends as meat, hide, tallow, and horn. Livestock breeds on its own, in its season, whenever a fertile pair shares a field and has eaten well. The keeper steers a herd by choosing who runs together, gelding the rest, and culling before winter. Lambs come in spring and calves take most of a year, so a herd grows at about its historical pace. Each young animal inherits its parents' traits, so careful breeding builds a line of heavy fleeces or calm oxen over generations. Vanilla animals breed in a minute from a handful of wheat and are all alike, so Feudum replaces them.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Animal husbandry owns the livestock of the [Species](#species) table: where it comes from, breeding, pregnancy and birth, nursing and lactation, growth and old age, traits and breeds, fleece, eggs, slaughter and butchering, ownership, and herding.
- [Dairy](https://github.com/NoNamer777/feudum/issues/135) owns milking and what milk becomes, [Foods](https://github.com/NoNamer777/feudum/issues/51) the meat cuts, and [Tanning](tanning.md) the hides.
- [Tack and barding](https://github.com/NoNamer777/feudum/issues/139) owns the gear of mounts and draft animals, [Working dogs](https://github.com/NoNamer777/feudum/issues/142) the work a dog does, and [Wildlife](https://github.com/NoNamer777/feudum/issues/47) wild animals, including the wild forms of livestock.
- [Beekeeping](https://github.com/NoNamer777/feudum/issues/128) owns bees, [Falconry](https://github.com/NoNamer777/feudum/issues/140) hawks and falcons, Wildlife the deer of a deer park, and [Fishing](fishing.md) the fish of a fishpond.

## Working

- A hand step, such as castrating, marking, or butchering, is done by holding the use key, as in [Brewing](brewing.md#working). Work advances by the Feudum time that passed, and stopping keeps what is done.
- Only the owner of an animal, or a villager who works for its owner, may castrate, mark, shear, milk, slaughter, or sell it, as [Ownership](#ownership) describes.
- Villagers do the same work at the same rate as a player. The [Shepherd](https://github.com/NoNamer777/feudum/issues/143), [Oxherd](https://github.com/NoNamer777/feudum/issues/144), [Swineherd](https://github.com/NoNamer777/feudum/issues/145), [Henwife](https://github.com/NoNamer777/feudum/issues/146), [Groom](https://github.com/NoNamer777/feudum/issues/147), [Warrener](https://github.com/NoNamer777/feudum/issues/148), and [Butcher](https://github.com/NoNamer777/feudum/issues/149) plan the villagers who keep a village's animals.

## Species

Every span on this page that comes from biology is the real span, scaled to the calendar as a share of the year. A year has 96 days, so a real month is about 8 days, and a real year is one Feudum year. Starting values to tune:

| Species       | Breeding season  | Gestation or incubation | Litter or clutch | Adult at  | Lifespan | Draws |
|:--------------|:-----------------|:------------------------|:-----------------|:----------|:---------|:------|
| Cattle        | All year         | About 75 days           | 1                | 2 years   | 20 years | Yes   |
| Water buffalo | All year         | About 80 days           | 1                | 3 years   | 25 years | Yes   |
| Sheep         | Shortening days  | About 39 days           | 1–2              | 1 year    | 12 years | No    |
| Goats         | Shortening days  | About 39 days           | 1–3              | 1 year    | 15 years | No    |
| Pigs          | All year         | About 30 days           | 6–12             | 2 seasons | 15 years | No    |
| Horses        | Lengthening days | About 89 days           | 1                | 3 years   | 25 years | Yes   |
| Donkeys       | Lengthening days | About 96 days           | 1                | 3 years   | 30 years | Yes   |
| Mules         | Sterile          | None                    | None             | 3 years   | 35 years | Yes   |
| Dogs          | All year         | About 17 days           | 4–8              | 1 year    | 12 years | No    |
| Cats          | All year         | About 17 days           | 3–5              | 2 seasons | 15 years | No    |
| Coneys        | All year         | About 8 days            | 4–8              | 1 season  | 9 years  | No    |
| Ferrets       | Lengthening days | About 11 days           | 4–8              | 2 seasons | 8 years  | No    |
| Chickens      | Laying season    | About 6 days            | 8–15             | 1 season  | 8 years  | No    |
| Ducks         | Laying season    | About 7 days            | 8–12             | 1 season  | 10 years | No    |
| Geese         | Laying season    | About 8 days            | 4–8              | 1 year    | 20 years | No    |
| Swans         | Laying season    | About 10 days           | 4–7              | 3 years   | 20 years | No    |
| Peafowl       | Laying season    | About 7 days            | 3–6              | 2 years   | 20 years | No    |
| Pigeons       | Laying season    | About 5 days            | 2                | 2 seasons | 15 years | No    |

- Cattle include oxen, the castrated males that do most of the draft work.
- The mule is the cross of a donkey sire and a horse dam. It is always sterile.
- Silkworms wait until Textiles takes up silk.

## Sources

- Generated villages start with livestock of the breeds of their region, as [Village generation](https://github.com/NoNamer777/feudum/issues/61) places them.
- Players buy and trade livestock through [Village economy](https://github.com/NoNamer777/feudum/issues/44).
- Some species also live wild in the wilderness, such as wild boar, wild horses, and mouflon. Wildlife owns them while they are wild. Once captured, a wild animal becomes owned livestock with a wild temperament, and its line tames over generations, as [Domestication](#domestication) describes.

## Sexes and castration

- Every animal is male or female, and the sexes look different: horns, wattles, a mane, a comb, or size.
- The owner castrates a male with a knife, at any age. It leaves light bleeding under [Health](health.md#injuries), and it is permanent.
- A castrated male, such as an ox, wether, gelding, or capon, can't breed. It grows larger, carries more meat, and is calmer than its temperament alone would make it.

## Breeding

- Breeding needs no player action: an animal conceives whenever every condition holds. [ADR 0019](../../adr/0019-livestock-breeds-on-its-own.md) records why.
- The conditions are:
  - A fertile female in season, and a fertile male of her species within reach.
  - Both are adult, not old past breeding, and not castrated.
  - Both are Fed with no deficiency, as [Hunger](hunger.md#animals) requires.
  - Neither is crowded, and the chunk is under the cap, as [Crowding](#crowding) describes.
- A female in season calls, and the males that can reach her follow her.
- A donkey sire and a horse dam conceive a mule. Every other cross between species fails.
- The keeper steers breeding by managing who is together: keeping males apart, castrating them, or penning a chosen sire with chosen dams.

### Breeding season

- Daylight, the season curve of [Time](time.md#seasons-and-climate), sets when each species comes in season, so the rule holds in every climate profile.
- Sheep and goats come in season as the days shorten, from Mid Autumn into Mid Winter, and give birth from Late Winter into Mid Spring.
- Horses, donkeys, and ferrets come in season as the days lengthen, from Mid Spring into Mid Summer.
- Cattle, water buffalo, pigs, dogs, cats, and coneys can come in season at any time of year.
- Poultry lay in the laying season, while daylight stays above about 45%: from Early Spring into Late Autumn. They stop in winter.
- The sub-seasons above are starting values. The livestock profile holds the daylight thresholds that produce them.

The chart plots the year of sheep, cattle, and poultry against daylight across the 12 sub-seasons. The shearing and slaughter bars are illustrative: they show the historical practice of shearing in early summer and culling in late autumn, before the winter fodder runs short, which the keeper is free to change.

![A year of 12 sub-seasons, from Early Spring to Late Winter. A daylight curve peaks at about 60% in Mid Summer and falls to about 40% in Mid Winter, crossing 50% in Mid Spring and Mid Autumn. Sheep come in season from Mid Autumn into Mid Winter and lamb from Late Winter into Mid Spring. Cattle can come in season and calve all year. Poultry lay and hatch from Early Spring into Late Autumn. Dashed bars mark the illustrative practice of shearing sheep in Early Summer and slaughtering sheep and cattle in Late Autumn.](images/animal-husbandry-year.svg)

## Pregnancy and birth

- Gestation lasts the span in the [Species](#species) table. The litter size is drawn from its range, toward the top for a dam with a balanced diet under Hunger.
- A pregnant dam's energy drain rises over her pregnancy, to about 1.5 times her base rate by the birth, and stays there while she nurses. Starting values to tune.
- She can lose the young when she reaches Famished or worse, takes a heavy hit to a vital pool under [Health](health.md#pools), or reaches Hypothermic under [Body temperature](body-temperature.md#stages).
- Birth needs no player action, and there is no difficult birth.
- Newborns carry the young modifiers of [Hunger](hunger.md#diet-profiles) and [Body temperature](body-temperature.md#thermal-profiles), so lambs born in the open in a cold snap die, and a lambing shed matters.
- A young animal takes its mother's owner.

## Nursing and lactation

- Lactation starts when a dam gives birth. It lasts the lactation length in her profile, and regular milking keeps it going past that. A cow that never calves gives no milk.
- Until it is weaned, a young mammal feeds by suckling from its dam, which fills its stomach as a meal does. It is weaned at the weaning age in its profile, and from then on eats by its diet profile.
- Dairy owns milking and what milk yields. Milking a dam shares her milk with her young.

## Growth and old age

- A young animal grows to adult size by the age in the [Species](#species) table, and can breed from then on. Growth stops while it is Hungry or worse, as Hunger describes, and slows while it is crowded.
- Lifespans are the real ones, so a cow lives about 20 Feudum years, and old age rarely comes in play.
- Old age begins at the age in the profile, at about three quarters of the lifespan as a starting value. An old animal breeds less often and yields less milk, wool, and eggs.
- An animal dies of old age at the end of its lifespan, with its own death message.

## Traits and breeds

- Every animal carries five heritable traits, each a value within its species' range:
  - **Size**: body size, meat, and draft strength.
  - **Yield**: milk for Dairy, wool, eggs, and fat.
  - **Hardiness**: natural insulation and the width of the comfort band under Body temperature.
  - **Temperament**: how far it flees, whether it fights back, and how readily it is led.
  - **Color**: its coat, fleece, or plumage, which sets the natural fleece color of [Textiles](textiles.md#wool).
- A young animal takes the midpoint of its parents' values for each trait, plus a random variation of up to about 10% of the species range, as a starting value. Selective breeding moves a line over generations. [ADR 0020](../../adr/0020-livestock-inherits-its-traits.md) records why.
- A breed is a data-driven set of trait ranges with a look and a home region, such as a white-faced wool sheep or a dark moorland sheep. An animal belongs to the breed whose ranges hold its traits, and a crossbred animal that fits none has no breed.

### Domestication

- A wild form starts with its temperament at the wild end of its species range: it flees far and fights back.
- Its young inherit temperament like any other trait, so keeping the calmest of each generation tames a line over generations.
- A line whose temperament enters the domestic range counts as livestock of its species, with no other change.

## Fleece

- A sheep's fleece grows steadily from shorn to full over about one Feudum year. A goat's hair grows the same way.
- Shearing takes whatever has grown, so an early shearing gives a smaller fleece. [Cloth quality](https://github.com/NoNamer777/feudum/issues/105) decides whether a short staple makes poorer cloth.
- A deficiency slows the growth, as Hunger describes.
- Fleece length sets the fleece share of the animal's natural insulation, so a shorn sheep is cold until its wool grows back, as Textiles describes.
- No breed sheds its fleece on its own.
- [Textiles](textiles.md#wool) owns the shears, shearing, and the fleece.

## Eggs

- A Fed hen in the laying season lays at the rate her yield sets, into a nest box when one is in reach, or on the ground when none is.
- An egg is fertile only when a male of her species runs with the flock.
- Collected eggs are food, which [Foods](https://github.com/NoNamer777/feudum/issues/51) owns and which keeps about 2 weeks under [Food preservation](food-preservation.md#starting-keeping-times).
- A hen left with a clutch in her nest can go broody. A broody hen stops laying and sits on the clutch, and the fertile eggs hatch after the incubation span. Eggs that don't hatch spoil.
- Geese, ducks, swans, peafowl, and pigeons follow the same rules, with their own seasons and clutch sizes.

## Slaughter and butchering

- An animal killed by any means leaves a carcass, which rots in about 4 days under [Food preservation](food-preservation.md#carcasses).
- Butchering a carcass is a hand step with a knife at a butcher's block. It yields:

| Yield           | From                                | Goes to                                                              |
|:----------------|:------------------------------------|:---------------------------------------------------------------------|
| Meat cuts       | Every species                       | [Foods](https://github.com/NoNamer777/feudum/issues/51)              |
| Hide            | Mammals                             | [Tanning](tanning.md)                                                |
| Fat             | Every species                       | Tallow, rendered in a heated cauldron                                |
| Bones           | Every species                       | The designs that use bone, or the [dung heap](relief.md#dung-heap)   |
| Blood and offal | Every species                       | Foods                                                                |
| Horn            | Cattle, water buffalo, sheep, goats | Bows, as [Weapons](../content/weapons.md#ranged-weapons) describes   |
| Sinew           | Mammals                             | Bows                                                                 |
| Feathers        | Poultry                             | Arrows, as [Weapons](../content/weapons.md#making-weapons) describes |

- Size sets the amount of each yield, and condition sets the fat and meat: an animal slaughtered lean, with low energy under Hunger, gives less of both.
- Fat renders to tallow in a heated cauldron, under [Cooking](cooking.md#rendering). Tallow oils armor, as [Armor](../content/armor.md#rust-and-oiling) describes.
- The raw yields spoil under Food preservation, while bone, horn, and feathers keep forever, as [its scope](food-preservation.md#scope) describes.

## Ownership

- Every domestic animal has an owner: a player, a manor, or a village holding.
- A newborn takes its mother's owner, a bought animal its buyer, and a captured wild animal its captor.
- Inspecting an animal shows its owner.
- Ownership changes by sale through Village economy, or by handing the lead rope of a haltered animal to another player as a gift.
- Killing or taking an animal of another owner is theft. It lowers the thief's [standing](villages.md#standing-and-wishes) with the owner's village.

### Marks

- The owner can mark an animal: an earmark cut with a knife, a brand burned with a branding iron, or a nick in a swan's bill. The mark shows on the model.
- A mark changes nothing but the look. It lets players tell whose animal is whose at a glance.

### Strays

- An animal that wanders out of its owner's territory, or into crops, is a stray.
- The [Hayward](https://github.com/NoNamer777/feudum/issues/57) impounds strays in the village pinfold. The owner pays a fine to redeem them, which Village economy prices.

### Manor holdings

- A dovecote, a warren, and swans can belong only to a manor, held by its lord.
- [Realm laws](https://github.com/NoNamer777/feudum/issues/102) decides whether a realm can forbid them to anyone else.

## Leading and herding

- A halter and a lead rope lead one animal, and the rope ties it to a fence post. The lead rope is [cordage](textiles.md#cordage).
- A flock follows a herder carrying a crook, or one working with a dog, as [Working dogs](https://github.com/NoNamer777/feudum/issues/142) describes.
- Temperament sets how far an animal flees from a stranger and whether it fights back. An entire bull, boar, ram, or gander can charge.

## Draft work

- Cattle, water buffalo, horses, donkeys, and mules can draw. Oxen are the main draft animal.
- Size sets how much an animal can draw.
- Draft work counts as heavy exertion: it raises the drain of [Hunger](hunger.md#drain) and the exertion offset of [Body temperature](body-temperature.md#felt-temperature).
- [Tack and barding](https://github.com/NoNamer777/feudum/issues/139) owns the harness, [Farming](farming.md#breaking-ground) the ard, the heavy plough, and the harrow, and [Carts and wagons](https://github.com/NoNamer777/feudum/issues/141) carts, wagons, and sledges.

## Housing

[Buildings](https://github.com/NoNamer777/feudum/issues/29) recognizes these structures:

| Structure    | Keeps                   | What it does                           |
|:-------------|:------------------------|:---------------------------------------|
| Byre or barn | Cattle, horses, donkeys | Shelter, with a stall for each animal. |
| Sty          | Pigs                    | Shelter.                               |
| Lambing shed | Sheep and goats         | Shelter for newborns.                  |
| Coop         | Poultry                 | Shelter, and nest boxes to lay in.     |
| Dovecote     | Pigeons                 | Nest holes to roost and breed in.      |
| Warren       | Coneys                  | Pillow mounds to live and breed in.    |

- Shelter works through [Body temperature](body-temperature.md#shelter-and-heat), and stabled animals pile their dung on the floor under [Relief](relief.md#animals).
- Pigeons roost in their dovecote and forage the fields freely, and squabs are taken from the nest holes.
- Coneys live half-free in their warren, and are netted as ferrets drive them out of their burrows.

## Crowding

- Each species needs a minimum area per animal, counted over the enclosure it stands in, or over a radius around it in open pasture.
- A crowded animal doesn't conceive, and grows and yields more slowly.
- A per-world setting caps livestock per chunk, with a high default of about 32 as a starting value. A breeding animal in a chunk at the cap stays barren.

## Livestock profiles

- Each species has a data-driven livestock profile: JSON in a data pack, assigned through entity type tags, as diet profiles are.
- A profile holds:
  - The breeding season, as daylight thresholds, or the laying season for poultry.
  - The gestation or incubation span, and the litter or clutch range.
  - The adult age, the old age, and the lifespan.
  - The lactation length and the weaning age.
  - The fleece growth, for sheep and goats.
  - The crowding area.
  - Whether it can draw.
  - The trait ranges, the wild range of temperament, and the breeds.
  - The slaughter yields.

## Cues

- Players read an animal from its looks, never from a meter or a number.
- Traits show in the model: size, color, horns, and fleece length.
- Inspecting an animal gives a herder's appraisal in words, such as "a large, heavy-fleeced ewe".
- Late pregnancy shows in the body.
- A female in season calls, and the males follow her.
- Age shows in size, and an old animal grays at the muzzle.

## Vanilla content

- Cows, mooshrooms, sheep, pigs, chickens, horses, donkeys, mules, llamas, rabbits, cats, wolves as dogs, goats, camels, and parrots never spawn or generate.
- Their spawn eggs and the vanilla lead stay hidden.
- Vanilla breeding and taming are off, and a thrown egg hatches nothing.
- The vanilla saddle and horse and wolf armor belong to [Tack and barding](https://github.com/NoNamer777/feudum/issues/139).
- [Wildlife](https://github.com/NoNamer777/feudum/issues/47) owns the wild vanilla animals, such as foxes, bears, and wolves as predators.

## Persistence

- Every animal saves its sex, whether it is castrated, its traits, its birth date, its owner, and its marks.
- A pregnant animal saves the date it conceived and the sire's traits. A dam saves the date her lactation started and when she was last milked, a sheep or goat its fleece growth, and a broody hen her clutch.
- Every nest box saves its eggs, with whether each is fertile and when it was laid.
- An owned animal outside any village territory keeps its saved state while its chunk is unloaded, as under Hunger.
- Village simulation brings the livestock of an unloaded village forward, as [Boundaries](#boundaries) describes.

## Query

- One query returns an animal's sex, whether it is castrated, its age and life stage, its traits and breed, its owner, whether it is in season, pregnant, lactating, or crowded, and its fleece growth.
- Other mechanics read livestock through this query.

## Commands

- `/feudum husbandry query [entity]` shows the result of the query.
- `/feudum husbandry set <entity> <trait|age|fleece|owner> <value>` sets a value, for testing.
- `/feudum husbandry breed <dam> <sire>` forces a conception, for testing.
- Every `/feudum husbandry` command requires operator permission.

## Boundaries

Animal husbandry owns the livestock roster, where livestock comes from, sexes and castration, breeding and its seasons, pregnancy, birth, nursing, lactation, growth, and old age. It also owns traits, breeds, and domestication, fleece growth, eggs and hatching, slaughter, butchering, and tallow, ownership, marks, and strays, leading, herding, and draft fitness, crowding, and livestock profiles. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Hunger](hunger.md)**: diet profiles, the feeding goal of animals, the young modifier, and the rule that only a Fed animal with no deficiency breeds.
- **[Thirst](thirst.md)**: the drinking goal of animals.
- **[Body temperature](body-temperature.md)**: thermal profiles, natural insulation, the young modifier, and shelter.
- **[Health](health.md)**: injuries, including the bleeding of castration, and the vital pools a hit can strike.
- **[Illness](illness.md)**: murrain and the other diseases of livestock, and the produce a sick animal stops giving.
- **[Relief](relief.md)**: dung on the pasture and the barn floor.
- **[Textiles](textiles.md)**: the shears, shearing, the fleece, and the cordage of the lead rope.
- **[Food preservation](food-preservation.md)**: how carcasses, eggs, and the yields of butchering spoil.
- **[Time](time.md)**: daylight and the calendar.
- **[Villages](villages.md)**: standing, manors, and the village holding.
- **[Dairy](https://github.com/NoNamer777/feudum/issues/135)**: milking and what milk becomes.
- **[Foods](https://github.com/NoNamer777/feudum/issues/51)**: meat cuts, blood and offal, and eggs as food.
- **[Tanning](tanning.md)**: hides.
- **[Cooking](cooking.md)**: the heated cauldron that renders tallow.
- **[Tack and barding](https://github.com/NoNamer777/feudum/issues/139)**: saddles, bridles, harness, and barding.
- **[Carts and wagons](https://github.com/NoNamer777/feudum/issues/141)**: what draft animals pull.
- **[Mounted combat](https://github.com/NoNamer777/feudum/issues/117)**: fighting from the saddle.
- **[Working dogs](https://github.com/NoNamer777/feudum/issues/142)**: herding, guarding, and hunting with dogs.
- **[Vermin](https://github.com/NoNamer777/feudum/issues/136)**: the cats that hunt rats and mice.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: wild animals, the wild forms of livestock, and deer parks.
- **[Falconry](https://github.com/NoNamer777/feudum/issues/140)**: hawks and falcons.
- **[Fishing](fishing.md)**: fishponds.
- **[Beekeeping](https://github.com/NoNamer777/feudum/issues/128)**: bees.
- **[Farming](farming.md)**: the ard, the heavy plough, and the harrow, crops that strays trample, and the sward of the pasture.
- **[Feed trough and hay](https://github.com/NoNamer777/feudum/issues/50)**: troughs and fodder.
- **[Buildings](https://github.com/NoNamer777/feudum/issues/29)**: recognizing byres, sties, coops, dovecotes, and warrens.
- **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: buying and selling livestock, and the pinfold fine.
- **[Village generation](https://github.com/NoNamer777/feudum/issues/61)**: the livestock a new village starts with.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: conceptions, births, growth, old age, lactation, fleece, eggs, and crowding while a village is unloaded, by the rules of this page.
- **[Realm laws](https://github.com/NoNamer777/feudum/issues/102)**: whether a realm reserves dovecotes, warrens, and swans.
- **[Cloth quality](https://github.com/NoNamer777/feudum/issues/105)**: whether a short fleece makes poorer cloth.
- **[Hayward](https://github.com/NoNamer777/feudum/issues/57)**: impounding strays.
- **[Shepherd](https://github.com/NoNamer777/feudum/issues/143)**, **[Oxherd](https://github.com/NoNamer777/feudum/issues/144)**, **[Swineherd](https://github.com/NoNamer777/feudum/issues/145)**, **[Henwife](https://github.com/NoNamer777/feudum/issues/146)**, **[Groom](https://github.com/NoNamer777/feudum/issues/147)**, **[Warrener](https://github.com/NoNamer777/feudum/issues/148)**, and **[Butcher](https://github.com/NoNamer777/feudum/issues/149)**: the villagers who keep a village's animals.
