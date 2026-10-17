# Vermin

Rats, mice, weevils, and clothes moths live wherever food and cloth are stored. Rats and mice raid the stores and foul what they leave behind, weevils eat the grain from within, and moths eat holes in the wool, silk, and fur. The fleas on rats bring plague. Cats, traps, raised granaries, sealed vessels, and the ratoner keep them down. A village that keeps its filth beside its stores feeds the rats, and the rats bring plague.

## Where vermin live

- **Everywhere there are stores.** Vermin come to any container or larder that holds what they eat, anywhere in the world, player bases and vanilla villages included. They never spawn in the wild away from stores.
- **Feudum villagers** fight vermin, as [Villagers](#villagers) describes. Vanilla villagers do nothing about them.
- **Players** in Creative or Spectator mode are never bitten. On Peaceful, rats, mice, and fleas never appear. Weevils and moths keep breeding, since they work like spoilage.

Rats, mice, weevils, and moths are mobs, which the [mobs index](../mobs/README.md) plans. Fleas are particles and sounds, like the mosquitoes of the [disease mechanic](disease.md#causes).

## Rats and mice

| Vermin | Nests in                                                     | Raids                               | Carries |
|:-------|:-------------------------------------------------------------|:------------------------------------|:--------|
| Rat    | Middens, dung heaps, laystalls, woodpiles, hay, under floors | Stores within a set range, at night | Fleas   |
| Mouse  | The walls and thatch of a home                               | The larder of its home              | Nothing |

The rat is the black rat, the rat of medieval Europe. The brown rat arrived centuries later.

### Nests

A nest is a new block that forms in a hidden, sheltered spot near food, and grows a colony over time. A nest holds at most 8 rats or 4 mice, and a chunk holds at most 2 nests.

- **Filth.** Every [polluter](sanitation.md#polluters) makes a rat nest more likely to form within its range.
- **Destroying a nest.** Breaking a nest ends the colony's breeding. The rats already out of the nest stay until something kills them.

### Raids

A rat or mouse that reaches a container eats a few items of food on each visit, and favors grain, flour, cheese, and bread. [Containers and sacks](#containers-and-sacks) describes which containers it can reach.

- **Droppings.** A new item that raids leave in the container. Food in a container that holds droppings is more likely to cause [food poisoning](disease.md#illnesses), until the droppings are cleared out. Droppings go to the [dung heap](sanitation.md#dung-heap-and-manure).
- **Henhouses.** Rats eat eggs lying on the ground, kill chicks, and eat from feed troughs.

### Rats and people

Rats and mice flee from players and villagers. A cornered rat bites for half a heart, and its bites never bring a player below half a heart. Rats and mice die in a hit or two, and drop nothing useful.

## Fleas and plague

Fleas live on rats, and show as particles and a faint sound around a colony and its rats. A body close to infested rats gets bitten. A bite gives the **itch**, a new short effect that does no harm.

The fleas of a healthy colony only itch. Plague comes when the colony itself falls ill:

1. **Plague reaches the colony.** It arrives on a merchant's cart, comes with rats from an infested colony, or breaks out at random in summer.
2. **The rats die.** The colony's rats sicken and die, and dead rats, a new item, lie in the streets and stores.
3. **The fleas leave.** As their rats die, the fleas move to the bodies nearby, and their bites can bring [plague](disease.md#illnesses).

So the bites that bring plague cluster after a die-off, and the dead rats are the warning. Medieval people saw rats die before an outbreak, but did not connect the two.

The hygiene mechanic will make bites less likely on clean bodies and in clean clothing. Lice and bedbugs belong to hygiene, not to vermin.

## Weevils

Weevils are tiny beetles that crawl on and inside containers that hold grain, flour, or dried beans. They breed in the store and eat from it. Warm air speeds their breeding, by the bands of the [food spoilage rate](food-spoilage.md#rate), and a damp store breeds them faster still. A store in the rain or beside water is damp.

- **Weevilled grain.** Grain, flour, and beans taken from an infested store carry eggs, and their tooltip says "weevilled". The eggs hatch in whatever store the food goes to next, so bought or shared grain can bring weevils in.
- **Crushing.** A player can crush a weevil by hand.

Weevils are kept down by:

- **Cool, dry stores.** Cool and cold air slows their breeding, and the freezing band stops it. The [granary](#the-granary) keeps its grain dry.
- **Sieving.** The miller's sieve, which already removes ergot from rye, removes weevils and eggs from grain. Sieved grain loses its "weevilled" tooltip.
- **Sweeping.** Crouching and using an empty container with an empty hand sweeps it out, and kills the eggs left in it.

## Clothes moths

Clothes moths are tiny moths that flutter around containers holding wool blocks, carpets, wool and silk cloth, furs, and wool, silk, and fur clothing. They settle in dark, still places that are rarely disturbed, and their larvae eat what is stored there:

| Stage      | Effect                                                              |
|:-----------|:--------------------------------------------------------------------|
| Sound      | None                                                                |
| Moth-eaten | [Clothing](clothing.md#wear-and-mending) keeps its wearer less warm |
| Ruined     | Becomes rags, a new item that goes to the dung heap                 |

Linen, cotton, hemp, and leather are safe, since clothes moths eat only wool, silk, and fur, as real clothes moths do.

Moths are kept down by:

- **Herb sachets.** A new item of linen filled with dried lavender, wormwood, or rue. Laid in a container, it keeps moths out for a season.
- **Airing.** Cloth and clothing that is taken out, worn, or brushed regularly stays free of moths, so moths do their damage in neglected chests.
- **The garderobe.** A room with a privy seat in it, under the room rules of the [temperature document](temperature.md#shelter-and-rooms). Containers and clothes pegs in a garderobe are safe from moths. Clothes pegs are a new block that holds cloth and clothing on the wall.

Medieval households hung their clothes in the privy, believing its fumes kept moths away, and the word garderobe comes from this. Cloth and clothing taken out of a garderobe carries a privy smell, which shows as particles until it has been worn or aired for an in-game day. Feudum villagers wrinkle their noses at the smell, but do not scold the wearer as they scold a soiled player.

## Defenses against rats and mice

### Cats and dogs

- **Cats.** Feudum changes vanilla cats to hunt rats and mice within a range of their home: a tamed cat around its owner's bed or base, and a village cat around its household and the stores. Cats ignore weevils and moths. The vanilla morning gift is sometimes a dead rat or mouse.
- **Dogs.** Tamed wolves attack rats and mice on sight, as they attack skeletons, but do not hunt them out.
- **Ratting dog.** The ratoner's dog, a tamed wolf that hunts rats down and digs out nests in the ground and under floors.

### Traps and ratsbane

- **Box trap.** A new wooden block, baited with food. It catches one rat or mouse, and holds it until someone empties the trap.
- **Ratsbane.** A new poison bait made from arsenic, the medieval ratsbane, laid in a store or by a nest. It kills the rats and mice that eat it, and poisons any cat, dog, livestock, or villager that finds it, and any player who eats it. Bait laid carelessly costs a village its cats.

### The granary

The granary is a room under the room rules of the [temperature document](temperature.md#shelter-and-rooms), detected like the smokehouse of [food spoilage](food-spoilage.md#preservation). Its floor stands at least 1 block above the ground on **staddles**, a new block in wooden and stone versions. A staddle has an overhanging cap that rats cannot climb past.

- **Out of reach.** Rats and mice cannot reach the stores inside a granary. Anything that links the ground to its floor or walls lets them in: steps, a ladder, a pile of blocks against a wall, or an open door at ground level.
- **Dry.** A granary keeps its grain dry, so weevils breed there at their slowest.

Granaries on wooden posts are old. Stone staddles came into wide use later, so the stone version is an improvement on the wooden one.

### Containers and sacks

| Container                       | Rats and mice                                |
|:--------------------------------|:---------------------------------------------|
| Chest, barrel, sack             | Get in                                       |
| Crock, sealed cask, shulker box | Kept out                                     |
| Ender chest                     | Kept out, since it has no place in the world |

Weevils and moths already inside a sealed vessel keep breeding, so sealing never cleans a store.

The **sack** is a new cheap container for grain, flour, dried beans, and seeds. It can be carried with its contents, like a bundle. Rats gnaw holes in sacks, which spill a little grain until the sack is patched with a piece of sackcloth.

## Reading vermin

Players judge vermin by what they can see and hear, with no meter and no number:

- Droppings in a container.
- Gnawed sacks.
- Scratching sounds near a nest at night.
- Dead rats in the streets and stores.
- The flea itch.
- Weevils crawling on stores, and "weevilled" in a tooltip.
- "Moth-eaten" in a tooltip.

Server config scales colony size, nest limits, raids, breeding, and the chance of plague among rats. It can turn each kind of vermin off, and it can turn the mechanic off.

## Villagers

Feudum villagers keep vermin down like a medieval village did:

- **Households.** Keep a cat, clear droppings out when they clear out rotten food each week, store grain in the granary or in crocks and casks, lay sachets in their clothes chests, and air their clothes.
- **Builder.** Raises the granary on staddles outside the range of every polluter, and keeps the ground around it clear of anything that links the ground to its floor.
- **Miller.** Sieves all grain before it is stored or ground.
- **Herder.** Keeps a barn cat, and covers the feed troughs at night.
- **Ratoner.** A new role that works through the village by night, as the gong farmer does. The ratoner destroys nests, sets traps, lays ratsbane, clears away dead rats, and goes wherever villagers find droppings or gnawed sacks.

These roles make what the village needs against vermin:

| Item           | Maker      | Ingredients                                    |
|:---------------|:-----------|:-----------------------------------------------|
| Box trap       | Carpenter  | Planks and a string catch                      |
| Ratsbane       | Apothecary | Arsenic, mined or bought, then mixed into bait |
| Herb sachet    | Herbalist  | Linen and dried lavender, wormwood, or rue     |
| Wooden staddle | Carpenter  | Logs                                           |
| Stone staddle  | Mason      | Stone                                          |
| Clothes pegs   | Carpenter  | Sticks and planks                              |
| Sack           | Weaver     | Sackcloth woven from flax tow or hemp          |

The herbalist grows lavender and rue in the physic garden, and forages them where they grow wild. Arsenic is mined from a new ore deep underground, as the planned [trade mechanic](README.md#planned) describes, and villages without a mine buy it from merchants. A village with neither relies on cats, traps, and the ratoner.

## Seasons and climate

- **Spring and summer.** Rats, mice, weevils, and moths breed fastest, and fleas breed in summer.
- **Autumn.** Rats move from the fields into the stores after the harvest.
- **Winter.** Rats and mice crowd indoors for warmth, and the freezing band stops weevils and moths from breeding.
- **Climate.** Hot climates breed vermin faster, and cold ones slower.

The Nether and the End have no vermin.

## Related mechanics

Vermin works together with these mechanics:

- **[Food spoilage](food-spoilage.md).** Vermin eat and foul the stores, the air band sets how fast weevils breed, and crocks and sealed casks keep rats out.
- **[Disease](disease.md).** Fleas from dying rats bring plague, and droppings cause food poisoning.
- **[Sanitation](sanitation.md).** Filth draws rat nests, and droppings and rags go to the dung heap. The garderobe is a privy room.
- **[Temperature](temperature.md).** Rooms make the granary and the garderobe, and the air band sets the pace of breeding.
- **[Seasons](seasons.md).** Vermin breed in spring and summer, move into the stores in autumn, and crowd indoors in winter.
- **Hygiene.** Clean bodies and clothing will draw fewer flea bites, and lice and bedbugs belong to hygiene.
- **[Clothing](clothing.md).** Moth-eaten clothing keeps its wearer less warm.
- **[Cloth](cloth.md).** Moths eat wool, silk, and fur in every form, and the weaver weaves the sackcloth for sacks.
- **Trade.** Merchants bring arsenic to villages without a mine, and can bring weevilled grain and plague-ridden rats.
- **Crop pests.** The pests of the fields belong to crop pests, not to vermin.

## Additions and changes

- **Vermin mobs.** New rats, mice, weevils, and clothes moths, in any store in the world.
- **Nests.** A new nest block that grows a colony of rats or mice, more likely near filth.
- **Raids.** Rats and mice eat stored food, eggs, chicks, and feed, and leave droppings, a new item that raises the risk of food poisoning.
- **Fleas and plague.** Flea particles and sounds around rats, a new itch effect, and plague among rats that leaves dead rats, a new item, before it reaches people.
- **Weevils.** Weevils breed in stored grain, flour, and beans, and weevilled food carries their eggs to the next store.
- **Moth damage.** Wool, silk, and fur go from sound to moth-eaten to ruined, and ruined cloth and fur become rags, a new item.
- **Cats.** Vanilla cats hunt rats and mice, and sometimes bring a dead rat as their morning gift.
- **Dogs.** Tamed wolves attack rats and mice, and the ratoner's ratting dog hunts them and digs out nests.
- **Traps and ratsbane.** A new box trap block, and new ratsbane bait that poisons whatever eats it.
- **Granary.** A raised room on new wooden and stone staddle blocks, out of reach of rats and mice.
- **Sack.** A new carried container for grain, flour, beans, and seeds, which rats gnaw open.
- **Sealed vessels.** Crocks, sealed casks, and shulker boxes keep rats and mice out.
- **Moth defenses.** A new herb sachet, airing, the garderobe, and a new clothes pegs block.
- **Plants and crops.** New lavender and rue plants, and a new hemp crop, retted and dressed like flax, as the [cloth mechanic](cloth.md#retting-and-dressing) describes.
- **Sackcloth.** A new [cloth](cloth.md#kinds-of-cloth) woven from tow, the coarse fiber left from dressing flax or hemp.
- **Sweeping.** Players sweep out an empty container to kill the weevil eggs in it.
- **Villager behavior.** Feudum villagers keep cats, clear droppings, store grain in the granary, sieve grain, lay sachets, air their clothes, and site the granary away from polluters.
- **Ratoner.** A new role that hunts rats and mice by night.
- **Configuration.** Server settings for colony size, nest limits, raids, breeding, the plague chance among rats, and turning each kind of vermin or the whole mechanic off.
