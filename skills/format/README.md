# Format family

Skills that decide *what the reader needs to see* — a diagram, a
table, a deck — and produce the content in an intermediate text form.
**Rendering is not the skill's job.**

## The pattern

Every skill in this family follows the same split:

1. **The skill** decides the shape (kind of diagram, axes of a table,
   one idea per slide) and produces structured text.
2. **The host** — or a renderer the user already has — turns that
   text into the artifact a human eventually sees.

The skill teaches *concepts and structure*. The renderer handles
*pixels and files*. Mixing the two locks you into one tool and
breaks the moment a better one shows up.

## Why this split

- **Portability.** Text output works in every host. A bundled
  renderer works in one.
- **Focus.** The skill has one job: get the shape right. Renderer
  dependencies, version drift, and pixel polish are a different
  problem.
- **Replaceability.** When a better renderer arrives, you swap the
  rendering step. The skill doesn't change.

## Implications for contributors

- No bundled scripts, no rendering deps, no vendor names hardcoded.
  See [`CONTRIBUTING.md`](../../CONTRIBUTING.md) — the
  *vendor-agnostic* rule.
- Each format skill includes a **"Handing off to a renderer"**
  section that describes the handoff in terms of renderer *kinds*,
  not products.
- If your skill needs to ship a renderer, it belongs in a sibling
  repo, not here.

## Skills in this family

- [`diagram-it`](./diagram-it/SKILL.md) — when a relationship is the
  point and prose buries it.
- [`compare-table`](./compare-table/SKILL.md) — when the reader is
  choosing between options and needs to scan the differences.
- [`slide-deck`](./slide-deck/SKILL.md) — when you're presenting to
  a room and need one idea per slide.
