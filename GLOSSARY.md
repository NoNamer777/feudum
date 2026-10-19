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

The yearly average of the local temperature at a place, which felt temperature and the room temperature of a cellar blend toward below the surface.

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

The slot over every layer, and the garment that fills it, which covers chest and legs, and the head too when its hood is up.

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

### Back slot

The slot that holds a slung shield, a slung bow, or a back quiver.

### Belt slot

The slot that holds a hip quiver or a sheathed weapon.\
_Avoid_: Hip slot

## Armor

### Armor piece

A wearable item of the armor layer or the helm slot: an armor type made in an armor material.\
_Avoid_: Armor item, gear

### Armor type

The cut of an armor piece, such as a hauberk or a great helm, which sets its slot, regions, and coverage.

### Armor material

What an armor piece is made of, such as iron mail or steel plate, which sets its protection, thermal stats, noise, weight, and durability.

### Helm

The slot over the armor layer of the head, and the open or great helm that fills it.\
_Avoid_: Helmet

### Damage kind

One of the three kinds of damage that protection reduces: cut, pierce, or blunt.\
_Avoid_: Damage type

### Protection

How much a garment or armor piece reduces the damage of each damage kind on the regions it covers.\
_Avoid_: Armor points, defense

### Struck region

The one region a hit lands on, whose worn layers alone protect against it.\
_Avoid_: Hit box, body part

### Chafed

The state of a region where armor rests on bare skin, which slows natural healing.

### Battered

The state of an armor piece, weapon, or shield at zero durability, which keeps only a small share of its stats until repaired.\
_Avoid_: Broken

### Rust

Durability that iron and steel lose while they stay wet.

### Oiled

The state of an iron or steel armor piece or weapon rubbed with tallow, which can't rust for about one week.

### Armorer's anvil

The block at which metal armor pieces are made and repaired.

### Leatherworker's bench

The block at which hardened leather is shaped, as for the hardened leather pieces of armor.

## Weapons

### Weapon

A held item made to attack with: a weapon type made in a weapon material.\
_Avoid_: Weapon item

### Weapon type

The make of a weapon, such as an arming sword or a poleaxe, which sets its grip, weight class, reach, attack speed, attack profile, traits, and parry protection.

### Weapon material

What a weapon is made of, such as bronze or steel, which sets its damage scale, flat penetration, sharpness, durability, and weight.

### Attack motion

One of the four ways an attack lands, read from the camera's turn: thrust, side swing, overhead, or rising.\
_Avoid_: Attack type, swing type

### Attack profile

The damage kind, damage scale, and penetration fraction of each attack motion of a held item.

### Penetration

How much of the protection on the struck region a hit ignores: a fraction from the attack motion, then a flat amount from the material.\
_Avoid_: Armor piercing

### Grip

Whether a weapon type is held in one hand, in two, or versatile, in either.\
_Avoid_: Handedness

### Weight class

Whether a weapon or shield type is light, medium, or heavy, which sets its attack or raise speed and whether it can be held in the off hand.

### Trait

A property of a weapon type, such as long reach, shield-breaker, or hook.

### Parry

Blocking with a weapon, which covers a narrow frontal arc with its parry protection.\
_Avoid_: Block

### Parry key

The key that raises a shield, or parries with a weapon when there is no shield.

### Raised

The position of a shield held up with the parry key, covering its regions against hits in its arc.

### Planted

The position of a pavise set on the ground, covering every region of a body behind it from the front.

### Shield bash

A weak blunt hit with a shield, which briefly knocks a raised shield or parry aside.

### Sharpness

How keen the edge or point of a weapon is, which drops with use and lowers its cut and pierce damage.\
_Avoid_: Edge durability

### Whetstone

The stone carried in the inventory that slowly restores sharpness.

### Grindstone

The block that quickly restores sharpness.

### Ammunition

What a ranged weapon shoots: a head type made in a head material, such as a steel bodkin.\
_Avoid_: Projectile

### Quiver

The container worn in the back or belt slot that holds about 24 arrows or bolts.

### Bowyer's bench

The block at which bows and crossbows are made and repaired.

### Fletcher's bench

The block at which arrows and bolts are put together.

## Realms

### Fealty

The bond under which a vassal manor is held of a liege manor.\
_Avoid_: Allegiance, vassalage

### Liege

The manor a manor is held of, or the lord of that manor.

### Vassal

