# Illness

Bodies fall sick. Foul water and spoiled food bring the flux, dirt in an open wound makes it rot, a winter cough passes through a crowded longhouse, and murrain sweeps a herd. Each disease has a name, a course of days, and symptoms that act through the needs and the body: a fever heats it, the flux drains its water, and weakness slows it. Care decides most of the outcome, so a sick body kept warm, fed, watered, and in bed comes through, while a neglected one, a child, or an old body may not. Diseases spread through breath, waste, touch, shared things, and the pests that carry them, so a village keeps its sick apart, its privies away from its wells, and its water boiled. Vanilla has no illness, so Feudum adds its own.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Every entity type whose body profile carries an illness block can fall sick: players, villagers, livestock, and wild animals. [ADR 0022](../../adr/0022-every-living-mob-can-fall-sick.md) records why.
- A body profile with no illness block never falls sick, and an entity type with no body profile has no illness.
- A per-world setting sets how harsh illness is for every entity: `off`, `mild`, or `harsh`. The default is `harsh`. It is separate from the settings of the needs, Health, and Body temperature.
  - `off`: no body falls sick. The foul load is still stored, but nothing reads it.
  - `mild`: diseases run their course, but severity stops just short of Grave, so illness never deals damage.
  - `harsh`: everything on this page.
