---
name: feynman
description: Tests whether the user actually understands a topic by explaining it back in plain language, then naming the specific point where the explanation gets fuzzy or hand-wavy — and proposes the smallest next step to close that gap. Make sure to use this skill whenever the user says "Feynman", "test my understanding", "do I actually understand this", "find the gap", "what am I missing", "I think I get it but…", "explain it back to me", or asks the agent to check their grasp of a topic rather than just present information — even if they don't use those exact phrases.
---

# Feynman

Test whether the user actually understands a topic. Explain it back plainly, then name the exact point where the explanation gets fuzzy — and propose the smallest next step to close that gap.

## Audience

Someone who has read or watched something and *thinks* they understand it, but suspects there's a hole. They don't want another explanation; they want a diagnosis.

## When to use

Trigger on any of:
- "Feynman" / "use the Feynman technique" / "explain it back to me"
- "test my understanding" / "do I actually understand this" / "find the gap"
- "I think I get it but…" / "where am I confused" / "what am I missing"
- The user has just learned or summarised something and asks for a check rather than more material

This skill is the inverse of `eli5`. ELI5 takes a topic and produces an explanation. Feynman takes a topic the user already has an explanation for, and finds where the explanation breaks.

## Output shape

Produce exactly this structure, in order:

1. **The plain explanation.** Re-explain the topic as if teaching a smart non-specialist. No jargon you can't define in 5 words. 2–4 short paragraphs. This is the *attempt* — and where it strains is the diagnostic signal.
2. **The fuzzy part.** One short paragraph naming the specific point in step 1 where the explanation went hand-wavy. Be precise. Not "the details are complicated" — "I said the system 'syncs state' but I didn't name *what triggers a sync* or *how conflicts resolve*."
3. **The gap.** One sentence naming the underlying concept, fact, or mechanism you'd need to understand to make step 2 sharp. This is the actual learning target.
4. **The next step.** One concrete action that closes the gap with the least effort. A specific section of the docs to re-read, a one-paragraph search query, a small experiment to run, a single question to ask a colleague. Not "study more."

End with: "Want me to run another pass after you've closed the gap?"

## Rules

**Be honest about the fuzz.** The whole point of this skill is to *find* the gap, not hide it. If step 1 came out clean and confident, say so — and pressure-test it by asking what edge case or failure mode would break the explanation. If that also comes out clean, the topic might be solid.

**One gap at a time.** If there are three fuzzy points, pick the one whose resolution would clarify the others. Surface the others as "after you close this, the next likely gaps are X and Y" — don't try to fix everything at once.

**Name the gap as a concept, not a topic.** "I need to understand TCP" is a topic. "I need to understand how TCP's congestion window grows and shrinks under loss" is a concept. Always the second form.

**The next step is small.** If the action would take more than 30 minutes, it's the wrong size — break it down further or pick a smaller entry point.

**No new analogies in step 1.** Use the same analogies the user has presumably been using. Switching frames mid-diagnosis hides the real gap.

**If the user supplied their own explanation, work from that.** Don't write a fresh one — find the fuzz in *theirs*. The output then becomes: their explanation (quoted or summarised) → fuzzy part → gap → next step.

## Anti-patterns

Do not:
- Skip step 1 — the explanation *is* the diagnostic; without it there's nothing to point at
- Say "you've got it!" without testing — confirmation isn't the same as comprehension
- Surface every fuzzy point — pick the one that matters most
- Recommend "read the whole spec" or "take a course" — those aren't next steps, they're capitulation
- Use this skill as an excuse to dump more information — if the user wanted more material they'd have asked for it
- Pad with encouragement ("great question, this is a really common confusion") — the diagnosis is the help

## Calibration

Default length: 200–400 words. The plain explanation is the bulk; steps 2–4 are tight.

If the user supplied their own explanation, the plain-explanation step shrinks to a 2–3 sentence restatement of theirs, and the bulk shifts to the diagnosis.

If the gap turns out to be a *terminology* issue (the user has the concept but is tripped up by a name), say so — that's a 30-second fix, not a study session.

If the gap turns out to be foundational (the user thought they understood X but actually X depends on Y which they haven't met yet), call that out plainly. "The real next step isn't deeper into X — it's a detour through Y."

## Examples

**Good** (user said "I think I understand how Postgres MVCC works"):

> **Plain explanation:** Postgres lets readers and writers run at the same time without blocking each other by giving each transaction a snapshot of the database as it existed at a specific moment. When you update a row, Postgres doesn't overwrite — it writes a new version and leaves the old one for any transaction whose snapshot still includes it. Eventually a background process called `VACUUM` cleans up versions no one can see anymore.
>
> **Fuzzy part:** I said transactions get "a snapshot of the database as it existed at a specific moment" — but I didn't say *what defines that moment*, or how Postgres decides which row versions a given transaction is allowed to see. That's hand-waving over the core mechanism.
>
> **The gap:** How transaction IDs (`xmin`, `xmax`) are assigned to row versions and how visibility is computed against the active snapshot. That's the actual machinery; everything else follows from it.
>
> **Next step:** Read the "Snapshots" and "Visibility" sections of the Postgres internals docs (about 10 minutes), then come back and re-explain MVCC. The fuzz should be gone.
>
> *Want me to run another pass after you've closed the gap?*

**Bad** (same prompt):

> Great question! MVCC is a really fundamental concept in databases and lots of people find it confusing at first. Let me give you a really thorough explanation. Multi-Version Concurrency Control is a method of handling concurrent access to a database. It was first introduced in… *[continues for 800 words and never identifies the actual gap]*