A manor held of a liege manor, or the lord of that manor.

### Realm

The tree of manors under a root manor, joined by fealty.\
_Avoid_: Kingdom, nation

### Sovereign

The lord of a realm's root manor.\
_Avoid_: King, ruler

### Tribute

The share of what a manor takes in that it passes up to its liege manor.

### Felony

Contesting a manor above or below one of your own manors in a realm.

### Leave

The permission a contest within a realm needs from the lord of the nearest manor above both sides.

### Liege realm

The realm a lord with manors in several realms serves first when those realms clash.\
_Avoid_: Liege homage

### Rank

A manor's title, which follows the number of manors in its subtree.\
_Avoid_: Tier, peerage

## Textiles

### Bast fiber

Fiber from the stalk of flax, hemp, or nettle, which is retted, broken, scutched, and hackled before it is spun.

### Retting

Rotting stalks or bark, in water or on grass, until the fiber loosens from the woody core.

### Line

The long, fine fiber that hackling draws from a bast fiber, spun into fine yarn and thread.

### Tow

The short, coarse fiber that hackling leaves behind, spun into coarse yarn and twine.

### Shives

The woody bits of the stalk that scutching beats out.

### Skirtings

The soiled edges stripped from a fleece, which count as dung.

### Woolen

Yarn spun from carded wool, and the cloth woven from it, which is fulled before use.

### Worsted

Yarn spun from combed wool, and the smooth cloth woven from it, which needs no fulling.

### Fulling

Shrinking and thickening woolen cloth by treading it in water with fuller's earth or stale urine.\
_Avoid_: Felting

### Felt

Carded wool matted with hot water and pressure, without spinning or weaving.

### Cordage

Thread, twine, and rope, which replace vanilla string.\
_Avoid_: String

### Ropewalk

A rope jack and a traveler set apart on a straight run, between which rope is laid.

### Dyestuff

A plant or other source of a dye color, such as woad or madder.\
_Avoid_: Dye item

### Mordant

A substance that fixes a dyestuff in the fiber, such as alum or iron.\
_Avoid_: Fixative

### Shade

How deep a dyed color is: pale, mid, or deep.\
_Avoid_: Tint

### Overdyeing

Dyeing an item that already has a color, which mixes the two colors or deepens the shade.

### Fastness

How slowly a dyed color fades, set by its dyestuff, its mordant, and the stage it was dyed at.

### Stale urine

Urine aged in a closed lant tub, used to full cloth and to ferment a woad vat.\
_Avoid_: Lant

### Lant tub

The vessel that collects urine alone and ages it into stale urine.

### Waiting step

A step of the craft that a placed block works through over time, such as retting or tentering, rather than a body at a workstation.

### Wall hanging

A thin block of cloth hung on a wall face, which raises its insulation.

## Health

### Body profile

The data-driven definition of an entity type's pools, blood, healing, and whether it can be Downed.

### Pool

The hit points of one part of a body, such as the head or the left arm.\
_Avoid_: Body part, health bar, limb

### Vital pool

A pool that downs the body when it reaches 0: the head and chest of a human, or the head and body of an animal.

### Disabled

The state of a limb whose pool is at 0, which can't be used until it heals.

### Blood

What bleeding drains, separate from the pools. A body that loses too much faints, falls Unconscious, and dies.

### Injury

A condition on a pool that a hit can cause and treatment ends: bleeding, a fracture, a burn, or a concussion.\
_Avoid_: Wound, status effect

### Open wound

What a bandaged heavy bleed leaves until it heals, which Illness can infect.

### Downed

The state of a body whose vital pool is at 0: conscious and crawling, but unable to fight.\
_Avoid_: Knocked down, incapacitated

### Unconscious

The state of a body knocked out by a concussion or by blood loss, which can't move until it wakes.

### Weakened

The state of a Downed body that a helper got up before its vital pools reached 10%.

### Body panel

The panel of the inventory screen that names the state of each pool in words and lists its injuries.

### Body-condition modifier

A modifier that a need, Body temperature, drunkenness, Health, or Illness puts on an attribute, of which only the strongest on each attribute applies.

## Brewing

### Malt

Grain steeped, sprouted on the malting floor, and dried in a kiln, which is mashed to make wort.

### Wort

The sweet liquid drawn from a mash of malt, which ferments into ale, beer, or small beer.

### Small beer

The weak drink fermented from the second running of a mash, after the strong wort is drawn off.

