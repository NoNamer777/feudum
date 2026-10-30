# Fatigue

How players, villagers, and animals tire, what tiredness does to them, and how sleep clears it. [Time](../world/time.md) sets when creatures sleep, and that fatigue keeps running through time that sleeping or catch-up skips.

## The scale

Every creature has one fatigue value. It counts in hours awake at rest, on in-game time, so the day-length [setting](../world/time.md#settings) scales it with the day. Fatigue has no settings of its own, so other designs can count on it.

Fatigue does nothing while it is low. From Tired on, its effects grow smoothly with the value up to the top of the scale. The labels below only name points on the scale: they set when a player sees a message, and they give villagers points to act on. Each label starts at this many hours awake at rest:

| Label     | From | For example                             |
|:----------|-----:|:----------------------------------------|
| Rested    |    0 | After a night's sleep                   |
| Tired     |   16 | Bedtime after a long summer day         |
| Weary     |   24 | A whole night without sleep             |
| Exhausted |   36 | Halfway into a second day without sleep |

The scale tops out at 48 hours, two full days awake, where a creature [collapses](#collapse).

## Building fatigue

Fatigue builds for every hour a creature is awake. Hard exertion builds it one and a half times as fast while it lasts: sprinting, swimming, fighting, mining, felling trees, a villager's heavy field work, or an animal pulling a plow or cart.

## Sleep

Sleep clears fatigue at a rate set by where a creature sleeps:

| Sleeping place    | Hours awake cleared per hour of sleep |
|:------------------|--------------------------------------:|
| Bed               |                                   2.5 |
| Pallet or bedroll |                                     2 |
| Bare ground       |                                  1.25 |

A creature sleeps on bare ground only when it collapses. A player sleeping on a pallet or bedroll at night counts toward the [sleeping share](../world/time.md#speeding-up-the-night), as one in a bed does. How cold and warmth affect sleep belongs to [Body temperature](https://github.com/NoNamer777/feudum/issues/227).

In a bed, even the shortest night of the year clears a long day. At midsummer, a creature that goes to bed at sunset sleeps about 7 hours around the [watch](../world/time.md#two-sleeps-and-the-watch), which clears 17.5 hours: the 16 hours of daylight and the hour of the watch. A long winter night leaves it rested with time to spare. Exertion tips the balance: 10 hours of field work on that summer day add 5 hours, which the night cannot clear. A midday nap of an hour or so makes up most of the difference; without it, fatigue piles up through the harvest.

Nothing but sleep lowers fatigue. No food, drink, or potion wakes a creature up; the [era](../setting/era.md) had no coffee or tea.

### Naps

During the day, any creature can nap in a bed or on a pallet or bedroll, at the same rate as sleep at night. Time runs at normal speed through a nap, and a napping player does not count toward the sleeping share. A napping player can get up whenever they like and wakes on their own once rested.

Villagers rest at midday during the summer field work, as harvest crews of the era did. When they nap belongs to [Villager schedules](https://github.com/NoNamer777/feudum/issues/214).

## Effects

### Players

From Tired on, a player works slower at mining, felling, and crafting, hits weaker, runs out of sprint sooner, and heals more slowly. Their vision darkens at the edges of the screen, and they yawn now and then. All of this grows with fatigue. The effect is Feudum's own, not vanilla's Mining Fatigue.

Nothing on screen shows fatigue. Players read it from these cues, and from a short message each time they reach a new label.

### Villagers

From Tired on, villagers work slower and make more mistakes, such as spoiling a craft. From Exhausted on, they stop working and go to bed, whatever the hour. When they work and sleep otherwise belongs to [Villager schedules](https://github.com/NoNamer777/feudum/issues/214).

### Animals

Animals sleep at night on their own, so they tire mostly from being worked or pushed: pulling a plow or cart, being ridden hard, or being chased. From Tired on, an animal moves slower and yields less, such as less milk. From Exhausted on, it refuses work until it has rested. Which animals work and what they yield belongs to [Animals](https://github.com/NoNamer777/feudum/issues/228).

### Reading others' fatigue

Players tell a tired villager or animal by sight: it yawns, moves slower, and droops its head. The management screen of a village also shows each villager's label.

## Collapse

A creature whose fatigue reaches the top of the scale collapses where it stands and sleeps on the bare ground until it is just below Exhausted. That takes about 10 in-game hours, some 16 real minutes at the default day length. It lies helpless meanwhile, but wakes when hurt, and collapses again once its fatigue climbs back to the top. A collapse ignores the watch, and a collapsed player does not count toward the sleeping share.

Fatigue never kills.

## When fatigue holds still

A player's fatigue holds still while they are logged out and while they play in creative or spectator mode, so they come back as tired as they left. A player who dies respawns rested.
