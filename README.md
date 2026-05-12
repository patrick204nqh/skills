# Skills

You ask the agent a simple question — *how does this thing work?* —
and what comes back is technically correct, three paragraphs long, and
slides off your brain like water off a window. You read it twice. You
still couldn't repeat it to a colleague.

The agent isn't wrong. It's just not *explaining*.

That gap — between knowing a topic and being able to say it like a
human would — is what these skills are for. Small, opinionated
instruction files that change how the agent talks: one analogy not
three, short sentences, no "at its core…" filler. The agent already
knows the material. The skill just gets it to land.

Portable across Claude Code, Codex, Cursor, Gemini CLI, and any other
[Agent Skills](https://agentskills.io)-compatible tool. Each skill is
a folder with a `SKILL.md` file, loaded only when relevant — so you
can keep many on hand without bloating context.

## The skills

A small family of *explanation* skills, each tuned to a different
audience:

- **[eli5](./skills/eli5/SKILL.md)** — for when you want to *get* it.
  Plain language, one strong analogy. Triggers on "ELI5", "in simple
  terms", "plain English", "dumb it down".
- **[exec-summary](./skills/exec-summary/SKILL.md)** — for when a busy
  leader has 60 seconds. Leads with the decision, not the mechanism.
  Triggers on "exec summary", "TL;DR for my boss", "for leadership",
  "one-pager".
- **[eli-engineer](./skills/eli-engineer/SKILL.md)** — for when a peer
  engineer wants precision over accessibility. Names the data
  structure, the invariant, the trade-offs. No analogies. Triggers on
  "ELI-engineer", "technical explanation", "skip the analogy".

*More coming, slowly.*

## Install

Copy the skill folder you want into one of these locations:

    ~/.claude/skills/             # Personal (Claude Code)
    .claude/skills/               # Project-local, shared via git
    ~/.agents/skills/             # Codex / generic Agent Skills

Then just talk to your agent normally — skills trigger on intent, not
slash commands (though most can be invoked explicitly too).

## Philosophy

The best explanation is the one you can repeat to a friend an hour
later. These skills are opinionated rules — one analogy not three,
short sentences, no filler — because vague guidance doesn't change
behavior. Specific guidance does.

## About

Built by Patrick ([@patrick204nqh](https://github.com/patrick204nqh)).
Steal them, fork them, send a PR if you sharpen one.

## License

MIT
