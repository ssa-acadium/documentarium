# documentarium

> Give an AI coding agent a methodology for cataloguing an unfamiliar web
> environment: frontend, edge, API, backend, data stores, third-party services
> and ops, into one written landscape document.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/format-Agent_Skills-blue)](https://agentskills.io/specification)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

**TL;DR** — Point it at a repo or staging site you've just got access to. It maps
before it reads, traces one request end to end, and hands you a `LANDSCAPE.md`
with every layer inventoried and every claim tied to a file path.

---

## The problem

You've been given access to a system nobody documented. The usual failure modes
are predictable: you open twenty files at random and never build a coherent model,
or you chase call sites through a layered stack and lose the thread. Both burn a week.

Agent tooling makes the *reading* faster but does nothing about the *method*. It
will happily summarise a codebase you don't understand yet, in words you can't
verify, and you'll build on top of confident guesses.

## What this does

`system-landscape` is an [Agent Skill](https://agentskills.io/specification) that
imposes a six-phase discovery loop on the agent and makes it produce a verifiable
artifact instead of a vibes-based summary.

| Phase | What happens | Output |
|---|---|---|
| 1. Shape | Metadata only. No source files. | One-page territory model |
| 2. Stack | Exact versions, not framework names | Version inventory |
| 3. Pattern | Which architecture is canonical, which is legacy | Pattern map |
| 4. Trace | One real user journey across every layer | Numbered boundary trace |
| 5. Write | Fill the inventory schema, sketch C4 L1 + L2 | `LANDSCAPE.md` |
| 6. Verify | Take open questions to a human, capture as ADRs | `docs/adr/*` |

### The design constraint that matters

Every row in the inventory carries an **Evidence** column: the file path, response
header, or command output that proves it.

This is the whole point. An inventory without evidence is a hallucination with
nice formatting.

## Install

Skills are plain files. Clone and copy into whichever agent you use.

```bash
git clone https://github.com/acadium/system-landscape.git
cd system-landscape
