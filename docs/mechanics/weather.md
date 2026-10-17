# Weather

Weather brings fronts that drift across the map, shaped by each biome's climate profile and the season curves of [Time](time.md). Feudum computes the weather rather than storing it, so the weather at any place and moment, past or future, can be known. Vanilla weather covers a whole dimension at once and advances by ticks, so Feudum replaces it.

[GLOSSARY.md](../../GLOSSARY.md) defines the terms this page uses.

## Computed weather

- Feudum owns the weather. Vanilla weather stays at clear, the weather cycle is locked off, and vanilla `/weather` is unregistered. [ADR 0004](../adr/0004-feudum-owns-the-weather.md) records why.
- The weather at a point follows from the world seed, the position, and the Feudum time. Nothing is stored except weather overrides.
- Weather advances by the Feudum time that passed, so it follows the day length and the sleep speed-up.
- Editing a climate profile or a weather setting changes the weather of every date, past dates included. Snow and ice already in the world stay as they are and continue from the new weather.

## Fronts

- Fronts form, drift, and pass within the weather field, which covers the whole map.
- A front spans 1 to 3 km by default, so it fills the horizon while distant villages can have different weather.
- A typical rain lasts 3 to 12 Feudum hours by default, about 5 to 20 real minutes at the default day length.
- Front size and duration are per-world settings.
- Fronts drift mostly from west to east, with some wander, in every season.
- The climate profile under a front sets how strong it is there. Each profile carries weather season curves, such as how often fronts bring precipitation and how stormy they get, so a tropical Wet season ramps in rather than switching on. The curves are data-driven, like the rest of the profile.
- A front crossing a biome border changes in strength, so weather never cuts off at a line.

## Weather values

- The weather at a point is four weather values: cloud cover, precipitation intensity, storminess, and fog.
- Local temperature decides whether precipitation falls as rain, sleet, or snow.
- A weather label names a range of weather values, such as Overcast, Drizzle, Storm, or Blizzard. A label is something to query, not a state the weather switches between.

## Local temperature

- Local temperature starts from the temperature season curve, scaled by the climate profile.
- It drops with altitude, so a mountaintop can get snow while the valley below gets rain.
- It swings between day and night, and cloud cover narrows the swing, so frost forms on clear nights and melts by midday.

## Snow and ice

- Snow cover builds up layer by layer while snow falls, up to 8 layers, and melts as the local temperature rises.
- Ice on water forms and thaws by the same rule.
- Each chunk records when it last caught up on snow and ice. A loaded chunk applies the change gradually as Feudum time passes; an unloaded chunk applies it all when it loads.
- A newly generated chunk starts with the snow cover and ice of the current date.
- Snow cover from about 4 layers up slows walking, more with each layer.

## In the world

- Feudum renders its own precipitation, clouds, and fog, and plays its own weather sounds.
- Heavy cloud dims the sky, and fog reduces how far a player can see.
- Lightning strikes high points during storms and ignites what it hits.
- Players sleep only at night, whatever the weather.

## Weather signs

- Players read coming weather from weather signs in the sky, never from a HUD.
- A front shows ahead of its arrival: high thin cloud and a halo around the moon a day before, a red sky at dawn before foul weather, and darkening on the horizon it comes from.

## Query

- One query returns the weather values, the weather label, and the local temperature at any position and moment, past or future, weather overrides included.
- Other mechanics read the weather through this query, such as Village simulation at a village center during each catch-up step, so none of them stores weather history.

## Commands

- `/feudum weather query [pos]` shows the weather values and label at a point.
- `/feudum weather set <clear|overcast|rain|storm|fog> [duration]` adds a weather override across the dimension. Overrides are kept on a timeline, so catch-up and weather signs stay consistent with them.
- `/feudum weather reset` ends the active weather override.
- Every `/feudum weather` command requires operator permission.
- Setting the date backwards with `/feudum time` makes the weather follow the new date.

## Boundaries

Weather owns the weather field, fronts, weather values and labels, local temperature, snow cover and ice, weather signs, lightning, and weather overrides. Other mechanics, most of them planned in the [index](README.md), own what weather does to them:

- **Farming**: how crops respond to the weather.
- **Village simulation**: what a village does with the weather of each catch-up step.
- **Villagers**: how weather changes villager behavior.
- **Buildings**: what weather does to buildings.
- **Skills**: how well players and villagers read weather signs, and what a skilled reader learns beyond them.
- **Fire**: how fire spreads and how rain puts it out.
- **Body temperature**: what cold, heat, and wetness do to players.

## Deferred

- **Wind**: wind as a weather value, snow drifts and snow moved by the wind, and seasonal shifts in the drift of fronts. The [weather vane](../content/README.md) waits for it.
