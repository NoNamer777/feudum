# Clothing

A body dresses in layers: linen against the skin, wool or leather over it, armor on top, and a cloak over everything. Each garment adds warmth and keeps out wind and rain, so dressing for a winter journey or a summer harvest is a real choice. Garments get wet, dry, wear out, and get soiled, and a village has to keep its people clothed. Vanilla has only armor in four slots, so Feudum adds its own clothing.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Players and humanoid mobs, such as villagers, wear clothing. [ADR 0012](../../adr/0012-bodies-wear-clothing-in-three-layers.md) records why bodies wear it in three layers.
- Animals wear nothing: their warmth is the natural insulation of their [thermal profile](../mechanics/body-temperature.md#thermal-profiles). Gear for mounts belongs to [Tack and barding](https://github.com/NoNamer777/feudum/issues/139).
- This page owns the slots and how their layers stack. [Armor](armor.md) owns the pieces of the armor layer and the helm slot, and [Weapons](weapons.md) owns what goes in the back and belt slots.
- Feudum garments replace vanilla's leather armor, and Armor replaces the rest of vanilla armor. Other vanilla wearables, such as the turtle shell, mob heads, and the elytra, stay hidden.

## Slots

A body has five regions: head, chest, legs, feet, and hands. Each region has layers, from the skin out:

| Region | Underlayer | Clothing | Armor |
|:-------|:----------:|:--------:|:-----:|
| Head   |    Yes     |   Yes    |  Yes  |
| Chest  |    Yes     |   Yes    |  Yes  |
| Legs   |    Yes     |   Yes    |  Yes  |
| Feet   |    Yes     |   Yes    |  Yes  |
| Hands  |     No     |   Yes    |  Yes  |

- A helm slot sits over the armor layer of the head, and a cloak slot over every other layer. [ADR 0013](../../adr/0013-a-helm-slot-sits-over-the-head-armor.md) records why the helm has a slot of its own.
- A back slot and a belt slot carry gear, such as a slung shield, a quiver, or a sheathed weapon, for 18 slots in all. [ADR 0015](../../adr/0015-back-and-belt-slots-carry-gear.md) records why.
- A garment declares its layer and every region it fills, and blocks those slots. A robe fills the clothing layer of chest and legs; a hooded cloak covers the head as well as chest and legs while its hood is up.
- Humanoid mobs carry the same 18 slots in place of vanilla's armor slots.

## Garments

- A garment is a garment type made in a material. Both are data-driven, so a data pack can add either.
- The type gives the layer, the regions it fills, its coverage, a thickness that scales the insulation and weight of its material, and any protection.
- The material gives the thermal stats that [Body temperature](../mechanics/body-temperature.md#clothing) defines (insulation, wind resistance, water resistance, and sun heating), the wetness factor, the weight, and the durability.
- A lined garment takes the outer stats of its shell and adds the insulation of its lining.

### Materials

| Material | Character                                                               | Insulation kept when soaked |
|:---------|:------------------------------------------------------------------------|----------------------------:|
| Linen    | Light and cool; the underlayer material.                                |                   about 10% |
| Nettle   | A rough, cheap linen that wears faster.                                 |                   about 10% |
| Woolen   | Warm, and stays fairly warm when wet.                                   |                   about 50% |
| Worsted  | Smooth and hard-wearing; less warm than woolen and more wind-resistant. |                   about 40% |
| Leather  | Resists wind and water, and wears slowly.                               |                   about 30% |
| Fur      | The warmest, and heavy.                                                 |                   about 35% |
| Felt     | Matted wool, for hats and boot linings.                                 |                   about 40% |
| Straw    | Hats that shade the face.                                               |                   about 10% |

Silk and other fine cloth wait for [Social standing of dress](https://github.com/NoNamer777/feudum/issues/82).

### Catalog

| Type         | Layer      | Regions           | Materials                               |
|:-------------|:-----------|:------------------|:----------------------------------------|
| Coif         | Underlayer | Head              | Linen                                   |
| Shirt        | Underlayer | Chest             | Linen, nettle                           |
| Braies       | Underlayer | Legs              | Linen, nettle                           |
| Wraps        | Underlayer | Feet              | Linen, woolen                           |
| Hood         | Clothing   | Head              | Woolen, fur                             |
| Hat          | Clothing   | Head              | Felt, straw                             |
| Arming cap   | Clothing   | Head              | Linen                                   |
| Headwrap     | Clothing   | Head              | Linen                                   |
| Tunic        | Clothing   | Chest             | Linen, nettle, woolen, worsted          |
| Gambeson     | Clothing   | Chest             | Linen                                   |
| Jerkin       | Clothing   | Chest             | Leather                                 |
| Coat         | Clothing   | Chest             | Fur                                     |
| Hose         | Clothing   | Legs              | Woolen, worsted                         |
| Trousers     | Clothing   | Legs              | Woolen, leather                         |
| Robe         | Clothing   | Chest, legs       | Linen, woolen                           |
| Shoes        | Clothing   | Feet              | Leather                                 |
| Boots        | Clothing   | Feet              | Leather, leather lined with felt or fur |
| Mittens      | Clothing   | Hands             | Woolen, fur                             |
| Gloves       | Clothing   | Hands             | Leather                                 |
| Cloak        | Cloak      | Chest, legs       | Woolen, leather                         |
| Hooded cloak | Cloak      | Head, chest, legs | Woolen                                  |
| Mantle       | Cloak      | Chest, legs       | Fur                                     |

- A robe and a gown are the same type.
- A gambeson is quilted from many layers of linen, and its thickness gives it warmth and protection. An arming cap is quilted the same way, as padding under a helm.
- A straw hat has a negative sun heating: it shades the face and cools the wearer in the sun.
- The hood of a hooded cloak is up or down, and the wearer raises or lowers it with a key or from the paper-doll panel. Putting on a helm lowers the hood, and it can't be raised under a helm.
- The armor layer and the helm slot hold the pieces of [Armor](armor.md).

## Combining stats

Body temperature reads one set of thermal stats per body. The worn garments combine into it:

- **Insulation** adds up over every worn garment, wet or dry, weighted by the share of the body its regions cover: about 10% for the head, 40% for the chest, 30% for the legs, 10% for the feet, and 10% for the hands.
- **Wind and water resistance** take, for each region, the highest value of any garment covering it, whatever its layer.
- **Sun heating** comes, for each region, from its outermost garment, so mail under a cloak doesn't bake.

The diagram shows a chest in a linen shirt, a woolen tunic, an iron mail haubergeon, and a woolen cloak, from the skin out, and how its stats combine across those layers. It also shows the rules of [Wetness](#wetness) and of [armor over an empty clothing layer](armor.md#over-an-empty-clothing-layer). The garments are an example.

![The chest from the skin out: body, underlayer, clothing, armor, and cloak. Insulation and protection add up over every layer, and wind and water resistance take the highest value. The sun heats the cloak, the outermost garment. Rain wets the cloak first and passes inward, and sweat wets the body and the underlayer. Armor over an empty clothing layer protects less and chafes.](images/clothing-layers.svg)

## Protection

- A clothing garment can carry protection, as a gambeson and an arming cap do, so a poor levy can fight in one. [Armor](armor.md#padding) sets how much.
- Armor on a region with an empty clothing layer protects less and chafes, as [Armor](armor.md#over-an-empty-clothing-layer) describes.

## Wetness

Each garment carries its own wetness, from dry to soaked. The wetness of [Body temperature](../mechanics/body-temperature.md#wetness) is that of the body under its clothing.

- Precipitation on an uncovered region wets its outermost garment first. Once a garment is near soaked, water passes to the next layer in, slowed by the garment's water resistance, and past the underlayer it reaches the body. A good cloak keeps the tunic dry through a shower but not through a day of rain.
- Wading wets the feet and legs from the inside out, as deep as the water reaches.
- Submersion soaks every garment and the body at once.
- Sweat wets the body and its underlayer.
- A garment loses insulation in proportion to its wetness, down to the share its material keeps when soaked.

### Drying

- Worn garments dry from the outside in, by felt temperature, sun, sheltered wind, and nearby heat sources, as the body does. Body heat also dries the underlayer.
- A garment carried in the inventory dries slowly, by the felt temperature of its holder.
- A garment in a container dries at a slow fixed rate, brought up to date from the elapsed time when the container is next opened, under the rule [Inventory](https://github.com/NoNamer777/feudum/issues/83) owns for items that change while stored.
- [Hygiene](../mechanics/hygiene.md#drying) owns fast drying: the clothesline, the drying rack, and the towel.

## Wear and mending

- A garment loses durability while worn, and when a hit lands on a region it covers.
- A garment at zero durability falls to tatters: it stays worn but keeps only a small share of its stats until mended.
- A garment is mended with thread and cloth, leather, or fur of its material: quickly at a tailor's bench, or slowly by hand with a needle.

## Soiling

- An [accident](../mechanics/relief.md#accidents) soils the garment on the legs, if one is worn, and leaves the body Soiled.
- A body wearing a soiled garment stays Soiled.
- Immersion washes the body and every garment it wears. Washing a body without the garment leaves the garment soiled until it is washed on its own.
- Garments also carry grime, mud, and bloodstain, and [Hygiene](../mechanics/hygiene.md#garments) owns how they get dirty and how [laundry](../mechanics/hygiene.md#laundry) washes them.

## Making clothing

- Garments are sewn at a tailor's bench from cloth, leather, or fur, plus thread, not at a crafting table.
- A [Tailor](https://github.com/NoNamer777/feudum/issues/81) works the bench in a village.
- [Textiles](../mechanics/textiles.md) makes thread, cloth, and felt, and [Tanning](https://github.com/NoNamer777/feudum/issues/80) makes leather and fur.
- A garment takes its color from the cloth it was sewn from, and a finished garment can be dyed again. Color is cosmetic here, and [Textiles](../mechanics/textiles.md#dyes) owns dyes, dyeing, and fading.

## Starting clothing

- A new player starts in a linen shirt, linen braies, a woolen tunic, woolen hose, and leather shoes, so a first night under the `harsh` setting of Body temperature isn't a death sentence.
- Worn garments drop on death like the rest of the inventory, and respawning gives no new set.
- Generated villagers wear clothing that suits the climate profile of their biome. [Villagers](https://github.com/NoNamer777/feudum/issues/46) and [Village economy](https://github.com/NoNamer777/feudum/issues/44) decide who gets new clothes once theirs wear out, and where they come from.

## Inventory screen

- A paper-doll panel replaces vanilla's column of armor slots.
- Tabs switch the panel between the Underlayer, Clothing, and Armor layers, and the cloak slot shows on every tab. The helm slot shows on the Armor tab, and the back and belt slots show on every tab.

## Appearance

- Every worn layer renders on the model, outer over inner, and nothing can be hidden, so a body's look shows what it wears.
- A wet garment renders darker and drips, a soiled one shows stains, and a tattered one looks torn, on the model and in the inventory.

## Persistence

- A garment's wetness, durability, soiling, and color save with the item.

## Query

- The [body query](../mechanics/body-temperature.md#query) of Body temperature also returns each worn garment with its wetness and durability, and the combined stats per region.

## Commands

- `/feudum clothing set <entity> <slot> <wetness|durability> <value>` sets a worn garment's value, for testing.
- Every `/feudum clothing` command requires operator permission.

## Boundaries

Clothing owns the regions, layers, and slots, garment types and materials, and how the stats of worn garments combine. It also owns garment wetness and drying, wear and mending, soiled garments, the tailor's bench, the starting set, the paper-doll panel, and how garments look. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Body temperature](../mechanics/body-temperature.md)**: the thermal stats a garment carries, and what insulation, wind and water resistance, sun heating, and body wetness do to felt temperature.
- **[Relief](../mechanics/relief.md)**: accidents and the Soiled state of a body.
- **[Fluids](../mechanics/fluids.md)**: the water a body wades and swims in.
- **[Armor](armor.md)**: the pieces of the armor layer and the helm slot, damage kinds and protection, the protection of padded garments included, and how much less armor protects over an empty clothing layer.
- **[Weapons](weapons.md)**: the weapons, shields, and quivers carried in the back and belt slots.
- **[Encumbrance](https://github.com/NoNamer777/feudum/issues/65)**: what the weight of worn garments does to a body.
- **[Textiles](../mechanics/textiles.md)**: thread, cloth, felt, dyes, dyeing, and fading.
- **[Tanning](https://github.com/NoNamer777/feudum/issues/80)**: leather and fur.
- **[Tailor](https://github.com/NoNamer777/feudum/issues/81)**: the villager who sews and mends at the tailor's bench.
- **[Social standing of dress](https://github.com/NoNamer777/feudum/issues/82)**: whether garments carry a fineness, and how Villagers and standing read dress.
- **[Inventory](https://github.com/NoNamer777/feudum/issues/83)**: the rest of the inventory screen, and the rule for items that change while stored.
- **[Hygiene](../mechanics/hygiene.md)**: the dirt of garments, laundry, and fast drying.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)** and **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: who gets new clothes, and where they come from.
- **[Tack and barding](https://github.com/NoNamer777/feudum/issues/139)**: gear for mounts.