### Gruit

Herbs such as bog myrtle and yarrow that flavor ale and help it keep a little longer.

### Must

Trodden grapes with their juice, skins, and seeds, which ferment into wine.

### Pomace

The pulp left after pressing apples or grapes, pressed again for ciderkin and piquette, then fed to pigs.

### Barm

The yeasty froth skimmed from a fermenting batch, kept to start the next and to leaven bread.\
_Avoid_: Yeast

### Low wines

The weak spirit of a first run through the alembic, distilled again into spirit.

### Spirit

A drink distilled twice in the alembic, such as aqua vitae from wine.\
_Avoid_: Liquor

### Alcohol level

How much alcohol a body has absorbed and not yet cleared, which sets its drunkenness stage.\
_Avoid_: Blood alcohol

### Hangover

The aftermath of reaching Drunk or worse, which speeds the thirst drain and slows work until it passes.

### Alcohol tolerance

How much drink a body takes to reach each drunkenness stage, set by its diet profile and raised by heavy drinking.

### Dependence

How much a body has come to need drink, built by days of drunkenness, which brings withdrawal once it sobers.

### Withdrawal

The stages a dependent body goes through once sober: Craving, Shakes, and Delirium.

## Food preservation

### Keeping time

How long an organic item lasts at 10 °C and dry before it rots, which runs down faster in warmth and wet.\
_Avoid_: Shelf life, freshness

### Spoilage stage

One of the four stages an organic item passes through as its keeping time runs down: Fresh, Stale, Spoiled, and Rotten.

### Rotten version

The item an organic item turns into once its keeping time runs out, such as rotten pork from pork, which never spoils further.\
_Avoid_: Rotten flesh

### Sealed

Of a container, such as a barrel or an earthenware crock: closed against rain, water, and vermin.

### Cellar

An enclosed room below the surface, whose room temperature settles toward the cave temperature.

### Ice house

An enclosed room kept near freezing by the ice or packed snow inside it.

### Dry salting

Curing meat or fish by layering it with salt in a barrel.

### Brining

Curing meat, fish, or vegetables by submerging them in strong brine, as for sauerkraut.

### Soaking

Steeping salted food in fresh water to draw out some of its salt before eating.

### Cold smoking

Preserving food on a smoking rack in an enclosed room with a smoldering fire, over days.

### Hot smoking

Cooking food on a smoking rack over an open hearth, which keeps it only a little longer.

### Stockfish

Cod dried unsalted in cold wind, which keeps for years.

### Potting

Preserving cooked meat in a crock sealed under a layer of fat.

## Animal husbandry

### Livestock

The domestic animals that a player, a manor, or a village holding owns and breeds.\
_Avoid_: Farm animals, mobs

### Livestock profile

An entity type's data for animal husbandry: its breeding season, gestation or incubation, litter or clutch, growth, lifespan, lactation, fleece, crowding area, draft fitness, trait ranges, breeds, and slaughter yields.

### Dam

The mother of a young animal, or a female kept to breed.

### Sire

The father of a young animal, or a male kept to breed.

### Breeding season

The part of the year in which a species comes in season, set by daylight.\
_Avoid_: Mating season, rut

### In season

Of a female: ready to conceive, which she shows by calling for the males.\
_Avoid_: In heat, love mode

### Trait

One of the five heritable values every animal carries: size, yield, hardiness, temperament, or color.\
_Avoid_: Gene, stat

### Breed

A data-driven set of trait ranges with a look and a home region, to which every animal whose traits fall within them belongs.

### Temperament

The trait that sets how far an animal flees, whether it fights back, and how readily it is led.\
_Avoid_: Tameness

### Castrate

To make a male unable to breed, which leaves an ox, wether, gelding, or capon that grows larger and calmer.\
_Avoid_: Neuter

### Lactation

The span after giving birth in which a dam gives milk, which milking can extend.

### Weaning

The age at which a young mammal stops suckling and eats by its diet profile.

### Broody

The state of a hen that sits on a clutch until it hatches, and lays no more meanwhile.

### Carcass

What an animal leaves when it dies, which rots in a few days unless it is butchered.\
_Avoid_: Corpse

### Butchering

Cutting a carcass up at a butcher's block into meat, hide, fat, and the rest of its yields.

### Tallow

Animal fat rendered in a heated cauldron, which oils iron and steel against rust.

### Pinfold

