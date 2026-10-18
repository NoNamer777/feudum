# Agent instructions

Read [README.md](README.md) first: it says what Feudum is and where its design docs live. Before you design or build a feature, read the design page that covers it.

## Planned designs

A topic that comes up while designing another and waits for a design of its own is a GitHub issue, not a line in the docs. File it with the `design` label and the label of each area it belongs to: `mechanics`, `world-generation`, `content`, or `villager-roles`. Wherever a design page names the topic, link to its issue. The pull request that adds the topic's page closes the issue with a `Closes` line and points those links at the new page.

Picking up a `design` issue starts a grilling session on its topic, run with the `grilling` skill, before you write any of the page. The user makes every decision of the design, and the page records the answers they settled.

## Vanilla content

Feudum replaces vanilla Minecraft rather than building on it: every block, item, entity, biome, structure, dimension, and mechanic a player meets comes from Feudum. The overworld is the one exception; it stays as the dimension Feudum's own biomes generate in.

- Give each feature its own Feudum content. When it needs something vanilla already has, such as a log, an ore, or a cow, add a Feudum version and reference that.
- Disable vanilla content wherever the game allows, and hide what the game needs to keep registered: keep it out of world generation, spawning, recipes, loot tables, advancements, creative tabs, and recipe viewers. Turn off vanilla mechanics such as enchanting and brewing, and close off the Nether and the End.
- A change is done when it gives the player no path to vanilla content.
