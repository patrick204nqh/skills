---
name: compare-table
description: Produces a short comparison table — 2–4 options against the same set of criteria — when the reader is making a decision and prose buries the differences. Make sure to use this skill whenever the user says "compare", "what's the difference", "X vs Y", "should I use A or B", "table this out", "side by side", or pastes parallel "X does this, Y does this" prose — even if they don't use those exact phrases.
---

# compare-table

Build a small table when the reader is choosing between things. Prose
buries differences; a row-by-row scan reveals them.

## Audience

Someone deciding. They want to glance down a column, glance down the
next, and feel the contrast. They will *not* read a paragraph that
says "X does A and Y does B and X also does C while Y…"

## When to use

Trigger on any of:
- "compare" / "what's the difference" / "X vs Y" / "side by side"
- "should I use A or B" / "which should I pick"
- "table this" / "make a table"
- The explanation is three or more sentences of the shape "X does
  [thing], whereas Y does [other thing]" — that's prose smuggling a
  table

Do **not** trigger when:
- There is only one option. A one-column table is a list.
- The differences are nuance-heavy and qualified ("it depends on…").
  Tables flatten. Use prose with caveats instead.
- The items aren't actually comparable on the same axes (apples vs
  oranges). Don't force a table; explain the category mismatch.

## Pick the shape first

Two layouts. Pick before you draw.

| Shape | Use when | Header row | First column |
|---|---|---|---|
| Options-as-columns | 2–4 options, 4+ criteria | option names | criteria |
| Options-as-rows | many options, 2–4 criteria | criteria | option names |

Default to **options-as-columns**. It's how readers expect to compare.
Switch to options-as-rows only when you have more than four options.

## Rules

1. **Four options max.** Five columns of comparison is a feature
   matrix, not a decision aid. If you need five, you're not
   comparing — you're cataloguing.
2. **The first column is the axis of comparison**, not an option.
   The axis names the criterion ("Startup cost", "Latency",
   "Maintenance"), not the answer.
3. **Cells: five words max.** A cell with a full sentence is prose
   in disguise. If a cell needs a sentence, the axis is too vague —
   split it into two narrower axes.
4. **Empty cells use `—`, not "N/A" or "none".** `—` reads
   instantly; "N/A" stops the eye.
5. **No "winner" row at the bottom.** Readers decide. A "winner" row
   is you selling, and you lose trust the moment they disagree with
   one criterion.
6. **Headline above the table: the takeaway, not the topic.** Not
   "Database comparison" but "Postgres wins on flexibility; SQLite
   wins on ops cost."
7. **Prose below the table, 2–3 sentences max.** Cover the nuance
   the table flattened — the "it depends on" and "but only if".

## Format

```
**Takeaway:** [one sentence — what the reader should conclude]

| Criterion | Option A | Option B | Option C |
|---|---|---|---|
| [axis] | [≤5 words] | [≤5 words] | [≤5 words] |
| [axis] | [≤5 words] | [≤5 words] | [≤5 words] |
| [axis] | [≤5 words] | [≤5 words] | [≤5 words] |

[2-3 sentences: the caveat, the "it depends", the thing the table
cannot say.]
```

## Example

**Bad** (prose smuggling a table):

> Postgres is a full relational database with strong concurrency and
> rich SQL features but you have to run it as a service. SQLite is a
> single-file embedded database that's trivial to deploy but has
> weaker concurrent-write performance. DynamoDB is fully managed and
> scales horizontally but locks you into AWS and a key-value model.

**Good** (takeaway + table + nuance):

> **Takeaway:** Postgres for flexibility, SQLite for simplicity,
> DynamoDB for scale-without-ops.

| Criterion | Postgres | SQLite | DynamoDB |
|---|---|---|---|
| Deployment | Run as service | Single file | Fully managed |
| Concurrent writes | Strong | Weak | Strong |
| Query model | Full SQL | Full SQL | Key-value |
| Vendor lock-in | None | None | AWS only |
| Ops cost | Medium | None | Low |

If you're prototyping and may grow, start with Postgres — the cost
of switching from SQLite later is real. DynamoDB only makes sense if
you're already on AWS and know your access patterns.

## What you are not doing

- You are not making a feature matrix for marketing. Marketing
  matrices have 30 rows and a checkmark column. Decision tables have
  five rows and force-rank the *real* differences.
- You are not selling. The reader is allowed to pick the option you
  wouldn't.
- You are not flattening real complexity. If the choice genuinely
  depends on something the table can't show, say so in the prose
  below — don't lie with a clean grid.
