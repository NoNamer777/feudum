# Health

Every living mob has a pool of health for each part of its body, so where a blow lands matters: a cut to the sword arm ends a duel, and a smashed leg ends a march. Hits can injure as well as hurt. A bleeding body loses blood until it is bandaged, a broken bone won't mend until it is set, and a blow to the head can knock a body out. A body whose head or chest gives out goes down rather than dying at once, and can still be helped up. Healing is slow and runs on the needs of the body, so a wounded guard needs days of food, drink, and rest. Vanilla has one pool of hit points that food refills in a minute, so Feudum replaces it.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Every entity type with a body profile has the health of this page: pools, blood, injuries, and healing driven by its needs. That covers players, villagers, livestock, and wild animals. [ADR 0016](../../adr/0016-every-living-mob-can-be-injured.md) records why.
- An entity type with no body profile keeps a single pool of hit points and has no blood or injuries, for species such as constructs or spirits.
- A per-world setting sets how harsh health is for every entity: `off`, `mild`, or `harsh`. The default is `harsh`.
  - `off`: no injuries, and healing at about vanilla's pace.
  - `mild`: injuries, but blood loss never knocks a body out or kills it.
  - `harsh`: everything on this page.
- The setting is separate from the hunger, thirst, relief, and body temperature settings.
- Under every setting, the pools and the Downed state apply, since they are the health model itself.
- Creative and spectator players are exempt.

## Model

