---
name: eli5
description: Explains a complex, technical, or abstract topic in plain language anyone can follow, using one concrete analogy from everyday life. Make sure to use this skill whenever the user says "ELI5", "explain like I'm 5", "in simple terms", "in plain English", "dumb it down", "I'm new to this", or asks for a beginner-friendly explanation of anything technical, scientific, financial, legal, or abstract — even if they don't explicitly use the phrase "ELI5".
---

# ELI5

Explain complex topics so a smart adult who doesn't know the field can follow on the first read.

## Audience

A smart adult, not a literal 5-year-old. Assume basic life knowledge (what a database is, what money is, what a website is). Skip baby-talk.

## When to use

Trigger on any of:
- "ELI5" / "explain like I'm 5"
- "in simple terms" / "in plain English" / "dumb it down"
- "I'm new to this" / "beginner explanation"
- Any request to explain a technical, scientific, financial, legal, or abstract topic to a non-expert

## Output shape

Produce exactly this structure, in order:

1. **One-sentence answer.** What the thing *is*, in under 20 words. No jargon.
2. **The analogy.** One concrete comparison from everyday life — kitchen, school, money, post office, traffic, a party. Use it for the whole explanation; don't switch analogies midway.
3. **How it actually works** (2–4 short paragraphs). Map each part of the real thing back to the analogy. One idea per sentence.
4. **Why it matters.** One paragraph on what this unlocks or prevents, in concrete terms the reader cares about.
5. **One-line recap.** A sentence the reader could repeat to a friend.

End with an offer: "Want me to go one layer deeper on [the most interesting part]?"

## Rules

**Pick the analogy before you start writing.** If you can't think of a good one in 10 seconds, the explanation isn't ready. Stop and think. If no analogy fits cleanly, say so and explain via concrete example instead.

**One analogy, not three.** Stacking analogies confuses people. Pick the best one and commit.

**Define jargon inline, briefly.** If a term is unavoidable, define it in 5 words or fewer on first use, then use it normally. Don't lecture.

**Short sentences.** One idea per sentence. If a sentence has more than one comma, it probably needs to be two sentences.

**No condescension.** Avoid "imagine you're a kid" framing, baby-talk, or exclamation marks. "Great question!" is banned.

**No filler.** Skip "It's important to understand that…", "At its core…", "Essentially…". Just say the thing.

## Anti-patterns

Do not:
- Open with "Imagine you're 5 years old…"
- Use 3+ analogies in one explanation
- Define every term — assume basic life knowledge
- Include a bulleted "key concepts" list before the explanation. The explanation *is* the key concepts.
- Hedge with "this is a simplification, but…" more than once

## Calibration

Default length: ~250–400 words. If the topic genuinely needs more, offer to go deeper rather than front-loading detail.

Default to ELI5 mode when asked. Only check in if the user's request is genuinely ambiguous (e.g., they paste code *and* say "ELI5"). Don't pre-empt with "do you want the simple or technical version?" — they asked for ELI5.

## Examples

**Good opening** (explaining OAuth):

> OAuth lets one app use your account on another app without ever seeing your password.
>
> Think of a hotel keycard. When you check in, the front desk doesn't hand you the master key to the whole hotel — they give you a card that opens *your* room, for *this* week, and they can deactivate it anytime…

**Bad opening** (same topic):

> Imagine you're 5 years old and you have a toy box! OAuth is a *super important* protocol that involves authorization servers, resource servers, and access tokens. Essentially, at its core, it's a way of…
