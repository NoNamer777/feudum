# Weapons

A weapon deals the damage kind of the way it lands: a sword cuts on the swing and pierces on the thrust, and a poleaxe chops with its blade or hammers with its back. Penetration lets a bodkin or an awl-pike punch through plate that turns a broad blade, so the choice of weapon answers the armor across the field. Shields cover what they face, parries stop a blow without one, and a heavy weapon drives through both. Vanilla has a handful of weapons and one shield, so Feudum adds its own weapons, ammunition, and shields, built on the damage kinds and protection of [Armor](armor.md).

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Players and humanoid mobs wield weapons. Animals attack under [Wildlife](https://github.com/NoNamer777/feudum/issues/47).
- This page owns melee weapons, ranged weapons and their ammunition, shields, and the attack profile of every held item, tools included.
- Fighting from the saddle belongs to [Mounted combat](https://github.com/NoNamer777/feudum/issues/117), and trebuchets, rams, and the like to [Siege engines](https://github.com/NoNamer777/feudum/issues/118).

## Weapon items

- A weapon is a weapon type made in a weapon material. Both are data-driven, so a data pack can add either.
- The type gives the grip, the weight class, the reach, the attack speed, the attack profile, the traits, and the parry protection.
- The material gives the damage scale, the flat penetration, the sharpness, the durability, and the weight.

### Materials

| Material | Damage | Flat penetration | Edge                                               | Rusts | Character                                          |
|:---------|:------:|:----------------:|:---------------------------------------------------|:-----:|:---------------------------------------------------|
| Wood     |  Low   |       None       | None                                               |  No   | Clubs, staffs, bows, hafts, and shield boards.     |
| Flint    |  Mid   |       None       | The keenest, but chips fast and can't be sharpened |  No   | Knapped blades and heads; the cheapest edged tier. |
| Bronze   |  Mid   |       Low        | Dulls fastest of the metals                        |  No   | Cast; its patina keeps it from rusting.            |
| Iron     |  High  |       Mid        | Holds an edge fairly well                          |  Yes  | The common metal of war.                           |
| Steel    |  High  |       High       | Holds an edge longest                              |  Yes  | The best, and the costliest.                       |

- **Durability**, from most to least: steel, iron, bronze, wood, flint.
- [Smithing](https://github.com/NoNamer777/feudum/issues/86) owns bronze, iron, and steel. [Encumbrance](https://github.com/NoNamer777/feudum/issues/65) decides what weight does.
- Stone, gold, diamond, and netherite have no counterpart.

## Attacks

Feudum keeps vanilla's attack cooldown, with each weapon type setting its attack speed. Jump critical hits, the sweep attack, and knockback are dropped for now. [Stamina](https://github.com/NoNamer777/feudum/issues/116) may replace the cooldown later.

### Attack motions

Every attack is one of four motions, read from how the camera turns over the last few ticks before the attack:

| Motion     | The view                               |
|:-----------|:---------------------------------------|
| Thrust     | Is still, or turns only a few degrees. |
| Side swing | Turns mostly left or right.            |
| Overhead   | Turns mostly downward.                 |
| Rising     | Turns mostly upward.                   |

- A diagonal turn counts as the motion it lies nearest: within 45° of horizontal it's a side swing, and otherwise an overhead or a rising swing.
- The hand animation shows which motion the attack made.
- A mob picks its motion through its AI.
- Where the hit lands still follows the [struck region](armor.md#struck-region) rules of Armor: the motion sets how a weapon strikes, not where.

### Attack profiles

- A weapon type declares, for each motion it has, the damage kind, a damage scale, and a penetration fraction.
- A motion the type doesn't declare falls back to its side swing, or to its thrust for a type without one, at reduced damage, so a falchion's thrust is a weak cut.
- The direction of a swing also changes its damage and its timing: an overhead deals about ×1.25 damage and recovers more slowly, and a rising swing deals about ×0.85 damage and recovers faster.
- Every held item has an attack profile. A pick pierces, an axe cuts, and a hammer or a shovel deals blunt damage. A bare fist or any other item deals a weak blunt hit. The design that owns a tool, such as Smithing or [Farming](../mechanics/farming.md#tools-and-blocks), may override its profile.

### Armor penetration

Penetration lowers the protection `p` of the struck region before [Protection](armor.md#protection) turns it into a damage reduction. It has two parts:

- The **fraction** comes from the attack motion of the weapon type: the shape of its point or edge. A dagger's or an awl-pike's thrust and a war hammer's spike have a high fraction, and a broad cut a low one.
- The **flat** amount comes from the material: the harder the metal, the deeper it bites. Wood and flint add none.
- The fraction applies first, then the flat amount comes off, so `p` becomes `p × (1 − fraction) − flat`, and never drops below 0.

The table works the rule through for a fraction of 30% and a flat amount of 5. Both values are illustrative.

| Armor on the region       | `p` | After penetration | Reduction before | Reduction after |
|:--------------------------|----:|------------------:|-----------------:|----------------:|
| Gambeson only             |   5 |                 0 |              20% |              0% |
| Iron mail over a gambeson |  20 |                 9 |              50% |             31% |
| Steel plate kit           |  40 |                23 |              67% |             53% |
| Plate, helm, and cloak    | 100 |                65 |              83% |             76% |

Against light armor the flat amount does most of the work, and against heavy armor the fraction does.

## Grip

### Handedness

Each weapon type has one of three grips:

- **One-handed**: held in either hand.
- **Two-handed**: held in the main hand, blocking the off hand, so it can't be used with a shield.
- **Versatile**: held in one hand, or in both while the off hand is empty. Held in both, it deals about ×1.25 damage and parries over a wider arc.

### Weight class

Each weapon type is light, medium, or heavy. The material scales its actual weight.

| Class  | Attack speed | In the off hand     | Against a parry or a raised shield          |
|:-------|:------------:|:--------------------|:--------------------------------------------|
| Light  |    Faster    | About ×0.9 damage   | Stopped as usual.                           |
| Medium |   Baseline   | About ×0.75 damage  | Stopped as usual.                           |
| Heavy  |    Slower    | Can't be held there | About a quarter of the damage goes through. |

[Skills](https://github.com/NoNamer777/feudum/issues/43) may raise the off-hand damage later.

### Off hand

- The off hand holds a shield, a one-handed weapon, or any other item.
- The use key attacks with an off-hand weapon, and the camera picks its motion as it does for the main hand. Each hand keeps its own cooldown, so a body can alternate between its weapons.
- The use key on a block that can be used, such as a door, a chest, or a workstation, still uses the block.
- Sneaking with the use key places or uses the off-hand item.
- Two weapons wielded together must both be one-handed or versatile, and the off-hand one can't be heavy. Their weights add up for Encumbrance.

### Traits

A weapon type may carry any of these traits:

- **Long reach**: a longer reach, for spears and polearms.
- **Shield-breaker**: a hit on a raised shield costs the shield several times as much durability.
- **Hook**: a hit on a raised shield pulls it down briefly, leaving the body open.

Bracing a spear against a charge waits for [Mounted combat](https://github.com/NoNamer777/feudum/issues/117).

## Melee catalog

| Type         | Grip       | Class  | Side swing | Overhead | Rising | Thrust | Traits                           | Materials                  |
|:-------------|:-----------|:-------|:-----------|:---------|:-------|:-------|:---------------------------------|:---------------------------|
| Dagger       | One-handed | Light  | Cut        | Pierce   | Cut    | Pierce |                                  | Flint, bronze, iron, steel |
| Arming sword | One-handed | Medium | Cut        | Cut      | Cut    | Pierce |                                  | Bronze, iron, steel        |
| Falchion     | One-handed | Medium | Cut        | Cut      | Cut    |        |                                  | Iron, steel                |
| Longsword    | Versatile  | Medium | Cut        | Cut      | Cut    | Pierce |                                  | Iron, steel                |
| Hand axe     | One-handed | Medium | Cut        | Cut      | Cut    |        | Shield-breaker                   | Flint, bronze, iron, steel |
| Bearded axe  | One-handed | Medium | Cut        | Cut      | Cut    |        | Shield-breaker, hook             | Iron, steel                |
| Dane axe     | Two-handed | Heavy  | Cut        | Cut      | Cut    |        | Shield-breaker, hook             | Iron, steel                |
| Club         | One-handed | Medium | Blunt      | Blunt    | Blunt  |        |                                  | Wood                       |
| Mace         | One-handed | Medium | Blunt      | Blunt    | Blunt  |        |                                  | Bronze, iron, steel        |
| War hammer   | One-handed | Medium | Blunt      | Pierce   | Blunt  |        |                                  | Iron, steel                |
| Quarterstaff | Two-handed | Medium | Blunt      | Blunt    | Blunt  | Blunt  | Long reach                       | Wood                       |
| Spear        | Versatile  | Medium | Blunt      | Pierce   | Blunt  | Pierce | Long reach                       | Flint, bronze, iron, steel |
| Pike         | Two-handed | Heavy  |            |          |        | Pierce | Long reach                       | Iron, steel                |
| Bill         | Two-handed | Heavy  | Cut        | Cut      | Cut    | Pierce | Long reach, hook                 | Iron, steel                |
| Halberd      | Two-handed | Heavy  | Cut        | Cut      | Pierce | Pierce | Long reach, hook, shield-breaker | Iron, steel                |
| Poleaxe      | Two-handed | Heavy  | Cut        | Blunt    | Cut    | Pierce | Hook                             | Iron, steel                |

- A war hammer's overhead strikes with its spike, at a high penetration fraction. A poleaxe's overhead strikes with its hammer back.
- A spear's swing is a blow with the shaft. Its overhead is a downward stab.
- A falchion is a broad, single-edged blade that cuts harder than an arming sword but can't thrust.
- Wooden weapons and the hafts of the rest take their wood from [Carpentry](https://github.com/NoNamer777/feudum/issues/115).
- Flails and greatswords are left out for now.

## Defense

One **parry key** defends with whatever a body holds: it raises a shield, or parries with a weapon when there is no shield.

### Parrying

- Holding the parry key raises the main-hand weapon, or both weapons when dual wielding, to parry.
- A parry covers a narrow frontal arc with the weapon's parry protection, which adds to the struck region as one more layer. A versatile weapon held in both hands parries over a wider arc.
- A dual wielder parries with the better parry protection of the two weapons, and both lose durability.
- A parrying weapon loses durability for each hit it stops, in proportion to the protection it gave.

### Shields

A shield is a shield type made with a build of board, facing, rim, and boss, which together give its protection per damage kind, its durability, and its weight.

A shield protects in four positions:

| Position                     | Covers                                           | Share of its protection |
|:-----------------------------|:-------------------------------------------------|------------------------:|
| Raised with the parry key    | Its type's regions, against hits in its arc      |                    100% |
| Held lowered in the off hand | The hands and chest, against hits from the front |                     25% |
| Slung in the back slot       | The chest, against hits from behind              |                     50% |
| Planted, for a pavise        | Every region, against hits from the front        |                    100% |

- A covered hit adds the shield's protection to the struck region as one more layer, and any other hit ignores the shield.
- An overhead ignores a raised shield's cover on the legs, and a rising swing ignores its cover on the head, so swinging around a shield is a tactic.
- A shield loses durability in proportion to the protection it gave, as an armor piece does. A shield-breaker multiplies the loss, and a hook pulls the shield down briefly.
- Weight class sets how fast a shield is raised, as well as its weight.
- With a shield in the off hand, the use key makes a **shield bash**: a weak blunt hit that briefly knocks a target's raised shield or parry aside.

### Shield catalog

| Type         | Class  | Raised covers            | Arc    | Build                                                  |
|:-------------|:-------|:-------------------------|:-------|:-------------------------------------------------------|
| Buckler      | Light  | Hands, chest             | Narrow | Small; all metal, or a wooden board with a metal boss. |
| Round shield | Medium | Head, chest, hands       | Mid    | Wooden board, with a rim and a boss.                   |
| Heater       | Medium | Chest, legs, hands       | Mid    | Wooden board with a leather facing.                    |
| Kite shield  | Heavy  | Head, chest, legs, hands | Wide   | Tall wooden board with a leather facing.               |
| Pavise       | Heavy  | Every region             | Wide   | A tall board that can be planted on the ground.        |

- Rims and bosses are hardened leather or metal, and facings are leather from [Tanning](../mechanics/tanning.md).
- A planted pavise stands where it was set, as a block-like entity, and covers every region of a body behind it from the front, so a crossbowman can span and reload in its cover. Picking it up returns it to the hand.

## Ranged weapons

| Type           | Grip       | Ammunition        | Character                                                        |
|:---------------|:-----------|:------------------|:-----------------------------------------------------------------|
| Self bow       | Two-handed | Arrows            | Cheap; one piece of wood.                                        |
| Longbow        | Two-handed | Arrows            | A long draw, long range, and high penetration.                   |
| Recurve bow    | Two-handed | Arrows            | Short, of wood, horn, and sinew; quick to draw.                  |
| Crossbow       | Two-handed | Bolts             | Spanned by hand or with a belt hook.                             |
| Heavy crossbow | Two-handed | Bolts             | Spanned with a cranequin or a windlass; the highest penetration. |
| Sling          | One-handed | Stones, lead shot | Blunt; made of cordage.                                          |
| Javelin        | One-handed | Itself            | Thrown; pierces.                                                 |
| Throwing axe   | One-handed | Itself            | Thrown; cuts; a shield-breaker.                                  |

- Bows, slings, and thrown weapons are drawn with a charge, as vanilla's bow is, and a fuller draw shoots harder.
- A crossbow is spanned and loaded slowly, then stays loaded until it shoots. A heavy crossbow can't be spanned without its cranequin or windlass in the inventory.
- The ranged weapon sets the power of a shot, which scales the damage and penetration of its ammunition.
- A shot lands on the struck region at its impact point, and drifts in the wind under the rules of [Weather](../mechanics/weather.md).
- Bowstrings and sling cords are twine from [Textiles](../mechanics/textiles.md#cordage). Horn and sinew come from [Animal husbandry](../mechanics/animal-husbandry.md#slaughter-and-butchering).

### Ammunition

Ammunition is a head type made in a head material. The head type gives the damage kind and the penetration fraction, and the head material gives the flat penetration.

| Type        | Kind   | Penetration | Head materials             | Character                                    |
|:------------|:-------|:-----------:|:---------------------------|:---------------------------------------------|
| Broadhead   | Cut    |     Low     | Flint, bronze, iron, steel | A wide head, for unarmored targets and game. |
| Bodkin      | Pierce |    High     | Iron, steel                | A narrow point, for mail and plate.          |
| Blunt arrow | Blunt  |     Low     | Wood                       | For small game and practice.                 |
| Quarrel     | Pierce |    High     | Iron, steel                | A square-headed crossbow bolt.               |
| Sling stone | Blunt  |     Low     | Stone                      | Picked up from riverbeds and fields.         |
| Lead shot   | Blunt  |     Mid     | Lead                       | Cast; heavier, and carries farther.          |

- Broadheads, bodkins, and blunt arrows are arrows, and quarrels are bolts.
- Lead comes from [Smithing](https://github.com/NoNamer777/feudum/issues/86).

### Quivers

- A quiver holds about 24 arrows or bolts, and is worn in the back slot or the belt slot.
- A bow or crossbow draws its ammunition from a worn quiver first. Without one, it draws from the inventory, at a slower draw.

### Spent ammunition

- Arrows and bolts stick where they land, and can be picked up again.
- Each one has a chance to break, set by its head: a bodkin breaks most often against armor, and a blunt arrow rarely breaks.
- Sling stones can be picked up again, and a javelin or a throwing axe drops where it lands.

## Carried gear

Two slots carry weapons on the body, and [ADR 0015](../../adr/0015-back-and-belt-slots-carry-gear.md) records why. [Clothing](clothing.md#slots) owns the slots, and this page owns what goes in them:

| Slot | Holds                                                       |
|:-----|:------------------------------------------------------------|
| Back | A slung shield, a slung bow, or a back quiver.              |
| Belt | A hip quiver, or a sheathed one-handed or versatile weapon. |

- A sheathed weapon at the belt is quick to draw. [Inventory](https://github.com/NoNamer777/feudum/issues/83) decides how drawing from a slot works.
- A slung shield covers the chest from behind, as [Shields](#shields) describes.

## Wear and care

- A weapon or shield loses durability for each hit it deals, parries, or blocks.
- One at zero durability is **Battered**: it stays usable but keeps only a small share of its stats until repaired.
- Iron and steel weapons and shield fittings **rust** while they stay wet, and tallow leaves them **Oiled**, under the [Rust and oiling](armor.md#rust-and-oiling) rules of Armor.

### Sharpness

- Every weapon with a cut or pierce motion has a **sharpness**, which drops with use and lowers the damage of its cut and pierce attacks as it falls. Ammunition has none.
- A **whetstone** carried in the inventory restores sharpness slowly, anywhere. A **grindstone** restores it quickly.
- Flint can't be sharpened: a dull flint edge has to be knapped again.
- The design that owns a tool decides whether that tool has sharpness. If it does, it uses the same whetstone and grindstone.

### Bowstrings

- A bowstring or sling cord weakens while wet, and a bow shoots with less power until the string dries.
- An unstrung bow keeps its string dry in the inventory, and stringing it takes a moment.

### Repair

- Metal weapons, heads, and shield fittings are repaired at the anvil with their own metal.
- Wooden weapons, hafts, and shield boards are repaired at the carpenter's bench with wood.
- Bows and crossbows are repaired at the bowyer's bench.
- Hardened leather rims and leather facings are repaired at the [leatherworker's bench](armor.md#making-armor).
- Ammunition isn't repaired.

## Making weapons

| Goods                                    | Made at               | Owned by                                                     | Worked by                                                       |
|:-----------------------------------------|:----------------------|:-------------------------------------------------------------|:----------------------------------------------------------------|
| Metal blades, heads, and shield fittings | Anvil                 | [Smithing](https://github.com/NoNamer777/feudum/issues/86)   | [Weaponsmith](https://github.com/NoNamer777/feudum/issues/119)  |
| Arrowheads and bolt heads                | Anvil                 | [Smithing](https://github.com/NoNamer777/feudum/issues/86)   | [Arrowsmith](https://github.com/NoNamer777/feudum/issues/120)   |
| Bows and crossbows                       | Bowyer's bench        | This page                                                    | [Bowyer](https://github.com/NoNamer777/feudum/issues/121)       |
| Arrows and bolts                         | Fletcher's bench      | This page                                                    | [Fletcher](https://github.com/NoNamer777/feudum/issues/122)     |
| Shields, hafts, clubs, and staffs        | Carpenter's bench     | [Carpentry](https://github.com/NoNamer777/feudum/issues/115) | [Carpenter](https://github.com/NoNamer777/feudum/issues/123)    |
| Hardened leather rims and grips          | Leatherworker's bench | [Armor](armor.md#making-armor)                               | [Leatherworker](https://github.com/NoNamer777/feudum/issues/88) |

- A fletcher's bench puts an arrow or bolt together from a shaft, feathers, [hide glue](../mechanics/tanning.md#by-products), and a head.
- The bowyer's bench shapes bows from wood, horn, and sinew, and strings them with twine.
- Weapons owns the whetstone and the grindstone.

## Noise

- A weapon or quiver being carried makes no noise.
- Every hit, parry, block, and shot makes a noise as loud as what meets what: metal on metal is loud, and wood or leather on flesh is quiet. A crossbow shot is loud, and a bow shot is quiet.
- [Stealth](https://github.com/NoNamer777/feudum/issues/89) decides how far a noise carries and who hears it.

## Who carries weapons

- A new player starts without a weapon, and generated villagers carry only the tools of their work.
- [Villagers](https://github.com/NoNamer777/feudum/issues/46), [Village economy](https://github.com/NoNamer777/feudum/issues/44), and [Village defense](https://github.com/NoNamer777/feudum/issues/90) decide who in a village is armed, and where the weapons come from.

## Vanilla content

- Every vanilla weapon is hidden: swords, the trident, the mace, the bow, the crossbow, the shield, and every arrow, tipped and spectral ones included.
- Feudum's attack profiles replace the attack damage of vanilla tools.
- Vanilla's grindstone is replaced by Feudum's, which only sharpens.
- Banner patterns on shields wait for [Heraldry](https://github.com/NoNamer777/feudum/issues/103).
- Vanilla weapon enchantments are disabled with the rest of enchanting.

## Appearance

- Weapons, shields, and quivers in the back and belt slots render on the body.
- A battered weapon looks dented, a rusting one shows orange spots, an oiled one has a sheen, and a dull one has a dull edge, on the model and in the inventory.
- A loaded crossbow shows its bolt, and an unstrung bow its loose string.

## Persistence

- A weapon's durability, sharpness, wetness, and remaining oiling save with the item, and so do a crossbow's loaded state and a bow's strung state.

## Query

- The [body query](../mechanics/body-temperature.md#query) also returns each held and carried weapon and shield with those values.

## Commands

- `/feudum weapons set <entity> <slot> <durability|sharpness|oiled> <value>` sets a held or carried weapon's value, for testing. The slot is `mainhand`, `offhand`, `back`, or `belt`.
- Every `/feudum weapons` command requires operator permission.

## Boundaries

Weapons owns weapon types and materials, attack motions and profiles, armor penetration, grips, weight classes, and traits. It owns the off hand and dual wielding, parrying, shields and their positions, ranged weapons, ammunition, quivers, and what goes in the back and belt slots. It also owns sharpness, the whetstone and grindstone, bowstrings, weapon repair, the bowyer's and fletcher's benches, and the noise of hits and shots. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Armor](armor.md)**: damage kinds, struck regions, protection, rust and oiling, and the leatherworker's bench.
- **[Clothing](clothing.md)**: the back and belt slots.
- **[Health](../mechanics/health.md)**: damage, the multiplier of each struck region, and the pool each hit lands in.
- **[Wildlife](https://github.com/NoNamer777/feudum/issues/47)**: the attacks of animals.
- **[Stamina](https://github.com/NoNamer777/feudum/issues/116)**: a pool that may replace the attack cooldown.
- **[Mounted combat](https://github.com/NoNamer777/feudum/issues/117)**: fighting from the saddle, and bracing against a charge.
- **[Siege engines](https://github.com/NoNamer777/feudum/issues/118)**: trebuchets, mangonels, rams, and ballistae.
- **[Skills](https://github.com/NoNamer777/feudum/issues/43)**: how skill raises off-hand damage.
- **[Encumbrance](https://github.com/NoNamer777/feudum/issues/65)**: what the weight of weapons does to a body.
- **[Stealth](https://github.com/NoNamer777/feudum/issues/89)**: how far the noise of a fight carries.
- **[Inventory](https://github.com/NoNamer777/feudum/issues/83)**: drawing from the back and belt slots.
- **[Weather](../mechanics/weather.md)**: the wind that makes shots drift.
- **[Smithing](https://github.com/NoNamer777/feudum/issues/86)**: bronze, iron, steel, lead, and the anvil.
- **[Carpentry](https://github.com/NoNamer777/feudum/issues/115)**: wood and the carpenter's bench.
- **[Textiles](../mechanics/textiles.md)**: the twine of bowstrings and sling cords.
- **[Tanning](../mechanics/tanning.md)**: leather facings, and hide glue.
- **[Animal husbandry](../mechanics/animal-husbandry.md)**: horn, sinew, feathers, and tallow.
- **[Heraldry](https://github.com/NoNamer777/feudum/issues/103)**: devices painted on shields.
- **[Weaponsmith](https://github.com/NoNamer777/feudum/issues/119)**, **[Arrowsmith](https://github.com/NoNamer777/feudum/issues/120)**, **[Bowyer](https://github.com/NoNamer777/feudum/issues/121)**, **[Fletcher](https://github.com/NoNamer777/feudum/issues/122)**, and **[Carpenter](https://github.com/NoNamer777/feudum/issues/123)**: the villagers who make and repair weapons.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)**, **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**, and **[Village defense](https://github.com/NoNamer777/feudum/issues/90)**: who in a village is armed, and where the weapons come from.
