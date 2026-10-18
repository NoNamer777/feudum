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

How wet a body or a garment is, from dry to soaked. A body's wetness is that of the skin under its clothing.

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

An entity type's data for hunger: its diet type, what it can eat, the food groups it tracks, its stomach and energy capacity, its metabolic rate, and its stage thresholds. An optional thirst block holds its data for thirst.

### Diet type

What kind of eater a species is: grazer, browser, carnivore, or omnivore.

### Stomach

What a body has eaten or drunk and not yet digested or absorbed, which limits how much more it can take in.\
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

## Thirst

### Hydration

The store that drinks absorb into and metabolism drains, whose level sets every thirst stage.\
_Avoid_: Thirst bar, water level

### Salt load

The salt a body carries from seawater and salted food, which raises the drain until clean water flushes it.

### Foul load

What a body carries from foul water, which fades over days and which Illness reads.

### Salinity

How salty a water block or the contents of a container are: 0 for fresh water, 1 for seawater, and higher for brine.

### Foulness

How foul a water block or the contents of a container are, from 0 for clean water to 1.

### Foul water

Water with a foulness above 0, such as swamp water or a pond fouled by livestock.

## Fluids

### Volume

The liters of water a block holds, up to 1000.\
_Avoid_: Level, fluid amount

### Settling

Water whose surface has leveled out going still until a change nearby wakes it.\
_Avoid_: Sleeping

### Wet ground

Water below the minimum volume, which shows as damp ground and doesn't flow.\
_Avoid_: Film, puddle

### Current

The direction and speed at which river water moves, set by its discharge and channel.\
_Avoid_: Flow

### Discharge

The liters per hour a river segment carries, from its tributaries and catchment.\
_Avoid_: Flow rate

### Catchment

The land whose rain and melt drain into a river segment.\
_Avoid_: Watershed, basin

### Infiltration

Rain soaking into the ground, up to a rate that depends on the block.\
_Avoid_: Absorption

### Water table

The depth below which the ground is full of water: a computed baseline plus the deviations stored where something touched the ground.\
_Avoid_: Groundwater level

### Brine

Water with a salinity above 1.\
_Avoid_: Saltwater

## Relief

### Bladder

The store that fills with the water a body passes off and empties when the body relieves.

### Bowels

The store that fills with the residue of digested food and empties when the body relieves.\
_Avoid_: Gut

### Residue

The share of a food that passes on to the bowels once digested.\
_Avoid_: Fiber

### Accident

A full store emptying where the body stands, under the `harsh` setting.

### Soiled

The state of a body after an accident, until it is washed.\
_Avoid_: Dirty, filthy

### Privy

A block that takes waste into its pit, or into the water under it.\
_Avoid_: Latrine, toilet, outhouse

### Waste

Night soil, dung, or manure, as a layer on the ground, an item, or the contents of a privy pit or dung heap.\
_Avoid_: Excrement, poop

### Night soil

The waste of humans.

### Dung

The waste of animals.

### Manure

The waste a dung heap has rotted, which Farming spreads on fields.\
_Avoid_: Compost, fertilizer

### Dung heap

A block that collects waste and straw bedding and rots them into manure.\
_Avoid_: Midden, compost heap

## Clothing

### Region

One of the five parts of a body that clothing covers: head, chest, legs, feet, or hands.

### Layer

One of the three depths at which a region is dressed, from the skin out: underlayer, clothing, and armor.

### Underlayer

The layer worn against the skin, such as a linen shirt or braies.\
_Avoid_: Underwear, base layer

### Cloak

The slot over every layer, and the garment that fills it, which covers chest and legs, and the head too when hooded.

### Garment

A wearable item of the underlayer, clothing, or cloak: a garment type made in a material.\
_Avoid_: Clothes item, outfit

### Garment type

The cut of a garment, such as a tunic or a hood, which sets its layer, regions, coverage, and thickness.

### Tattered

The state of a garment at zero durability, which keeps only a small share of its stats until mended.\
_Avoid_: Broken

### Tailor's bench

The block at which garments are sewn and quickly mended.