The village pound in which the Hayward holds strays until their owner pays to redeem them.\
_Avoid_: Pound

### Crowding

The state of an animal with less than its species' minimum area, which can't conceive and grows and yields more slowly.\
_Avoid_: Overcrowding

## Hygiene

### Dirt

The grime, mud, and bloodstain on a body or a garment, each from clean to filthy.\
_Avoid_: Cleanliness, hygiene level

### Grime

The dirt of sweat, dust, and soot, which builds with time and labor.

### Mud

The dirt of wet soil, half of which flakes off as it dries.

### Bloodstain

Blood on the skin or a garment, from bleeding, fighting, or butchering. Not the blood that bleeding drains.

### Smell

What a body gives off, derived from its grime, its bloodstain, the dirt of its worn garments, and Soiled, in the stages Fresh, Stale, Rank, and Foul.\
_Avoid_: Odor, stink

### Scent

How far a body's smell and bloodstain carry for animals and villagers to sense, farther downwind.

### Dirt block

The part of a diet profile that sets how a species gets dirty, and whether it wallows.

### Washbasin

A basin on a stand that holds 5 liters for a sponge bath.

### Wooden tub

A block that holds 300 liters, in which a body soaks.\
_Avoid_: Bathtub

### Stone bath

A pool of water lined on every side and below with bath stone.\
_Avoid_: Pool

### Bath furnace

A block set against a stone bath that heats its water while it burns fuel.

### Soak

Washing by sitting in a tub or a stone bath, which washes the body and every garment it wears.

### Lathered

The state of a body or garment rubbed with soft soap, until its next wash.

### Laundry

Washing a garment off the body, at open water, a tub, or a washbasin.

### Battledore

A wooden bat that halves the time of laundry.

### Clothesline

A line strung between two posts, on which garments and towels dry in the open air.

### Drying rack

A block on which garments and towels dry by the heat sources around it.

### Lye

The liquid leached from wood ash in a lye barrel, which is boiled into soft soap.

### Soft soap

Lye boiled with tallow or oil, which washes grime off in cold water.\
_Avoid_: Soap bar

### Curry brush

A tool that clears the mud and grime from an animal.

### Wallowing

A species rolling in mud while Overheated, since mud cools like wetness and dries slower.

## Illness

### Disease

A named, data-driven sickness with its hosts, symptoms, routes, spans, and immunity, such as the flux or murrain.\
_Avoid_: Status effect, infection

### Variant

A disease that inherits every value of another and overrides some, as bloody flux does for the flux.

### Turning

A disease at Grave becoming another, as wound rot becomes gangrene.

### Severity

How far a disease has gone in a body, from 0 to 100%, which its symptoms scale with.

### Incubating

The state of a body that carries a disease but shows no symptoms yet.

### Ailing

The stage of a disease below 33% severity for a human, with faint symptoms.

### Sick

The stage of a disease from 33% severity for a human, with strong symptoms and no healing.

### Grave

The stage of a disease from 66% severity for a human, which deals illness damage under `harsh`.

### Recovering

The state of a body whose disease has turned, while its severity falls back to 0.

### Immune

The state of a body that can't catch a disease again until its immunity span runs out.

### Care

How a sick body is kept: in bed, warm, fed, and watered, which turns its course sooner and speeds its recovery.

### Symptom

One effect of a disease that acts through an existing mechanic, such as fever, the flux, or weakness.

### Route

A way a disease passes to a body: the foul load, an open wound, breath, waste, touch, a shared thing, shared water, or a vector.

### Shared thing

A garment, bedding, drink container, bowl, or trough that carries the disease of the sick body that used it.

### Shared water

The route by which a disease passes between fish in the same water body, more readily the more crowded it is.

### Vector

An entity type that passes a disease to the bodies it bites or lives near, without falling sick itself, such as a flea.

### Carrier

A survivor of a disease that shows no symptoms but keeps spreading it, as some survivors of enteric fever do.

### Foul tolerance

How well a species shrugs off its foul load, set in the thirst block of its diet profile.

### Murrain

The name villagers give every plague of livestock, such as cattle plague or swine fever.

### Fish plague

A disease of fish, such as water mold, which strikes mostly crowded water.

### Tainted ground

Ground where an animal that died of anthrax lies or was buried, which infects grazing livestock for many years.

### Illness damage

The periodic damage to the chest of a body whose disease is Grave.

## Cooking

### Hearth

