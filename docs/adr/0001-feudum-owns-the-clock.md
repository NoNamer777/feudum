# Feudum owns the clock

Feudum keeps its own clock, a day count plus the fraction of the current day, and derives vanilla `dayTime` from it with the `doDaylightCycle` gamerule locked off. Building on vanilla `dayTime` would have been simpler, but it advances one unit per server tick, so a longer day and the sleep speed-up would need workarounds. On top of that, `/time set` would corrupt the calendar, and changing the day length would move the date. Owning the clock means Feudum must replace `/time` and keep `dayTime` in step with its own count.
