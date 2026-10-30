---
applyTo: "**"
excludeAgent: "cloud-agent"
---

# Copilot code review

Feudum is a Minecraft mod still being designed: the repository holds only docs so far, with no mod code. [AGENTS.md](../../AGENTS.md) and [CONTRIBUTING.md](../../CONTRIBUTING.md) set the rules for those docs, so review each pull request against them. Keep each comment to one problem, and suggest the fix.

## What to check

- **Indexes.** A pull request that adds, renames, or removes a document updates its index: `docs/README.md` for project documents, `docs/design/README.md` for areas, and `docs/design/<area>/README.md` for the pages of an area. Each entry is a bold link with a one-line summary, and an area's index lists its pages in alphabetical order.
- **Page paths.** A design page lives at `docs/design/<area>/<topic>.md`.
- **Planned topics.** Where a page names a topic still waiting for its own design, it links the topic's GitHub issue instead of designing it in place. The pull request that adds a topic's page closes its issue with a `Closes #<number>` line and points the existing links at the new page.
- **Vanilla content.** Flag any design that gives the player a path to vanilla Minecraft content, such as a block, item, entity, biome, structure, dimension, or mechanic. The overworld is the one exception. A design that needs something vanilla already has adds a Feudum version of it.
- **Consistency.** Flag a rule that contradicts another design page, and a value that differs between a page's text and its tables or diagrams. The text is the source of truth.
- **Links.** Every relative link and heading anchor resolves.
- **Diagrams and tables.** Check them against [Diagrams and tables](../../CONTRIBUTING.md#diagrams-and-tables). Table columns line up in the source, with an alignment indicator in each separator cell. Each SVG sits at `docs/design/<area>/images/<page>-<topic>.svg` and has a `<title>`, a light background, and alt text. A sentence introduces every visual aid, which shows only what the text says.
- **Prose.** US English, no em dashes, one line per paragraph or list item, and no sentence of 40 words or more.

## What to leave alone

- **Design decisions.** The maintainer settles each design in a session of its own. Question a decision only where it breaks a rule above.
- **Titles and commit messages.** CI lints them as Conventional Commits.
- **Wording that is a matter of taste.**