- Difficulty plays no part, and the setting alone decides whether illness kills.
- Creative and spectator players are exempt.
- Illness covers natural disease from pathogens. [Poisons and venom](https://github.com/NoNamer777/feudum/issues/156) covers toxins, which act within minutes by their dose, and [Magic](https://github.com/NoNamer777/feudum/issues/129) covers any magical sickness or cure.

## Model

- **Disease**: a named, data-driven definition: JSON in a data pack. It sets the hosts it can infect by body profile tag, its symptoms, the ways it spreads, its spans, and its immunity.
- A body can carry several diseases at once, each running its own course.
- **Variant**: a disease can declare itself a variant of another, inheriting every value and overriding some, as bloody flux does for the flux.
- **Turning**: a disease can turn into another once it reaches Grave, as wound rot turns into gangrene.
- **Severity**: how far a disease has gone in a body, from 0 to 100%. Its symptoms scale with it.
- Every span of a disease is the real span scaled to the calendar, as [Animal husbandry](animal-husbandry.md#species) scales biology: a year has 96 days, so a real week is about 2 Feudum days, and a real year is one Feudum year.
- Illness advances by the Feudum time that passed, so it follows the day length and the sleep speed-up.

## Course

The diagram shows the states a body passes through with one disease, and what moves it from one to the next. Its labels name the stages of a human; the thresholds come from the body profile.

![A flow of eight states. Healthy goes to Incubating when the body catches a disease by one of its routes. Incubating goes to Ailing when incubation ends. Ailing, Sick, and Grave sit in one box of rising severity, from Ailing to Sick at 33% and from Sick to Grave at 66%, where neglect keeps severity rising. From any of the three, the course turns, sooner with care, into Recovering. Recovering goes to Immune when severity falls to 0, and Immune returns to Healthy when immunity runs out. Grave goes to Dead through illness damage under harsh, and a dashed line shows that a disease at Grave can turn into another disease.](images/illness-course.svg)

- **Incubating**: the body carries the disease, with no symptoms, for the incubation span of the disease. Each disease sets the share of its incubation during which the body already spreads it.
- **Ailing**, **Sick**, and **Grave**: the stages of severity, which rises from the end of incubation until the course turns.
- **Recovering**: severity falls back to 0. The body still spreads the disease until it has recovered.
- **Immune**: the body can't catch the same disease again until its immunity span runs out. Some diseases leave lifelong immunity, and some none.

### Stages

The stages follow severity. Thresholds come from the body profile. For a human:

| Stage  | Severity  | Effects                                                              |
|:-------|:----------|:---------------------------------------------------------------------|
| Ailing | Below 33% | Faint symptoms.                                                      |
| Sick   | 33%       | Strong symptoms, and no healing.                                     |
| Grave  | 66%       | Under `harsh`, periodic illness damage to the chest, which can kill. |

- Illness damage lands on the chest pool, as [Health](health.md#damage-with-no-struck-region) describes, and carries its own death message.
- The flux kills mostly through [Thirst](thirst.md#stages): its drain makes a body Dehydrated before it reaches Grave.
- Under `mild`, severity holds just below Grave.
- No-healing is a flag under the [rule](health.md#modifiers) of Health, and every symptom's modifiers take the strongest with those of the other mechanics.

### Care

Severity rises at the rate of the disease until its course turns, then falls. How the body is kept moves both:

- The course turns sooner, and severity falls faster, while the body sleeps or rests in a bed, and while it is neither Chilled nor Overheated under [Body temperature](body-temperature.md#stages).
- While the body is Famished, Starving, Parched, Dehydrated, Hypothermic or colder, or in Heat exhaustion or hotter, its course doesn't turn, and severity keeps rising. These are the stages that stop healing under [Health](health.md#healing), so one rule covers both.
- [Herbal remedies](https://github.com/NoNamer777/feudum/issues/155) can ease a symptom or speed recovery on top of care. No remedy cures a disease at once.
- A chronic disease, such as consumption or leprosy, rises slowly over its whole course. Care slows its rise, and only care can turn it.

### Age and resistance

- The young modifier of a body profile, and the old age of [Animal husbandry](animal-husbandry.md#growth-and-old-age), make severity rise faster, so the peak climbs higher. Infants, lambs, and the old are the ones a sickness kills.
- The illness block sets the resistance of a species, which slows the rise.

## Symptoms

A disease is built from symptoms, each acting through a mechanic that already exists. Each scales with severity:

| Symptom     | Effect                                                                                                                           |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------|
| Fever       | A warming offset to felt temperature under [Body temperature](body-temperature.md#felt-temperature).                             |
| Chills      | A cooling offset to felt temperature.                                                                                            |
| Flux        | The bowels of [Relief](relief.md#model) fill fast, and hydration under [Thirst](thirst.md#drain) drains faster.                  |
| Cough       | A cough that others hear, and stronger spread by breath.                                                                         |
| Weakness    | Slower movement and work, and from Sick on, no sprinting.                                                                        |
| No appetite | A smaller stomach under [Hunger](hunger.md#model), so the body is Stuffed sooner and eats less.                                  |
| Pain        | Slower work.                                                                                                                     |
| Wasting     | Energy under [Hunger](hunger.md#drain) drains faster.                                                                            |
| Stiffness   | Heavy slowness, and from Grave on, no eating.                                                                                    |
| Decay       | A pool that the disease names, such as the pool of a wound or the legs, slowly loses hit points under [Health](health.md#pools). |
| Blood loss  | Blood under [Health](health.md#blood) drains slowly.                                                                             |
| Rash        | Marks on the model, with no other effect.                                                                                        |

- Work covers mining, chopping, and attacking, as in Body temperature.
- Effects apply as Feudum attribute modifiers, never as mob effects, so no icon shows in the inventory.

## Catching a disease

A body catches a disease through one of its routes, or from one of the first sources that start an outbreak.

### Foul load

- Each Feudum hour, the [foul load](thirst.md#model) of Thirst gives a chance of catching the flux, and a smaller chance of enteric fever. The chance grows with the load, so a sip of slightly foul water is a small risk, and a fouled well drunk from for weeks makes sickness close to certain.
- The foul tolerance of the thirst block scales the chance, so pigs and dogs shrug off water that sickens a human.
- The foul load comes from foul water, [Spoiled food](food-preservation.md#keeping-time), and the meat of a sick animal, as [Animals](#animals) describes.

### Open wounds

- Each Feudum hour, an [open wound](health.md#injuries) gives a chance of wound rot on its pool. A burn of a high degree counts as an open wound.
- Grime and mud on the body, a Soiled body under [Relief](relief.md#accidents), and a dirty bandage raise the chance. Bloodstain doesn't, since it is blood, not filth.
- Washing the body under [Hygiene](hygiene.md#washing), and changing the bandage, lower it. [Bandage, splint, and salve](https://github.com/NoNamer777/feudum/issues/125) decides how a bandage gets dirty; Illness reads it.
- A pierce wound on a body that carries mud or is Soiled also gives a chance of lockjaw.

### First cases

A contagious disease needs a first case. Each disease names its own sources, as starting values to tune:

- **The cough**: a small chance each hour while a body is Chilled or colder, higher in Winter. Influenza inherits it.
- **The sweat**: a small chance each hour in Summer, and never in other seasons.
- **Murrain**: a chance each hour for livestock that rises with the deep [dung layers](relief.md#animals) under them, with [crowding](animal-husbandry.md#crowding), and with their foul load.
- **Foot rot**: deep dung and [wet ground](fluids.md#volume) under sheep, goats, and cattle.
- **Anthrax**: the tainted ground of [Anthrax](#animals-to-humans).
- **Strangers**: a body that arrives from outside, such as a wanderer, a trader, or newly bought stock, can arrive Incubating. [Villagers](https://github.com/NoNamer777/feudum/issues/46) and [Village economy](https://github.com/NoNamer777/feudum/issues/44) decide who arrives; Illness sets the chance.
- **Wild mobs**: a wild mob has a small chance to start Incubating one of the diseases its body profile can host when its chunk loads, so wild boar can bring swine fever to the village pigs.

## Spread

Each disease names the routes it spreads by. A body spreads a disease from the share of its incubation that the disease sets until it has recovered.

The diagram shows the cycle of the flux, which joins rules from Fluids, Thirst, Illness, and Relief. It also marks where the cycle can be broken.

![A cycle of five steps. Foul water, owned by Fluids, is drunk into the foul load of Thirst. Boiled water, ale, and wine are clean, which breaks the cycle there. The foul load gives a chance each hour of the flux, owned by Illness, whose bowels fill fast. That leaves waste, owned by Relief, and a sick body's waste fouls more. Waste in a stream is carried downstream to foul water. Waste in a privy pit seeps through the ground to the groundwater and wells of Fluids, where sand and loam filter it, and it is drawn up as foul water again.](images/illness-flux-cycle.svg)

### Breath

- A body that spreads by breath passes the disease to bodies near it, within about 4 blocks or in the same [enclosed space](body-temperature.md#shelter-and-heat). The chance each hour grows with its severity and with the time spent together.
- An enclosed space raises the chance, and open air lowers it, so a shared longhouse spreads the cough and an open field barely does.
- The cough symptom strengthens the spread.

### Waste

- The waste of a body that spreads by waste is a stronger [fouling source](fluids.md#fouling) than other waste, wherever [Relief](relief.md#relieving) puts it. The foul water it leaves then makes others sick through their foul load.
- Water carries only its foulness, never a mark of a disease.

### Touch

- Touch covers close contact that is already an action: treating a body's injuries, helping a Downed body up, sharing a bed, and butchering, skinning, or handling the carcass, hide, or fleece of a sick animal. Combat hits don't count.
- Each touch gives a chance of passing a disease that spreads by touch.
- Grime on the hands of the body that touches raises the chance, so a healer who washes between patients spreads less. The same grime on a treater raises the chance of wound rot on the wound they treat.

### Shared things

- Garments, bedding, and drink containers used by a sick body pick up a disease that spreads that way, and keep it for a span the disease sets.
- Another body that wears the garment, sleeps in the bedding, or drinks from the container can catch it.
- [Laundry](hygiene.md#laundry) clears a garment or bedding, boiling under [Cooking](https://github.com/NoNamer777/feudum/issues/30) clears a container, and time clears all of them.
- The water and feed troughs of [Feed trough and hay](https://github.com/NoNamer777/feudum/issues/50) count as shared things for animals. Emptying a trough clears it.

### Vectors

- A data pack can mark an entity type as a vector of a disease. A vector passes the disease to the bodies it bites or lives near, without falling sick itself.
- [Parasites](https://github.com/NoNamer777/feudum/issues/157) and [Vermin](https://github.com/NoNamer777/feudum/issues/136) use the hook, and [Wildlife](https://github.com/NoNamer777/feudum/issues/47) uses it for the bite of a rabid animal.

### Carriers

- A disease can leave some of its survivors as carriers: they show no symptoms but keep spreading it, for a span the disease sets. Their waste fouls water as a sick body's does.
- In the starting set, only enteric fever leaves carriers, so an outbreak that keeps coming back to one well has a cause to track down.

## Diseases

Feudum ships the diseases below. Spans are starting values to tune, scaled to the calendar.

### Caught by breath

| Disease     | Hosts  | Symptoms                            | Spreads by                          | Incubation     | Course                 | Immunity      |
|:------------|:-------|:------------------------------------|:------------------------------------|:---------------|:-----------------------|:--------------|
| The cough   | Humans | Cough, chills, weakness             | Breath, cups                        | Under a day    | About 2 days           | A few seasons |
| Influenza   | Humans | Fever, cough, weakness, no appetite | Breath, cups                        | Under a day    | About 3 days           | A year        |
| Smallpox    | Humans | Fever, pain, weakness, then rash    | Breath, touch, bedding and garments | About 3 days   | About 5 days           | Lifelong      |
| Measles     | Humans | Fever, cough, rash                  | Breath                              | About 3 days   | About 3 days           | Lifelong      |
| The sweat   | Humans | Fever, pain, weakness               | Breath                              | A few hours    | Within a day           | None          |
| Consumption | Humans | Cough, wasting, weakness            | Breath, slowly                      | About a season | Several years, chronic | None          |
| Leprosy     | Humans | Rash, decay of the limb pools       | Breath and touch, very slowly       | About a year   | Many years, chronic    | None          |

- The cough rarely kills. Influenza is a variant of the cough, with a higher peak in the young and the old.
- Smallpox spreads only once its rash shows, and leaves pox scars on the model of a survivor. Measles spreads a short while before its rash, and strikes mostly children, since adults are mostly immune.
- The sweat runs its whole course within a day and kills fast.
- Leprosy never reaches Grave, so it doesn't kill on its own. Its standing cost is in [Standing](#standing).

### Caught from foul water and food

| Disease       | Hosts        | Symptoms                                | Spreads by                                       | Incubation  | Course       | Immunity |
|:--------------|:-------------|:----------------------------------------|:-------------------------------------------------|:------------|:-------------|:---------|
| The flux      | Humans, dogs | Flux, pain, weakness                    | Foul load, waste, touch with a Soiled body, cups | Under a day | About 2 days | None     |
| Bloody flux   | Humans, dogs | Flux, pain, weakness, blood loss        | Foul load, waste, touch with a Soiled body, cups | Under a day | About 4 days | None     |
| Enteric fever | Humans       | Fever, then flux, weakness, no appetite | Foul load, waste, cups, carriers                 | 2 to 4 days | About a week | Years    |

- Bloody flux is a variant of the flux.
- Enteric fever leaves some survivors as [carriers](#carriers).

### Caught in wounds

| Disease   | Hosts              | Symptoms                                          | Spreads by                                                       | Incubation   | Course         | Immunity |
|:----------|:-------------------|:--------------------------------------------------|:-----------------------------------------------------------------|:-------------|:---------------|:---------|
| Wound rot | Every body profile | Pain, decay of its pool, and from Grave on, fever | Its open wound, at a higher chance under a treater's grimy hands | None         | Until it turns | None     |
| Lockjaw   | Every body profile | Stiffness, pain                                   | Its pierce wound only                                            | About 2 days | About a week   | None     |

- Wound rot sits on the pool of its open wound, and that pool doesn't heal while it lasts. At Grave, it brings fever and illness damage, as blood poisoning.
- Lockjaw often kills, since a body that can't eat starves while the disease runs.
- [Amputation](https://github.com/NoNamer777/feudum/issues/158) plans gangrene, the turn of wound rot on a limb, with the surgery that answers it.

### Murrain

Murrain is the name villagers give every plague of livestock:

| Disease       | Hosts                                           | Symptoms                           | Spreads by                                     | Incubation   | Course         | Immunity    |
|:--------------|:------------------------------------------------|:-----------------------------------|:-----------------------------------------------|:-------------|:---------------|:------------|
| Cattle plague | Cattle, water buffalo                           | Fever, flux, weakness, no appetite | Breath, touch, troughs                         | 1 to 4 days  | About 2 days   | Lifelong    |
| Swine fever   | Pigs                                            | Fever, weakness, no appetite       | Breath, troughs, eating the meat of a sick pig | About 2 days | About 4 days   | Lifelong    |
| Fowl pest     | Chickens, ducks, geese, swans, peafowl, pigeons | Cough, weakness, no appetite       | Breath, troughs                                | Under a day  | About a day    | Lifelong    |
| Strangles     | Horses, donkeys, mules                          | Fever, cough, no appetite          | Breath, troughs                                | About 2 days | About a week   | A few years |
| Distemper     | Dogs                                            | Fever, cough, flux, weakness       | Breath                                         | About 2 days | About a week   | Lifelong    |
| Foot rot      | Sheep, goats, cattle                            | Pain, decay of the leg pools       | Deep dung and wet ground, and barely by touch  | None         | Until kept dry | None        |

- Cattle plague is fast and deadly. Strangles strikes mostly the young and rarely kills, and foot rot lames rather than kills.
- Foot rot turns once the animal stands on dry, clean ground.

### Animals to humans

| Disease  | Hosts                                               | Symptoms                     | Spreads by                                                              | Incubation   | Course                                     | Immunity |
|:---------|:----------------------------------------------------|:-----------------------------|:------------------------------------------------------------------------|:-------------|:-------------------------------------------|:---------|
| Glanders | Horses, donkeys, mules, humans                      | Fever, cough, weakness, rash | Among animals by breath, touch, and troughs, and to humans by touch     | About 2 days | A season, chronic                          | None     |
| Anthrax  | Cattle, water buffalo, sheep, goats, horses, humans | Fever, weakness, rash        | Livestock by tainted ground, and humans by touch and by eating the meat | About a day  | About a day in livestock, longer in humans | None     |

- Both are deadly. Glanders makes a sick horse a danger to its groom.
- An animal that dies of anthrax taints the ground where it lies, and where it is buried, for many Feudum years. Grazing livestock on tainted ground can catch it. Burning the carcass leaves no taint. Each chunk stores its tainted spots as a short list, as [Fluids](fluids.md#water-quality) stores only the blocks that differ.
- A wild grazing animal that starts Incubating anthrax, and dies of it, is how the first tainted ground appears.

### Planned diseases

Diseases that need content or mechanics Feudum doesn't have yet wait in the issue that plans them:

- **[Parasites](https://github.com/NoNamer777/feudum/issues/157)**: plague, bubonic turning pneumonic, carried by the fleas of rats; typhus, carried by lice; ague, carried by mosquitoes; sheep scab, from mites; and liver rot of sheep, from flukes.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: rabies, from the bite of a rabid animal, which crosses to humans.
- **[Amputation](https://github.com/NoNamer777/feudum/issues/158)**: gangrene.
- **[Poisons and venom](https://github.com/NoNamer777/feudum/issues/156)**: ergotism, which is a poisoning rather than a disease.
- Scurvy and the other effects of a missing food group are [deficiencies](hunger.md#deficiencies) of Hunger.

## Animals

- A sick animal gives no milk or eggs, and its fleece doesn't grow, under [Animal husbandry](animal-husbandry.md#fleece).
- Meat cut from an animal that died of a disease, or that was slaughtered while Sick, adds a foul load when eaten, as Spoiled food does. Swine fever and anthrax also spread by eating it, as their rows describe. [Food preservation](food-preservation.md) still owns how the meat spoils.
- A carcass left lying in water is already a fouling source under [Fluids](fluids.md#fouling).
- Sick animals droop, cough, and keep apart from the herd, so a player can spot one before it spreads.

## Standing

- A player with visible leprosy, from Sick on, inside a village's territory and in sight of one of its villagers, lowers standing with that village once per sighting, as smell does under [Hygiene](hygiene.md#standing).
- No other disease moves standing, since falling sick isn't conduct. [Villagers](https://github.com/NoNamer777/feudum/issues/46) decides how villagers react to a cough, a pox, or the flux, such as shying away or refusing to trade.
- [Buildings](https://github.com/NoNamer777/feudum/issues/29) decides whether a village has a leper house.

## Cues

- Players read their own state from body cues, never from a meter. Each symptom borrows the cue of the mechanic it acts through: a fever shows the Overheated view, chills shiver, the flux brings the urge of Relief, and a cough sounds for everyone near.
- Visible marks show on the model: a rash, pox and pox scars, and the swelling of a rotting wound.
- The [body panel](health.md#cues) names each disease once it shows symptoms, such as "the flux", "wound rot (left leg)", or "the cough", with no numbers. An Incubating disease shows nothing.
- Mobs show their state too, as [Animals](#animals) describes.

## Body profiles

- The [body profile](health.md#body-profiles) of Health carries an optional illness block, so illness needs no profile or entity type tags of its own.
- The illness block holds the stage thresholds, the resistance, and how much youth and old age raise the peak.
- The thirst block of the [diet profile](thirst.md#diet-profiles) holds the foul tolerance, next to the salt tolerance.
- Each disease names its hosts by body profile tag, so a data pack can add a disease to a species, or a species to a disease, without editing the other.
- Villagers use the human body profile, the same as players.

## Persistence

- A player's diseases, immunities, and carrier state save with the player. Logging back in resumes from the saved values, since a player's absence is not simulated.
- A new player starts healthy, with no immunities.
- Respawning keeps every disease, immunity, and carrier state, so dying never cures a disease, as it never clears the foul load under [Thirst](thirst.md#persistence).
- Wild mobs in unloaded chunks are not simulated. When their chunk loads, each starts healthy, apart from the chance to start Incubating that [First cases](#first-cases) describes.
- An owned animal outside any village territory keeps its saved values while its chunk is unloaded, as a logged-out player does.
- Village simulation brings the villagers and livestock of an unloaded village forward, as [Boundaries](#boundaries) describes.
- Garments, bedding, drink containers, and troughs save the disease they carry and the time left. Each chunk saves its anthrax spots.

## Vanilla effects

- The vanilla Poison, Nausea, Hunger, and Wither mob effects are unregistered. The vanilla items and mobs that gave them are replaced, under the rule of Feudum's own content.
- Milk no longer clears effects. It is a drink under Thirst, nothing more.
- The zombie villager and its cure are removed with the vanilla mobs.

## Query

- One query returns an entity's diseases, each with its state, severity, and time left, its immunities and carrier state, and the current chance from each route.
- A second function returns the disease a garment, bedding, drink container, or trough carries, and a third the anthrax spots of a chunk.
- Other mechanics read illness through these.

## Commands

- `/feudum illness query [entity]` shows the result of the query.
- `/feudum illness infect <entity> <disease>` starts a disease at Incubating, for testing.
- `/feudum illness cure <entity> [disease]` ends one disease, or every disease, with no immunity.
- `/feudum illness immunize <entity> <disease>` makes a body immune.
- Every `/feudum illness` command requires operator permission.

## Boundaries

Illness owns disease definitions, variants and turning, severity and the course with its stages, care, age, and resistance, the symptoms and their effects, and illness damage. It also owns how the foul load and open wounds turn into disease, the first sources of an outbreak, every route of spread, vectors and carriers, the starting diseases, sick meat and produce, the standing cost of leprosy, the cues of sickness and its names in the body panel, the illness block of body profiles, and the foul tolerance. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Health](health.md)**: open wounds, pools, blood, the body panel, damage on the chest, the stages that stop healing, and the rule for combining modifiers.
- **[Thirst](thirst.md)**: the foul load, and the drain that the flux speeds.
- **[Hunger](hunger.md)**: the stomach, energy, deficiencies, and the stages that stop recovery.
- **[Body temperature](body-temperature.md)**: felt temperature and its offsets, the stages that set care, and enclosed spaces.
- **[Relief](relief.md)**: the bowels, accidents and the Soiled state, where waste goes, and dung layers.
- **[Hygiene](hygiene.md)**: grime and mud on the body and the hands, washing, laundry, and how smell moves standing.
- **[Fluids](fluids.md)**: foulness, fouling sources, groundwater, and wet ground.
- **[Food preservation](food-preservation.md)**: Spoiled food and its foul load.
- **[Animal husbandry](animal-husbandry.md)**: livestock, old age, crowding, milk, eggs, fleece, and butchering.
- **[Villages](villages.md)**: the standing scale.
- **[Herbal remedies](https://github.com/NoNamer777/feudum/issues/155)**: the remedies that ease symptoms and speed recovery.
- **[Bandage, splint, and salve](https://github.com/NoNamer777/feudum/issues/125)**: how a bandage gets dirty and is changed.
- **[Healer](https://github.com/NoNamer777/feudum/issues/126)**: the villager who tends the sick, gives remedies, and keeps the sick apart.
- **[Amputation](https://github.com/NoNamer777/feudum/issues/158)**: gangrene, and removing a limb.
- **[Parasites](https://github.com/NoNamer777/feudum/issues/157)** and **[Vermin](https://github.com/NoNamer777/feudum/issues/136)**: fleas, lice, mosquitoes, mites, flukes, and rats, and the diseases they carry as vectors.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: rabies and rabid animals.
- **[Poisons and venom](https://github.com/NoNamer777/feudum/issues/156)**: toxins, and ergotism.
- **[Magic](https://github.com/NoNamer777/feudum/issues/129)**: magical sickness and cures.
- **[Cooking](https://github.com/NoNamer777/feudum/issues/30)**: boiling water and containers.
- **[Feed trough and hay](https://github.com/NoNamer777/feudum/issues/50)**: the troughs.
- **[Buildings](https://github.com/NoNamer777/feudum/issues/29)**: leper houses and sickrooms.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: how villagers care for the sick, keep apart from them, and react to signs of sickness, and who arrives from outside.
- **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: the stock bought from outside.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: outbreaks, courses, and recovery while a village is unloaded.
