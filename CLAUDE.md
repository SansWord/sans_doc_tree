<!-- This is a starter template. Every section below is a DEFAULT — keep, rewrite, or delete it to fit
     your project. The imperative voice is just how a coding agent reads instructions; once the content
     is yours, the tone works for the agent, it isn't a rulebook for you. Delete this comment when done. -->

# <!-- TODO: Project Name --> — Project Context

<!-- One short paragraph: what this project is. This file is AUTO-LOADED into every coding session,
     so it's prime real estate — keep it an INDEX, not an encyclopedia. Stable facts + links out;
     push detail into the docs/ leaves and link to them. -->

## Who's working on this

<!-- TODO: who you are + how you like the agent to work — this shapes every session. Examples:
     - "Prefer clear options with a recommendation over open-ended questions."
     - "Care about code quality and doc hygiene beyond shipping — proactively review for duplication."
     - "Surface decisions that are mine to make (scope, product framing, copy) — don't assume them." -->

## Current status

> **Where we are right now lives in two maintained sources — this section deliberately does NOT
> restate the version/phase, to avoid drift:**
> - **What's shipped** → [`docs/devlog.md`](docs/devlog.md) — the *top row* is the current state.
> - **What's next** → [`todo.md`](todo.md).

<!-- Below: only STABLE facts that rarely change — repo, hosting/CI, code shape, hard constraints. -->

## Locked decisions

> **Settled calls. The lock guards against *silent* drift — not against changing your mind on
> purpose.** Keep each as a one-liner pointing to the canonical doc (rule + rationale), so the
> decision lives in **one place**.
>
> **It depends on the phase:**
> - **Writing a plan from a spec, or implementing a plan → obey them.** These stages are about
>   fidelity, not invention — don't re-open or quietly work around a locked decision here. If the work
>   seems to *require* breaking one, **stop and surface it**; don't improvise past it.
> - **Brainstorming, spec'ing, or an explicit human decision → challenge them freely.** This is the
>   moment to revisit a constraint. If a new idea conflicts with a locked decision, name the conflict
>   and ask whether to (a) keep the decision or (b) unlock it. Past constraints shouldn't silently
>   block new thinking here — they should be visible so the choice is deliberate.
>
> **To unlock / change a decision (in the open, never silently):** update the canonical doc + this
> one-liner with the new rule, and **log the change and its reason** in [`docs/devlog.md`](docs/devlog.md)
> (or an ADR under `docs/decisions/` if your flow uses one). The superseded decision stays in the
> historical record, so the *why* of the change is preserved — then the new decision is the one to honor.

<!-- - **<decision>** — one-liner. Detail → [`docs/<canonical>.md`](docs/<canonical>.md). -->

## Docs

**Two tiers — keep the maintained docs current; the historical docs are allowed to go stale:**

- **Maintained `docs/*.md` (authoritative, kept up to date):** the source of truth; must match the
  code. The agent may **trust these for quick answers without opening the source**, so a stale line
  silently misleads — keep them exact. When you add a `docs/*.md`, add it to this list with a one-line
  description **and its update trigger** (when it must be refreshed).
  <!-- e.g. - [`docs/architecture.md`](docs/architecture.md) — modules, ownership, data flow.
            Update when a module is added/removed or ownership changes. -->
- **Historical (allowed to stale, but kept forever as decision history):** `docs/specs/*`,
  `docs/plans/*`, and `docs/devlog.md` — per-milestone thinking, a record of *how we got here*,
  **not** the source of truth. Don't trust them where they conflict with the code or this file.
  *(Optional historical types some flows add: `docs/decisions/` for ADRs made mid-build, and
  `docs/meeting-minutes/` for decisions/new directions from human discussions — same rule: append,
  keep, and fold any still-live decision into the maintained docs.)*

## Before you plan or build — consult the tree

Don't rely on whatever happens to already be in context. Before you plan a change, brainstorm, or
continue a module, **read the relevant docs first**, then plan against what you read:

- The maintained `docs/*.md` whose subject the task touches, plus the **Locked decisions** above.
- If the task continues earlier work, or a bug traces to a version, open that version's
  [`docs/devlog.md`](docs/devlog.md) entry and the spec/plan it links, and load those.

**Name the files you consulted** (e.g. "per `docs/architecture.md`…") so it's visible which docs
informed the plan — and so the user can catch it when a relevant doc was *not* read.

## Workflow — the dev cycle

The loop each milestone runs through (adapt to your tooling):

1. **Brainstorm → spec** before building; **plan** once the spec is agreed. Spec + plan land in the
   historical tier (`docs/specs/`, `docs/plans/`) — they may go stale later, and that's fine.
2. **Implement** against the plan.
3. **Fold lasting decisions into the maintained docs** (Locked decisions above, the relevant
   `docs/*.md`) — those, not the spec, are the source of truth afterward.
4. **Close the loop at end of session** (below): refresh maintained docs + devlog + todo.
5. The next round of discussion starts from these docs as the base — so the agent can spot where a new
   idea diverges from a past decision and surface it (see Locked decisions).

## Conventions

<!-- Capture conventions ONCE so every future session inherits them instead of relearning (or
     violating) them. Add your project-specific ones (naming, copy/voice, security rules…). A few that
     travel well: -->

- **Versioning:** three-part semver (`vX.Y.Z`); the devlog heading, git tag, and TL;DR row all match.
- **Staging: explicit paths only — never `git add -A` / `git add .`.** Blanket staging sweeps
  unrelated files into a commit. `git add` the exact files you changed; confirm scope with
  `git diff --name-only main...HEAD` before opening a PR.
- **Code comments describe the *current* state only** — no `// moved from…` / `// used to be…`
  breadcrumbs. History lives in git, not in source.
- **Escape user-supplied input** even when you render it verbatim ("verbatim" means don't *translate*
  it, not skip escaping).

## End-of-session checklist — close the loop

Updating the docs is a **gate, not a nicety** — do it before the work counts as done (e.g. before a
PR opens), and commit the doc changes **in the same PR** as the code:

1. **Update every maintained `docs/*.md`** whose subject this session touched, so it matches the
   shipped state. ("No docs needed" is a claim to justify, not a default.)
2. **Append a newest-on-top entry to [`docs/devlog.md`](docs/devlog.md)** (see Devlog format) and link
   it to this milestone's spec/plan.
3. **Update [`todo.md`](todo.md)** — clear done items, add next steps.

When the user says **"ship it"** / **"raise a PR,"** run this, commit, open the PR — then **stop**
(don't merge; that's the user's call). If the user heads to push/merge without it, **remind them** to
update the docs first. Letting `CLAUDE.md` hold these habits is the point — so no one has to remember.

## Devlog format

`docs/devlog.md` is **newest-first**; its top row is the current state. Each entry:

```
## vX.Y.Z — <title> (YYYY-MM-DD)
**Review:** not yet
**Design docs:** [spec](docs/specs/<file>.md) · [plan](docs/plans/<file>.md)   <!-- this version's spec/plan -->
**What was built:** <bullets>
**Key learnings:** <tagged bullets — [note] / [insight] / [gotcha]>
```

Linking each version to its spec/plan lets a later session pull the right history into context when it
revisits that module or traces a bug to a version. Keep a **TL;DR table** at the top — one row per
version, each linking to its section.

## Before committing

If the repo is (or will be) public, scan every commit for secrets / API keys / tokens, `.env*` files,
and private personal info beyond what's already public. This scan is load-bearing, not precautionary.
