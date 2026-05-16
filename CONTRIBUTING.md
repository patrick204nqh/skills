# Contributing

Thanks for considering a skill. This repo is opinionated on purpose —
the voice and the shape are part of the product. Read this once before
opening a PR.

## What belongs here

Skills that help a *human* understand something the agent is trying to
say. Three families:

- **Audience** — *who is reading this?* (`eli5`, `exec-summary`, `eli-engineer`)
- **Structure** — *how is the argument shaped?* (`bluf`, `minto-pyramid`, `feynman`)
- **Format** — *what does the reader need to see?* (`diagram-it`)

If your skill doesn't make a human's comprehension faster, it
probably belongs somewhere else.

## What does *not* belong here

- Skills that ship code, binaries, scripts, or external dependencies.
  This repo is instruction-only. If your skill needs a renderer, build
  it in a sibling repo and link to it.
- Skills that wrap a specific tool (a particular API, CLI, or SDK).
- Skills that produce artifacts the human isn't directly reading.
- Skills about *what to think* (domain knowledge). This repo is about
  *how to communicate*.

A new family is rarer than it sounds. If you think you need one, open
an issue first — three orthogonal families is the whole architecture.

## The standard — must follow

Every skill must comply with the [Agent Skills
specification](https://agentskills.io/specification). Non-negotiable:

- One folder, one `SKILL.md`. YAML frontmatter, then Markdown.
- `name` field: 1–64 chars, lowercase a–z, digits, hyphens. No leading
  or trailing hyphens. No consecutive hyphens. **Must match the
  parent directory name exactly.**
- `description` field: 1–1024 chars. Non-empty. Describes both *what*
  the skill does and *when* to use it. Include trigger phrases.

Validate before opening a PR:

```bash
npx skills-ref validate skills/<family>/<your-skill>
```

## The house rules — opinionated, on top of the spec

These are what make the repo feel like one voice, not a museum.

### Voice

- Short sentences. One idea per sentence.
- Second person. *You*, not "the user" or "one".
- Opinionated rules, not gentle suggestions. "Five nodes max." Not
  "consider keeping diagrams small."
- No filler. Strike "at its core…", "essentially…", "it's important
  to note that…", "in order to", "leverages", "utilises".
- Read an existing skill before writing yours — `skills/structure/bluf/SKILL.md`
  is the cleanest reference for cadence.

### Shape

Each `SKILL.md` body has roughly this structure:

1. **One-line opening** under the H1 — the whole point in a sentence.
2. **`## Audience`** — who's reading this output, what state they're in,
   how long they'll spend on it.
3. **`## When to use`** — trigger phrases (formal name + casual ask +
   symptom) and "do not trigger when…".
4. **`## Rules`** — numbered, concrete, enforceable. "Label every
   arrow," not "use clear labels."
5. **One worked example** — Bad → Good.
6. **`## What you are not doing`** — common over-reaches, called out.

### Length

- Keep `SKILL.md` under ~150 lines. The spec recommends <500; we hold
  ourselves tighter. If you're over, you're either explaining too
  much or have two skills smashed together.
- No `scripts/`, no `references/`, no `assets/`. If you reach for
  them, the skill probably doesn't fit this repo.

### Vendor-agnostic

Skills teach concepts, not products. Do not hardcode the names of
specific apps, hosts, or rendering tools in your `SKILL.md`:

- ❌ "Paste into Notion, PowerPoint, or GitHub."
- ✅ "If the host renders your output, paste it. If not, hand it to
  whatever renderer the user prefers."

Talk about *kinds* of tool — a renderer, a presentation tool, an
async reader — and let the user supply their specific one. A skill
that names today's products dates the moment a new one wins.

### Triggers

Cover three phrasings in your `description` and `## When to use`:

- The **formal name** (e.g. "Minto pyramid")
- A **casual ask** (e.g. "tighten this proposal")
- A **symptom** (e.g. "this argument is hard to follow")

Agents activate on intent, not slash commands. Triggers are how the
agent recognises intent.

## Pull request process

1. **Branch off `main`.** One skill per PR (or one structural change
   per PR — don't bundle).
2. **Folder placement:** `skills/<family>/<your-skill>/SKILL.md`.
3. **Register in `.claude-plugin/plugin.json`** in the same PR. Add
   `"./skills/<family>/<your-skill>"` to the `skills` array.
4. **Link from `README.md`** under the right family section, with a
   one-line description matching the existing pattern (skill name as
   a link, em dash, sentence, trigger phrases).
5. **Conventional commits.** Examples:
    - `feat(format): add diagram-it skill — draw the relationship, not the system`
    - `docs(readme): add diagram-it under format family`
    - `chore(plugin): register diagram-it skill`
6. **No `--no-verify`, no force-push.** If a hook fails, fix it.

## Reviewing your own PR

Before requesting review, check:

- [ ] `npx skills-ref validate` passes for the new skill folder.
- [ ] `name` in frontmatter matches the folder name.
- [ ] Description includes *what* + *when* + trigger phrases.
- [ ] Body is under ~150 lines.
- [ ] Voice matches existing skills (read yours aloud — does it sound
  like the same person wrote it?).
- [ ] Triggers cover formal + casual + symptom phrasings.
- [ ] Registered in `plugin.json` and linked in `README.md`.

## License

By contributing, you agree your contribution is licensed under the
repo's [MIT License](./LICENSE).
