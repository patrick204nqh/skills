---
name: slide-deck
description: Turns content into a short slide deck where every slide has one idea, the headline states the takeaway (not the topic), and speaker notes hold what the presenter says aloud. Make sure to use this skill whenever the user says "make slides", "deck", "presentation", "slidify this", "turn this into slides", "PowerPoint", "Keynote", or asks to present something to an audience — even if they don't use those exact phrases.
---

# slide-deck

Build a deck where every slide earns its place. One idea per slide. The
headline is what the audience should *conclude*, not what the slide is
*about*.

## Audience

People in a room (or staring at a Zoom tile). They will read the
headline in two seconds while you're still talking. The body exists
for the person reviewing the deck later, or the one in the back row
who tuned out for thirty seconds. The slide is your scaffold; *you*
are the presentation.

## When to use

Trigger on any of:
- "make slides" / "slide deck" / "deck" / "presentation"
- "turn this into slides" / "slidify" / "for a presentation"
- "PowerPoint" / "Keynote" / "Google Slides"
- The user is preparing to present to a group and asks for help

Do **not** trigger when:
- One slide is enough — write a one-pager instead.
- The content is fundamentally a narrative argument best read in
  order. A deck flattens; prose threads.
- Slides are decorative wrapping for a memo. If the audience could
  read it as a memo, send a memo.

## The arc

A deck is not a pile of slides. It is a three-part structure:

1. **First slide states the answer.** BLUF. The decision, the
   recommendation, the finding. Not "Q3 Review" but "We should kill
   Project Atlas. Three reasons follow."
2. **Middle slides build the case.** One reason per slide, in the
   strongest-to-weakest order — your audience may stop paying
   attention before slide five.
3. **Last slide states the ask.** What you want the audience to *do*.
   Not "Thank you / Questions?" — those are decoration. "We need
   $200k by end of month. Sign-off today, or we lose the window."

If you cannot write the first slide and the last slide in one
sentence each, you are not ready to write the middle.

## Rules

1. **One idea per slide.** If a slide has two arguments, split it.
   Two thin slides beat one fat one.
2. **Headline is the takeaway, not the topic.** Wrong: "Q4 Results."
   Right: "Q4 revenue beat target by 8%, driven entirely by APAC."
   The headline is a sentence with a verb.
3. **Body supports the headline.** Up to three bullets, or one
   chart, or one image. No body that doesn't reinforce the headline.
4. **Speaker notes ≠ slide content.** Speaker notes are what you
   *say*. Slide body is what they *see*. Never duplicate. If the
   body says everything you'll say, the audience reads instead of
   listening — and they read faster than you talk.
5. **No filler slides.** No "Agenda", "Thank you", "Questions?",
   "About me". Every slide pays its way with a takeaway.
6. **Cut by half.** Whatever your draft length is, halve it. The
   slides you delete are the ones no one missed.
7. **Numbers belong on slides; reasoning belongs in notes.** A slide
   that says "Up 8%" is a slide. A slide that explains *why* it's up
   8% is prose pretending to be a slide.

## Format

Emit each slide as a small block. The user (or their host) renders
into the actual deck tool.

```
---
# Slide N

**Headline:** [one sentence, has a verb, states the takeaway]

**Body:**
- [bullet — supports headline, ≤10 words]
- [bullet — supports headline, ≤10 words]
- [bullet — supports headline, ≤10 words]

  *(or: a chart description, or a single image cue — not all three)*

**Speaker notes:** [2–4 sentences of what the presenter says aloud.
The story, the caveat, the joke, the segue to the next slide.]
---
```

## Example

**Bad** (topic headline, body that overlaps speaker notes):

```
# Slide 3
**Headline:** Project Atlas Status
**Body:**
- Project Atlas has been running for 18 months
- We've spent $1.2M so far
- We expected to launch in Q2 but slipped to Q4
- Engineering team is burnt out
- Customer interviews suggest weak demand
- We should consider whether to continue
**Speaker notes:** I'll walk through the Atlas status.
```

**Good** (takeaway headline, tight body, notes carry the story):

```
# Slide 3
**Headline:** Atlas is 6 months late, $1.2M in, and customers don't want it.

**Body:**
- 18 months in, Q4 slip from Q2
- $1.2M spent, $400k more to finish
- Customer interviews: weak demand signal

**Speaker notes:** This is the slide where I lose the room or keep it.
The timeline and spend are facts — they'll see those. The thing they
won't see unless I say it: the customer interviews we ran in October
told us the wedge isn't there. That's the reason to kill it, not the
spend.
```

## What you are not doing

- You are not writing a document with slide breaks. A deck is a
  *talk*; a doc is a *read*.
- You are not decorating. No icons, no stock photos, no animated
  transitions in your output. Those are the user's call at render
  time.
- You are not writing the *whole talk* on the slides. The slides are
  what survives without you. *You* are what makes the deck land
  while you're in the room.
- You are not building a "comprehensive" deck. Comprehensive = long.
  Long = unread. Cut.
