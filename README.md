# Skills

You ask the agent a simple question — *how does this thing work?* —
and what comes back is technically correct, three paragraphs long, and
slides off your brain like water off a window. You read it twice. You
still couldn't repeat it to a colleague.

The agent isn't wrong. It's just not *communicating*.

That gap — between knowing a topic and being able to say it like a
human would — is what these skills are for. Small, opinionated
instruction files that change how the agent talks: one analogy not
three, the answer before the journey, short sentences, no "at its
core…" filler. The agent already knows the material. The skill just
gets it to land.

Portable across Claude Code, Codex, Cursor, Gemini CLI, and any other
[Agent Skills](https://agentskills.io)-compatible tool. Each skill is
a folder with a `SKILL.md` file, loaded only when relevant — so you
can keep many on hand without bloating context.

## The skills

Two families. Pick the one that matches what's wrong with the
explanation you're getting.

### Audience modes — *who is reading this?*

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

### Methodology modes — *how should this be structured?*

- **[bluf](./skills/bluf/SKILL.md)** — Bottom Line Up Front. The
  answer in the first sentence, supporting detail after. Triggers on
  "BLUF", "TL;DR", "lead with the answer", "get to the point".
- **[minto-pyramid](./skills/minto-pyramid/SKILL.md)** — for
  proposals, recommendations, and decision docs. Answer first, then
  grouped reasons, then detail. Triggers on "structure this proposal",
  "Minto", "pyramid principle", "make this argument tighter".
- **[feynman](./skills/feynman/SKILL.md)** — for checking your own
  understanding. Explain it plainly, then identify the part where you
  got fuzzy. Triggers on "do I actually understand this", "Feynman",
  "test my understanding", "what am I missing".

*More coming, slowly.*

## Install

### Claude Code (recommended)

Install as a plugin to get every skill at once and pick up updates
automatically:

    /plugin marketplace add patrick204nqh/skills
    /plugin install patrick204nqh@skills

### Manual (any Agent Skills-compatible tool)

Copy the skill folder you want into one of these locations:

    ~/.claude/skills/             # Personal (Claude Code)
    .claude/skills/               # Project-local, shared via git
    ~/.agents/skills/             # Codex / generic Agent Skills

Then just talk to your agent normally — skills trigger on intent, not
slash commands (though most can be invoked explicitly too).

## Philosophy

The best explanation is the one you can repeat to a friend an hour
later. The best summary is the one a leader can act on without
scrolling. These skills are opinionated rules — one analogy not three,
the answer before the journey, short sentences, no filler — because
vague guidance doesn't change behaviour. Specific guidance does.

Each skill stays in the same shape: a single instruction file that
shapes *how the agent talks*, with no tools, no rendering, no
dependencies. Add an audience or a method; never a medium.

## About

Built by [Patrick](https://github.com/patrick204nqh).
Steal them, fork them, send a PR if you sharpen one.

## License

MIT
