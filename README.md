# sans_doc_tree

A reusable starter for **agentic-coding context** — a "document tree" that keeps a coding agent
(Claude Code, and friends) aligned with your past decisions across sessions, with **automatic
awareness** and **lazy loading** so the context window stays focused.

> Based on the essay **[The document tree](https://sansword.github.io/sans_blog/doc-tree/)** — with a
> companion on verifying it: **[How to tell if it's working](https://sansword.github.io/sans_blog/doc-tree/how-to-tell/)**.

**This is a starting point, not a rulebook.** Every file here is a draft — keep, rewrite, or delete
anything to fit your project. The wording is opinionated on purpose, so you have something to react to.

## The idea in one breath

- One **root file** (`CLAUDE.md` / `AGENTS.md`) is auto-loaded every session. Keep it a small
  **index, not an encyclopedia**: stable facts + links out to topic docs.
- Topic docs live in `docs/` and are **lazy-loaded** — the agent opens only what the task needs, so
  working on module A doesn't drag module B's docs into the context window.
- **Two tiers:** *maintained* docs (must match the code) and *historical* docs (specs / plans /
  devlog — allowed to go stale, but **kept forever** as your decision history — never deleted). Label
  them so the agent knows which to trust.
- **One fact, one place.** Don't restate the version/roadmap in the root — point to the devlog's top
  row and `todo.md`.
- **Consult before you build.** The root file tells the agent to *read* the relevant docs before
  planning — and to flag when a new idea conflicts with a past decision, so you decide align-or-update.
- **Close the loop.** Every session ends by updating the touched `docs/*.md` and appending to
  `docs/devlog.md` (linking that entry's spec/plan), so knowledge accumulates into a growing rubric.
- **Let CLAUDE.md hold the habits.** Anything you'd otherwise have to remember — update the docs
  before a PR, honor locked decisions — lives in the root file, so the workflow runs without you
  policing it.

## Make it yours

Treat the files as clay, not law — three steps to start:

1. Click **Use this template** (or copy these files in). Rename `CLAUDE.md` → `AGENTS.md` if your tool
   uses that name — the content is tool-agnostic.
2. Open `CLAUDE.md`, fill the `<!-- TODO -->` bits (project, who you are, how you like the agent to
   work), and **cut any section that doesn't fit**.
3. Add your first topic doc (copy `docs/_templates/topic-doc.md` into `docs/`, list it under **Docs**),
   then build — and at session end, run the **End-of-session checklist**, tweaking it until the loop
   feels like yours.

**Or let your coding agent do it — paste this:**

```
Set up this repo's "document tree." Read README.md and CLAUDE.md, then ask me a few quick
questions to fill every <!-- TODO --> in CLAUDE.md — what this project is, who I am and how I
like you to work, the stable facts (repo / hosting / stack), and our conventions. Delete any
section that doesn't fit, keep the root file small (link out to docs/), and add a first topic
doc under docs/ listed in the Docs section. Then show me what you set up.
```

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
