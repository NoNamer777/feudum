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
