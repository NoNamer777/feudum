# Clothing

Players and Feudum villagers wear clothing in slots of their own, separate from armor. Garments keep the wearer warm in the cold and cool in the heat, wear out with use, and are patched until they fall to rags. A village needs its tailor and the trades around it to keep everyone in wool for winter and linen for summer.

Clothing starts from finished cloth, leather, and fur. Spinning, weaving, fulling, dyeing, and bleaching belong to the planned cloth mechanic, which the [mechanics index](README.md#planned) lists.

## Who wears it

- **Players** wear clothing everywhere in the world, vanilla villages included. In Creative and Spectator mode, garments never wear. On Peaceful, clothing works as usual, since it protects rather than threatens.
- **Feudum villagers** own and wear clothing, as [Villagers](#villagers) describes. Vanilla villagers keep their vanilla outfits.
- **Horses, donkeys, mules, camels, and llamas** wear blankets, as [Blankets](#blankets) describes. Other livestock relies on barns and fleece.

## Slots

Clothing has seven slots, in a panel of its own beside the armor slots of the inventory:

| Slot         | Holds                                  |
|:-------------|:---------------------------------------|
| Underclothes | A linen shirt, worn with braies        |
| Head         | Coifs, hoods, and hats                 |
| Body         | Tunics and the pelisse                 |
| Legs         | Hose                                   |
| Feet         | Shoes and boots                        |
| Cloak        | Cloaks, the waxed coat, and the mantle |
| Hands        | Mittens and gloves                     |

Garments render on the player model under armor, and the cloak renders over it. The cloak hides while an elytra is worn. A client option hides the clothing render for players who want the vanilla look, and changes nothing but the look.

Medieval people wore linen next to the skin. The shirt took up sweat and dirt and was washed often, while the wool over it was brushed and seldom washed. The planned hygiene mechanic launders the shirt.

## Garments

| Slot         | Garment          | Material            | Character                                       |
|:-------------|:-----------------|:--------------------|:------------------------------------------------|
| Underclothes | Shirt            | Linen               | Slight warmth, cooling in heat                  |
| Underclothes | Silk shirt       | Silk                | Slight warmth, cooling in heat                  |
| Head         | Coif             | Linen               | Slight warmth, cool                             |
| Head         | Silk coif        | Silk                | Slight warmth, cool                             |
| Head         | Hood             | Wool                | Warm, windproof, with a shoulder cape           |
| Head         | Felt hat         | Felt                | Fair warmth, sheds rain                         |
| Head         | Fur hat          | Fur and felt        | Very warm                                       |
| Head         | Straw hat        | Straw               | Shade                                           |
| Body         | Linen tunic      | Linen               | Cooling                                         |
| Body         | Wool tunic       | Wool                | Warm                                            |
| Body         | Fustian tunic    | Fustian             | Fair warmth, slight cooling                     |
| Body         | Silk tunic       | Silk                | Cooling, keeps its warmth when wet              |
| Body         | Pelisse          | Wool lined with fur | Very warm                                       |
| Legs         | Linen hose       | Linen               | Cooling                                         |
| Legs         | Wool hose        | Wool                | Warm                                            |
| Legs         | Fustian hose     | Fustian             | Fair warmth, slight cooling                     |
| Legs         | Silk hose        | Silk                | Cooling, keeps its warmth when wet              |
| Feet         | Turnshoes        | Leather             | Slight warmth                                   |
| Feet         | Boots            | Leather             | Warm, windproof, keep the feet dry while wading |
| Feet         | Fur-lined boots  | Leather and fur     | Very warm, windproof                            |
| Cloak        | Cloak            | Fulled wool         | Warm, windproof, sheds rain                     |
| Cloak        | Fur cloak        | Fur                 | Very warm, windproof                            |
| Cloak        | Waxed coat       | Waxed linen         | Windproof, sheds rain, slight warmth            |
| Cloak        | Mantle           | Linen               | Shade and cooling, for arid climates            |
| Hands        | Mittens          | Wool                | Warm                                            |
| Hands        | Gloves           | Leather             | Slight warmth                                   |
| Hands        | Fur-lined gloves | Leather and fur     | Very warm                                       |

Garments are the same for everyone: the tunic covers both the medieval tunic and the kirtle. A garment takes the color of the cloth it is sewn from, and a finished garment can be re-dyed at the dye vat. Color is cosmetic. Silk garments have the values of their linen versions, and the planned ranks mechanic will add sumptuary rules that set what each estate may wear, silk included.

### Warmth, cooling, and windproofing

Each garment has a warmth, a cooling, and a windproof value, which add up across the slots:

- **Warmth** raises the air a body feels while the air is below mild, so the body drifts toward a milder band. From the warm band up, warmth works against the wearer, so wool in summer makes a body hotter.
- **Cooling** lowers the air a body feels while the air is above mild. A linen shirt under wool takes away part of the heat the wool adds.
- **Windproofing** adds up as coverage, and blocks that share of the [wind chill](temperature.md#modifiers).
- **Shade.** The straw hat and the mantle remove the sun modifier for the wearer, as standing in shade does.
- **Hands.** Mittens or gloves cancel the slower mining of the cold band.

### Armor

Clothing and armor stack, and armor takes linings, as the [temperature document](temperature.md#protection) describes:

- **Leather armor** stays armor, the cuir bouilli of the period. It keeps its vanilla dyeing, and gives fair warmth and windproofing without a lining.
- **Gambeson.** A new light armor of quilted linen stuffed with cotton wadding, wool, or tow, the padded armor of the period, worn in the chest armor slot. Each stuffing gives the same protection, and the gambeson gives warmth along with it.

### Wetness

[Wetness](temperature.md#body-temperature) changes what garments give:

- **Wool** keeps about half its warmth when wet.
- **Linen** loses all its warmth when wet.
- **Fustian** keeps about half its warmth when wet, like wool.
- **Silk** keeps all its warmth when wet.
- **Shedding rain.** The waxed coat and the cloak keep the wearer dry in rain and snow. A felt hat slows the wetting on its own.
- **Wading.** Boots keep the wearer dry in water too shallow to swim in.
- **Swimming.** Nothing keeps a swimmer dry.

Wet garments dry on the body, faster in warm air or by a fire.

## Wear and mending

Garments wear out with time worn and with damage taken, through four stages:

| Stage      | Effect                                        |
|:-----------|:----------------------------------------------|
| Sound      | Full values                                   |
| Worn       | Full values, with faded color                 |
| Threadbare | Half values                                   |
| Rags       | Becomes rags, the item of the vermin mechanic |

- **Pace.** A garment worn every day moves one stage per season, so an unpatched garment lasts about three seasons. Shirts, hose, and gloves wear twice as fast. Silk garments, and garments sewn from finished cloth, last one season longer.
- **Damage.** Damage taken without armor wears the garments it hits one stage faster. Armor shields the garments under it.
- **Moths.** Stored wool, silk, and fur can turn moth-eaten, as the [vermin mechanic](vermin.md#clothes-moths) describes, and wearing a garment airs it. A moth-eaten garment gives half its warmth and no windproofing. The moth mark and the wear stage are separate, so a threadbare, moth-eaten cloak gives a quarter of its warmth.

A **patch** is cut from cloth, leather, or fur with vanilla shears, and sewn on at the [sewing table](#sewing). A patch of the garment's own material takes it back one stage, or removes the moth mark. Each patch shows on the garment. Households patch their own clothes, and the tailor mends the rest.

Rags go to the [dung heap](sanitation.md#dung-heap-and-manure). Medieval papermakers pulped linen rags, so rags are a future input for the paper that the books of the planned skills mechanic will need.

## Sewing

Garments are sewn at the **sewing table**, a new block that the carpenter builds:

- **Tools.** A needle, linen thread, and shears to cut the cloth. A bone needle is whittled from a bone, and the smith forges an iron needle that lasts longer.
- **Patterns.** The table lists the garments its materials can make, as the stonecutter lists its cuts.
- **Time.** A player holds use for a few seconds per garment, and less for a patch. A villager takes a working day per garment, so a village needs its tailor to keep up.

Players can make every garment themselves, with the same blocks the roles use, from fiber to finished garment. Buying from the tailor and the other makers is the shortcut.

Sewing needs no skill. The planned skills mechanic will let skilled sewing make garments that last longer and patches that restore more.

## Fur

Fur comes from three animals:

- **Rabbit hide.** Vanilla rabbits drop it, and its vanilla recipe into leather stays.
- **Sheepskin.** A new drop of a sheep slaughtered unshorn, with its fleece still on.
- **Fox pelt.** A new drop of foxes.

Wolves, polar bears, and other animals give no fur.

A pelt needs dressing before it can be sewn. The skinner taws it with alum and salt into **dressed fur**, a new item. Alum comes from alunite, a new stone in badlands, as the planned [trade mechanic](README.md#planned) describes, so villages elsewhere buy it from the merchant. The salter supplies the salt.

### The warren

The warrener keeps rabbits in **pillow mounds**, a new block of long, low earthen mounds that rabbits burrow and breed in. Warren rabbits are livestock, which the warrener culls for meat and hides. Foxes raid the warren, so the warrener traps them for their pelts. The Normans brought rabbits to England, and medieval warreners raised pillow mounds for them.

## Blankets

Horses, donkeys, mules, camels, and llamas get a blanket slot. On a horse, the blanket renders under the horse armor. The llama's carpet becomes a wool blanket that gives warmth, in the colors that carpets come in.

| Blanket       | Material  | Character                           |
|:--------------|:----------|:------------------------------------|
| Horse blanket | Wool      | Warm                                |
| Fly sheet     | Linen     | Cooling and shade                   |
| Caparison     | Dyed wool | Slight warmth, shown over the armor |

Blankets follow the rules of clothing for wear, moths, wetness, and mending, and shift the body temperature of [livestock](temperature.md#livestock). The tailor sews them.

## Starting clothes

New players spawn in a worn starting set that follows the climate of the spawn point:

- **Temperate and cold climates.** A shirt, a wool tunic, wool hose, and turnshoes.
- **Arid and tropical climates.** A shirt, a linen tunic, linen hose, and turnshoes.

Clothing drops on death, like the rest of the inventory.

## Reading clothing

Players judge garments by what they see, with no meter and no number:

- Tooltips describe values in words, such as "very warm", "cool", or "windproof", and name the wear stage and the moth mark.
- Wear shows on the model as faded color and visible patches.

The temperature gauge stays the only HUD element.

Server config scales the pace of wear, can turn wear off, and can turn off the starting set. Moth settings stay with the vermin mechanic.

## Villagers

Feudum villagers dress like a medieval village did:

- **Wardrobe.** Each villager owns a winter set, a summer set, and two shirts, as real items in the household chest. One shirt can be laundered while the other is worn.
- **Dressing.** Villagers dress each morning for the air band they wake to, so a cold spring morning gets the wool. They take off their cloak indoors by a fire, and put it back on before going out.
- **Look.** A villager's look comes from the garments they wear, in place of the vanilla profession outfits. Each role adds one mark to the model, such as the smith's leather apron or the miller's floured smock. The marks are part of the look, not items.
- **Mending.** Households patch their own clothes. The tailor keeps track of which garments in the village are worn out, and replaces them.
- **Shortage.** A villager without winter clothing chills faster outside, as the [temperature document](temperature.md#villagers) describes.

Children outgrow their clothes once a year, once the planned aging mechanic exists.

These roles make what the village wears:

| Item                                         | Maker      | Materials                                       |
|:---------------------------------------------|:-----------|:------------------------------------------------|
| Shirts, coifs, hoods, tunics, hose           | Tailor     | Linen, wool cloth, fustian, and silk cloth      |
| Cloaks, waxed coats, mantles                 | Tailor     | Fulled wool, waxed linen, and linen             |
| Pelisse                                      | Tailor     | Wool cloth, with the skinner's lining           |
| Gambeson                                     | Tailor     | Linen, and cotton wadding, wool, or tow         |
| Horse blankets, fly sheets, caparisons       | Tailor     | Wool, linen, and dyed wool                      |
| Fur cloaks, fur linings, and pelisse linings | Skinner    | Dressed fur                                     |
| Dressed fur                                  | Skinner    | Rabbit hides, sheepskins, fox pelts, alum, salt |
| Felt hats, straw hats, fur hats              | Hatter     | Felt, straw, and dressed fur                    |
| Turnshoes, boots, fur-lined boots            | Cordwainer | Leather and dressed fur                         |
| Mittens, gloves, fur-lined gloves            | Glover     | Wool cloth, leather, and dressed fur            |
| Rabbit hides and fox pelts                   | Warrener   | Warren rabbits and trapped foxes                |
| Iron needles                                 | Smith      | Iron                                            |
| Sewing table                                 | Carpenter  | Planks                                          |

The medieval London tailors were a guild of tailors and linen armorers, so the tailor sews the gambeson. The cordwainer makes new shoes and mends old ones, the work that the medieval cobbler did alone.

## Seasons and climate

- **Temperate climates.** Wool in winter, linen in summer, and a change each morning in spring and autumn.
- **Cold climates.** Wool and fur for most of the year.
- **Arid climates.** Linen and the mantle by day, and a cloak against the cold nights.
- **Tropical climates.** Linen all year.
- **Moths.** Moths breed in spring and summer, so stored winter wool and fur need sachets and airing while it waits for autumn.

## Related mechanics

Clothing works together with these mechanics:

- **[Temperature](temperature.md).** Garments give warmth, cooling, windproofing, and shade, and wetness changes what they give.
- **[Seasons](seasons.md).** The season sets which clothing a body needs.
- **[Vermin](vermin.md).** Moths eat stored wool, silk, and fur, and moth-eaten garments give less warmth.
- **[Sanitation](sanitation.md).** Rags go to the dung heap, and straw for hats comes from the harvest.
- **Cloth.** Supplies the cloth, thread, felt, and waxed cloth that garments are sewn from.
- **Hygiene.** Owns dirt on garments, laundry, and lice, and launders the shirt.
- **Skills.** Skilled sewing will make garments that last longer and patches that restore more.
- **Ranks.** Will add sumptuary rules that set what each estate may wear.
- **Aging.** Children will outgrow their clothes once a year.
- **Trade.** Brings alum for tawing fur to villages far from the badlands.
- **Wind.** The strength of the wind sets the chill that windproofing blocks.

## Additions and changes

- **Clothing slots.** Seven slots in a new inventory panel, separate from armor: underclothes, head, body, legs, feet, cloak, and hands.
- **Garments.** New garments of linen, wool, fustian, silk, felt, straw, fur, leather, and waxed linen, with warmth, cooling, windproof, and shade values.
- **Rendering.** Garments render under armor and the cloak over it, with a client option to hide them.
- **Gambeson.** A new light armor of quilted linen stuffed with cotton wadding, wool, or tow, that gives warmth.
- **Leather armor.** Vanilla leather armor gives fair warmth and windproofing.
- **Wear.** Garments wear from sound to worn, threadbare, and rags, faster when hit without armor.
- **Patches.** New patches of cloth, leather, or fur, cut with vanilla shears, that mend a garment or remove the moth mark.
- **Sewing table.** A new block that sews garments and patches from a list of patterns.
- **Needles.** A new bone needle and iron needle.
- **Fur.** New sheepskin and fox pelt drops, dressed fur, and alum for tawing.
- **Pillow mound.** A new block where warren rabbits burrow and breed.
- **Blankets.** A blanket slot for horses, donkeys, mules, camels, and llamas, with a new horse blanket, fly sheet, and caparison. The llama's carpet becomes a wool blanket.
- **Starting clothes.** New players spawn in a worn set that suits the climate of the spawn point.
- **Display.** Tooltips that describe values and condition in words, and faded color and patches on the model.
- **Villager behavior.** Feudum villagers keep a wardrobe, dress for the morning's air band, take off their cloak by a fire, patch their clothes, and wear a mark of their role.
- **Roles.** The tailor sews gambesons and blankets, and new cordwainer, skinner, glover, hatter, and warrener roles make the rest.
- **Configuration.** Server settings for the pace of wear, turning wear off, and turning off the starting set.