The open fire of a kitchen, with its spit, pot hook, trivet, and griddle, where food is roasted, fried, and set over the heat.

### Heated cauldron

A metal cauldron set over a hearth or a fire, which simmers dishes, boils water, and renders fat.\
_Avoid_: Pot, kettle

### Bake oven

A stone or clay oven fired with wood and then raked out, which bakes on its stored heat.

### Dish template

A data-driven pattern for a dish, such as pottage or pie, whose slots take ingredients from item tags and whose food component is computed from what goes in.\
_Avoid_: Recipe

### Serving

One portion of a cooked batch, about one good meal.

### Doneness

How far food on the heat has cooked: Raw, Cooked, or Burnt.

### Pottage

A thick dish of grain or peas and beans simmered with vegetables, herbs, and sometimes meat, the everyday meal of a household.

### Trencher

A thick slice of stale bread used as a plate, eaten with the meal or given to the poor or the dogs.

### Coffin

The pastry crust of a pie, which seals its filling.

### Manchet

Bread from white wheat flour, the finest kind.

### Maslin

Grain or bread of wheat and rye together.

### Sourdough starter

A piece of dough kept back from one batch to leaven the next, fed with flour to keep it alive.

### Rendering

Melting fat in the heated cauldron into tallow or lard.

## Fire

### Fuel load

How long a flammable block feeds a fire before it turns into its burnt form.

### Ignition threshold

How easily a flammable block catches fire.

### Burnt form

What a flammable block turns into once its fuel load runs out, such as air, charred timber, or burnt ground.

### Charred timber

The burnt form of logs and timber beams, which still stands but breaks fast and drops charcoal.

### Burnt ground

The burnt form of grass and planted dirt, which greens again over a few weeks.

### Fire size

How large a fire burns: Small, Medium, or Large, each hotter and faster than the last.

### Smoldering fire

A fire that gives much smoke and little heat, on green or damp fuel, on sawdust, under a cover of earth, or banked.

### Dryness

How dry a block is, computed from the recent weather and cover: Soaked, Damp, Dry, or Parched.\
_Avoid_: Flammability, moisture

### Green wood

Firewood freshly cut, which burns at a lower heat and with heavy smoke until it seasons.

### Seasoned wood

Firewood stored under cover for about a season, which burns hot and clean.

### Ember

A burning fragment the wind carries downwind across a gap, which sets alight the blocks it lands on.

### Spark

A burning fragment an open fire throws onto the flammable blocks within 2 blocks of it.

### Fire steel

A steel striker that, struck on flint over tinder, lights the tinder.\
_Avoid_: Flint and steel

### Tinder

Material that catches from a spark of the fire steel: char cloth, tinder fungus, dry grass, or shives.

### Char cloth

Linen charred in a closed tin in a fire, the readiest tinder.

### Brand

A stick lit at one fire to carry fire to another.

### Kindling

Fuel that catches fast and burns out fast, such as straw, shives, and dry grass, used to light larger fuel.

### Fireplace

A hearth set into a wall, which carries its smoke up a chimney.

### Open fire

A fire laid on the ground from fuel.\
_Avoid_: Campfire

### Contained fire

A fire that burns in a block made for it, such as a hearth, a fireplace, an open fire, or an oven.

### Banking

Covering a fire with ash at night so it smolders until morning and can be revived without striking a light.

### Ash pit

The part of a hearth, fireplace, or open fire where its ash builds up, which chokes the fire to Medium once full.

### Hearthstone

A stone laid under an open fire that stops its sparks.

### Fireguard

An iron screen set in front of an open fire that stops its sparks.

### Charcoal clamp

Wood stacked and covered with turf or earth, then lit, which smolders for days and chars the wood into charcoal.

### Room smoke

The smoke an enclosed space holds, fed by its fires and drained by its openings and smoke exits: Hazy, Smoky, or Choking.

### Smoke louver

A roof block that drains smoke and loses heat as half an opening does.

### Chimney

A stone flue from a fireplace to open sky, which drains smoke well and loses little heat.

## Farming

### Crop profile

The data-driven description of a crop: its growth stages, the ranges of temperature, soil moisture, and acidity it grows in, its frost tolerance, its nutrient demand, its seed rate, and its yield.

### Growth progress

How far a crop has grown, which builds up with Feudum time at a rate its growth conditions set.

### Growth conditions

The local temperature, soil moisture, nutrients and acidity, and daylight at a crop's block, which set how fast it grows.

