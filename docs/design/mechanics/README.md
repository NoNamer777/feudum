# Mechanics

The game mechanics of Feudum. A mechanic gets its own page in this folder once its design is settled. The [design index](../README.md) lists the other areas, such as world generation and content.

## Designed

- **[Body temperature](body-temperature.md)**: thermal profiles for every living mob, felt temperature and its inputs, wetness, shelter and room temperature, and the stages of cold and heat.
- **[Hunger](hunger.md)**: diet profiles for every mob that eats, the stomach, energy, and food groups, drain and its stages, deficiencies and cravings, and the feeding goal of animals.
- **[Thirst](thirst.md)**: hydration for every mob that eats, the salt and foul loads, drain and its stages, cues, and the drinking goal of animals.
- **[Time](time.md)**: the clock, the calendar with its seasons and sub-seasons, climate profiles, and catch-up for unloaded villages.
- **[Villages](villages.md)**: what a village is, its territory and lifecycle, standing, manors, and lordship.
- **[Weather](weather.md)**: fronts that drift across the map, weather values, wind, local temperature, snow and ice, and weather signs.

## Planned

Mechanics that came up while designing other topics and wait for a design of their own.

- **Animal husbandry**: breeding livestock, beyond the Fed animal with no deficiency that Hunger requires.
- **Brewing**: ale, small beer, cider, and wine, which make water safe to drink, and the drunkenness they bring. Replaces vanilla brewing.
- **Buildings**: how buildings are designed, built, and recognized as part of a village.
- **Cooking**: how preparing and combining food sets the energy and food groups it carries.
- **Extreme weather**: tornadoes, hurricanes, and other extreme wind events, beyond what fronts bring.
- **Farming**: crops whose growth depends on the season.
- **Fire**: how fire catches, spreads downwind, and burns out, and how rain puts it out.
- **Fluids**: how water flows, whether its sources are finite, rivers and their currents, and the salinity and foulness of water: the fresh and salt water of world generation, fouling by livestock, and how waters mix. Its starting point for fouling: still fresh water turns foul when three or more livestock spend a Feudum day within 6 blocks of it, and stays foul for about two days after they leave, while flowing water never fouls. Replaces vanilla water.
- **Food preservation**: how food spoils, and how salting, smoking, and cellars keep it.
- **Health**: natural healing, injuries such as bleeding and broken bones, and the rule that modifiers of the same kind from Hunger, Thirst, and Body temperature take the strongest.
- **Illness**: how a body falls sick, such as from the foul load of [Thirst](thirst.md#model), and how sickness spreads and heals.
- **Lordship contests**: how a player challenges a sitting lord, how a contest is won, and what the loser keeps.
- **Realms**: fealty between lords, up to a sovereign with no lord above them, which a player can become.
- **Relief**: the bladder and bowels that fill with what the stomach passes on, the need to relieve oneself, where to go, and the waste left behind, which can foul water and fertilize fields.
- **Sailing**: boats under sail that read the wind.
- **Segmented sleep**: a first and second sleep with a waking hour between, for villager schedules and possibly player sleep. Revisits the sleep speed-up of Time.
- **Skills**: how players and villagers learn and improve skills, such as reading weather signs, through reading (a skill of its own), being taught by villagers, and practice.
- **Village economy**: stock and production, and the harvests, markets, tithes, and taxes on the calendar.
- **Village simulation**: how a village reaches its decisions, and how it advances as abstract data while its chunks are unloaded.
- **Villagers**: the villager model that daily schedules, aging, homes, and village officers run on, including villager lords.
- **Wildlife**: how hungry predators hunt live prey, with stalking and pack tactics, and how prey flees.
