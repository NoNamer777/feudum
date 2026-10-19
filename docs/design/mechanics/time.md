# Time

Time gives Feudum one clock and one calendar, and every time-based system follows them: the day and night cycle, villager schedules, recurring village events, aging, and the seasons that change the world. Vanilla's clock is too fast for a management game and cannot carry a calendar, so Feudum replaces it.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Clock

- Feudum owns the clock. It stores elapsed time as a day count plus the fraction of the current day, and derives the vanilla `dayTime` from it. The `doDaylightCycle` gamerule stays locked off. [ADR 0001](../../adr/0001-feudum-owns-the-clock.md) records why.
- A day lasts 40 real minutes by default, twice the vanilla day. Day length is a per-world setting that can change at any time; since the clock counts days rather than ticks, a change never moves the date.
- Every Feudum system advances by the Feudum time that has passed, never by counting server ticks. Day length, sleep speed-up, and catch-up all run through this one path.
- A day has 24 hours and starts at midnight. Dawn falls at 06:00, as in vanilla.
- A new world starts on Early Spring 1, Year 1 at 06:00.

## Calendar

- A year has four seasons: Spring, Summer, Autumn, and Winter.
- Each season has three sub-seasons, Early, Mid, and Late, so that seasons flow into each other. A sub-season lasts 8 days by default.
- A year therefore has 96 days. At the default day length, a season takes 16 hours of play and a year 64 hours.
- Days per sub-season is the only configurable calendar length. The number of seasons and sub-seasons stays fixed, since names, curves, and content depend on it.
- A week has 8 days and lines up with the sub-season, so every sub-season holds each weekday exactly once and the day number in the date is the weekday.
- The moon completes one cycle per week, with a full moon on weekday 1.
- A date reads as "Mid Summer 5, Year 3".

## Seasons and climate

- Seasonal values, such as daylight, temperature, and foliage color, follow season curves that change a little every day. A sub-season is a label to query, not a step where values jump.
- Daylight is the same everywhere, since a dimension has one sun. Its share of the day runs from about 60% at midsummer to about 40% at midwinter, with the vanilla split at the equinoxes.
- The calendar is global. Each biome has a climate profile that maps the global sub-seasons to its local seasons and sets how strongly each season curve other than daylight applies there. A temperate profile keeps the four seasons, a tropical profile reads Late Spring through Early Autumn as Wet and the rest as Dry, and an arid profile may have no local seasons at all.
- Climate profiles are data-driven: JSON in a data pack, assigned to biomes through biome tags such as `#feudum:climate/tropical`.

The table shows how the example profiles above read the global sub-seasons, taking an arid profile with no local seasons. The profiles are illustrative, since a data pack sets each one.

| Global sub-season | Temperate | Tropical | Arid |
|:------------------|:----------|:---------|:-----|
| Early Spring      | Spring    | Dry      | None |
| Mid Spring        | Spring    | Dry      | None |
| Late Spring       | Spring    | Wet      | None |
| Early Summer      | Summer    | Wet      | None |
| Mid Summer        | Summer    | Wet      | None |
| Late Summer       | Summer    | Wet      | None |
| Early Autumn      | Autumn    | Wet      | None |
| Mid Autumn        | Autumn    | Dry      | None |
| Late Autumn       | Autumn    | Dry      | None |
| Early Winter      | Winter    | Dry      | None |
| Mid Winter        | Winter    | Dry      | None |
| Late Winter       | Winter    | Dry      | None |
- The player sees the global date with the local season after it, as in "Mid Summer 5, Year 3 (Wet)". Schedules and events follow the global date only, so they never depend on where a player stands.

## Sleep

- Sleeping speeds the clock up instead of skipping the night: once vanilla's `playersSleepingPercentage` threshold is met, time runs at 20 times its normal rate until dawn. A night at the default day length then passes in about 40 seconds.
- Every system keeps running through the speed-up, since each advances by the time that passed.
- The speed-up stops as soon as too few players are asleep.

## Unloaded villages

- A village keeps progressing while no player is near it, as abstract data on the Feudum clock.
- Catch-up is lazy: any read of a village's state first brings it up to the current time.
- Catch-up steps one hour at a time over the last 7 days, and one day at a time before that. It spreads its work across ticks, so loading a village never stalls the server.
- Calendar boundaries fire in two scopes. Global hooks fire once, live, as the clock passes a boundary. Village hooks replay during catch-up as each village passes the same boundary. Both carry the date being processed, so an event due on day 12 happens on day 12 even when it is processed later.

## Commands

- Feudum unregisters vanilla `/time`.
- `/feudum time set|add|query` takes calendar-aware arguments, such as `spring 3`, and requires operator permission.
- Setting the date backwards resets each village's catch-up point to the new date. Nothing is undone and nothing replays.

## Boundaries

Time owns the clock, the calendar, the season curves, climate profiles, and the hooks on calendar boundaries. Other mechanics own what happens on them, each linked to its page or, while it waits for a design, its issue:

- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: daily schedules and how fast villagers age.
- **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: harvests, markets, tithes, and taxes on the calendar.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: what a village does during each catch-up step.
- **[Farming](farming.md)**: how crop growth reads the season curves and daylight.
- **Weather**: what a local season brings, such as rain, storms, and snow.

## Deferred

- **[Timekeeping items](https://github.com/NoNamer777/feudum/issues/54)**: a Feudum clock and calendar that show the time, date, and season. The vanilla clock stays hidden until then, and no permanent HUD replaces it.
