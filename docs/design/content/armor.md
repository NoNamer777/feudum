# Armor

Armor goes on over clothing: mail over a gambeson, a helm over a coif and an arming cap. Every hit lands on one region, and only what that region wears protects it, so a missing helm or bare legs are a real risk. Mail stops a blade but not a mace, plate stops most things but bakes in the sun, and armor over bare skin chafes. Vanilla has armor points in four slots, so Feudum adds its own armor to the layers of [Clothing](clothing.md).

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Players and humanoid mobs wear armor, in the armor layer and helm slot of [Clothing](clothing.md#slots). Clothing owns the slots and how their layers stack.
- Animals wear none. Gear for mounts belongs to [Animal husbandry](https://github.com/NoNamer777/feudum/issues/27).
- This page owns the armor pieces, damage kinds, where a hit lands, and how protection combines, including the protection of padded garments.

## Slots

- The armor layer of the head holds a mail coif, and the helm slot over it holds an open or great helm. A body can wear either or both. [ADR 0013](../../adr/0013-a-helm-slot-sits-over-the-head-armor.md) records why the helm has a slot of its own.
- Putting on a helm lowers the hood of a hooded cloak, and the hood can't be raised under a helm.

## Pieces

- An armor piece is an armor type made in an armor material. Both are data-driven, so a data pack can add either.
- The type gives the slot, the regions it fills, and its coverage. A piece blocks every slot it fills, as a garment does.
- The material gives the protection per damage kind, the thermal stats, the noise, the weight, and the durability.

### Materials

| Material         | Cut  | Pierce | Blunt | Rusts | Noise | Character                                       |
|:-----------------|:----:|:------:|:-----:|:-----:|:-----:|:------------------------------------------------|
| Hardened leather | Low  |  Low   |  Low  |  No   |  Low  | Boiled leather; cheap, light, and metal-free.   |
| Bronze scale     | High |  Mid   |  Low  |  No   | High  | Overlapping scales on a backing; heavy.         |
| Iron mail        | High |  Mid   |  Low  |  Yes  |  Mid  | Linked rings; flexible, and stops blades.       |
| Steel mail       | High |  High  |  Low  |  Yes  |  Mid  | Better rings that resist an arrow's point.      |
| Brigandine       | High |  High  |  Mid  |  Yes  |  Low  | Steel plates riveted inside a cloth cover.      |
| Iron plate       | High |  Mid   |  Mid  |  Yes  | High  | Shaped plates that spread a blow; heavy.        |
| Steel plate      | High |  High  | High  |  Yes  | High  | The best, and the costliest.                    |

- **Durability**, from most to least: steel plate, iron plate, steel mail, brigandine, bronze scale, iron mail, hardened leather.
- **Weight**, from most to least: iron plate, steel plate, bronze scale, iron mail, steel mail, brigandine, hardened leather. [Encumbrance](https://github.com/NoNamer777/feudum/issues/65) decides what weight does.
- Gold, diamond, and netherite have no counterpart.

### Catalog

| Type        | Slot  | Regions     | Materials                                                        |
|:------------|:------|:------------|:-----------------------------------------------------------------|
| Mail coif   | Armor | Head        | Iron mail, steel mail                                            |
| Open helm   | Helm  | Head        | Hardened leather, bronze scale, iron plate, steel plate          |
| Great helm  | Helm  | Head        | Iron plate, steel plate                                          |
| Haubergeon  | Armor | Chest       | Iron mail, steel mail, bronze scale                              |
| Hauberk     | Armor | Chest, legs | Iron mail, steel mail, bronze scale                              |
| Cuirass     | Armor | Chest       | Hardened leather, brigandine, iron plate, steel plate            |
| Chausses    | Armor | Legs, feet  | Iron mail, steel mail                                            |
| Leg harness | Armor | Legs        | Hardened leather, brigandine, iron plate, steel plate            |
| Sabatons    | Armor | Feet        | Hardened leather, iron plate, steel plate                        |
| Gauntlets   | Armor | Hands       | Hardened leather, iron mail, steel mail, iron plate, steel plate |

- An open helm is a kettle hat or a nasal helm, with the face open. A great helm closes over the whole head and face.
- A haubergeon is a short mail shirt, and a hauberk reaches the knees.
- A leg harness is the cuisses and greaves that cover the thigh and shin.

## Damage kinds

- Armor reduces three damage kinds: **cut**, **pierce**, and **blunt**. [Weapons](https://github.com/NoNamer777/feudum/issues/85) and [Wildlife](https://github.com/NoNamer777/feudum/issues/47) give each attack its kind.
- An explosion deals blunt damage.
- Falls, fire, drowning, starvation, and temperature bypass armor.

## Struck region

Every hit lands on one region, and only the layers worn on that region protect against it.

- A melee hit or a projectile lands on the region at the height where it strikes the hitbox. The top eighth is the head, the bottom eighth the feet, and the middle splits into chest and legs at the waist. A hit on the chest or legs lands on the hands about 10% of the time.
- An attack without an impact point, such as a mob's plain melee, picks a region by weighted chance: about 10% head, 40% chest, 30% legs, 10% feet, and 10% hands. The chance shifts toward legs and feet when the attacker stands lower, and toward the head when it stands higher.
- An explosion spreads its damage over every region by those same shares.
- A hit's damage is multiplied by its struck region before protection applies, so an unarmored head is the weak spot. [Health](https://github.com/NoNamer777/feudum/issues/36) owns the multipliers, starting from about ×1.5 for the head, ×1 for chest and legs, and ×0.5 for hands and feet. Health also owns how hits land on bodies without regions, such as animals.

## Protection

- On the struck region, protection against the hit's damage kind adds up over every worn layer: underlayer, clothing, armor, helm, and cloak.
- The sum `p` becomes a damage reduction of `p / (p + 20)`, so stacking never reaches immunity.
- Weapons may add armor penetration, which lowers `p` for that hit.
- Each armor piece and garment on the struck region loses durability in proportion to the protection it contributed.

### Padding

- A gambeson and an arming cap of [Clothing](clothing.md#catalog) are quilted linen. Each gives about the blunt protection of hardened leather, half that against cut, and little against pierce, so a poor levy can fight in one.
- Any garment in the clothing layer pads the armor over it, whether quilted or not.

### Over an empty clothing layer

Armor and a helm on a region whose clothing layer is empty protect less and chafe:

- Their blunt protection drops to half, and their pierce protection to three quarters. Cut protection stays, since the metal still stops the edge.
- An underlayer garment on that region wears four times as fast.
- With the underlayer empty too, the armor rests on bare skin and the region is **Chafed**, which slows natural healing until the armor comes off or the region is dressed. Health owns the healing rate.

## Thermal stats

Armor materials carry the thermal stats of [Body temperature](../mechanics/body-temperature.md#clothing), and combine with garments under the rules of [Clothing](clothing.md#combining-stats).

| Material         | Insulation          | Wind resistance | Water resistance | Sun heating |
|:-----------------|:--------------------|:---------------:|:----------------:|:-----------:|
| Hardened leather | Low                 |      High       |       High       |     Low     |
| Bronze scale     | Draws heat in cold¹ |       Mid       |       Low        |    High     |
| Iron mail        | Draws heat in cold¹ |       Low       |       Low        |    High     |
| Steel mail       | Draws heat in cold¹ |       Low       |       Low        |    High     |
| Brigandine       | Low                 |      High       |       Mid        |     Low     |
| Iron plate       | Draws heat in cold¹ |      High       |       Mid        |  Very high  |
| Steel plate      | Draws heat in cold¹ |      High       |       Mid        |  Very high  |

¹ Metal has a negative insulation in the cold, but only on a region with an empty clothing layer, so padding keeps a body warm as well as protected.

- Brigandine's cloth cover keeps its plates from baking or chilling.
- A helm is the outermost piece on the head, so it gives the head's sun heating, and rain falls on it first.

## Wear and care

- An armor piece loses durability only from the hits it takes, not from being worn.
- A piece at zero durability is **Battered**: it stays worn but keeps only a small share of its stats until repaired.
- Armor pieces get wet and dry as garments do, under the [wetness](clothing.md#wetness) rules of Clothing.

### Rust and oiling

- Iron and steel pieces, brigandine included, **rust** while they stay wet: they slowly lose durability until they dry.
- Rubbing a piece with tallow leaves it **Oiled**, and it can't rust for about one week (8 days). The tallow comes from [Tanning](https://github.com/NoNamer777/feudum/issues/80) or [Animal husbandry](https://github.com/NoNamer777/feudum/issues/27).
- Bronze doesn't rust, since its patina protects it.
- Hardened leather softens instead: it loses durability while soaked, much more slowly than metal rusts.

### Repair

- A metal piece is repaired at the armorer's anvil with its own metal: iron, steel, or bronze.
- A hardened leather piece is repaired at the leatherworker's bench with hardened leather.
- Mail and hardened leather can also be patched slowly by hand with an **armorer's kit** of pliers, rings, awl, and thread. The kit is made at the armorer's anvil and wears out with use. Every other material is repaired only at its workstation.

## Making armor

- Metal pieces, brigandine included, are made at the **armorer's anvil**. [Smithing](https://github.com/NoNamer777/feudum/issues/86) owns the anvil and the iron, steel, and bronze, and an [Armorer](https://github.com/NoNamer777/feudum/issues/87) works it in a village.
- Hardened leather pieces are made at the **leatherworker's bench**, a block that shapes leather from Tanning by boiling and molding it into hardened leather. A [Leatherworker](https://github.com/NoNamer777/feudum/issues/88) works it in a village, and other designs can add their own goods to it, such as saddles, sheaths, and leather bottles.
- Brigandine takes its hemp cloth cover from [Textiles](../mechanics/textiles.md#cloth).

## Vision and noise

- A great helm narrows the view: it darkens the edges of the screen for a player, and shortens the sight range of a mob that wears it.
- Each armor material declares a noise value, from low to high, which [Stealth](https://github.com/NoNamer777/feudum/issues/89) reads.

## Armor stand

- Feudum's armor stand holds all 16 slots of a body, so a whole kit, from the gambeson to the cloak, hangs together.
- A body swaps everything it wears with the stand in one action.

## Who wears armor

- A new player starts without armor, and generated villagers wear none.
- [Villagers](https://github.com/NoNamer777/feudum/issues/46), [Village economy](https://github.com/NoNamer777/feudum/issues/44), and [Village defense](https://github.com/NoNamer777/feudum/issues/90) decide who in a village gets armor, such as guards, knights, and soldiers, and where it comes from.

## Vanilla content

- Every vanilla armor item is hidden, along with armor trims, smithing templates, and the vanilla armor stand.
- Vanilla armor enchantments are disabled with the rest of enchanting.
- Shields belong to Weapons, and horse and wolf armor to Animal husbandry.

## Appearance

- Every worn piece renders over the layers under it, under the [appearance](clothing.md#appearance) rules of Clothing.
- A battered piece looks dented, a rusting piece shows orange spots, and an oiled piece has a sheen, on the model and in the inventory.

## Persistence

- A piece's durability, wetness, battered state, and remaining oiling save with the item.

## Query

- The [body query](../mechanics/body-temperature.md#query) also returns each worn armor piece with its wetness, durability, and oiling, and the protection per damage kind of each region.

## Commands

- `/feudum clothing set` also takes the armor and helm slots, and sets the `oiled` value of a worn piece in days left, for testing.

## Boundaries

Armor owns the armor pieces, their types and materials, damage kinds, struck regions, and how protection combines, including the protection of padded garments. It also owns armor over an empty clothing layer, rust and oiling, battered pieces and their repair, the leatherworker's bench, the great helm's narrowed view, and the armor stand. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Clothing](clothing.md)**: the regions, layers, and slots, the helm slot and the hood of a hooded cloak included, and garment wetness and drying.
- **[Body temperature](../mechanics/body-temperature.md)**: what the thermal stats of armor do to felt temperature.
- **[Health](https://github.com/NoNamer777/feudum/issues/36)**: damage, the multiplier of each struck region, and the healing rate a Chafed region slows.
- **[Weapons](https://github.com/NoNamer777/feudum/issues/85)**: weapons and shields, the damage kind of each attack, and armor penetration.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: the damage kinds of animal attacks.
- **[Encumbrance](https://github.com/NoNamer777/feudum/issues/65)**: what the weight of armor does to a body.
- **[Stealth](https://github.com/NoNamer777/feudum/issues/89)**: what the noise of armor does.
- **[Smithing](https://github.com/NoNamer777/feudum/issues/86)**: iron, steel, bronze, and the armorer's anvil.
- **[Armorer](https://github.com/NoNamer777/feudum/issues/87)**: the villager who makes and repairs metal armor.
- **[Leatherworker](https://github.com/NoNamer777/feudum/issues/88)**: the villager who works the leatherworker's bench.
- **[Tanning](https://github.com/NoNamer777/feudum/issues/80)**: leather and tallow.
- **[Textiles](../mechanics/textiles.md)**: the hemp cloth of brigandine.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**, **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**, and **[Village defense](https://github.com/NoNamer777/feudum/issues/90)**: who in a village wears armor, and where it comes from.
- **[Animal husbandry](https://github.com/NoNamer777/feudum/issues/27)**: gear for mounts, and tallow.
