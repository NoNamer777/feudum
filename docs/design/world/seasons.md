# Seasons

What the seasons change in Feudum beyond daylight: the temperature, snow and ice, and the year of plants, animals, and villagers. [Time](time.md) sets the calendar and how daylight changes across the year. This page sets the seasonal signals and what each season changes; how plants, animals, and villagers work has designs of their own that build on it.

## Seasons everywhere

Every biome follows the same calendar and the same seasons, those of Western Europe at around 50° north. A biome changes only how strongly a season applies, through a temperature offset of its own: a highland biome runs colder and keeps its snow longer. Each biome's offset belongs to [Biomes](https://github.com/NoNamer777/feudum/issues/225), and whether Feudum adds regions with seasons of their own, such as a dry season, belongs to [Regions beyond Western Europe](https://github.com/NoNamer777/feudum/issues/231).

The seasons change a little each day, as daylight does, so nothing jumps when a new season starts.

Server owners cannot turn the seasons off or hold the world in one season, so every other design can count on them. The days-per-month [setting](time.md#settings) sets how long they last.

## Temperature

The world has an outdoor air temperature at every place and hour. It follows the season, the biome offset, the height, and the time of day. Snow, ice, and plants all read it.

The temperature is kept in degrees Celsius, and nothing on screen shows it: the thermometer came some 300 years after Feudum's [era](../setting/era.md). Players read it from the world instead, from frost, snow, and ice.

### Through the year and the day

The temperature follows daylight about half a month behind it, as real seasons lag the sun. The coldest days fall in the second half of Midwinter and the warmest in the second half of Midsummer. In a biome with no offset, a day in the coldest part of the year averages 1 °C, from -3 °C at night to 5 °C in the afternoon. A day in the warmest part averages 19 °C, from 13 °C at night to 25 °C in the afternoon. The temperature rises and falls smoothly between them, and each day is coldest just before sunrise and warmest in mid-afternoon. The table sums up those two extremes:

| Time of year            | Daily mean | Night low | Afternoon high |
|:------------------------|-----------:|----------:|---------------:|
| Coldest, late Midwinter |       1 °C |     -3 °C |           5 °C |
| Warmest, late Midsummer |      19 °C |     13 °C |          25 °C |

### Height

The air cools by 1 °C for every 150 blocks above sea level, the rate of real air when a block is taken as a meter. At vanilla heights that is under 2 °C, but [Terrain height](https://github.com/NoNamer777/feudum/issues/224) raises the build height. On peaks around 3,000 blocks up, snow lasts all year without a biome offset.

### What this page leaves to others

The yearly curve gives the same temperature on the same date every year. [Weather](https://github.com/NoNamer777/feudum/issues/215) adds the swings on top of it, such as cold snaps, warm spells, and mild cloudy nights, so first frosts and thaws fall on different days each year.

This page sets only the outdoor air temperature. How players, villagers, and animals feel cold and heat, and how shelter, hearths, and clothing keep them warm, belongs to [Body temperature](https://github.com/NoNamer777/feudum/issues/227).

## Snow and ice

Whether rain or snow falls belongs to [Weather](https://github.com/NoNamer777/feudum/issues/215). Precipitation falls as snow wherever the temperature is below 0 °C. Snow builds up on the ground and melts once the temperature rises above freezing. A roof keeps snow off what lies beneath it, as it keeps off rain.

Still water freezes over after a sustained frost, and its ice grows thicker the longer the frost lasts. Flowing water never freezes.

Spring has no fixed thaw date: snow and ice melt when the temperature allows. Highlands and colder biomes keep them longer.

### Land nobody keeps loaded

Land outside villages misses time while no player keeps it loaded. When such land loads again, its snow and ice jump to the state the date and temperature imply, rather than replaying the missed days. A player who returns in summer finds no winter snow left. How villages catch up belongs to [Village catch-up](https://github.com/NoNamer777/feudum/issues/216).

## Plants

Plants grow faster with warmth and longer days, and stop growing below about 5 °C. Hard frost kills plants that are not frost-hardy. Since growth follows the temperature rather than the calendar, plants in colder biomes and higher land start later in spring and stop earlier in autumn.

Sowing seasons follow from these rules, as in the three-field rotation of the era. Winter grains such as wheat and rye are sown in autumn, survive the winter, and ripen in summer. Spring crops such as barley, oats, peas, and beans are sown in spring and harvested in late summer. Wild plants keep the same year: flowers bloom in spring, berries and nuts ripen in autumn, and grass stops growing in winter.

Which plants exist and how they grow belongs to [Plants](https://github.com/NoNamer777/feudum/issues/226).

## Animals

Wild animals and livestock give birth in spring. Grazing follows plant growth, so through winter livestock live on stored fodder such as hay. Some wild animals grow scarce or dormant in winter.

Which animals exist and how they behave belongs to [Animals](https://github.com/NoNamer777/feudum/issues/228).

## Villagers

Villagers work through the farming year of the manor. They plow and sow in spring, make hay in early summer, and bring in the grain harvest in late summer. In autumn they sow the winter grain and slaughter the livestock they cannot feed through winter. In winter they thresh, craft, and make repairs indoors. The table sums up the year:

| Season | Work                                        |
|:-------|:--------------------------------------------|
| Spring | Plowing and sowing spring crops             |
| Summer | Haymaking early, the grain harvest late     |
| Autumn | Sowing winter grain, slaughtering livestock |
| Winter | Threshing, crafts, and repairs indoors      |

Their needs rise in winter: they eat from their stores and burn firewood for heat. How their days run belongs to [Villager schedules](https://github.com/NoNamer777/feudum/issues/214), what they need to [Villager needs](https://github.com/NoNamer777/feudum/issues/229), and the feast days of their year to [Feast days](https://github.com/NoNamer777/feudum/issues/230).

## How seasons look

Players read the season mostly by looking. Grass and foliage change color through the year. Deciduous trees turn in autumn and stand bare in winter, and snow and ice show on the ground and on water.
