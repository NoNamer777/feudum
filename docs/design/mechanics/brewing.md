# Brewing

A village drinks what it brews. Grain is steeped, sprouted, and kilned into malt for a week before it is mashed into ale, and the second running of the same mash gives the small beer that children and laborers drink all day. Apples and pears are milled and pressed for cider and perry, grapes are trodden for wine, and honey ferments into mead. Fermenting makes a drink clean, so ale is safer than the water it was brewed from. Ale sours within days, so the brewing never stops, and barm skimmed from one batch starts the next. Drink also makes a body merry, then drunk, and a body that drinks hard every day comes to need it. Vanilla brewing makes magic potions, so Feudum replaces it.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Brewing makes ale, hopped beer, small beer, cider, perry, wine, rosé, fortified wine, mead, ciderkin, piquette, verjuice, and spirits.
- It starts where the ingredient is harvested. [Farming](farming.md#crops) grows barley, oats, wheat, hops, apple and pear orchards, and vineyards, and the climate profile of [Time](time.md#seasons-and-climate) limits where grapes grow. [World generation](../world-generation/README.md) places crab apples, wild hops, and the gruit herbs bog myrtle and yarrow. Honey comes from [Beekeeping](https://github.com/NoNamer777/feudum/issues/128), and from wild hives until that design lands.
- It ends at the drink in a cask, jug, or cup, and at drunkenness and its aftermath in the body that drinks it.
- Every historical step of the craft is its own step here, and each takes about as long as it did.
- Drinks carry a strength but no quality: every drink of a kind is the same until [Drink quality](https://github.com/NoNamer777/feudum/issues/130) lands.

## Working

- A hand step is done at its block by holding the use key, as in [Textiles](textiles.md#working). Work advances by the Feudum time that passed, and stopping keeps what is done.
- A waiting step is a placed block that keeps its own progress, as [Waiting steps](#waiting-steps) describes.
- Villagers work the same blocks at the same rate. Household ale is work any villager does. [Brewer](https://github.com/NoNamer777/feudum/issues/131), [Vintner](https://github.com/NoNamer777/feudum/issues/132), and [Distiller](https://github.com/NoNamer777/feudum/issues/133) are trades: the brewer makes ale and beer at scale, the vintner wine, cider, perry, and mead, and the distiller spirits.
- [Tools and blocks](#tools-and-blocks) lists what each step needs.

## Drinks and inputs

The diagram maps each ingredient to the drinks it yields, and shows where a chain branches. Each arrow stands for its main step and skips the rest, which the sections below list. Unlabeled arrows into a drink are fermenting. Ingredients have a light fill, drinks are bold, and pomace, a byproduct, is gray. Below the dashed line, distilling turns any fermented drink into spirit.

![Each ingredient and the drinks it yields. Grain is malted, and the malt is mashed into strong wort and mashed again into second wort. Strong wort ferments into ale, or is boiled with hops into hopped beer, and second wort ferments into small beer. Pears and apples are milled and pressed into juice, which ferments into perry and cider. Pressing apples and grapes leaves pomace, which is soaked and pressed again into ciderkin and piquette. Grapes are trodden into must, which ferments into red wine, rosé, and white wine, and any wine with aqua vitae added becomes fortified wine. Unripe grapes are pressed into verjuice. Honey mixed with water ferments into mead. Any fermented drink is distilled into low wines and distilled again into spirit, and cider or perry left to freeze, with the ice removed, becomes freeze-distilled cider or perry.](images/brewing-drinks.svg)

## Malt

Barley, oats, and wheat all malt. Barley gives the most wort per measure of malt.

| Step  | What happens                                                          | Takes          |
|:------|:----------------------------------------------------------------------|:---------------|
| Steep | Soaking the grain in a tun of water.                                  | About 2 days   |
| Couch | Spreading the wet grain on the malting floor to sprout, turned daily. | About 5–7 days |
| Kiln  | Drying the sprouted grain over a fire in the malt kiln.               | About 1 day    |

- Turning the couch is the hand step. Each day it misses loses some of the malt to mold.
- Steeping and kilning are waiting steps. The kiln burns fuel, as [Fire](fire.md#contained-fires) decides.
- Dried malt keeps for months.

## Ale and beer

| Step       | What happens                                                                 | Yields                   |
|:-----------|:-----------------------------------------------------------------------------|:-------------------------|
| Mill       | Grinding malt on a quern or at a mill.                                       | Ground malt              |
| Mash       | Steeping ground malt in hot water in the mash tun.                           | Mash                     |
| Run off    | Drawing the first running from the mash.                                     | Strong wort              |
| Mash again | Adding fresh hot water to the same mash and drawing the second running.      | Second wort, spent grain |
| Boil       | For hopped beer only: boiling strong wort with hops for about a Feudum hour. | Hopped wort              |
| Ferment    | Pitching barm into the cooled wort in the fermenting tun.                    | Ale, beer, small beer    |
| Condition  | For hopped beer only: resting the beer in a sealed cask.                     | Hopped beer              |

- One mash yields strong wort for ale or hopped beer and second wort for small beer (the parti-gyle method). A third running gives nothing worth brewing.
- Ale needs no boil: the heat of mashing is enough. Hopped beer boils in the heated cauldron of [Cooking](cooking.md).
- Gruit herbs go into the mash or the fermenting tun, and ale brewed with them is still ale. Gruit doubles how long ale keeps, far less than hops do.
- Malt is ground on whatever grinds grain: the quern of [Foods](https://github.com/NoNamer777/feudum/issues/51), a [Watermill](https://github.com/NoNamer777/feudum/issues/67), or a [Windmill](https://github.com/NoNamer777/feudum/issues/56).

## Cider and perry

- Apples and pears are crushed in the fruit mill and the pulp is pressed for juice, which ferments in a fermenting tun or a cask.
- Pressing leaves pomace. Apple pomace soaked in water and pressed again gives ciderkin, a weak drink for the household.
- Fruit carries wild yeast on its skin, so juice ferments well without barm.

## Wine

- Grapes are trodden in the treading vat into must: juice, skins, and seeds.
- **Red wine** ferments on its skins for about a week, then the must is pressed and the wine ferments on without them.
- **White wine** is pressed at once and ferments as juice alone.
- **Rosé** is red grapes left on their skins for about a day, then pressed and fermented as white wine.
- **Fortified wine** is wine of any color with aqua vitae added. Added while the wine still ferments, it stops fermentation and leaves a sweet fortified wine; added to finished wine, it gives a dry one. It keeps its base wine's color.
- **Verjuice** is the juice of unripe grapes, pressed but never fermented, and sour enough to keep about as long as cider. Cooking uses it.
- Grape pomace, soaked and pressed again, gives piquette, the small beer of wine.
- Grapes, like other fruit, carry wild yeast, so must needs no barm.

## Mead

- Honey mixed with water in the fermenting tun ferments into mead over about a season.
- Mead starts from barm, as wort does.

## Yeast

- Fermentation starts from barm, the yeasty froth skimmed from a fermenting batch and kept to pitch the next.
- Wort or honey without barm ferments only by spontaneous fermentation: slower, and more likely to sour. Fruit juice and must carry their own wild yeast and need no barm.
- Barm goes stale after a few Feudum days, so a village keeps brewing to keep its yeast. Cooking uses barm to leaven bread.

## Fermentation

- Fermentation speed follows the temperature where the vessel stands: the [room temperature](body-temperature.md#shelter-and-heat) of Body temperature indoors, and the [local temperature](weather.md#local-temperature) of Weather outdoors.
- Too cold stalls it, and too hot speeds it but raises the chance that the batch sours. Ale ferments best in a cool room, which makes spring and autumn the brewing seasons and a cellar a good place to brew.
- A finished fermentation clears all foulness, whatever water went into it, so a village can make foul water safe to drink. Salinity carries through unchanged, so ale brewed with seawater is salty.
- Unfermented wort and juice keep the foulness and salinity of their inputs.
- Every temperature limit is a starting value to tune.

## Distilling

- The alembic distills any fermented drink. A first run gives low wines, and a second run of low wines gives spirit, named after its source: aqua vitae from wine, grain spirit from ale or beer, cider brandy, perry brandy, and mead spirit.
- Each run takes a few Feudum hours over a hearth and burns fuel. The volume drops sharply: about 10 parts of wine give 1 part of spirit.
- Lees go into the alembic along with the wine.
- **Freeze distilling**: cider or perry left in a cask through a frost, with the ice removed, becomes freeze-distilled cider or perry. It is cruder than the alembic, and only works when the weather is cold enough.
- A spirit counts as an antiseptic, which [Bandage, splint, and salve](https://github.com/NoNamer777/feudum/issues/125) can use to clean wounds. That design decides what it does.

## Strength and nourishment

Each kind of drink carries a fixed alcohol amount, so a player learns what each drink does. The food component of [Hunger](hunger.md#food) also gives each drink its water, energy, and food groups. Starting values to tune:

| Drink                           | Alcohol | Water          | Nourishment        |
|:--------------------------------|--------:|:---------------|:-------------------|
| Small beer                      |     ~2% | Almost full    | Some energy, grain |
| Ciderkin, piquette              |     ~2% | Almost full    | A little fruit     |
| Ale, hopped beer                |   ~4–6% | Almost full    | Energy, grain      |
| Cider, perry                    |   ~4–6% | Almost full    | Some fruit         |
| Wine, rosé                      | ~10–12% | About half     | A little fruit     |
| Mead                            | ~10–12% | About half     | Energy             |
| Freeze-distilled cider or perry |    ~15% | Less than half | A little fruit     |
| Fortified wine                  |    ~18% | Little         | A little fruit     |
| Low wines                       |    ~25% | None           | None               |
| Spirit                          |    ~50% | None           | None               |

- The water amount of a drink falls as its alcohol amount rises. No drink drains hydration.
- Ale is liquid bread: a peasant's daily ale supplies a share of their energy and grain.
- The alcohol amount also speeds the filling of the bladder, as [Relief](relief.md#food) describes.

## Keeping and souring

Brewing owns how its drinks keep, since the rules come from fermentation: hops, a sealed cask, and air. Starting values to tune:

| Drink                                    | Keeps sealed   | Keeps once opened |
|:-----------------------------------------|:---------------|:------------------|
| Ale, small beer, ciderkin, piquette      | A few days     | A few days        |
| Ale with gruit                           | About a week   | About a week      |
| Hopped beer                              | About a season | A few days        |
| Cider, perry, wine, rosé, mead, verjuice | About a year   | A few days        |
| Fortified wine                           | Years          | A few weeks       |
| Spirits, low wines                       | Forever        | Forever           |

- Cold slows souring and heat speeds it. [Food preservation](food-preservation.md#cold-storage) owns the cellar, and Brewing reads its temperature.
- Soured ale, beer, and small beer become sour ale: still drinkable, with no cue of spoilage beyond its name and taste.
- Soured cider, perry, wine, and mead become vinegar, which Food preservation uses for pickling and Cooking uses too.
- A drink counts as opened once its cask is unsealed or it is drawn into a jug or cup. [Drink containers](https://github.com/NoNamer777/feudum/issues/49) owns the casks, jugs, and cups.

## Byproducts and waste

| Byproduct   | From                                | Use                                            |
|:------------|:------------------------------------|:-----------------------------------------------|
| Spent grain | Mashing                             | Livestock feed, with forage and grain.         |
| Barm        | Fermenting wort                     | Pitching the next batch, and leavening bread.  |
| Pomace      | Pressing apples and grapes          | Ciderkin and piquette, then pig feed.          |
| Lees        | Fermenting wine                     | Distilled with the wine, or poured out.        |
| Vinegar     | Soured cider, perry, wine, and mead | Pickling under Food preservation, and Cooking. |
| Spent wash  | Distilling                          | None; poured out.                              |

- Spent wash, poured-out lees, and dumped sour ale are mild [fouling sources](fluids.md#fouling).
- Spent grain and pomace are feed, not waste, under [Hunger](hunger.md).

## Pace

Starting values in Feudum days:

| Drink            | Hand work                                 | Waiting                                          |
|:-----------------|:------------------------------------------|:-------------------------------------------------|
| Malt             | Turning the couch daily                   | Steep 2, couch 5–7, kiln 1                       |
| Ale, small beer  | Mill, mash, and run off: about ½ day      | Ferment 2–3                                      |
| Hopped beer      | As ale, plus the boil                     | Ferment about 1 week, condition about 1 week     |
| Cider, perry     | Mill and press: about ½ day               | Ferment about 3 weeks                            |
| White wine, rosé | Tread and press: about ½ day              | Ferment about 2 weeks, settle about 1 sub-season |
| Red wine         | Tread: about ¼ day; press after the skins | 1 week on the skins, then as white wine          |
| Mead             | Mix honey and water: about ¼ day          | Ferment about 1 season                           |
| Spirit           | Tend the alembic: a few hours per run     | None                                             |

- At the default day length of [Time](time.md), ale takes about 2 Feudum weeks from grain to cup, most of it malting: about 9 hours of play.
- Every value is a starting value to tune.

## Drunkenness

### Scope

- Every body whose diet profile carries a thirst block can get drunk, through the alcohol tolerance that [Diet profiles](#diet-profiles) adds to that block. Animals only get drunk when they eat or drink something that carries alcohol, such as spent grain or rotting windfall fruit.
- A per-world setting sets how harsh drunkenness is for every entity: `off` (drink has no effect on the body), `mild` (effects but never lethal), or `harsh` (alcohol poisoning and delirium can kill). The default is `harsh`. It is separate from the hunger, thirst, relief, and body temperature settings.
- Creative and spectator players are exempt.

### Model

- A body carries an alcohol level, a hangover, a tolerance, and a dependence.
- **Alcohol level**: alcohol in the [stomach](hunger.md#model) absorbs into the alcohol level over about one Feudum hour, as water absorbs into [hydration](thirst.md#model). Food in the stomach slows absorption, so drinking on an empty stomach hits harder.
- The body clears its alcohol level at a steady rate from its diet profile. Drinking faster than the body clears it raises the level, and the stage follows the level.
- The stomach keeps absorbing after a body passes out, so the level of a deep enough binge keeps rising while the body lies unconscious.
- Drunkenness advances by the Feudum time that passed, so it follows the day length and the sleep speed-up.

### Stages

The stages follow the alcohol level. Thresholds come from the diet profile, scaled by the body's tolerance. For a human at base tolerance:

| Stage      | Roughly reached                     | Effects                                                                                             |
|:-----------|:------------------------------------|:----------------------------------------------------------------------------------------------------|
| Sober      | Nothing to drink                    | None.                                                                                               |
| Merry      | 1 to 2 jugs of ale                  | Cues only.                                                                                          |
| Drunk      | 3 to 4 jugs                         | Swaying view, poorer aim, slightly slower work.                                                     |
| Staggering | 6 or more jugs                      | Unsteady movement that drifts off course, no sprinting, much slower work.                           |
| Stupor     | Far beyond, or a few cups of spirit | Passes out: [Unconscious](health.md#downed-and-unconscious) until the level falls below Staggering. |
| Poisoned   | Beyond Stupor, under `harsh`        | Periodic damage while the level stays above the threshold.                                          |

- Work covers mining, chopping, and attacking, as in Body temperature.
- Under `mild`, Poisoned deals no damage.
- Effects apply as Feudum attribute modifiers, never as mob effects, so no icon shows in the inventory. Modifiers of the same kind as those of other mechanics take the strongest, under the [rule](health.md#modifiers) of Health.
- Feudum's own alcohol poisoning damage type carries its own death message.

### Cold and pain

- Drink makes the cold feel milder while the body loses heat faster: the alcohol level adds a warming offset to [felt temperature](body-temperature.md#felt-temperature) and speeds the drift of body temperature toward the cold, so a drunk asleep in the snow freezes. Body temperature owns both values, and Brewing feeds it the alcohol level.
- While Merry or Drunk, the slowness of [damaged pools](health.md#damaged-pools) is a little weaker.
- Drink gives no combat bonus. [Villagers](https://github.com/NoNamer777/feudum/issues/46) decides what drink does to a villager's mood.

### Hangover

- A body that reached Drunk or worse is left with a hangover once its level falls back to Sober.
- A hangover lasts about half a Feudum day, longer the further past Drunk the body went.
- It speeds the thirst drain and slows work slightly.
- Time cures it, and drinking water and sleeping shorten it.

### Tolerance

- Each Feudum day a body reaches Drunk or worse raises its tolerance a little, up to about 1.5 times the base tolerance of its profile.
- Tolerance drifts back toward the base over about 2 Feudum weeks without heavy drinking.
- Tolerance scales every stage threshold, Poisoned included, so a hardened drinker needs half again as much to get as drunk.

### Dependence

- Dependence runs from 0 to 1. It rises on each Feudum day the body reaches Drunk or worse, and falls slowly on days it doesn't. Drinking at Merry or below never builds it, so a peasant's daily ale is safe.
- About a week of daily drunkenness makes a body dependent.
- Dependence fades only while the body stays below Drunk. A full recovery takes about 2 Feudum weeks, with withdrawal at its worst early on.

### Withdrawal

A dependent body whose alcohol level falls to Sober goes into withdrawal:

| Stage    | Reached                                 | Effects                                                                         |
|:---------|:----------------------------------------|:--------------------------------------------------------------------------------|
| Craving  | Some hours sober                        | Cues only.                                                                      |
| Shakes   | About half a day sober                  | Shaking hands: poorer aim and slower work, no [healing](health.md#healing).     |
| Delirium | About a day sober, if heavily dependent | Heavy slowness, hallucinated sounds and shapes; under `harsh`, periodic damage. |

- Drinking to Merry or beyond ends withdrawal at once but keeps the dependence. Merry takes a jug or two.
- Tapering, drinking to Merry to stave off the shakes, keeps the body below Drunk, so dependence still fades. It is the slower, safe path out, and stopping outright is the fast, risky one.
- Under `mild`, Delirium deals no damage.
- Feudum's own delirium damage type carries its own death message.

## Cues

- Players read their own state from body cues, never from a meter.
- **Merry**: a warm tint and hiccups.
- **Drunk**: a swaying view.
- **Staggering**: a strong sway and double vision.
- **Hangover**: a pounding heartbeat and a slightly washed-out view.
- **Craving**: drinks show "Craved" in their tooltip, as craved food does.
- **Shakes**: the held item trembles.
- **Delirium**: hallucinated sounds and shapes at the edge of the view.
- Mobs and villagers stagger and hiccup, so a player can spot a drunk at a glance.

## Diet profiles

- The thirst block of the [diet profile](hunger.md#diet-profiles) also carries the alcohol tolerance, the clearance rate, the stage thresholds, and a dependence flag, so drunkenness needs no profile of its own.
- The dependence flag lets a profile opt out of tolerance, dependence, and withdrawal. Animal profiles opt out by default, since they never drink often enough.
- Villagers use the human profile, the same as players. Villagers decides how a dependent villager behaves.

## Waiting steps

- These steps are placed blocks that keep their own progress: the steeping tun, the malting floor, the malt kiln, the fermenting tun, and a cask that conditions, keeps, or freezes its drink.
- Each reads its temperature from Body temperature and Weather.
- Each catches up on the elapsed time when its chunk loads, as [Fluids](fluids.md#unloaded-chunks) does.
- Picking one up returns the item with its progress saved.

## Tools and blocks

| Step                    | Block                                                                                     |
|:------------------------|:------------------------------------------------------------------------------------------|
| Steep                   | Steeping tun                                                                              |
| Couch                   | Malting floor                                                                             |
| Kiln                    | Malt kiln                                                                                 |
| Mill malt               | Quern, under [Foods](https://github.com/NoNamer777/feudum/issues/51); watermill; windmill |
| Mash and run off        | Mash tun                                                                                  |
| Boil                    | Heated cauldron, under [Cooking](cooking.md)                                              |
| Ferment                 | Fermenting tun                                                                            |
| Condition, keep, freeze | Cask, under [Drink containers](https://github.com/NoNamer777/feudum/issues/49)            |
| Mill fruit              | Fruit mill                                                                                |
| Press                   | Press                                                                                     |
| Tread                   | Treading vat                                                                              |
| Distill                 | Alembic                                                                                   |

- [Smithing](https://github.com/NoNamer777/feudum/issues/86) makes the copper of the alembic.

## Vanilla content

- The brewing stand, every potion (drinkable, splash, and lingering), and tipped arrows stay hidden. Potions and magical drinks wait for [Magic](https://github.com/NoNamer777/feudum/issues/129).
- Nether wart, blaze powder, and the potion-only ingredients stay hidden: fermented spider eye, glistering melon slice, magma cream, rabbit's foot, ghast tear, phantom membrane, and dragon's breath.
- Every other vanilla item that applies a mob effect stays hidden too: golden apples, enchanted golden apples, golden carrots, suspicious stew, and the honey bottle.
- Every vanilla recipe and loot table that used these items moves to the design that owns its output, or drops them.

## Persistence

- Every drink item and block saves its kind, step, fermentation progress, and remaining keeping time.
- Every waiting-step block saves its progress and the time it last caught up.
- A player's alcohol level, hangover, tolerance, and dependence save with the player. Logging back in resumes from the saved values, since a player's absence is not simulated.
- A new player starts Sober, at base tolerance, with no dependence.
- Respawning clears the alcohol level and the hangover, but tolerance and dependence stay, so dying never cures a dependence.
- Wild mobs in unloaded chunks are not simulated. When their chunk loads, each starts Sober.
- Village simulation brings the villagers of an unloaded village forward, as [Boundaries](#boundaries) describes.

## Query

- One query returns the brewing state of an item or block: drink kind, step reached, fermentation progress, and remaining keeping time.
- One query returns an entity's alcohol in the stomach, alcohol level, stage, hangover, tolerance, dependence, and withdrawal stage.
- Other mechanics read brewing and drunkenness through these queries.

## Commands

- `/feudum brewing query <pos|entity|entity slot>` shows the result of the query.
- `/feudum brewing set <pos|entity slot> <progress|keeping> <value>` sets the state of a drink, and `/feudum brewing set <entity> <alcohol|tolerance|dependence> <value>` the state of a body, for testing.
- Every `/feudum brewing` command requires operator permission.

## Boundaries

Brewing owns malting, brewing, pressing, treading, fermenting, and distilling, every drink it makes, their strength, nourishment, and keeping, barm, the byproducts and waste of each step, and the blocks of the craft. It also owns drunkenness: the alcohol level, its stages and effects, hangovers, tolerance, dependence, withdrawal, and their cues. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Hunger](hunger.md)**: the stomach, food components, and diet profiles that Brewing extends.
- **[Thirst](thirst.md)**: hydration, the thirst block of diet profiles, and the alcohol amount that each drink carries.
- **[Relief](relief.md)**: the faster filling of the bladder after drink.
- **[Body temperature](body-temperature.md)**: room temperature, and how the alcohol level warms felt temperature and speeds the drift toward the cold.
- **[Health](health.md)**: the Unconscious state of Stupor, injuries, healing, and the rule that modifiers of the same kind take the strongest.
- **[Fluids](fluids.md)**: the foulness and salinity of water, and fouling sources.
- **[Weather](weather.md)**: the local temperature and the frost of freeze distilling.
- **[Time](time.md)**: climate profiles that limit where grapes grow.
- **[Farming](farming.md)**: grain, hops, orchards, and vineyards.
- **[Beekeeping](https://github.com/NoNamer777/feudum/issues/128)**: honey.
- **[Cooking](cooking.md)**: the hearth, the heated cauldron, bread leavened with barm, and dishes with verjuice and vinegar.
- **[Foods](https://github.com/NoNamer777/feudum/issues/51)**: the quern, and windfall fruit.
- **[Food preservation](food-preservation.md)**: the cellar, and pickling with vinegar.
- **[Drink containers](https://github.com/NoNamer777/feudum/issues/49)**: casks, jugs, and cups.
- **[Watermill](https://github.com/NoNamer777/feudum/issues/67)** and **[Windmill](https://github.com/NoNamer777/feudum/issues/56)**: milling malt.
- **[Fire](fire.md)**: the fire under the alembic and the fuel of the kiln.
- **[Smithing](https://github.com/NoNamer777/feudum/issues/86)**: the copper alembic.
- **[Bandage, splint, and salve](https://github.com/NoNamer777/feudum/issues/125)**: what a spirit does as an antiseptic.
- **[Drink quality](https://github.com/NoNamer777/feudum/issues/130)**: whether drinks carry a quality.
- **[Magic](https://github.com/NoNamer777/feudum/issues/129)**: potions and magical drinks.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**: when and what a villager drinks, its mood, and how a dependent villager behaves.
- **[Village economy](https://github.com/NoNamer777/feudum/issues/44)** and **[Inns and taverns](https://github.com/NoNamer777/feudum/issues/74)**: selling drink.
- **[Realm laws](https://github.com/NoNamer777/feudum/issues/102)**: an assize of ale and rules against drunkenness.
- **[Village simulation](https://github.com/NoNamer777/feudum/issues/45)**: brewing and drunkenness while a village is unloaded.
- **[Brewer](https://github.com/NoNamer777/feudum/issues/131)**, **[Vintner](https://github.com/NoNamer777/feudum/issues/132)**, and **[Distiller](https://github.com/NoNamer777/feudum/issues/133)**: the trades of the craft.
