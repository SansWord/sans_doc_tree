# sans_doc_tree

A reusable starter for **agentic-coding context** — a "document tree" that keeps a coding agent
(Claude Code, and friends) aligned with your past decisions across sessions, with **automatic
awareness** and **lazy loading** so the context window stays focused.

> Based on the essay **[The document tree](https://sansword.github.io/sans_blog/doc-tree/)**.

## The idea in one breath

- One **root file** (`CLAUDE.md` / `AGENTS.md`) is auto-loaded every session. Keep it a small
  **index, not an encyclopedia**: stable facts + links out to topic docs.
- Topic docs live in `docs/` and are **lazy-loaded** — the agent opens only what the task needs, so
  working on module A doesn't drag module B's docs into the context window.
- **Two tiers:** *maintained* docs (must match the code) and *historical* docs (specs / plans /
  devlog — allowed to go stale). Label them so the agent knows which to trust.
- **One fact, one place.** Don't restate the version/roadmap in the root — point to the devlog's top
  row and `todo.md`.
- **Close the loop.** Every session ends by updating the touched `docs/*.md` and appending to
  `docs/devlog.md`, so knowledge accumulates into a growing rubric.

## How to use

1. Click **Use this template** (or copy these files into your repo).
2. Rename `CLAUDE.md` → `AGENTS.md` if your tool uses that name — the content is tool-agnostic.
3. Fill the `<!-- TODO -->` placeholders in `CLAUDE.md`.
4. Add topic docs under `docs/` (copy `docs/_templates/topic-doc.md`) and list each one in `CLAUDE.md`.
5. Build. End each session with the **End-of-session checklist** in `CLAUDE.md`.

## Layout

```
CLAUDE.md            ← auto-loaded root: small, stable facts + links out
todo.md              ← the roadmap ("what's next") — its single home
docs/
  devlog.md          ← append-only history that's also always current (newest on top)
  _templates/
    topic-doc.md     ← copy this to add a new maintained topic doc
  specs/             ← historical tier: per-milestone specs (allowed to go stale)
  plans/             ← historical tier: per-milestone plans (allowed to go stale)
```
