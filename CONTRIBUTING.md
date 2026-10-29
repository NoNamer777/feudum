# Contributing

Feudum is still being designed and holds no mod code yet. Ideas start in [Discussions](https://github.com/NoNamer777/feudum/discussions), where they can be talked through before the maintainer, [@NoNamer777](https://github.com/NoNamer777), turns them into `design` issues and designs each page from one.

## Suggesting an idea

Post your idea in the [Ideas](https://github.com/NoNamer777/feudum/discussions/categories/ideas) category, rather than as an issue. Cover:

- What the idea is.
- How a player would meet it in play.
- Which area it belongs to: mechanics, world generation, content, or villager roles.
- Any design pages or issues it relates to.

When a topic already has a home, add to it there instead. Comment on its open [`design` issue](https://github.com/NoNamer777/feudum/issues?q=is%3Aissue%20is%3Aopen%20label%3Adesign) when its page is still waiting to be written. To change a page that is already designed, post an idea that links the page.

The maintainer turns an idea into a `design` issue once:

- No design page or open issue covers it yet.
- It fits Feudum: managing medieval fantasy villages, built from Feudum's own content rather than vanilla Minecraft's.
- The discussion has settled what the topic covers, enough to scope it in a paragraph.

The maintainer makes the final call. Either way, the discussion closes as resolved: with a link to the new issue when the idea is taken up, or with the reason when it is not.

## Asking a question

Ask about the design or the project in the [Q&A](https://github.com/NoNamer777/feudum/discussions/categories/q-a) category, and mark the reply that answers you. When an answer shows that a page is unclear, the maintainer fixes the page.

## Following announcements

The maintainer posts news about Feudum in [Announcements](https://github.com/NoNamer777/feudum/discussions/categories/announcements); subscribe to the category to hear about it.

## Fixing the docs

Pull requests are welcome for small fixes to the docs, such as a typo or a broken link. Design pages come out of the maintainer's design sessions, so propose design changes as an idea instead.

- [Sign your commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits): the default branch rejects unsigned ones. If you can't sign, report the fix in Q&A.
- Title the pull request as a [Conventional Commit](https://www.conventionalcommits.org/en/v1.0.0/) subject, such as `docs: fix broken link in thirst page`.
- Say in a sentence why the change is needed.

## Diagrams and tables

A design page may use a visual aid, such as a diagram, table, or chart, where it makes the design easier to grasp. It never has to, and prose is often enough. Add a diagram or chart only where it does at least one of these:

- Joins rules spread across sections or pages into one picture.
- Shows structure that prose can only list, such as branches, cycles, or trees that change shape.
- Shows something spatial or plotted.

Leave out a diagram of what a table already orders, such as the thresholds of a set of stages.

Pick the lightest format that does the job:

| Content                                               | Format                               |
|:------------------------------------------------------|:-------------------------------------|
| Values to compare, or a rule to work through          | A Markdown table, or worked examples |
| A small hierarchy                                     | A Mermaid fenced block               |
| Flows, cycles, and branching chains                   | An SVG file                          |
| Spatial or plotted, such as a map, layers, or a chart | An SVG file                          |

Mermaid lays out a graph on its own. That suits a small hierarchy, but it scatters flows and cycles, so draw those as an SVG with every box placed by hand.

Line up the columns of every table in the source, and give each cell of the separator row an alignment indicator, such as `:---`.

Store each SVG in an `images/` folder beside the pages of its area, named `<page>-<topic>.svg`. Give it a `<title>` and a light background of its own, so it reads in both GitHub themes. Embed it with alt text that describes what it shows.

Introduce every visual aid with a sentence that says what it shows. The page's text stays the source of truth, so a visual aid shows only what the page already says. In that sentence, mark as illustrative any value the page leaves open, such as an example name, a threshold, or an assumed layout. A diagram that needs a rule the page lacks waits until that rule is designed.

GitHub's renderer is the target. Check each Mermaid block in the GitHub file view, and each SVG in both the light and the dark theme. Mermaid lays out nodes in the order they are defined, so reorder the definitions when edges cross.
