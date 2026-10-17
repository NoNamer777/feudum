# Villages

A village is a persistent, self-steering community with its own name, territory, and history. Players do not own villages; they earn standing with them. A village can divide into manors, and with enough standing a player can be offered one and become its lord. A lord can hold manors in any number of villages, but every village keeps deciding its own next steps.

[GLOSSARY.md](../../GLOSSARY.md) defines the terms this page uses.

## Identity

- A village is a persistent record with an identity, a name, and its own state. Its buildings and villagers belong to it rather than define it.
- Names are generated from data-driven name pools, which can vary by biome or culture.
- Every village steers itself and decides its own next steps, such as what to build and where to grow. It weighs every wish it receives against its own needs.

## Territory

- A village's territory is every chunk within a margin of its buildings, 1 chunk by default. It is recalculated whenever the village gains or loses a building.
- Territory may lie in several parts, such as a mill by a distant river, and the record keeps them one village.
- Each chunk belongs to at most one village, and every unclaimed chunk is wilderness. Where two villages meet, the first claim wins: a margin stops at another village's border, and no village builds inside another's territory.
- The village center is the territory chunk nearest the middle of the buildings. It moves as the village changes and serves only as a reference point, for distances and for where the name shows.
- A building is an entry in the village record with a footprint in the world.
- A village runs live while any of its chunks is loaded, and as abstract data otherwise, as [Time](time.md#unloaded-villages) describes.

## Lifecycle

- World generation places living villages with no lord. Each village begins on the date it generates, and its generated buildings and villagers are its starting state; it never catches up from before that date.
- A village can send settlers out to found a new village in the wilderness or in ruins. The new village begins on the day it is founded, as one manor sworn to the lord of the manor that held most of the settlers' homes. When most of those homes were in the village holding, the new village has no lord.
- Players found villages only by swaying a village to send out settlers.
- A village with no buildings keeps existing, with no territory, while it has villagers.
- A village ends when its last villager is gone. Its buildings stay as ruins, its chunks return to wilderness, and its record closes.

## Standing and wishes

- Each village keeps a standing for every player it knows, and standing sets how much weight the player's wishes carry. [ADR 0002](../adr/0002-lords-earn-standing.md) records why lordship rests on standing rather than ownership.
- Villages owns the standing scale and its thresholds. The mechanics that own an action decide how it moves standing.
- Standing can fall below neutral, which makes a village wary of or hostile to a player. The mechanics that own a behavior, such as trade or defense, decide what hostility looks like.
- Standing never decays with time alone.
- A player gives a wish in person, inside the village's territory. The wish lasts until it is fulfilled or withdrawn.
- Village-wide matters, such as the name, belong to the village. Renaming is a wish the village weighs.

## Manors

- A manor is a set of the village's buildings, sworn to one lord. [ADR 0003](../adr/0003-lordship-attaches-to-manors.md) records why lordship attaches to manors rather than villages.
- A villager belongs to the manor that holds their home. A villager who loses their home stays with that manor until they find a new one.
- Buildings in no manor form the village holding. A village with no manors has no lord.
- A manor is carved only from the village holding, never from another manor.
- A building raised at a lord's wish joins that lord's manor. Every other new building joins the village holding.
- A manor lasts while it holds buildings or villagers.

## Lordship

- A lord is the one player or villager a manor is sworn to. A lord holds at most one manor per village, and a second manor in the same village merges into the first. A lord can hold manors in any number of villages.
- A lord's wishes carry a lord's weight for their own manor, and their standing's weight for the rest of the village.
- Lord-only rights apply to the lord's own manor. Other mechanics define them, such as tithes in Village economy.
- When the village forms a manor, it offers it to the highest-standing player above the lordship threshold who holds no manor there yet, and that player accepts or declines. Failing that, the village may appoint one of its own villagers or keep the buildings in the village holding.
- A lord cannot hand a manor to anyone else.
- A lord leaves the title by renouncing it, by their standing falling below a lower threshold, by a lapse, or by losing a contest. A higher standing alone never unseats a lord.
- When a lord renounces, falls below the threshold, or lapses, their manor's buildings return to the village holding. When a lord loses a contest, the winner takes the manor whole.
- A player lord's title lapses after a span of Feudum time since they last tended the village. The span is a per-world setting of 4 years by default. A lord tends a village by being inside its territory, or by steering it remotely once remote means exist.
- Only a player whose standing is above the lordship threshold can start a contest.
- A villager lord carries the same weight and rights as a player lord, and lapse does not apply to it.

## Boundaries

Villages owns a village's identity, its territory, its lifecycle, standing, manors, and lordship. Other mechanics, most of them planned in the [index](README.md), own the rest:

- **Villagers**: villager life, death, and homes. The roles a villager can hold, such as a reeve or a villager lord, are listed in the [villager roles index](../villager-roles/README.md).
- **Village economy**: tithes, trade, and how they move standing.
- **Village simulation**: how a village reaches its decisions, such as through officers and custom; when it forms a manor, appoints a villager lord, or founds a village; and what happens in the unloaded parts of a loaded village.
- **Buildings**: how buildings are designed, built, and recognized, and how building moves standing.
- **Village generation**: the layouts and placement of world-gen villages, listed in the [world generation index](../world-generation/README.md).
- **Lordship contests**: how a contest starts and is won, and what the loser keeps.
- **Realms**: fealty between lords, up to a sovereign with no lord above them, which a player can become.

## Deferred

- **Remote steering**: messengers, letters, or other ways to give a wish from afar.
- **Wish form**: whether a wish is a conversation, a building, or a menu.
- **Heirs**: naming a successor to a manor.
