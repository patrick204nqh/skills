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

Three families. Pick the one that matches what your reader needs.

### Audience — *who is reading this?*

- **[eli5](./skills/audience/eli5/SKILL.md)** — for when you want to *get* it.
  Plain language, one strong analogy. Triggers on "ELI5", "in simple
  terms", "plain English", "dumb it down".
- **[exec-summary](./skills/audience/exec-summary/SKILL.md)** — for when a busy
  leader has 60 seconds. Leads with the decision, not the mechanism.
  Triggers on "exec summary", "TL;DR for my boss", "for leadership",
  "one-pager".
- **[eli-engineer](./skills/audience/eli-engineer/SKILL.md)** — for when a peer
  engineer wants precision over accessibility. Names the data
  structure, the invariant, the trade-offs. No analogies. Triggers on
  "ELI-engineer", "technical explanation", "skip the analogy".

### Structure — *how is the argument shaped?*

- **[bluf](./skills/structure/bluf/SKILL.md)** — Bottom Line Up Front. The
  answer in the first sentence, supporting detail after. Triggers on
  "BLUF", "TL;DR", "lead with the answer", "get to the point".
- **[minto-pyramid](./skills/structure/minto-pyramid/SKILL.md)** — for
  proposals, recommendations, and decision docs. Answer first, then
  grouped reasons, then detail. Triggers on "structure this proposal",
  "Minto", "pyramid principle", "make this argument tighter".
- **[feynman](./skills/structure/feynman/SKILL.md)** — for checking your own
  understanding. Explain it plainly, then identify the part where you
  got fuzzy. Triggers on "do I actually understand this", "Feynman",
  "test my understanding", "what am I missing".

### Format — *what does the reader need to see?*

- **[diagram-it](./skills/format/diagram-it/SKILL.md)** — for when a
  relationship is the point and prose buries it. Picks the right diagram
  kind (flow, sequence, hierarchy, state), keeps it under five nodes,
  emits mermaid. Triggers on "draw this", "diagram", "visualise",
  "show me the flow", "picture this".
- **[compare-table](./skills/format/compare-table/SKILL.md)** — for when
  the reader is choosing between 2–4 options and prose buries the
  differences. Four columns max, five-word cells, takeaway above,
  nuance below. Triggers on "compare", "what's the difference", "X vs Y",
  "should I use A or B", "side by side".
- **[slide-deck](./skills/format/slide-deck/SKILL.md)** — for when you're
  presenting to a room. One idea per slide, headline = takeaway (not
  topic), speaker notes carry the story, no filler slides. Triggers on
  "make slides", "deck", "presentation", "slidify this", "turn this
  into slides".

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

The best explanation is the one a colleague can repeat an hour later.
The best summary is the one a leader can act on without scrolling. The
best diagram is the one you don't have to squint at. These skills are
opinionated rules — one analogy not three, the answer before the
journey, five nodes not fifteen — because vague guidance doesn't
change behaviour. Specific guidance does.

Each skill stays in the same shape: a single instruction file that
shapes *how the agent communicates* — in words, in structure, or in a
picture. No tools, no rendering, no dependencies. The skill tells the
agent what to produce; the host renders it. Match the medium to what
the reader needs.

## About

Built by [Patrick](https://github.com/patrick204nqh).
Steal them, fork them, send a PR if you sharpen one.

## License

MIT
