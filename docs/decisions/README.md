# Historical tier — decisions (ADRs)

**Architecture Decision Records** — one short file per significant decision: the context, the options,
what you chose, and **why**. Append-only and **kept forever** (allowed to go stale). When a decision
changes, add a *new* ADR that supersedes the old one — don't rewrite history.

**Tier rule (the important bit):** an ADR is the *historical record* of a decision and its rationale.
The **current rule** that decision enforces lives in a **maintained** doc — a `docs/*.md` or
`CLAUDE.md`'s Locked decisions — and *that* is what the agent obeys. The ADR says *"we decided X, and
why, on this date"*; the maintained doc says *"X is the rule."* Don't make the ADR the source of truth.

Copy [`../_templates/adr.md`](../_templates/adr.md) to add one (e.g. `0007-leaderboard-storage.md`).

This folder is **optional** — delete it if you'd rather log decisions in the devlog instead.
