# Weather

Weather brings fronts that drift across the map on the wind, shaped by each biome's climate profile and the season curves of [Time](time.md). Feudum computes the weather rather than storing it, so the weather at any place and moment, past or future, can be known. Vanilla weather covers a whole dimension at once and advances by ticks, so Feudum replaces it.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Computed weather

- Feudum owns the weather. Vanilla weather stays at clear, the weather cycle is locked off, and vanilla `/weather` is unregistered. [ADR 0004](../../adr/0004-feudum-owns-the-weather.md) records why.
- The weather at a point follows from the world seed, the position, and the Feudum time. Nothing is stored except weather overrides.
- Weather advances by the Feudum time that passed, so it follows the day length and the sleep speed-up.
- Editing a climate profile or a weather setting changes the weather of every date, past dates included. Snow and ice already in the world stay as they are and continue from the new weather.

## Fronts

- Fronts form, drift, and pass within the weather field, which covers the whole map.
- A front spans 1 to 3 km by default, so it fills the horizon while distant villages can have different weather.
- A typical rain lasts 3 to 12 Feudum hours by default, about 5 to 20 real minutes at the default day length.
- Front size and duration are per-world settings.
- Fronts ride the [steering flow](#steering-flow), so they drift mostly from west to east, faster in winter, and turn when it turns.
- The climate profile under a front sets how strong it is there. Each profile carries weather season curves, such as how often fronts bring precipitation and how stormy they get, so a tropical Wet season ramps in rather than switching on. The curves are data-driven, like the rest of the profile.
- A front crossing a biome border changes in strength, so weather never cuts off at a line.

## Weather values

- The weather at a point is five weather values: cloud cover, precipitation intensity, storminess, fog, and wind.
- Local temperature decides whether precipitation falls as rain, sleet, or snow.
- A weather label names a range of weather values, such as Overcast, Drizzle, Storm, or Blizzard. A label is something to query, not a state the weather switches between.
- Storm and Blizzard require Strong wind or more, so heavy snow in calm air is not a Blizzard.

## Wind

### Steering flow

- The steering flow is one wind across the whole map, mostly west to east. It varies slowly over tens of kilometers, so neighboring regions differ while staying coherent at the scale of a front, and its direction wanders over days.
- Its strength follows a global season curve: stronger in winter, weaker in summer.
- No climate profile turns the steering flow, so fronts keep one coherent drift.

### Wind at a point

Wind is measured in meters per second. The wind at a point adds up these parts:

- **Steering flow**: the base of the wind. A climate profile can turn it along a seasonal wind direction curve, so a tropical profile can blow its Wet season wind from the southwest and its Dry season wind from the northeast. The turn blends across biome borders like the other values of the profile, and fronts keep riding the unturned steering flow.
- **Windiness**: a season curve of the climate profile scales the wind, so coasts, plains, and tundra blow hard while forests and jungle stay calm.
- **Front wind**: each front brings wind that grows with storminess and peaks along its leading edge, and a storm pushes a gust front ahead of its rain. The wind backs as a front approaches and veers after it passes. Calm fronts, such as fog, bring little or no wind.
- **Exposure**: ridges, peaks, and windward slopes speed the wind up, and valleys and lee slopes slow it. A valley that runs close to the wind direction channels the wind along itself. The wind also grows with height above the generated surface, so a tower top or a cliff edge is windier than the ground below.
- **Daily cycle**: the wind is calmer at night and strongest in the afternoon.
- **Gusts**: the wind rises above its mean speed in gusts that vary over seconds, more with storminess and rough terrain. Gusts are computed from the seed, the position, and the time, like the rest of the wind.

Exposure reads the base height of Feudum's world generation, which follows from the seed alone, never the blocks in the world. A hill a player levels keeps its original wind. Exposure is sampled on a coarse grid, tens of blocks apart, and cached. [ADR 0006](../../adr/0006-weather-reads-the-generated-terrain.md) records why.

The strongest storm fronts top out around 30 m/s. Tornadoes, hurricanes, and other extreme wind events are planned in the [index](README.md).

### Wind labels

A wind label names a range of mean wind speeds:

| Label        | Mean speed |
|:-------------|-----------:|
| Calm         |    < 1 m/s |
| Light breeze |  1–5.5 m/s |
| Breeze       | 5.5–11 m/s |
| Strong wind  |  11–17 m/s |
| Gale         |  17–25 m/s |
| Tempest      |   ≥ 25 m/s |

### Wind shelter

- Placed blocks act on the wind only through wind shelter, at the entity or block that feels it.
- The wind shelter check looks upwind about 8 blocks at body height. Solid blocks cut the wind; leaves, hedges, and fences cut part of it.
- An enclosed space, as [Body temperature](body-temperature.md#shelter-and-heat) defines it, gets no wind.
- The wind shelter of a position is cached and recomputed when a block in its range changes.

### Wind and the other weather values

- Fog thins as the wind rises and clears from Breeze up.
- Fronts drop more precipitation on windward slopes and less in their lee, which leaves a rain shadow behind high terrain. This reads the same exposure as the wind.
- Wind narrows the swing of the local temperature between day and night, as [Local temperature](#local-temperature) describes.

### Wind forces

Wind forces read the sheltered wind, gusts included, so a wall or a house protects from them.

- From 5.5 m/s, arrows, thrown items, and dropped items drift downwind in proportion to the wind speed.
- From 11 m/s, a headwind slows walking, and a tailwind helps a little.
- From 17 m/s, gales push players and mobs. Sneaking halves the push.

## Local temperature

- Local temperature starts from the temperature season curve, scaled by the climate profile.
- It drops with altitude, so a mountaintop can get snow while the valley below gets rain.
- It swings between day and night. Cloud cover and wind narrow the swing, so frost forms on calm, clear nights and melts by midday.

## Snow and ice

- Snow cover builds up layer by layer while snow falls, up to 8 layers on open ground, and melts as the local temperature rises.
- Ice on water forms and thaws by the same rule.
- Each chunk records when it last caught up on snow and ice. A loaded chunk applies the change gradually as Feudum time passes; an unloaded chunk applies it all when it loads.
- A newly generated chunk starts with the snow cover and ice of the current date.
- Snow cover from about 4 layers up slows walking, more with each layer.

### Snow drifts

- While snow falls in Breeze or more, each column's share of the snowfall depends on its wind shelter. Columns in the lee of a wall, fence, or hedge collect extra layers, and exposed windward columns collect fewer. Placed blocks count, since snow cover is world state.
- From Strong wind up, lying snow on exposed columns blows into sheltered ones while the local temperature is below freezing, even without snowfall.
- In the lee of an obstacle, a snow drift can grow past 8 layers, up to 2 blocks deep. A drift against a door blocks it until someone digs it out.
- An unloaded chunk catching up lays down the net snowfall first, then redistributes it once with the wind weighted by snowfall over the elapsed period.

## In the world

- Feudum renders its own precipitation, clouds, and fog, and plays its own weather sounds.
- Heavy cloud dims the sky, and fog reduces how far a player can see.
- Wind slants rain and snow, sways foliage, and blows particles such as smoke and leaves. High clouds move with the steering flow and low clouds with the wind. Wind sounds rise with the wind speed, gusts included.
- From Strong wind up, blowing snow and blowing sand cut how far a player can see, as fog does, even under a clear sky.
- Lightning strikes high points during storms and ignites what it hits.
- Players sleep only at night, whatever the weather.

## Weather signs

- Players read coming weather from weather signs in the sky and the wind, never from a HUD.
- A front shows ahead of its arrival: high thin cloud and a halo around the moon a day before, a red sky at dawn before foul weather, and darkening on the horizon it comes from.
- The wind shows a front too. A wind that backs and strengthens means a front is coming, and a wind that veers and drops means it has passed. Low clouds moving across the high ones mean the weather is about to change.
- Players read the wind from the weather vane, smoke, swaying foliage, and the movement of the clouds.

## Query

- One query returns the weather values, the weather label, the wind label, and the local temperature at any position and moment, past or future, weather overrides included.
- The query returns the wind as its mean speed, its direction, and the current gust speed, with exposure applied and blocks ignored.
- A second function returns the sheltered wind at an entity or block. Body temperature, wind forces, and the weather vane read it.
- Other mechanics read the weather through this query, such as Village simulation at a village center during each catch-up step, so none of them stores weather history.

## Commands

- `/feudum weather query [pos]` shows the weather values, the wind, and the labels at a point.
- `/feudum weather set <clear|overcast|rain|storm|fog> [duration]` adds a weather override across the dimension. Overrides are kept on a timeline, so catch-up and weather signs stay consistent with them.
- Each weather override brings a matching wind: Clear brings little, and Storm brings Strong wind or more.
- `/feudum weather wind <speed> [direction] [duration]` adds a wind override to the same timeline.
- `/feudum weather reset` ends the active weather and wind overrides.
- Every `/feudum weather` command requires operator permission.
- Setting the date backwards with `/feudum time` makes the weather follow the new date.

## Boundaries

Weather owns the weather field, fronts, weather values and labels, the wind and its labels, wind shelter, wind forces, local temperature, snow cover, snow drifts, and ice, weather signs, lightning, and weather overrides. Other mechanics, most of them planned in the [index](README.md), own what weather does to them:

- **Farming**: how crops respond to the weather, storm damage included.
- **Village simulation**: what a village does with the weather of each catch-up step.
- **Villagers**: how weather changes villager behavior.
- **Buildings**: what weather does to buildings, storm damage included.
- **Skills**: how well players and villagers read weather signs, and what a skilled reader learns beyond them.
- **Fire**: how fire spreads, downwind included, and how rain puts it out.
- **Body temperature**: what cold, heat, wetness, and wind do to living mobs.
- **Sailing**: how boats under sail read the wind.
- **Extreme weather**: tornadoes, hurricanes, and other extreme wind events.
- **Windmill**: how wind powers milling, planned in [Content](../content/README.md).

World generation must offer the base height that exposure reads, as [ADR 0006](../../adr/0006-weather-reads-the-generated-terrain.md) records.