### Ripe

The stage at which a crop gives its full yield and its seed sprouts.

### Overripe

The stage of a crop left in the field past Ripe, when grain sheds, fruit drops, and roots start to rot.

### Dormant

The state of a winter-sown crop through the cold, when it doesn't grow and survives hard frost.

### Frost tolerance

How much frost a crop survives: Tender, Hardy, or Winter-hardy.

### Dead stalks

What a crop turns into when stress kills it.

### Soil texture

The kind of ground of a column, generated from the seed: sand, loam, clay, or peat.\
_Avoid_: Soil type

### Soil moisture

How wet the soil is, computed from the recent weather, the drainage, and the water table: Waterlogged, Wet, Moist, Dry, or Parched.\
_Avoid_: Hydration, dryness

### Irrigation ditch

A trench of water that raises the soil moisture of the tilled soil near it.

### Tilled soil

Ground broken by a spade, mattock, ard, or plough, in which crops are sown.\
_Avoid_: Farmland

### Nutrient

One of the three things a crop draws from tilled soil: nitrogen, phosphorus, or potassium.\
_Avoid_: Fertility

### Leaching

The loss of nitrogen from bare tilled soil to the rain.

### Acidity

How sour tilled soil is, which sets how much of each nutrient a crop can draw: Sour, Neutral, or Sweet.

### Marl

A limy clay dug from marl pits and spread on fields to sweeten the soil.

### Fallow

Tilled soil left unsown for a season or more, so its nutrients recover.

### Ard

A light plough drawn by one draft animal, which scratches the soil rather than turning it.

### Heavy plough

A plough drawn by a team of oxen, which turns any soil, clay included.

### Harrow

A frame drawn over tilled soil to break the clods and cover sown seed.

### Headland

The strip at the end of a field where the plough turns.

### Broadcasting

Sowing by throwing seed from a seed basket over a patch of tilled soil.

### Setting

Sowing one block at a time, with a dibber or by hand.

### Seed rate

How much seed a block of a crop takes.

### Biennial

A crop that sets seed only in its 2nd year, after standing through a winter.

### Perennial

A crop that lives for years in its block and grows again each spring.

### Crown

The rootstock of a hop plant, which lives on from year to year and sends up bines.

### Bine

The climbing stem of a hop plant, cut at harvest.

### Weed

A plant that spreads onto tilled soil and takes nutrients and moisture from the crops around it.

### Lodging

Ripe grain flattened by the wind, which is slower to reap and loses part of its yield.

### Sheaf

A bundle of reaped stalks, bound to dry and to carry.

### Stook

Sheaves stood together in the field to dry.\
_Avoid_: Shock

### Threshing

Beating sheaves with a flail on a threshing floor, which gives grain, straw, and chaff.

### Winnowing

Tossing threshed grain in a draft, which carries the chaff away.

### Chaff

The husks winnowing separates from the grain, fed to livestock.

### Stubble

The stalks a reaped crop leaves standing in the field.

### Sward height

How tall the grass of a block stands, which grazing lowers and the season regrows.

### Meadow

Grassland kept for mowing into hay.

### Pasture

Grassland kept for grazing.

### Grafting

Joining a scion onto a rootstock, so the tree bears the scion's variety.

### Scion

A cutting from a tree of a known variety, grafted onto a rootstock.

### Rootstock

The young tree a scion is grafted onto, such as a crab apple seedling.

### Windfall

Fruit that drops from an overripe tree, and spoils.

## Fishing

### Water body

The unit whose fish breed, feed, and catch up together: a river segment, a lake basin, a pond of connected still water, or a chunk of sea water.

### Shoal

One mob that stands for a group of small schooling fish, carrying a count and an average weight, and rendered as that many fish swimming together._Avoid_: School

### Carrying capacity

The weight of fish a water body can feed, set by its size, depth, warmth, shallows, and cover.

### Oxygen

The breathable air dissolved in water, from 0 to 1, computed from its temperature, current, foulness, and ice cover.

### Spawning ground

The bottom a species lays its eggs on, such as gravel for salmon or weed for pike.

### Fry

Newly hatched fish, which rise from their clutch as a shoal.

### Run

The seasonal journey of a migratory species between the sea and its spawning ground, such as the salmon run in Autumn.

### Home river

The river a migratory fish hatched in, which it returns to when it runs.

### Barrier

