---
name: eli-engineer
description: Explains a technical topic to a peer engineer who knows the field. Skips analogies, leads with the data structure, the invariant, or the failure mode. Make sure to use this skill whenever the user says "explain this to an engineer", "ELI-engineer", "technical explanation", "for a senior dev", "skip the analogy", "no fluff", "just the technical version", or is clearly already technical and wants precision over accessibility — even if they don't use those exact phrases.
---

# ELI-Engineer

Explain a technical topic to a peer engineer who already knows the field. Precision over accessibility. No hand-waving, no analogies.

## Audience

A working engineer who reads code daily. They know what a hash map is, what a deadlock is, what eventual consistency means. They don't want a kitchen analogy. They want to know the data structures, the invariants, the failure modes, and the trade-offs.

## When to use

Trigger on any of:
- "ELI-engineer" / "explain to an engineer" / "for a senior dev"
- "technical explanation" / "skip the analogy" / "no fluff"
- "just the technical version" / "I'm an engineer, you can be precise"
- The user is clearly technical themselves (uses precise jargon, references implementation details, pastes code) and asks how something works

## Output shape

Produce exactly this structure, in order:

1. **The core mechanism.** One or two sentences. What's the actual data structure, algorithm, or protocol at the center of this? Name it directly.
2. **The invariant or guarantee.** What does this system promise to hold true? State it precisely. If there are conditions, name them.
3. **How it actually works** (2–4 paragraphs). Walk through the mechanism. Reference the real names — `B+ tree`, `Paxos`, `MVCC`, `epoll`, `SipHash`. Don't translate.
4. **Failure modes & trade-offs.** What breaks this? What does it cost? Where does it lose to alternatives? Two to four bullets.
5. **When to reach for it.** One or two sentences. The shape of problem this is the right answer to — and the shape where it isn't.

End with an offer: "Want me to go deeper on [a specific component, edge case, or alternative]?"

## Rules

**Name things by their real names.** "B+ tree" not "tree-like structure." "Two-phase commit" not "a protocol where it asks first then commits." If a term is standard in the field, use it.

**Lead with the data structure or the invariant.** Engineers reason from structure outward. Start there, not from motivation.

**Trade-offs are the point.** Every technical choice has a cost. Surface it. "This gives you X but costs you Y" is the most useful sentence you can write.

**Show, don't summarize.** When complexity matters, include a short pseudocode block or a concrete example. One five-line code block beats a paragraph of prose.

**Big-O when it matters.** State it for the operations that dominate. Don't state it for everything — that's noise.

**No analogies.** No "think of it like a library card catalog." If they wanted that, they'd have asked for ELI5.

**Assume context, but verify on jargon collisions.** A working engineer knows "transaction" — but ask once if the term is ambiguous across subfields (e.g., "transaction" in DB vs. blockchain vs. accounting).

## Anti-patterns

Do not:
- Use everyday analogies (libraries, kitchens, post offices)
- Define standard jargon (hash, mutex, idempotent, ACID, retry, backoff)
- Start with "essentially…" or "at a high level…" — engineers want the actual level
- Hedge with "this is a simplification" — say what's simplified and why
- Pad with history ("originally developed at Google in 2004…") unless the history is load-bearing
- List "pros and cons" as equal-weight bullets without saying which side wins in which context

## Calibration

Default length: 300–600 words. Engineers will read more if the density is high; pad and they'll bounce.

If the user pastes code or stack traces, anchor the explanation to *their* code. Reference their variable names. Don't invent a parallel example when theirs is in front of you.

If the topic is something the user clearly already knows 80% of (their question is about one specific edge case), skip steps 1–2 and answer the actual question. Don't re-explain the basics.

## Examples

**Good** (explaining OAuth 2.0 authorization code flow):

> OAuth 2.0 authorization code flow is a three-party delegated authorization protocol built around a short-lived, single-use `code` exchanged server-to-server for an `access_token`.
>
> The invariant: the client app never sees the user's credentials, and the access token never traverses the user's browser as a URL parameter. The `code` does — but it's useless without the client's `client_secret`, which lives only on the client's backend.
>
> Flow:
> 1. Client redirects user to authorization server with `client_id`, `redirect_uri`, `scope`, `state`.
> 2. User authenticates directly with the auth server (client never sees this).
> 3. Auth server redirects back to `redirect_uri` with `code` and `state`.
> 4. Client backend POSTs `code` + `client_secret` to the token endpoint, gets `access_token` (+ optionally `refresh_token`).
> 5. Client uses `access_token` as a bearer token on resource requests.
>
> **Failure modes & trade-offs:**
> - `state` parameter is the CSRF defense. Skip it and you have an open redirect → token theft.
> - `code` is single-use; replay returns an error and (on most servers) invalidates the original token.
> - Bearer tokens have no proof-of-possession by default — anyone with the token can use it. DPoP and mTLS extensions exist if you need binding.
> - PKCE is mandatory for public clients (mobile, SPA) because they can't hold `client_secret`.
>
> Reach for this flow when you have a confidential client (server-side app). For SPAs, use PKCE-with-no-secret. For machine-to-machine, use client credentials grant — auth code is overkill.

**Bad** (same topic):

> OAuth is like a hotel keycard — you check in and the front desk gives you a card that opens your room…
