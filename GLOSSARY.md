# Feudum

Feudum is a Minecraft mod in which players manage medieval fantasy villages. This glossary fixes the names of its concepts, so the design pages and the code use the same words.

## Time

### Clock

The one count of elapsed days and time of day that every time-based Feudum system follows.\
_Avoid_: World time, day time, ticks

### Day

The 24 hours from one midnight to the next.

### Week

The 8 days of one sub-season.

### Weekday

The position of a day within its week, from 1 to 8; the same number as the day in its date.

### Season

One of the four parts of the year: Spring, Summer, Autumn, or Winter. Always global; see local season for what a biome makes of it.

### Sub-season

One of the three parts of a season: Early, Mid, or Late.\
_Avoid_: Month, phase

### Year

Four seasons, starting with Early Spring.

### Date

A day named by its sub-season, its weekday, and its year, as in "Mid Summer 5, Year 3".

### Calendar boundary

The moment a new day, sub-season, season, or year begins.

### Season curve

A value that changes a little every day across the year, such as daylight, temperature, or foliage color.

### Climate profile

A biome's reading of the calendar: which local season each sub-season is there, and how strongly each season curve applies.\
_Avoid_: Climate, biome season

### Local season

The season a climate profile assigns to a sub-season, such as Wet or Dry.

### Sleep speed-up

The faster running of the clock while enough players sleep.\
_Avoid_: Night skip

### Catch-up

Bringing an unloaded village forward to the current time.\
_Avoid_: Fast-forward, offline simulation

## Villages

### Village

A persistent, self-steering community with its own name, territory, and history.\
_Avoid_: Settlement, town

### Territory

The chunks a village claims: every chunk within a margin of its buildings.\
_Avoid_: Claim, borders

### Wilderness

Every chunk that no village claims.

### Village center

The territory chunk nearest the middle of a village's buildings, used as a reference point.

### Ruins

The buildings an ended village leaves behind.

### Manor

A set of a village's buildings, with the villagers whose homes are in them, sworn to one lord.\
_Avoid_: Fief, estate

### Village holding

The buildings of a village that belong to no manor.\
_Avoid_: Commons

### Lord

The one player or villager a manor is sworn to.\
_Avoid_: Owner, ruler

### Standing

How much a village trusts a player, and so how much weight that player's wishes carry.\
_Avoid_: Reputation, favor

### Wish

Something a player or lord asks of a village, which the village weighs against its own needs.\
_Avoid_: Order, command

### Tend

To be inside a village's territory, or to steer it remotely.

### Lapse

A player lord losing the title after not tending the village for too long.\
_Avoid_: Expiry

### Contest

A player's challenge for a sitting lord's title.

## Weather

### Weather field

The weather over the whole map at a moment, from which every front comes.\
_Avoid_: Weather map

### Front

One body of weather that forms, drifts across the map, and passes.\
_Avoid_: Storm, weather cell

### Weather values

The cloud cover, precipitation intensity, storminess, fog, and wind at a point.

### Weather label

The name for a range of weather values, such as Drizzle or Blizzard.\
_Avoid_: Weather type, weather state

### Local temperature

The temperature at a point: the season's temperature in its biome, adjusted for altitude and the time of day.

### Weather sign

Something in the sky or the wind that shows weather to come.\
_Avoid_: Forecast

### Weather override

An operator's timed change to the weather across the dimension.\
_Avoid_: Forced weather

### Snow cover

The snow lying on a column, in layers.

### Snow drift

Snow cover that the wind has heaped in the lee of an obstacle, up to 2 blocks deep.

### Wind

The moving air at a point: a mean speed and the direction it blows from.\
_Avoid_: Surface wind

### Steering flow

The large-scale wind, mostly west to east, that carries fronts across the map.\
_Avoid_: Prevailing wind, jet stream

### Front wind

The wind a front brings with it, growing with storminess.

### Gust

A brief rise of the wind above its mean speed.

### Backing

A wind direction turning counterclockwise, as ahead of a front.

### Veering

A wind direction turning clockwise, as after a front passes.

### Windiness

The season curve in a climate profile that scales the wind in its biomes.

### Exposure

How much the generated terrain speeds up or slows down the wind at a position.

### Wind shelter

How much the blocks upwind of an entity or block cut the wind.

### Sheltered wind

The wind at an entity or block after wind shelter.

### Wind label

The name for a range of wind speeds, such as Breeze or Gale.\
_Avoid_: Wind force, Beaufort number

### Rain shadow

The drier lee of high terrain, where fronts have dropped their precipitation on the windward side.

## Body temperature

### Body temperature

The core temperature of a living mob, which drifts toward the equilibrium its felt temperature sets.\
_Avoid_: Heat, warmth

### Felt temperature

The local temperature as a body feels it, after sun, wind chill, wetness, exertion, heat sources, food and drink, depth, and water.\
_Avoid_: Ambient temperature

### Comfort band

The range of felt temperature in which a body stays at its normal temperature.

### Thermal profile

An entity type's data for body temperature: its normal temperature, comfort band, natural insulation, drift rate, and stage thresholds.

### Insulation

How much clothing, fur, or fleece widens the comfort band toward the cold, narrows it toward the heat, and slows the drift.

### Wetness

How wet a body is, from dry to soaked.

### Covered

Under no open sky.

### Enclosed

Inside a bounded space that the enclosure check finds within its volume cap.

### Room temperature

The temperature an enclosed space holds, which drifts toward the balance between its heat sources and its losses.

### Opening

A face of an enclosed space that loses heat much faster than a wall: an open or closed door-like block, or air with open sky above.\
_Avoid_: Leak, gap

### Heat source

A block or living entity that warms the felt temperature around it, or cools it, for a cold source.

### Cave temperature

The yearly average of the local temperature at a place, which felt temperature blends toward below the surface.

### Water temperature

The temperature a body in water feels instead of the air.

### Ectotherm

A species whose body temperature tracks its felt temperature, and whom the cold slows rather than hurts.\
_Avoid_: Cold-blooded

## Hunger

### Diet profile

An entity type's data for hunger: its diet type, what it can eat, the food groups it tracks, its stomach and energy capacity, its metabolic rate, and its stage thresholds.

### Diet type

What kind of eater a species is: grazer, browser, carnivore, or omnivore.

### Stomach

What a body has eaten and not yet digested, which limits how much more it can eat.\
_Avoid_: Saturation

### Energy

The store that digestion fills and metabolism drains, whose level sets every hunger stage but Stuffed.\
_Avoid_: Food bar, hunger points

### Food group

One of the six kinds of nourishment a diet needs: grain, protein, vegetables, fruit, dairy, or forage.\
_Avoid_: Nutrient

### Group level

How well a body is stocked with one food group, from 0 to 100%.

### Forage

The food group of grass and hay, which grazing animals need and humans can't digest.\
_Avoid_: Fodder

### Deficiency

A group level below 25%, whose effects grow as the level falls.

### Craving

The cue that marks a food carrying a group the body lacks.
