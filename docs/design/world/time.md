# Time

How time passes in Feudum: the length and light of a day, the calendar, sleeping, and how players read and change the time. What runs on time, such as villager schedules, fatigue, and crop growth, has designs of its own that build on this page.

Times of day on this page are in-game hours on a 24-hour clock.

## The day

A full day lasts 40 real minutes by default, so one in-game hour lasts 100 real seconds. Server owners can change the length, as [Settings](#settings) describes.

Daylight follows the seasons, as it does in medieval Western Europe at around 50° north. It lasts 8 hours at midwinter, 12 at the equinoxes, and 16 at midsummer, changing a little each day. Noon always falls at 12:00, with daylight spread evenly around it. Dawn takes the 40 minutes before sunrise and dusk the 40 minutes after sunset, and night fills the rest.

At the default day length, the day divides like this:

| Day       | Sunrise | Sunset | Daylight | Dawn and dusk, each |   Night |
|:----------|--------:|-------:|---------:|--------------------:|--------:|
| Midwinter |   08:00 |  16:00 |  ~13 min |              ~1 min | ~24 min |
| Equinox   |   06:00 |  18:00 |  ~20 min |              ~1 min | ~18 min |
| Midsummer |   04:00 |  20:00 |  ~27 min |              ~1 min | ~11 min |

## The calendar

The year has four seasons, each of three months. A month has 8 days by default, which makes a year of 96 days, about 64 hours of play. Weeks have 4 days, so every month holds two weeks and starts on the first day of the week.

| Season | Months                                | Days of the year |
|:-------|:--------------------------------------|-----------------:|
| Spring | Early Spring, Mid Spring, Late Spring |          1 to 24 |
| Summer | Early Summer, Midsummer, Late Summer  |         25 to 48 |
| Autumn | Early Autumn, Mid Autumn, Late Autumn |         49 to 72 |
| Winter | Early Winter, Midwinter, Late Winter  |         73 to 96 |

The longest day falls in the middle of Midsummer and the shortest in the middle of Midwinter. The equinoxes fall in the middle of Mid Spring and Mid Autumn.

The days of the week are First Day, Second Day, Third Day, and Fourth Day. Years count from the world's creation, so a new world starts at dawn on First Day, 1 Early Spring, Year 1. A date reads as "Third Day, 7 Early Spring, Year 2".

What the seasons change beyond daylight belongs to [Seasons](https://github.com/NoNamer777/feudum/issues/212).

### The moon

The moon runs through its cycle once a month: it is new on the first day and full on the fifth. When the month length changes, each of its eight phases takes an eighth of the month. The moon has no effect of its own here; other designs may build on its phases.

## Sleeping

Players can sleep only at night, from sunset to sunrise. Whether storms allow sleep during the day belongs to [Weather](https://github.com/NoNamer777/feudum/issues/215).

### Speeding up the night

When enough players in the overworld lie in bed, time speeds up until sunrise. At full speed, a night passes in about 10 real seconds. By default, every player in the overworld has to be in bed. When a server sets a lower share, time speeds up as soon as that share sleeps, slowly at first and faster as more players join them, up to full speed when everyone sleeps.

The world itself does not tick faster: only the sky and the clock race ahead, and players who stay awake see them do so while everything around them runs at normal speed. Villages make up for the time they skipped through [catch-up](#time-a-village-misses).

When a sleeper gets up or gets hurt, or the sleeping share drops below the threshold, the speed-up stops where it reached. Time runs on normally from there, and nothing is rewound.

### Two sleeps and the watch

Feudum follows the segmented sleep historians have found in pre-industrial Europe: people slept in two parts, waking around midnight for an hour or so in between. Everyone who sleeps wakes at midnight for the watch, which lasts one in-game hour. A player who lies down again sleeps on to sunrise, skipping the watch, and so does a player who goes to bed after midnight.

Villagers keep the watch. What they do during it belongs to [Villager schedules](https://github.com/NoNamer777/feudum/issues/214).

### Fatigue

Players, villagers, and animals tire, and sleep is how they recover. Fatigue keeps running through time that sleeping or catch-up skips, as if that time had played out. A player who sleeps while others stay awake still recovers, even though time does not speed up. How fatigue builds and what it does belongs to [Fatigue](https://github.com/NoNamer777/feudum/issues/213).

## Telling the time

Players tell the time with one of two items they hold, both from Feudum's [era](../setting/era.md):

| Item           | Shows             | Works                  |
|:---------------|:------------------|:-----------------------|
| Pocket sundial | The time          | From sunrise to sunset |
| Astrolabe      | The time and date | At any hour            |

Both read the sun or the stars, so they work only under open sky: under a roof or underground, neither gives a reading. Whether clouds and storms block one belongs to [Weather](https://github.com/NoNamer777/feudum/issues/215). They show the time in equal hours on a 24-hour clock, as astronomers counted them.

The management screen of a village also shows the date. Nothing else on screen shows the time or date.

## Changing the time

Time runs at one speed for everyone, with no controls to pause it or speed it up. Sleeping is the only way to skip ahead.

Operators manage time with the `/feudum time` command:

| Subcommand | Effect                                 |
|:-----------|:---------------------------------------|
| `query`    | Shows the time and date.               |
| `set`      | Sets the time of day or the date.      |
| `add`      | Moves the clock forward by a duration. |
| `freeze`   | Stops the clock.                       |
| `unfreeze` | Starts the clock again.                |

Moving the clock forward counts as time passed, so villages catch up on it. Moving it back changes only the clock and the date; villages are not rewound.

Vanilla's `/time` command is removed, and the `doDaylightCycle` and `playersSleepingPercentage` game rules have no effect. Feudum's command and [settings](#settings) take their place.

## Time a village misses

The world clock runs for the whole world while the server runs. A village misses time when no player is near enough to keep it loaded, while players sleep through the night, and when an operator moves the clock forward. Each time, the village catches up on what it missed rather than the world ticking faster. How it catches up belongs to [Village catch-up](https://github.com/NoNamer777/feudum/issues/216).

## Settings

| Setting        | Default                       |
|:---------------|:------------------------------|
| Day length     | 40 real minutes               |
| Days per month | 8                             |
| Sleeping share | Every player in the overworld |

Days per month must be a multiple of 4, so every month holds whole weeks and starts on First Day.

Changing a setting on an existing world makes nothing jump. The time of day keeps its place in the day, so noon stays noon. The date keeps its month, and the day of the month scales to the new month length: day 4 of 8 becomes day 6 of 12.