A structure across the full width of a river, or a fall too high to leap, that stops a run.

### In transit

The state of a migrating fish that has crossed into an unloaded chunk, stored with its route until the chunk ahead loads.

### Fish kill

The death of the fish of a water body when its oxygen falls too low or its foulness rises too high.

### Shellfish bed

A block on the floor of shallow coastal water that holds mussels, oysters, cockles, or whelks at a density.

### Night line

A line with a few baited hooks, staked on the bank and left to fish on its own.

### Longline

A line with many baited hooks, set from a boat.

### Landing net

A small net on a hoop and pole that lands a heavy fish.

### Mesh

The size of the holes of a net, which sets the fish that slip through it.

### Cast net

A round net thrown over shallow water.

### Seine

A long net hauled through shallow water from the shore by a team.

### Drift net

A wall of net set from a boat at sea that hangs from the surface and catches shoal fish by the gills.

### Fish trap

A basket woven from withies and set in water, such as an eel trap or a crab pot.

### Fish weir

A structure of stakes and wattle in a river that steers fish into a trap or a pound.

### Pound

An enclosure at the end of a fish weir that holds the fish it steers in alive.

### Leister

A spear with several barbed prongs for fish.

### Keepnet

A net on the bank that keeps a catch alive in the water.

### Fish box

A box moored in the water that keeps a catch alive for market.

### Whole fish

A fish that has died out of water and waits to be gutted.

### Gutting

Opening a whole fish with a knife to take its flesh, offal, roe, liver, and bones.

### Fishpond

A still water body dug or dammed by a player or villager, stocked and drained by its keeper.\
_Avoid_: Stew pond

## Tanning

### Hide

The skin of a butchered mammal, as an item before it is tanned. As a class, the large hides of cattle, horses, water buffalo, and deer, apart from skins and pelts.

### Skin

The class of hide from smaller animals, such as calves, sheep, goats, and pigs, which every process but fur dressing can work.

### Pelt

The class of hide from rabbits and wild fur-bearers, which is dressed into fur.

### Prime

The state of a pelt taken from Late Autumn to Early Spring, when its fur is thick.

### Flint hide

A hide cured by air-drying on a stretching frame, which keeps about a year and is soaked soft before work.

### Fleshing beam

The block at which a hide is fleshed, unhaired, scudded, oiled, and staked.

### Fleshings

The flesh and fat scraped off a hide, which boil into hide glue.

### Liming

Laying a hide in a lime pit until its hair loosens.

### Bate

Dog or poultry dung in water, which draws the lime out of a hide and makes it supple.

### Pit

The block, dug into the ground and filled with water, that soaks, salts, limes, bates, tans, or taws hides by its contents.

### Tan pit

A pit of water and ground bark, in which hides lie in ooze for a season or a year.

### Ooze

The tannin steeped out of ground bark into the water of a tan pit.

### Re-layering

Restarting a tan pit with fresh ground bark once its strength has fallen.

### Tan

The spent bark taken out of a tan pit, which burns as fuel.

### Currying

Finishing a bark-tanned skin by shaving it, stuffing it with dubbin, and slicking it, into upper leather.

### Dubbin

Tallow melted with fish oil, which stuffs leather in currying.

### Sole leather

Bark-tanned leather from a hide, thick and stiff, for soles, belts, harness, and hardened leather.

### Upper leather

Bark-tanned and curried leather from a skin, for garments.

### Tawing

Soaking a skin or pelt in a bath of alum and salt instead of tanning it.

### White leather

Soft leather tawed from a skin, which stiffens when soaked until it is tawed again.

### Fur dressing

Tawing a pelt or woolly sheepskin with its hair left on, into fur.

### Oil tanning

Working brains or fish oil into a skin and smoking it, into buckskin.

### Buckskin

Oil-tanned leather that stays soft when wet and washed.

### Smudge pit

A small pit of smoldering wood over which oil-tanned hides are smoked.

### Rawhide

A hide or skin limed, scraped, and dried stiff with no tanning.

### Parchment

A sheep or goat skin limed, stretched, and scraped thin for writing.

### Vellum

Parchment made from calfskin.

### Lunellum

The crescent knife that scrapes parchment on a stretching frame.

### Stretching frame

The block on which hides dry, stiffen into rawhide, or are scraped into parchment.

### Hide glue

Fleshings and scraps boiled in a heated cauldron, which set hard and keep forever once dry.