- A body carries a pool for each part of its body, a blood value, and the injuries on its pools.
- **Pools**: the hit points of one part of the body. [ADR 0017](../../adr/0017-health-lives-in-a-pool-for-each-body-part.md) records why health is split this way. Some pools are vital: a body whose vital pool reaches 0 goes [Downed](#downed-and-unconscious). Any other pool at 0 is disabled.
- **Blood**: what bleeding drains. It is separate from the pools, so a body can be badly cut but not yet bled out.
- **Injuries**: conditions on a pool, such as bleeding or a fracture, which a hit can cause and treatment ends.
- Health advances by the Feudum time that passed, so healing and bleeding follow the day length and the sleep speed-up.

## Pools

A human has seven pools, with starting values to tune on the vanilla damage scale. [Weapons](../content/weapons.md) sets the damage of attacks against them.

| Pool      | Vital | Hit points |
|:----------|:-----:|-----------:|
| Head      |  Yes  |         10 |
| Chest     |  Yes  |         24 |
| Left arm  |  No   |         14 |
| Right arm |  No   |         14 |
| Left leg  |  No   |         16 |
| Right leg |  No   |         16 |

Other species take their pools from their [body profile](#body-profiles).

## Hits

The diagram shows the seven pools of a human beside the five struck regions of [Armor](../content/armor.md#struck-region), and which pools each region's hits land in. The body's outline is illustrative.

![A front view of a human split into seven pools: head, chest, two arms, and two legs. Beside it, Armor's five struck regions point to the pools their hits land in. The head goes to the head pool. The chest goes to the chest pool, or to the arm on the struck side about 30% of the time. The hands go to the arm on the struck side, and the legs and feet go to the leg on the struck side.](images/health-pools.svg)

- [Armor](../content/armor.md#struck-region) picks the struck region of a hit, multiplies its damage by that region's multiplier, and reduces it by protection. Health owns the multipliers, starting from ×1.5 for the head, ×1 for chest and legs, and ×0.5 for hands and feet.
- What is left lands in a pool:

| Struck region | Pool                                                 |
|:--------------|:-----------------------------------------------------|
| Head          | Head                                                 |
| Chest         | Chest, or the arm on that side about 30% of the time |
| Hands         | Arm on that side                                     |
| Legs          | Leg on that side                                     |
| Feet          | Leg on that side                                     |

- A hit with an impact point lands on the side of the body's center plane it strikes, relative to the way the body faces. Hitboxes don't turn with the body, so the side comes from the facing, not the hitbox. A point near the center line picks a side at even chance.
- A hit with no impact point, such as a mob's plain melee, lands on the side the attacker stands on, relative to the way the body faces. An attacker straight ahead or behind picks a side at even chance.
- Front and back make no difference: a hit from behind lands in the same pools as one from the front.
- Damage past what a limb pool has left passes to the chest at half, so a disabled limb can't soak hits forever.

### Damage with no struck region

- **Falls**: split over both legs. A heavy fall overflows to the chest, as any limb damage does.
- **Drowning, starvation, dehydration, hypothermia, heatstroke, and illness**: the chest.
- **Suffocation** inside a block: the head.
- **Fire and lava**: the pools they reach, which is the legs for a body standing in fire and every pool for a burning body. Fire and lava also burn, as [Injuries](#injuries) describes.
- **Explosions**: spread over every region by the shares of [Armor](../content/armor.md#struck-region), and split evenly between the sides.

## Damaged pools

A pool below half of its hit points hinders the body, and a pool at 0 disables its part or downs the body:

| Pool  | Below half                                          | At 0                                                                      |
|:------|:----------------------------------------------------|:--------------------------------------------------------------------------|
| Head  | A slightly blurred view, and slower work            | Downed                                                                    |
| Chest | Slower movement and work, no sprinting              | Downed                                                                    |
| Arm   | Slower work and weaker attacks with that hand       | Disabled: it drops what it holds, and can't use, attack, or parry         |
| Leg   | A limp, with slower movement                        | Disabled: heavy slowness, no sprinting or jumping                         |

- A body with both legs disabled can only crawl.
- The main arm follows the main hand of the body, which a player sets in the game options.
- Work covers mining, chopping, and attacking, as in [Body temperature](body-temperature.md#stages).
- Effects apply as Feudum attribute modifiers, never as mob effects, under the rule of [Modifiers](#modifiers).

## Blood

Bleeding drains blood, and the stages follow what is left. For a human, as starting values to tune:

| Stage       | Blood     | Effects                                         |
|:------------|:----------|:------------------------------------------------|
| Faint       | Below 70% | Slower movement and work, and a washed-out view |
| Unconscious | Below 50% | [Unconscious](#downed-and-unconscious)          |
| Dead        | Below 30% | The body dies.                                  |

- Blood comes back from 30% to full in about two Feudum days, the same pace as the pools, and only while the body is neither Parched, Dehydrated, Famished, nor Starving.
- Under `mild`, blood never falls below the Unconscious threshold, so bleeding leaves a body Faint at worst.
- Under `off`, nothing bleeds, so blood stays full.
- Bleeding out carries its own death message.

## Injuries

A hit can injure the pool it lands in. The chance and the severity of an injury grow with the damage left after armor, as a share of the pool's size, so a hit that takes most of a pool at once is the one that breaks it.

- **Bleeding**: from cut and pierce hits. Light bleeding drains about 5% of blood and stops on its own within about half a Feudum hour, under a real minute at the default day length. Heavy bleeding takes a body from full blood to Unconscious in about one Feudum hour, about 100 real seconds at the default day length, and to death soon after, unless it is bandaged. Several bleeds add up.
- **Fracture**: from a blunt hit or a fall that takes a large share of a limb pool at once. Only arm and leg pools fracture.
- **Burn**: from fire and lava on the pools they reach. Its degree grows with the exposure.
- **Concussion**: from a blunt hit to the head over a threshold, with a chance of knocking the body out. It rings and blurs the view.
- Under `off`, hits cause no injuries.
- A bandaged heavy bleed leaves an open wound, and [Illness](https://github.com/NoNamer777/feudum/issues/37) decides whether it festers.

### Treatment

| Injury         | Ends on its own                              | Treatment            | After treatment                                                        |
|:---------------|:---------------------------------------------|:---------------------|:-----------------------------------------------------------------------|
| Light bleeding | Within about half a Feudum hour              | A bandage stops it.  | Nothing.                                                               |
| Heavy bleeding | Never                                        | A bandage stops it.  | An open wound until it heals, which Illness can infect.                |
| Fracture       | Never, and the pool can't heal past half     | A splint sets it.    | Heals over about 6 Feudum days, with the pool held at half until then. |
| Burn           | Slowly, by degree                            | A salve speeds it.   | Heals faster.                                                          |
| Concussion     | Within about a Feudum day                    | Rest only.           | Nothing.                                                               |

- Treating takes a few seconds, during which the body that treats stands still.
- A body can treat itself, more slowly, but not while an arm is disabled.
- Health owns which treatment ends which injury. [Bandage, splint, and salve](https://github.com/NoNamer777/feudum/issues/125) plans the items themselves, and [Healer](https://github.com/NoNamer777/feudum/issues/126) plans the villager who treats a village.

## Healing

- Every pool heals at once, each at a rate that fills it from empty in about the same time. A human who is awake fills a pool from empty in about two Feudum days, and twice as fast while sleeping or sitting. These are starting values to tune.
- Healing runs on the needs of the body: it spends [energy](hunger.md#drain), and stops while the body is Famished, Starving, Parched, or Dehydrated.
- A [balanced diet](hunger.md#food-groups) speeds healing, and a [fruit deficiency](hunger.md#deficiencies) slows it.
- An injury on a pool slows or stops its healing, as [Treatment](#treatment) describes for a fracture.
- A [Chafed](../content/armor.md#over-an-empty-clothing-layer) region slows the healing of every pool its hits can land in: the head, the chest and both arms, both arms, or both legs.
- Under `off`, a fed body heals at about vanilla's pace, in minutes rather than days.

## Downed and Unconscious

The diagram shows the states a body passes through between unhurt and dead, and what moves it from one to the next.

![A flow of five states: Up, Downed, Weakened, Unconscious, and Dead. A vital pool at 0 takes a body from Up to Downed. A Downed body stands up on its own once both vital pools reach 10%, or a helper stops its bleeding and helps it up into Weakened, which returns to Up once both vital pools reach 10%. A knock-out or blood below 50% makes any living body Unconscious, and it wakes as Up, or as Downed while a vital pool is still at 0. Damage to a vital pool at 0, blood below 30%, or giving up takes a Downed or Unconscious body to Dead.](images/health-states.svg)

- A body whose vital pool reaches 0 goes **Downed** when its body profile allows it, which it does for humans. A species that can't be Downed dies instead.
- A Downed body stays conscious. It can crawl slowly, but can't use items, attack, or sprint, and its view darkens.
- A Downed body dies when it takes more damage to a vital pool at 0, or when it bleeds out. Damage from other mechanics, such as starvation or cold, lands on the chest, so it can kill a Downed body too. A Downed body in water can't swim, so it drowns.
- A Downed body never dies just from lying there.
- A Downed body heals at the resting rate. Once it stops bleeding and both vital pools reach 10%, it stands on its own: about 2.5 Feudum hours from a chest at 0, or about 4 real minutes at the default day length.
- A helper can stop a Downed body's bleeding and help it up at once. It then stands **Weakened**, with heavy slowness and no sprinting or attacking, until both vital pools reach 10%.
- A body knocked out by a concussion, or whose blood falls below 50%, goes **Unconscious**. It can't move, and a player hears muffled sounds over a dark screen.
- A knock-out lasts about one Feudum hour, about 100 real seconds at the default day length. Unconsciousness from blood loss lasts until blood rises above 50%. Nothing wakes a body sooner.
- An Unconscious body wakes Downed while a vital pool is still at 0.
- A Downed or Unconscious body stays a target, so hostile mobs and enemies can finish it off.
- A Downed or Unconscious player can give up, which kills them so they can respawn.
- Under `mild`, a Downed body still dies from further damage to a vital pool, since that comes from a fight, not from an injury.

## Modifiers

Hunger, Thirst, Body temperature, and Relief defer to this rule for how their modifiers combine, and Health and Illness follow it too.

- A kind of modifier is one attribute, such as movement speed, attack speed, mining speed, or attack damage.
- Body-condition modifiers come from Hunger, Thirst, Body temperature, Relief, Health, and Illness. On each attribute, only the strongest of them applies.
- Modifiers from what a body wears or carries, such as those of [Encumbrance](https://github.com/NoNamer777/feudum/issues/65), stack on top of the strongest body-condition modifier.
- A flag, such as no sprinting or no healing, applies when any mechanic sets it.
- Damage from each mechanic still applies on its own.

## Cues

- Players read their own health from body cues, never from a meter. The vanilla heart bar is hidden.
- A red edge creeps into the view as the head and chest pools fall, and the heartbeat of Starving plays near 0.
- A damaged leg limps, and a damaged arm's hand trembles.
- A bleeding body drips blood. A concussion rings and blurs the view, and Faint washes it out.
- The inventory screen has a body panel that names the state of each pool in words (unhurt, bruised, hurt, badly hurt, or disabled) and lists its injuries, with no numbers.
- A player can open the same panel on another body they look at, so a healer can see what to treat.
- Mobs show their state too: bandages, limps, and blood.

## Body profiles

- Each entity type has a data-driven body profile: JSON in a data pack, assigned through entity type tags, as diet and thermal profiles are.
- A profile holds its pools, their hit points, and which of them are vital. It also holds the region multipliers, where hits land, and the chance shares for hits with no impact point. Last come the blood volume and blood stages, the healing rate, and whether the species can be Downed.
- Villagers use the human body profile, the same as players.
- Animals take their pools from templates that a data pack can extend:
  - **Quadruped**: head, body, and four legs (left and right, fore and hind).
  - **Bird**: head, body, two wings, and two legs.
  - **Legless**, such as fish and snakes: head and body.
- The head and the body are an animal's vital pools, as the head and chest are for a human.
- A hit on an animal lands by its impact point along the hitbox. The front end is the head, and the lower third the legs: fore or hind by the front or back half, and left or right by the side struck. A hit with no impact point picks a pool by the profile's chance shares.
- A disabled leg slows an animal, and a disabled wing grounds a bird.
- Only the human profile can be Downed by default, so animals die when a vital pool reaches 0. A data pack can let any species be Downed.
- A profile can carry a young modifier, which shrinks the pools and the blood.

## Persistence

- A player's pools, blood, and injuries save with the player. Logging back in resumes from the saved values, since a player's absence is not simulated.
- Respawning restores full pools and blood and clears every injury.
- Wild mobs in unloaded chunks are not simulated. When their chunk loads, each starts at full health.
- An owned animal outside any village territory keeps its saved values while its chunk is unloaded, as a logged-out player does.
- Village simulation applies injuries and healing abstractly for villages that no one is near, as [Boundaries](#boundaries) describes.

## Vanilla health

- Feudum routes all damage through the pools, and vanilla's own health only drops to 0 when Feudum kills the body.
- The vanilla heart bar is hidden, and [Hunger](hunger.md#vanilla-hunger) already disables vanilla's regeneration from food.
- The vanilla Regeneration, Instant Health, Instant Damage, Absorption, and Health Boost mob effects are unregistered.

## Query

- One query returns an entity's pools, its blood, the injuries on each pool, its state (Downed, Unconscious, or Weakened), and its healing rate with the share of each input.
- Other mechanics read health through this query.

## Commands

- `/feudum health query [entity]` shows the result of the query.
- `/feudum health set <entity> <pool|blood> <value>` sets a value, for testing.
- `/feudum health injure <entity> <pool> <injury>` adds an injury, for testing.
- `/feudum health heal <entity>` restores full pools and blood and clears every injury.
- Every `/feudum health` command requires operator permission.

## Boundaries

Health owns body profiles, pools and the region multipliers, which pool a hit lands in, and damage with no struck region. It also owns blood, injuries and which treatment ends each, natural healing, the Downed, Unconscious, and Weakened states, the rule for combining modifiers, cues, and the body panel. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Armor](../content/armor.md)**: damage kinds, the struck region of a hit, protection, and the Chafed state.
- **[Hunger](hunger.md)**: the energy that healing spends, the stages that stop it, and the balanced diet and fruit deficiency that change its pace.
- **[Thirst](thirst.md)**: the stages that stop healing.
- **[Body temperature](body-temperature.md)** and **[Relief](relief.md)**: modifiers under the rule of [Modifiers](#modifiers), and the damage of hypothermia and heatstroke.
- **[Fluids](fluids.md)**: breath, and when a body under water starts to drown.
- **[Illness](https://github.com/NoNamer777/feudum/issues/37)**: whether an open wound festers, and the damage that sickness deals.
- **[Weapons](../content/weapons.md)**: the damage and damage kind of each attack, armor penetration, parrying, and shields.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: the damage and damage kinds of animal attacks.
- **[Fire](https://github.com/NoNamer777/feudum/issues/33)**: how fire catches and spreads. Health owns the burns it leaves.
- **[Encumbrance](https://github.com/NoNamer777/feudum/issues/65)**: the modifiers of weight, which stack on top of body-condition modifiers.
- **[Bandage, splint, and salve](https://github.com/NoNamer777/feudum/issues/125)**: the items that treat injuries.
- **[Healer](https://github.com/NoNamer777/feudum/issues/126)**: the villager who treats a village's injuries.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: how villagers react to their wounds, and when they help a Downed body up.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: applying injuries and healing abstractly while a village is unloaded.
