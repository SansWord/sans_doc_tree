<!-- ADVANCED MENU — not auto-loaded (only CLAUDE.md / AGENTS.md is). These are the blocks NOT in the
     default CLAUDE.md. When you want one, copy it into CLAUDE.md and replace any matching stub — one
     fact, one place. -->

# Governance menu — extras beyond the default

The default `CLAUDE.md` already ships: **Locked decisions · Docs two-tier · Before-you-plan ·
Workflow/dev cycle (superpowers) · End-of-session PR gate · Conventions · Before-committing scan.**
The blocks below are the *extras* — copy into `CLAUDE.md` if/when you want them.

## Unlock protocol — change a Locked decision (the detailed version)

> The default carries a one-line rule ("update the canonical doc + log it in the devlog"). This is the
> fuller discipline:

Changing a locked decision must be **deliberate and logged, never silent**:

1. Update the canonical doc/section with the new rule, and the one-liner in `CLAUDE.md` Locked decisions.
2. **Log the change and its reason** in `docs/devlog.md` (or an ADR under `docs/decisions/`). The
   superseded decision stays in the historical record, so the *why* of the change is preserved.

Past constraints shouldn't silently block new thinking — make the change visible so the choice is
deliberate, then the new decision is the one to honor.

## ADR flow — Architecture Decision Records (`docs/decisions/`)

Record each significant decision as `docs/decisions/NNNN-<slug>.md` (context · decision · why ·
consequences), dated and append-only — copy [`docs/_templates/adr.md`](docs/_templates/adr.md).

**Tier rule:** an ADR is the *historical record* ("we decided X, and why, on this date"). The **current
enforced rule** lives in a maintained doc (`docs/*.md` or `CLAUDE.md` Locked decisions) — that's what
the agent obeys. The ADR is the paper trail; the maintained doc is the source of truth.

## Deeper "before you plan" guidance

Fold into the Before-you-plan block as the tree grows:

- **Trace to a version:** if the task continues earlier work or a bug traces to a version, open that
  version's `docs/devlog.md` entry and the spec/plan it links, and load those.
- **Write pointers worth following:** in the Docs list, say what each doc *decides* and *when to read
  it*, not just its name — a bare filename gets skipped; *"product rules — read before any product/UX
  choice"* gets opened. The structure only works if the agent actually follows the link.

## Optional historical types

- `docs/decisions/` — ADRs (see above).
- `docs/meeting-minutes/` — human-discussion decisions / new directions, when those happen outside the
  brainstorm→spec flow.
