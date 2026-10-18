# Clothing

A body dresses in layers: linen against the skin, wool or leather over it, armor on top, and a cloak over everything. Each garment adds warmth and keeps out wind and rain, so dressing for a winter journey or a summer harvest is a real choice. Garments get wet, dry, wear out, and get soiled, and a village has to keep its people clothed. Vanilla has only armor in four slots, so Feudum adds its own clothing.

[GLOSSARY.md](../../../GLOSSARY.md) defines the terms this page uses.

## Scope

- Players and humanoid mobs, such as villagers, wear clothing. [ADR 0012](../../adr/0012-bodies-wear-clothing-in-three-layers.md) records why bodies wear it in three layers.
- Animals wear nothing: their warmth is the natural insulation of their [thermal profile](../mechanics/body-temperature.md#thermal-profiles). Gear for mounts belongs to [Animal husbandry](https://github.com/NoNamer777/feudum/issues/27).
- This page owns the slots and how their layers stack. [Armor](https://github.com/NoNamer777/feudum/issues/78) owns the pieces of the armor layer.
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

- A cloak slot sits over every other layer, for 15 slots in all.
- A garment declares its layer and every region it fills, and blocks those slots. A robe fills the clothing layer of chest and legs; a hooded cloak covers the head as well as chest and legs.
- Humanoid mobs carry the same 15 slots in place of vanilla's armor slots.

## Garments

- A garment is a garment type made in a material. Both are data-driven, so a data pack can add either.
- The type gives the layer, the regions it fills, its coverage, a thickness that scales the insulation and weight of its material, and any protection.
- The material gives the thermal stats that [Body temperature](../mechanics/body-temperature.md#clothing) defines (insulation, wind resistance, water resistance, and sun heating), the wetness factor, the weight, and the durability.
- A lined garment takes the outer stats of its shell and adds the insulation of its lining.

### Materials

| Material | Character                                 | Insulation kept when soaked |
|:---------|:------------------------------------------|----------------------------:|
| Linen    | Light and cool; the underlayer material.  |                   about 10% |
| Wool     | Warm, and stays fairly warm when wet.     |                   about 50% |
| Leather  | Resists wind and water, and wears slowly. |                   about 30% |
| Fur      | The warmest, and heavy.                   |                   about 35% |
| Felt     | Fulled wool, for hats and boot linings.   |                   about 40% |
| Straw    | Hats that shade the face.                 |                   about 10% |

Silk and other fine cloth wait for [Social standing of dress](https://github.com/NoNamer777/feudum/issues/82).

### Catalog

| Type         | Layer      | Regions           | Materials                               |
|:-------------|:-----------|:------------------|:----------------------------------------|
| Coif         | Underlayer | Head              | Linen                                   |
| Shirt        | Underlayer | Chest             | Linen                                   |
| Braies       | Underlayer | Legs              | Linen                                   |
| Wraps        | Underlayer | Feet              | Linen, wool                             |
| Hood         | Clothing   | Head              | Wool, fur                               |
| Hat          | Clothing   | Head              | Felt, straw                             |
| Headwrap     | Clothing   | Head              | Linen                                   |
| Tunic        | Clothing   | Chest             | Linen, wool                             |
| Gambeson     | Clothing   | Chest             | Linen                                   |
| Jerkin       | Clothing   | Chest             | Leather                                 |
| Coat         | Clothing   | Chest             | Fur                                     |
| Hose         | Clothing   | Legs              | Wool                                    |
| Trousers     | Clothing   | Legs              | Wool, leather                           |
| Robe         | Clothing   | Chest, legs       | Linen, wool                             |
| Shoes        | Clothing   | Feet              | Leather                                 |
| Boots        | Clothing   | Feet              | Leather, leather lined with felt or fur |
| Mittens      | Clothing   | Hands             | Wool, fur                               |
| Gloves       | Clothing   | Hands             | Leather                                 |
| Cloak        | Cloak      | Chest, legs       | Wool, leather                           |
| Hooded cloak | Cloak      | Head, chest, legs | Wool                                    |
| Mantle       | Cloak      | Chest, legs       | Fur                                     |

- A robe and a gown are the same type.
- A gambeson is quilted from many layers of linen, and its thickness gives it warmth and protection.
- A straw hat has a negative sun heating: it shades the face and cools the wearer in the sun.
- The armor layer holds the pieces of [Armor](https://github.com/NoNamer777/feudum/issues/78).

## Combining stats

Body temperature reads one set of thermal stats per body. The worn garments combine into it:

- **Insulation** adds up over every worn garment, wet or dry, weighted by the share of the body its regions cover: about 10% for the head, 40% for the chest, 30% for the legs, 10% for the feet, and 10% for the hands.
- **Wind and water resistance** take, for each region, the highest value of any garment covering it, whatever its layer.
- **Sun heating** comes, for each region, from its outermost garment, so mail under a cloak doesn't bake.

## Protection

- A clothing garment can carry a small protection value, as a gambeson does, so a poor levy can fight in one.
- Armor on a region with an empty clothing layer protects less and chafes. [Armor](https://github.com/NoNamer777/feudum/issues/78) sets the numbers for both.

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
- [Washing and bathhouses](https://github.com/NoNamer777/feudum/issues/75) owns fast drying, such as a clothesline or a rack by the hearth.

## Wear and mending

- A garment loses durability while worn, and when its wearer takes damage.
- A garment at zero durability falls to tatters: it stays worn but keeps only a small share of its stats until mended.
- A garment is mended with thread and cloth, leather, or fur of its material: quickly at a tailor's bench, or slowly by hand with a needle.

## Soiling

- An [accident](../mechanics/relief.md#accidents) soils the garment on the legs, if one is worn, and leaves the body Soiled.
- A body wearing a soiled garment stays Soiled.
- Immersion washes the body and every garment it wears. Washing a body without the garment leaves the garment soiled until it is washed on its own.

## Making clothing

- Garments are sewn at a tailor's bench from cloth, leather, or fur, plus thread, not at a crafting table.
- A [Tailor](https://github.com/NoNamer777/feudum/issues/81) works the bench in a village.
- [Textiles](https://github.com/NoNamer777/feudum/issues/79) makes thread, cloth, and felt, and [Tanning](https://github.com/NoNamer777/feudum/issues/80) makes leather and fur.
- A garment takes its color from the cloth it was sewn from, and a finished garment can be dyed again. Color is cosmetic here, and Textiles owns dyes and dyeing.

## Starting clothing

- A new player starts in a linen shirt, linen braies, a wool tunic, wool hose, and leather shoes, so a first night under the `harsh` setting of Body temperature isn't a death sentence.
- Worn garments drop on death like the rest of the inventory, and respawning gives no new set.
- Generated villagers wear clothing that suits the climate profile of their biome. [Villagers](https://github.com/NoNamer777/feudum/issues/46) and [Village economy](https://github.com/NoNamer777/feudum/issues/44) decide who gets new clothes once theirs wear out, and where they come from.

## Inventory screen

- A paper-doll panel replaces vanilla's column of armor slots.
- Tabs switch the panel between the Underlayer, Clothing, and Armor layers, and the cloak slot shows on every tab.

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

Clothing owns the regions, layers, and slots, garment types and materials, and how the stats of worn garments combine. It also owns the protection of clothing garments, garment wetness and drying, wear and mending, soiled garments, the tailor's bench, the starting set, the paper-doll panel, and how garments look. Other mechanics own the rest, each linked to its page or, while it waits for a design, its issue:

- **[Body temperature](../mechanics/body-temperature.md)**: the thermal stats a garment carries, and what insulation, wind and water resistance, sun heating, and body wetness do to felt temperature.
- **[Relief](../mechanics/relief.md)**: accidents and the Soiled state of a body.
- **[Fluids](../mechanics/fluids.md)**: the water a body wades and swims in.
- **[Armor](https://github.com/NoNamer777/feudum/issues/78)**: the armor layer's pieces, protection, and durability, and how much less armor protects over an empty clothing layer.
- **[Encumbrance](https://github.com/NoNamer777/feudum/issues/65)**: what the weight of worn garments does to a body.
- **[Textiles](https://github.com/NoNamer777/feudum/issues/79)**: thread, cloth, felt, dyes, and dyeing.
- **[Tanning](https://github.com/NoNamer777/feudum/issues/80)**: leather and fur.
- **[Tailor](https://github.com/NoNamer777/feudum/issues/81)**: the villager who sews and mends at the tailor's bench.
- **[Social standing of dress](https://github.com/NoNamer777/feudum/issues/82)**: whether garments carry a fineness, and how Villagers and standing read dress.
- **[Inventory](https://github.com/NoNamer777/feudum/issues/83)**: the rest of the inventory screen, and the rule for items that change while stored.
- **[Washing and bathhouses](https://github.com/NoNamer777/feudum/issues/75)**: washing soiled garments, and fast drying.
- **[Villagers](https://github.com/NoNamer777/feudum/issues/46)** and **[Village economy](https://github.com/NoNamer777/feudum/issues/44)**: who gets new clothes, and where they come from.
- **[Animal husbandry](https://github.com/NoNamer777/feudum/issues/27)**: gear for mounts.
