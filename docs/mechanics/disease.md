# Disease

Players, Feudum villagers, and livestock fall ill. The cold, the heat, unclean water, spoiled food, damp rye, and vermin each bring an illness, and some illnesses spread from body to body. Rest, warmth, and food heal most of them, and the village's healers make remedies for the rest. A village that neglects its sick, its water, or its dead can lose many of its villagers to a single epidemic.

## Who feels it

- **Players** fall ill everywhere in the world, vanilla villages included. Players in Creative or Spectator mode, and players on Peaceful, do not fall ill.
- **Feudum villagers** fall ill, as [Villagers](#villagers) describes.
- **Livestock** falls ill with diseases of its own, as [Livestock](#livestock) describes. The [temperature document](temperature.md#livestock) defines which animals count as livestock.

Vanilla villagers, wild animals, and monsters never fall ill and never carry disease. Fleas and mosquitoes are the only carriers, as [Causes](#causes) describes.

## Course of an illness

Each illness is a condition a body carries, and it moves through up to five stages:

| Stage         | What happens                                                              |
|:--------------|:--------------------------------------------------------------------------|
| Incubation    | No symptoms, though some illnesses already spread                         |
| Onset         | A light symptom, with a sound and a screen cue, warns before any harm     |
| Illness       | The full symptoms                                                         |
| Crisis        | Serious illnesses only: the body recovers or dies, and care tips the odds |
| Convalescence | Lingering weakness while the body regains its strength                    |

Each illness sets the length of its stages in in-game days. A body can carry several different illnesses at once, but never two of the same kind. Death clears a player's illnesses, as respawning resets thirst.

### Severity

- **Mild** illnesses never kill.
- **Serious** illnesses can kill at their crisis. For players, illness damage follows the vanilla starvation limits, as dehydration does: it stops at 5 hearts on Easy and at half a heart on Normal, and can kill on Hard. Villagers and livestock can die of a serious illness on any difficulty, and [care](#care) lowers the risk.

Server config scales the strength of the symptoms and the pace of the stages, and can turn disease off for players and contagion off for everyone.

### Symptoms

Symptoms show as status effects. They reuse vanilla nausea, weakness, slowness, and hunger where these fit, and add four new effects:

| Effect         | What it does                                                                           |
|:---------------|:---------------------------------------------------------------------------------------|
| Fever          | Raises body temperature one band, drains thirst faster, and stops natural regeneration |
| Cough          | A cough and particles that nearby bodies notice, and short breaks in sprinting         |
| Hallucinations | Phantom sounds and a warped screen                                                     |
| Rash           | Marks on the skin, mostly cosmetic                                                     |

## Illnesses

| Illness            | Cause                                           | Tier    | Spreads between people |
|:-------------------|:------------------------------------------------|:--------|:-----------------------|
| Chill              | Long spells in the freezing band                | Mild    | No                     |
| Lung fever         | A chill kept cold or left untended (pneumonia)  | Serious | No                     |
| Heatstroke         | Long spells in the scorching band               | Mild    | No                     |
| Rheum              | Contagion, worst in winter (the common cold)    | Mild    | Yes                    |
| Food poisoning     | Spoiled food                                    | Mild    | No                     |
| The flux           | Unclean water (dysentery)                       | Serious | Through water only     |
| Marsh ague         | Mosquitoes in swamps on warm evenings (malaria) | Serious | No                     |
| St. Anthony's fire | Rye that carries ergot (ergotism)               | Serious | No                     |
| The pox            | Contagion (smallpox)                            | Serious | Yes                    |
| Plague             | Flea bites; can turn pneumonic                  | Serious | Pneumonic form only    |

Each illness shows these symptoms. The days run from onset to the end of the illness stage, and are configurable:

| Illness            | Symptoms                                                            | Days |
|:-------------------|:--------------------------------------------------------------------|-----:|
| Chill              | Fever, slowness, hunger drains faster                               |    2 |
| Lung fever         | Fever, cough, weakness, slowness                                    |    5 |
| Heatstroke         | Nausea, weakness, slowness                                          |    1 |
| Rheum              | Cough, hunger drains slightly faster                                |    3 |
| Food poisoning     | Nausea, hunger drains faster                                        |    1 |
| The flux           | Nausea, thirst drains faster, weakness                              |    4 |
| Marsh ague         | Fever and shivering on alternate days, weakness between             |    6 |
| St. Anthony's fire | Burning limbs that flash damage, hallucinations, slowness           |    5 |
| The pox            | Fever, then a rash, weakness                                        |    6 |
| Plague             | Fever, swellings, weakness, slowness; a cough in the pneumonic form |    4 |

- **Chill and lung fever.** A chill heals once the body is warm and fed. Kept cold or left untended, it turns into lung fever.
- **The flux.** It spreads only through water: the waste of a sick body fouls the latrines and the water nearby, as the sanitation mechanic describes.
- **Marsh ague.** It can relapse after the body recovers, and bring its fever back.
- **Plague.** It starts from a flea bite and does not spread between people. It can turn pneumonic, which adds a cough, spreads like a strong pox, and reaches its crisis in half the time.

A datapack can add illnesses or change any of them.

## Catching an illness

### Causes

- **Cold and heat.** Long spells in the freezing band cause a chill, and long spells in the scorching band cause heatstroke, as the [temperature document](temperature.md#effects) describes.
- **Water.** Unclean water risks the flux, as the [thirst document](thirst.md#purity) describes.
- **Food.** Spoiled food risks food poisoning, as the [food spoilage document](food-spoilage.md#stages) describes. Rye that carries ergot causes St. Anthony's fire, as [Medicinal plants and rye](#medicinal-plants-and-rye) describes.
- **Fleas.** Fleas from rats bring plague. The vermin mechanic describes the rats and their fleas.
- **Mosquitoes.** New ambient mosquitoes swarm in swamps and mangrove swamps on warm evenings, and their bites carry marsh ague. They are particles and sounds, not mobs.
- **Contagion.** Rheum, the pox, and pneumonic plague spread between bodies.

### Contagion

Exposure to a contagious body builds up over time, rather than rolling once on contact. A body gathers exposure in three ways:

- **Sharing a room** with a sick body, under the room rules of the [temperature document](temperature.md#shelter-and-rooms).
- **Standing close** to a sick body outdoors.
- **Sleeping** in the same bed or home.

Longer exposure and a smaller room raise the chance of catching the illness, and each illness sets how strongly it spreads. Players and villagers spread illness to each other, and players to other players. People and livestock never infect each other: livestock diseases spread among livestock only.

### Resistance

A body catches illness more easily and recovers more slowly when it is weakened:

- Low hunger or low thirst.
- A body in the cold or freezing band.
- Convalescence from an earlier illness.
- Another illness at the same time.

This is what the thirst document means by a dehydrated villager or animal falling ill: it catches whatever illness is about far more easily. Age will lower resistance once the aging mechanic exists.

### Immunity

- **For life.** Surviving the pox or plague makes a body immune to it.
- **For a while.** After rheum, the flux, or marsh ague, a body is immune for a configurable time. Marsh ague can still relapse.

The other illnesses give no immunity.

## Recognizing an illness

Players see the symptoms, not the illness. The effect list shows fever, cough, or rash, and the illness name joins it once the symptoms leave no doubt, such as a fever with a rash for the pox, or swellings for plague.

- **Herbal.** A new book, crafted from a book and dried herbs, or bought from the herbalist. Using it on a player, villager, or animal names their illnesses. It also lists the illnesses its holder has survived, and every remedy the holder has made, bought, or taken.
- **Healers.** A player can ask a herbalist or an apothecary villager to examine them, which names their illnesses.

Illness shows in the world too:

- **Players** hear their own coughs and sneezes. In multiplayer they see each other's cough particles.
- **Sick villagers** look pale, cough, and lie in bed, with pox marks during the rash.
- **Sick livestock** droops and moves slowly.

There is no display of immunity beyond the herbal.

## Care and treatment

### Care

- **Rest.** Lying in a bed. A player can lie in a bed by day to rest, and every resting hour counts.
- **Warmth.** A body temperature in the cool to warm bands.
- **Food and drink.** Hunger and thirst kept high. Broth and pottage count double while ill.

Care speeds up every stage and improves the crisis odds. Without care, a mild illness still heals, more slowly, and a serious illness runs its full course with the worst crisis odds.

### Remedies

Each remedy eases a symptom or shortens an illness. Nothing cures the pox or plague; care and plague water improve the odds.

| Remedy           | Maker         | Form     | Effect                                                     |
|:-----------------|:--------------|:---------|:-----------------------------------------------------------|
| Willow bark tea  | Herbalist     | Tea      | Eases fever                                                |
| Horehound syrup  | Herbalist     | Syrup    | Eases cough, shortens rheum                                |
| Mint tea         | Herbalist     | Tea      | Eases nausea                                               |
| Chamomile tea    | Herbalist     | Tea      | Deepens rest, so care counts more                          |
| Posset           | Any household | Drink    | Hot milk curdled with ale: eases rheum and chill, warms    |
| Broth            | Any household | Food     | Counts double as care while ill                            |
| Mustard poultice | Herbalist     | Poultice | Shortens chill and lung fever                              |
| Wormwood draught | Apothecary    | Draught  | Shortens marsh ague, prevents a relapse for a while        |
| Flux electuary   | Apothecary    | Paste    | Shortens the flux, eases thirst drain                      |
| Theriac          | Apothecary    | Paste    | Clears non-illness effects; eases all symptoms for a while |
| Plague water     | Apothecary    | Draught  | Improves plague and pox crisis odds                        |

- **Theriac.** The medieval cure-all, made from many herbs with honey and wine. It clears every effect that is not an illness symptom, as vanilla milk did, which the [thirst document](thirst.md#drinks) takes away from milk. Honey bottles still cure poison, as in vanilla.
- **Spoilage.** Remedies spoil under the [food spoilage](food-spoilage.md#shelf-life) rules. Teas, posset, and broth keep 4 days, and syrups, draughts, pastes, and poultices keep 48.
- **Imports.** Every remedy can be made from local ingredients, so a village without trade can still treat its sick. Imported spices and minerals make stronger versions, such as Venice treacle, a stronger theriac, and merchants sell finished remedies.

### Humoral treatments

The barber-surgeon offers bloodletting and purges, the treatments of medieval humoral medicine. Each eases one symptom for an in-game hour at a cost in health, and never cures. Villagers believe in them, so a treatment raises the morale of the villager who gets it. Players can ask for them too.

### Medicinal plants and rye

- **Wild herbs.** New horehound, mint, chamomile, mustard, and wormwood plants grow in the biomes and seasons that fit each herb.
- **Willow.** A new tree along rivers and in swamps, whose bark gives willow bark for tea.
- **Physic garden.** The herbalist grows herbs in a garden, so the village does not depend on foraging.
- **Dried herbs.** Herbs dry on the drying rack of the [food spoilage document](food-spoilage.md#preservation) and keep 96 days.
- **Rye.** A new crop. Rye harvested in the rain, or kept where it gets wet, can carry ergot, which shows as dark grains in the tooltip. Sifting the rye at the mill removes it. Bread and ale made from rye that carries ergot carry it too.

## Villagers

### Nursing

- **Bed rest.** A sick villager stays in bed and does not work.
- **Household.** The household brings food, water, and broth, keeps the fire lit, and fetches the herbalist.
- **Living alone.** The midwife nurses a villager with no household.
- **Healers.** The herbalist and the apothecary examine the sick, and bring remedies from the village stock or brew them.

### Quarantine

- **At home.** A villager with a contagious illness is kept apart from the rest of the household, in another room or another bed.
- **Pest house.** Once two or more villagers have the pox or plague, the village moves them to a pest house: a new structure, a home at least 32 blocks from the nearest other home. The builder raises it when the village first needs one.
- **Marked doors.** The doors of plague houses get a painted cross, a new decoration, and villagers avoid marked homes.

None of this binds a player; it only shows what villagers do.

### Epidemics

A village enters an epidemic when a quarter of its villagers is ill with the same contagious illness, configurable. During an epidemic:

- Merchants and travelers avoid the village.
- Festivals are called off.
- Morale drops.
- Healers work only for the sick.
- With plague, villagers may flee to a neighboring Feudum village.

The epidemic ends a week after the last case recovers or dies.

## Death and burial

### Bodies

- **Shroud.** A dead villager leaves a body wrapped in a shroud, a new entity. Villagers carry it to the burial ground, and the sexton buries it.
- **Pollution.** An unburied body pollutes the water nearby, as the corpses of mobs do in the [thirst document](thirst.md#contamination).
- **Plague bodies.** Carrying the body of a plague victim exposes the carrier to plague.
- **Plague pits.** During a plague epidemic, bodies go to a plague pit outside the village instead of the burial ground.

### Graves

A proper grave is at least 2 blocks deep, inside a burial ground with a wall or fence, and marked with a new grave marker block. Once the faith mechanic exists, the burial ground also has to be consecrated by a priest. Until then, the physical rules stand in for consecration.

### The risen dead

Medieval villagers feared that the improperly buried dead would walk. In Feudum they do:

| Body                                    | Rises as | When                         |
|:----------------------------------------|:---------|:-----------------------------|
| Unburied                                | Zombie   | After a few nights, at night |
| In a shallow grave or a plague pit      | Zombie   | Within the first weeks       |
| In an improper grave once it has rotted | Skeleton | After a season               |

A body in a proper grave rarely rises. The risen are plain zombies and skeletons, not zombie villagers, so nobody can cure them back to life. They spawn on top of vanilla spawning rather than in place of it, and carry no disease.

## Livestock

Livestock has diseases of its own:

| Disease     | Animals         | Cause                               | Tier    | Spreads |
|:------------|:----------------|:------------------------------------|:--------|:--------|
| Murrain     | Cattle          | Contagion between herds             | Serious | Yes     |
| Sheep rot   | Sheep           | Grazing wet pasture in rain (fluke) | Serious | No      |
| Scab        | Sheep           | Contagion                           | Mild    | Yes     |
| Swine fever | Pigs            | Contagion, unclean troughs          | Serious | Yes     |
| Fowl pest   | Chickens        | Contagion                           | Serious | Yes     |
| Colic       | Horses, donkeys | Spoiled feed, sudden change of feed | Mild    | No      |

Livestock also catches a chill and heatstroke from exposure, as the [temperature document](temperature.md#livestock) describes, and dehydration lowers its resistance.

- **Effects.** A sick animal stops breeding, gives less milk, wool, and eggs, and moves slowly. Serious diseases can kill it.
- **Contagion.** Livestock diseases spread among livestock by the [contagion](#contagion) rules: a shared barn, a shared pen, or closeness outdoors.
- **The herder.** Isolates sick animals in a separate pen, doses them with herbal drenches from the herbalist, and culls what is past saving.
- **Carcasses.** Murrain carcasses are burned, not butchered, and the butcher refuses meat from diseased animals.

## Seasons and climate

- **Winter.** Chill, lung fever, and rheum peak.
- **Summer and hot climates.** The flux, marsh ague, and plague peak: water stagnates and food spoils faster, mosquitoes swarm, and fleas breed.
- **Wet harvests.** Rain at harvest raises the ergot risk in rye.

In the Nether, only heatstroke threatens. The End adds no risk.

## Related mechanics

Disease works together with these mechanics:

- **[Temperature](temperature.md).** The freezing and scorching bands cause a chill and heatstroke, fever raises body temperature, and rooms decide who shares the air of a sick body.
- **[Thirst](thirst.md).** Unclean water causes the flux, low thirst lowers resistance, and theriac takes over the effect clearing of milk.
- **[Food spoilage](food-spoilage.md).** Spoiled food causes food poisoning, and remedies spoil by the same rules.
- **[Seasons](seasons.md).** Each season brings its own illnesses, and wet harvests bring ergot.
- **Sanitation.** The waste of the sick fouls latrines and water, which spreads the flux.
- **Vermin.** Rats carry the fleas that bring plague.
- **Injuries.** Wounds, broken bones, bleeding, and wound infection belong to injuries, not disease.
- **Intoxication.** Hangovers belong to intoxication, not disease.
- **Trade.** Imported spices and minerals make stronger remedies, and merchants avoid a village in an epidemic.
- **Aging.** Age lowers resistance.
- **Morale.** Epidemics lower morale, and humoral treatments raise it.
- **Faith.** A consecrated burial ground keeps the dead from rising.

## Additions and changes

- **Illnesses.** Players, Feudum villagers, and livestock carry illnesses that move from incubation through onset, illness, crisis, and convalescence. Datapacks can add or change illnesses.
- **Roster.** New chill, lung fever, heatstroke, rheum, food poisoning, the flux, marsh ague, St. Anthony's fire, the pox, and plague.
- **Symptom effects.** New fever, cough, hallucinations, and rash effects, with icons, alongside vanilla nausea, weakness, slowness, and hunger.
- **Contagion.** Exposure that builds up by room, distance, time, and a shared bed or home.
- **Resistance and immunity.** Hunger, thirst, cold, and other illness lower resistance, and some illnesses leave immunity behind.
- **Care.** A player can lie in a bed by day to rest, and rest, warmth, food, and drink speed recovery.
- **Remedies.** New willow bark tea, horehound syrup, mint tea, chamomile tea, posset, broth, mustard poultice, wormwood draught, flux electuary, theriac, Venice treacle, and plague water.
- **Milk.** Vanilla milk no longer clears effects, and theriac does instead.
- **Humoral treatments.** Bloodletting and purges from the barber-surgeon.
- **Plants.** New horehound, mint, chamomile, mustard, and wormwood plants, a new willow tree, a physic garden, and a new rye crop that can carry ergot, which the mill sifts out.
- **Herbal.** A new book that names illnesses and records survived illnesses and known remedies.
- **Mosquitoes.** Ambient mosquito swarms in swamps and mangrove swamps on warm evenings.
- **Villager behavior.** Feudum villagers rest in bed when sick, nurse their households, isolate the contagious, move pox and plague cases to a pest house, mark plague doors, and carry their dead to burial.
- **Pest house.** A new structure, built at least 32 blocks from the nearest home.
- **Painted cross.** A new door decoration that marks a plague house.
- **Epidemics.** A village state that keeps merchants away, calls off festivals, lowers morale, and can make villagers flee.
- **Bodies and burial.** A new shrouded body entity, a grave marker block, burial grounds, and plague pits. Unburied bodies pollute water.
- **Risen dead.** Zombies and skeletons rise from bodies that were not properly buried, in addition to vanilla spawning.
- **Livestock diseases.** New murrain, sheep rot, scab, swine fever, fowl pest, and colic, with herbal drenches, culling, and burned carcasses.
- **Illness display.** Effect icons, cough and sneeze sounds, cough particles, pale and pox-marked villagers, and drooping livestock.
- **Configuration.** Server settings for the strength of the symptoms, the pace of the stages, the epidemic threshold, the immunity time, and turning disease off for players and contagion off for everyone.
