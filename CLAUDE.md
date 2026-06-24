# <!-- TODO: Project Name --> — Project Context

<!-- One short paragraph: what this project is. This file is AUTO-LOADED into every coding session,
     so it's prime real estate — keep it an INDEX, not an encyclopedia. Stable facts + links out. -->

## Who's working on this

<!-- TODO: who you are + how you like the agent to work. Example:
     "Prefer clear options with a recommendation over open-ended questions. Care about code quality
     and doc hygiene beyond shipping — proactively review for duplication." -->

## Current status

> **Where we are right now lives in two maintained sources — this section deliberately does NOT
> restate the version/phase, to avoid drift:**
> - **What's shipped** → [`docs/devlog.md`](docs/devlog.md) — the *top row* is the current state.
> - **What's next** → [`todo.md`](todo.md).

<!-- Below: only STABLE facts that rarely change — repo, hosting/CI, code shape, hard constraints. -->

## Docs

**Two tiers — keep the maintained docs current; the historical docs are allowed to go stale:**

- **Maintained `docs/*.md` (authoritative, kept up to date):** the source of truth, must match the
  code. When you add a new `docs/*.md`, add it to this list with a one-line description.
  <!-- e.g. - [`docs/architecture.md`](docs/architecture.md) — modules, ownership, data flow -->
  <!-- e.g. - [`docs/conventions.md`](docs/conventions.md) — naming, voice, release flow -->
- **Historical `docs/specs/*` + `docs/plans/*` (allowed to stale):** per-milestone thinking — a
  record of *how we got here*, **not** the source of truth. Don't trust them where they conflict with
  the code or this file. **These files are kept permanently — never deleted.** "Stale" means their
  content may drift over time; they remain as your product-decision history.

## Conventions

<!-- Capture conventions ONCE so every future session inherits them instead of relearning (or
     violating) them: naming, copy/voice, branching & release flow, security rules
     ("escape user input even when you render it verbatim"), etc.
     Pin doc-specific rules to the doc they govern, e.g.
     "keep docs/architecture.md up to date whenever you add or remove a module." -->

## End-of-session checklist — close the loop

Before the work counts as done, every session:

1. **Update the maintained `docs/*.md`** touched this session so they match the code.
2. **Append a newest-on-top entry to [`docs/devlog.md`](docs/devlog.md)** — what shipped + key learnings.
3. **Update [`todo.md`](todo.md)** — clear done items, add next steps.

This is what turns a pile of one-off sessions into a growing, accumulating rubric — each session
leaves the next one a little smarter.
