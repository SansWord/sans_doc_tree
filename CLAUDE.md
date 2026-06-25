<!-- A starter — every section is a default; keep, rewrite, or delete it, and fill the <!-- TODO -->s.
     Want more structure (locked-decision logic, the dev cycle, a PR gate, devlog format, conventions)?
     See CLAUDE.advanced.md and copy the blocks you want into here. Only CLAUDE.md / AGENTS.md is
     auto-loaded — keep this file small. -->

# <!-- TODO: Project --> — Project Context

<!-- One paragraph: what this project is. This file is auto-loaded every session — keep it a small
     INDEX (stable facts + links out), not an encyclopedia. -->

## Who's working on this

<!-- TODO: who you are + how you like the agent to work — e.g. "give me clear options with a
     recommendation," "surface decisions that are mine to make (scope, copy)." -->

## Current status

> Not restated here, to avoid drift: **what's shipped** → top row of [`docs/devlog.md`](docs/devlog.md);
> **what's next** → [`todo.md`](todo.md).

<!-- Add only STABLE facts below — repo, hosting/CI, stack, hard constraints. -->

## Docs — two tiers

- **Maintained `docs/*.md`** — the source of truth; must match the code. The agent may trust these for
  quick answers without opening the source, so **keep them exact — a stale line silently misleads.**
  List each below with a one-line description.
  <!-- - [`docs/architecture.md`](docs/architecture.md) — modules & data flow. Update when a module changes. -->
- **Historical** — `docs/specs/`, `docs/plans/`, `docs/devlog.md`: how we got here; allowed to go
  stale, kept forever. **Don't trust them where they conflict with the code or this file.**

## Before you plan — read first

Before planning a change or continuing a module, **read the relevant `docs/*.md` first** (and any
settled decisions), then plan against them — and **name the files you consulted**, so it's visible
which docs informed the work, and obvious when a relevant one wasn't read.

## End of session — close the loop

Before a change is done: update the maintained `docs/*.md` it touched, add a newest-on-top entry to
[`docs/devlog.md`](docs/devlog.md), and update [`todo.md`](todo.md). This is what makes each session
leave the next one a little smarter.

<!-- Want the fuller checklist, locked-decisions logic, the dev cycle, and a "raise a PR" gate?
     They live in CLAUDE.advanced.md — copy in what you need. -->
