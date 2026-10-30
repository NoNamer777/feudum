# Agent instructions

Read [README.md](README.md) first: it says what Feudum is and where its docs live. Before you design or build a feature, read the design page that covers it.

## Documentation

[docs/README.md](docs/README.md) indexes the documents of the project, and [docs/design/README.md](docs/design/README.md) indexes the design by area. Each index lists its documents as a link with a one-line summary each. The pull request that adds, renames, or removes a document updates its index to match.

## Design pages

The areas of the design are open: the user settles each one, and its name, when its first topic is filed or designed. A design page lives at `docs/design/<area>/<topic>.md`, where `<area>` is the name in its `area: <area>` label, such as `docs/design/world/biomes.md` for `area: world`. The design index links the index of each area, at `docs/design/<area>/README.md`, which lists the area's pages in alphabetical order. The first page of an area adds its index and its line in the design index, which says "No areas yet." while it has none.

## Planned designs

A topic that comes up while designing another and waits for a design of its own is a GitHub issue, not a line in the docs. File it with the `design` and `type: feature` labels and an `area: <area>` label for each area it belongs to. Run `gh label list` first: reuse a label that already covers the topic or area, and create one only when none does, with a kebab-case area name. List the labels you would create in the issue draft, so they are reviewed with it. Wherever a design page names the topic, link to its issue. The pull request that adds the topic's page closes the issue with a `Closes` line and points those links at the new page.

Each new issue joins the [Feudum project](https://github.com/users/NoNamer777/projects/9) with the Triage status. After filing issues, add a Blocked by relationship to each issue for every topic it builds on. Then reorder the project's items so they run in the order they should be picked up. `gh project` has no command for reordering, so use the `updateProjectV2ItemPosition` GraphQL mutation.

An issue promoted from an idea in Discussions ends its body with a `Refs: <discussion URL>` line, since GitHub has no issue relationship for a discussion.

Picking up a `design` issue starts a grilling session on its topic, run with the `grilling` skill, before you write any of the page. The user makes every decision of the design, and the page records the answers they settled.

Keep each design session to the topic of its issue. When a question grows too broad to settle within that topic, or leads into another topic or area, leave it unsettled: draft an issue for it as described above, and carry on with the rest of the topic. Wherever the page depends on that question, it links the issue in place of an answer.

## Diagrams and tables

A design page may carry a visual aid, such as a diagram, table, or chart, where it makes the design easier to grasp. Before you add or change one, read [Diagrams and tables](CONTRIBUTING.md#diagrams-and-tables) in CONTRIBUTING.md: it says when a page earns one, which format to pick, and how to check that it renders.

## Vanilla content

Feudum replaces vanilla Minecraft rather than building on it: every block, item, entity, biome, structure, dimension, and mechanic a player meets comes from Feudum. The overworld is the one exception; it stays as the dimension Feudum's own biomes generate in.

- Give each feature its own Feudum content. When it needs something vanilla already has, such as a log, an ore, or a cow, add a Feudum version and reference that.
- Disable vanilla content wherever the game allows, and hide what the game needs to keep registered: keep it out of world generation, spawning, recipes, loot tables, advancements, creative tabs, and recipe viewers. Turn off vanilla mechanics such as enchanting and brewing, and close off the Nether and the End.
- A change is done when it gives the player no path to vanilla content.
