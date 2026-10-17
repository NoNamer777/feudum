# Hunger

Every mob that eats has a stomach, an energy store, and a diet. A meal fills the stomach, and digestion turns it into the energy that work, cold, and healing burn. Over the following days a body also needs a varied diet: a winter of bread with no fruit or dairy wears a village down. Hunger drives animals too, so a starving wolf pack raids the flocks. Vanilla hunger is one bar for players alone, so Feudum replaces it.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Every entity type with a diet profile has hunger: players, villagers, livestock, and wild animals. [ADR 0007](../../adr/0007-every-mob-that-eats-has-hunger.md) records why.
- An entity type with no diet profile has no hunger, for species that don't eat, such as undead, constructs, or spirits.
- A per-world setting sets how harsh hunger is for every entity: `off`, `mild` (debuffs only, never lethal), or `harsh` (starvation kills). The default is `harsh`. It is separate from the body temperature setting.
- Difficulty plays no part: Peaceful never refills hunger, and the harshness setting alone decides whether starvation kills.
- Creative and spectator players are exempt.

## Model

- A body carries three layers: its stomach, its energy, and its group levels.
- **Stomach**: how much the body has eaten and not yet digested. Eating fills it at once, and drinking fills it too, as [Thirst](thirst.md#model) describes. A body can eat past its capacity, up to 125%, and is Stuffed above 100%.
- **Energy**: what digestion fills, over a few Feudum hours, and metabolism drains.
- **Group levels**: one level from 0 to 100% for each food group the species tracks.
- Hunger advances by the Feudum time that passed, so it follows the day length and the sleep speed-up.
- At normal activity, a human needs two good meals per Feudum day, matching the medieval dinner at midday and supper in the evening. Heavy labor calls for a third.

## Food groups

- The six food groups are grain, protein, vegetables, fruit, dairy, and forage. Legumes, such as peas and beans, count as protein. Forage covers grass and hay, which humans can't digest.
- Each diet profile names the groups its species tracks. Players and villagers track the five human groups. A cow tracks forage, grain, and vegetables, and a dog tracks protein and grain.
- Wild species track no groups by default, since they rarely stay loaded long enough for a group to drain. A data pack can add groups to any profile.
- A group level rises when the body eats food that carries the group, and falls steadily from full to empty in about 6 Feudum days.
- A group below 25% is deficient. Its effects grow stronger as the level falls toward 0.
- A body with every group above 75% has a balanced diet and heals faster.

## Drain

Energy drains at the base metabolic rate of the diet profile, adjusted by:

- **Rest**: resting and sleeping drain at a lower rate, so a night's sleep costs about one meal.
- **Exertion**: the activities that build the exertion offset of [Body temperature](body-temperature.md#felt-temperature), such as sprinting, mining, and fighting, raise the drain.
- **Cold**: Chilled multiplies the drain by 1.25 and Hypothermic by 1.5, as starting values to tune.
- **Healing**: natural healing spends energy.
- **Grain deficiency**: raises the drain, as [Deficiencies](#deficiencies) describes.

Heat stages leave energy alone; they drain [thirst](thirst.md#drain).

## Stages

The stages follow energy, apart from Stuffed, which follows the stomach. Thresholds come from the diet profile. For a human at normal activity:

| Stage    | Reached                           | Effects                                                         |
|:---------|:----------------------------------|:----------------------------------------------------------------|
| Stuffed  | Stomach above 100%                | Slower movement until the stomach settles.                      |
| Fed      | After a meal                      | None.                                                           |
| Hungry   | By the next meal                  | Cues only.                                                      |
| Famished | About one Feudum day without food | Slower movement and work, no sprinting, no healing.             |
| Starving | About two Feudum days             | Periodic damage, which kills from full health in about one day. |

- Work covers mining, chopping, and attacking, as in Body temperature.
- Under `mild`, Starving brings heavy slowness and deals no damage.
- Effects apply as Feudum attribute modifiers, never as mob effects, so no icon shows in the inventory.
- Modifiers of the same kind as those of Body temperature and Thirst take the strongest rather than adding up, under a rule that Health owns. Damage from each mechanic still applies on its own.
- Feudum's own starvation damage type carries its own death message.

## Deficiencies

For a human:

| Group      | Effect                                                  |
|:-----------|:--------------------------------------------------------|
| Grain      | Energy drains faster, since there is no staple to burn. |
| Protein    | Weaker attacks and slower work.                         |
| Vegetables | A narrower comfort band, so cold and heat bite sooner.  |
| Fruit      | Slower healing.                                         |
| Dairy      | More fall damage.                                       |

- A deficient animal yields less milk, wool, and eggs, grows more slowly, and won't breed.
- Deficiencies apply under `mild` too, since none of them kills.

## Healing

- A fed body heals slowly while awake, and faster while it sleeps or sits.
- Healing spends energy, and a Famished or Starving body doesn't heal.
- A balanced diet speeds healing, and a fruit deficiency slows it.

## Cues

- Players read their own state from body cues, never from a meter. The vanilla food bar is hidden.
- **Hungry**: a growling stomach.
- **Famished**: trembling hands and a faint darkening at the edge of the view.
- **Starving**: heavier darkening and a heartbeat.
- **Stuffed**: a sluggish step and the occasional belch.
- A deficient body craves the groups it lacks: a food carrying a craved group shows "Craved" in its tooltip and is eaten a little faster. A craving is the only cue for a deficiency.
- Mobs show their state too, so a player can read a herd at a glance: hungry animals call out and nose at troughs and the ground, and starving ones look thin and stagger.

## Food

- Every consumable carries a food component: energy, stomach fill, an amount for each food group, eating time, the optional thermal offset of [Body temperature](body-temperature.md#felt-temperature), and the water and salt amounts of [Thirst](thirst.md#food-and-drink).
- Food components are data-driven, so a data pack can add foods.

## Animals

- Animals share one feeding goal: when hungry, they eat what their diet allows from what is in reach, by grazing, browsing, eating from troughs or dropped food, or eating a carcass.
- A grazing animal eats down the grass block under it. Snow cover blocks grazing, so pasture runs short in winter and a village must put up hay.
- Hand-feeding an animal only feeds it; it never starts vanilla love mode.
- Breeding requires a Fed animal with no deficiency.

## Diet profiles

- Each entity type has a data-driven diet profile: JSON in a data pack, assigned through entity type tags, as thermal profiles are.
- A profile holds the diet type, an item tag of what the species can eat, the groups it tracks, the stomach and energy capacity, the base metabolic rate, and the stage thresholds.
- The diet type is grazer, browser, carnivore, or omnivore.
- Villagers use the human diet profile, the same as players.
- A profile can carry a thirst block, which [Thirst](thirst.md#diet-profiles) describes.
- A profile can carry a young modifier with a faster drain. A young body stops growing while it is Hungry or worse.

## Persistence

- A player's hunger saves with the player. Logging back in resumes from the saved values, since a player's absence is not simulated.
- A new player starts Fed, with an empty stomach and every group at 75%.
- Respawning resets energy to Fed and empties the stomach, but group levels stay as they were, so dying never cures a deficiency.
- Wild mobs in unloaded chunks are not simulated. When their chunk loads, each starts at a value that fits the season, well fed in summer and lean in late winter, and never starving.
- An owned animal outside any village territory keeps its saved values while its chunk is unloaded, as a logged-out player does.
- Village simulation brings the villagers and livestock of an unloaded village forward, as [Boundaries](#boundaries) describes.

## Vanilla hunger

- Feudum disables the vanilla food bar, saturation, exhaustion, and starvation, and its natural regeneration from food.
- The vanilla Hunger mob effect is unregistered.

## Query

- One query returns an entity's stomach fullness, energy, group levels, stage, and current drain with the share of each input.
- Other mechanics read hunger through this query.

## Commands

- `/feudum hunger query [entity]` shows the result of the query.
- `/feudum hunger set <entity> <stomach|energy|group> <value>` sets a value, for testing.
- Every `/feudum hunger` command requires operator permission.

## Boundaries

Hunger owns diet profiles, the stomach, energy, food groups and group levels, drain, the stages and their effects, deficiencies and cravings, natural healing, cues, food components, and the feeding goal of animals. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **Body temperature**: the cold stages that raise the drain, and the comfort band that a vegetable deficiency narrows.
- **[Thirst](thirst.md)**: drinking, hydration, and the salt and foul loads, which share the stomach, the food component, and the diet profile of Hunger.
- **[Health](https://github.com/NoNamer777/feudum/issues/36)**: injuries, and the rule that modifiers of the same kind take the strongest. Natural healing moves to Health once it has a design.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: when and what a villager eats, such as meals on its schedule.
- **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: the food stock a village eats from.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: drawing on the stock at each catch-up step, and applying hunger and deficiencies abstractly, so a village that runs out of fruit in winter falls sick while no one is near.
- **[Farming](https://github.com/NoNamer777/feudum/issues/32)**: how grass grows back with the season.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: hunting live prey, such as stalking, pack tactics, and prey that flees.
- **[Cooking](https://github.com/NoNamer777/feudum/issues/30)**: how preparing and combining food sets its food component.
- **[Food preservation](https://github.com/NoNamer777/feudum/issues/35)**: spoilage, salting, smoking, and cellars.
- **[Animal husbandry](https://github.com/NoNamer777/feudum/issues/27)**: breeding, beyond its hunger requirement.
- **[Foods](https://github.com/NoNamer777/feudum/issues/51)** and **[Feed trough and hay](https://github.com/NoNamer777/feudum/issues/50)**: the food and fodder that Feudum adds.
