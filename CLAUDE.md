<!-- A starter — every section is a default; keep, rewrite, or delete it, and fill the <!-- TODO -->s.
     This default is "batteries-included": it bakes in locked-decisions logic, the superpowers dev
     cycle, a PR gate, conventions, and a pre-commit scan. Want it leaner, or want extra blocks (ADRs,
     a stricter unlock protocol)? See CLAUDE.advanced.md. Only CLAUDE.md / AGENTS.md is auto-loaded —
     keep this file an INDEX (stable facts + links out), not an encyclopedia. -->

# <!-- TODO: Project --> — Project Context

<!-- One paragraph: what this project is. Auto-loaded every session — a small INDEX, not an
     encyclopedia. Shared conventions kept in a global ~/.claude/CLAUDE.md (semver, devlog format,
     house style) don't need restating here. -->

## Who's working on this

<!-- TODO: who you are + how you like the agent to work — e.g. "give me clear options with a
     recommendation," "surface decisions that are mine to make (scope, copy)." -->

## Current status

> Not restated here, to avoid drift: **what's shipped** → top row of [`docs/devlog.md`](docs/devlog.md);
> **what's next** → [`todo.md`](todo.md).

<!-- Add only STABLE facts below — repo, hosting/CI, stack, hard constraints. -->

## Locked decisions

> Settled calls. **Implementing/planning → obey them.** **Brainstorming or an explicit human decision →
> challenge freely.** If a new idea conflicts with one, name the conflict and ask align-or-unlock; to
> change one, update the canonical doc + log it in [`docs/devlog.md`](docs/devlog.md). Keep each a
> one-liner pointing to the canonical doc (rule + rationale) — one fact, one place.

<!-- - **<decision>** — one-liner. Detail → [`docs/<canonical>.md`](docs/<canonical>.md). -->

## Docs — two tiers

- **Maintained `docs/*.md`** — the source of truth; must match the code. The agent may trust these for
  quick answers without opening the source, so **keep them exact — a stale line silently misleads.**
  List each below with a one-line description **and its update trigger**.
  <!-- - [`docs/architecture.md`](docs/architecture.md) — modules & data flow. Update when a module changes. -->
- **Historical** (how we got here; allowed to go stale; kept forever):
  [`docs/superpowers/specs/`](docs/superpowers/specs/), [`docs/superpowers/plans/`](docs/superpowers/plans/),
  and [`docs/devlog.md`](docs/devlog.md). **Don't trust them where they conflict with the code or this
  file.** (The specs/plans paths are the **superpowers plugin defaults** — see the dev cycle below.)

## Before you plan — read first

Before planning a change or continuing a module, **read the relevant `docs/*.md` first** (and the
Locked decisions above), then plan against them — and **name the files you consulted**, so it's visible
which docs informed the work, and obvious when a relevant one wasn't read.

## Workflow — the dev cycle (superpowers)

Each milestone: **brainstorm → spec → plan → implement → fold decisions into the maintained docs.**

1. **Brainstorm/spec** with `superpowers:brainstorming` → saves to `docs/superpowers/specs/`.
2. **Plan** with `superpowers:writing-plans` → saves to `docs/superpowers/plans/`.
3. **Implement** against the plan (`superpowers:executing-plans` / `superpowers:subagent-driven-development`).
4. Specs & plans are **historical** (allowed to go stale). Afterward, **fold lasting decisions into the
   maintained docs** (Locked decisions / a `docs/*.md`) — those, not the spec, are the source of truth.
5. **Phase handoff:** run each phase (brainstorm / plan / execute) in a fresh session, carrying only the
   written doc forward.

## End of session — close the loop (a gate before any PR)

Updating docs is a **gate, not a nicety** — before a change is done / before a PR opens:

1. Update every maintained `docs/*.md` the session touched. ("No docs needed" is a claim to justify.)
2. Append a newest-on-top entry to [`docs/devlog.md`](docs/devlog.md), linking its spec/plan.
3. Update [`todo.md`](todo.md).

When the user says **"ship it" / "raise a PR":** run this, commit the doc changes **in the same PR** as
the code, open the PR — then **stop; don't merge** (the user's call). If they head to push without it,
**remind them**. Letting `CLAUDE.md` hold these habits is the point — so no one has to remember.

## Conventions

<!-- Add project-specific ones (naming, copy/voice, security). A few that travel well: -->

- **Staging: explicit paths only** — never `git add -A` / `git add .`. Confirm scope with
  `git diff --name-only main...HEAD` before a PR.
- **Code comments describe the *current* state only** — no "moved from…" / "used to be…" breadcrumbs;
  history lives in git.
- **Escape user-supplied input** even when you render it verbatim ("verbatim" means don't *translate*
  it, not skip escaping).

## Before committing (load-bearing)

If the repo is (or will be) public, scan **every** commit for secrets / API keys / tokens, `.env*`
files, and private PII beyond what's already public. This scan is load-bearing, not precautionary.

<!-- Want a stricter unlock protocol, or ADRs under docs/decisions/? Those blocks live in
     CLAUDE.advanced.md — copy in what you need. -->
