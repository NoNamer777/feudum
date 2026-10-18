# Thirst

Every mob that eats also drinks. A drink fills the stomach and absorbs into hydration within the hour, and metabolism drains it, faster in the heat and at hard work. What a body drinks matters as well: seawater and salted food leave a salt load that dries it out, and foul water leaves a foul load that can make it sick. Thirst drives animals too, so a herd needs a trough kept free of ice in winter, and predators wait at the river. Vanilla has no thirst, so Feudum adds its own.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Every entity type whose diet profile carries a thirst block has thirst: players, villagers, livestock, and wild animals. [ADR 0008](../../adr/0008-every-mob-that-eats-has-thirst.md) records why.
- A diet profile with no thirst block has no thirst, for species that get their water from food. An entity type with no diet profile has neither hunger nor thirst.
- A per-world setting sets how harsh thirst is for every entity: `off`, `mild` (debuffs only, never lethal), or `harsh` (dehydration kills). The default is `harsh`. It is separate from the hunger and body temperature settings.
- Difficulty plays no part, and the harshness setting alone decides whether dehydration kills.
- Creative and spectator players are exempt.

## Model

- A body carries its hydration, a salt load, and a foul load, and shares the [stomach](hunger.md#model) of Hunger.
- **Stomach**: a drink fills the stomach, as food does, so drinking on a full stomach can make a body Stuffed.
- **Hydration**: what the water in the stomach absorbs into, and metabolism drains. The water of a drink absorbs within about one Feudum hour, and the water in food absorbs as the food digests. Absorption stops once hydration is full, and the rest of the water passes off to Relief as the stomach empties, so a body can't drink ahead.
- **Salt load**: what seawater and salted food leave behind. It raises the drain in proportion to its size, and clean water absorbing into the body lowers it, so seawater dehydrates on balance.
- **Foul load**: what foul water leaves behind. It fades over a few Feudum days. Thirst only stores it; Illness decides whether the body falls sick.
- Thirst advances by the Feudum time that passed, so it follows the day length and the sleep speed-up.
- At normal activity in a mild climate, a human needs to drink three to four times per Feudum day.

## Water quality

- [Fluids](fluids.md#water-quality) gives every water block and every container a salinity and a foulness. Clean water is 0 for both, seawater has a salinity of 1, and brine more, up to about 7.5. Foulness runs up to 1.
- A drink adds to the salt load in proportion to its salinity, and to the foul load in proportion to its foulness.
- The diet profile's salt tolerance scales what salinity adds, so a species that tolerates salt can drink seawater.
- A drink of brine adds more salt than seawater, so it dehydrates faster.
- Fluids decides how water gets its quality, such as the fresh and salt water of world generation, the foul water of swamps and of ponds near livestock, and how waters mix.
- Boiled water, ale, small beer, cider, and wine are clean, so a village can make foul water safe. Cooking owns boiling, and Brewing owns the rest.

## Drinking

- A player drinks from a container, such as a cup, a waterskin, or a jug, filled at a source.
- A player can also sip by hand: crouching and using an empty hand on a water block takes slow sips. A lost player can live by a stream, but needs a container to carry water away from it.
- Eating snow from the ground gives a little clean water and carries a cold thermal offset, so a snowfield keeps a body alive at the cost of its warmth. Ice must be melted before it can be drunk.
- A rain barrel collects clean water from the precipitation of [Weather](weather.md).
- Neither swimming nor rain on the body hydrates.

## Drain

Hydration drains at the base rate of the diet profile, adjusted by:

- **Rest**: resting and sleeping drain at a lower rate.
- **Exertion**: the activities that build the exertion offset of [Body temperature](body-temperature.md#felt-temperature), such as sprinting, mining, and fighting, raise the drain.
- **Heat**: Overheated multiplies the drain by 1.5 and Heat exhaustion by 2, as starting values to tune.
- **Salt load**: raises the drain, as [Model](#model) describes.

Exertion while Overheated already counts as sweat, so sweat adds no input of its own. Cold stages leave hydration alone; they drain energy.

## Stages

The stages follow hydration. Thresholds come from the diet profile. For a human at normal activity in a mild climate:

| Stage      | Reached                               | Effects                                                         |
|:-----------|:--------------------------------------|:----------------------------------------------------------------|
| Hydrated   | After a drink                         | None.                                                           |
| Thirsty    | By the next drink                     | Cues only.                                                      |
| Parched    | About half a Feudum day without water | Slower movement and work, no sprinting, no healing.             |
| Dehydrated | About one Feudum day without water    | Periodic damage, which kills from full health in about one day. |

- Heat roughly halves the time to each stage.
- Work covers mining, chopping, and attacking, as in Body temperature.
- Under `mild`, Dehydrated brings heavy slowness and deals no damage.
- Effects apply as Feudum attribute modifiers, never as mob effects, so no icon shows in the inventory.
- Modifiers of the same kind as those of Hunger and Body temperature take the strongest rather than adding up, under a rule that Health owns. Damage from each mechanic still applies on its own.
- Healing spends no water, but a Parched or Dehydrated body doesn't heal.
- Feudum's own dehydration damage type carries its own death message.

## Cues

- Players read their own state from body cues, never from a meter.
- **Thirsty**: a dry swallow.
- **Parched**: hoarse breathing and a slightly washed-out view.
- **Dehydrated**: a heavily washed-out, swaying view and the heartbeat of Starving.
- A high salt load makes the body crave clean water: clean drinks show "Craved" in their tooltip, as craved food does.
- The foul load has no cue of its own; the symptoms of Illness are its cue.
- Mobs show their state too, so a player can read a herd at a glance: thirsty animals pant and gather at water, and dehydrated ones stagger.

## Food and drink

- The food component of [Hunger](hunger.md#food) also carries a water amount and a salt amount. Fruit, milk, broth, and stew hydrate, and salted meat carries salt, so a winter on salt pork calls for more ale.
- A drink is a consumable with a food component, so a drink with energy, such as milk or ale, also feeds.
- Each drink also carries an alcohol amount, which Brewing reads.

## Animals

- Animals share one drinking goal: when Thirsty, they walk to reachable water or a water trough and drink.
- Ice and frozen troughs block drinking, so a village must keep its troughs open in winter.
- Animals drink clean or foul water, and avoid salt water unless their profile tolerates salt. Illness decides whether foul water makes livestock sick.

## Diet profiles

- The [diet profile](hunger.md#diet-profiles) of Hunger carries an optional thirst block, so thirst needs no profile or entity type tags of its own.
- The thirst block holds the hydration capacity, the base drain, the absorption rate, the stage thresholds, and the salt tolerance.
- The young modifier of a profile also speeds the drain, and a young body stops growing while it is Thirsty or worse.

## Persistence

- A player's thirst saves with the player. Logging back in resumes from the saved values, since a player's absence is not simulated.
- A new player starts Hydrated, with no salt or foul load.
- Respawning resets hydration to Hydrated and clears the salt load, but the foul load stays, so dying never cures what foul water started.
- Wild mobs in unloaded chunks are not simulated. When their chunk loads, each starts Hydrated, in every season, since water doesn't run short in winter the way food does.
- An owned animal outside any village territory keeps its saved values while its chunk is unloaded, as a logged-out player does.
- Village simulation brings the villagers and livestock of an unloaded village forward, as [Boundaries](#boundaries) describes.

## Query

- One query returns an entity's water in the stomach, hydration, salt load, foul load, stage, and current drain with the share of each input.
- Other mechanics read thirst through this query.

## Commands

- `/feudum thirst query [entity]` shows the result of the query.
- `/feudum thirst set <entity> <hydration|salt|foul> <value>` sets a value, for testing.
- Every `/feudum thirst` command requires operator permission.

## Boundaries

Thirst owns hydration, absorption, the salt and foul loads, drain, the stages and their effects, cues, the water and salt amounts of food components, the thirst block of diet profiles, and the drinking goal of animals. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Hunger](hunger.md)**: the stomach, food components, and diet profiles that Thirst extends.
- **[Body temperature](body-temperature.md)**: the heat stages that raise the drain, and the thermal offset of drinks and snow.
- **[Fluids](fluids.md)**: the salinity and foulness of water blocks and containers, how water flows, mixes, and fouls, and Feudum's replacement for vanilla water.
- **[Health](https://github.com/NoNamer777/feudum/issues/36)**: natural healing, and the rule that modifiers of the same kind take the strongest.
- **[Illness](https://github.com/NoNamer777/feudum/issues/37)**: what the foul load does to a body.
- **[Relief](https://github.com/NoNamer777/feudum/issues/40)**: the water that passes off once hydration is full.
- **[Cooking](https://github.com/NoNamer777/feudum/issues/30)**: boiling water.
- **[Brewing](https://github.com/NoNamer777/feudum/issues/28)**: ale, beer, cider, wine, and drunkenness.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: when and what a villager drinks.
- **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: the stock of water, ale, and beer a village drinks from.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: applying thirst and the foul load abstractly while a village is unloaded.
- **[Buildings](https://github.com/NoNamer777/feudum/issues/29)**: wells and cisterns.
- **[Drink containers](https://github.com/NoNamer777/feudum/issues/49)**, **[Rain barrel](https://github.com/NoNamer777/feudum/issues/52)**, and **[Feed trough and hay](https://github.com/NoNamer777/feudum/issues/50)**: the containers, the rain barrel, and the water troughs.
