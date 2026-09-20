# Research Incubator

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

This directory is for ideas that are still being investigated — before they are promoted into a playbook chapter.

## Why It Exists

Chapters 01–24 now form the current published chapter set.

This directory is for what has not yet earned a place in it: problems still under investigation, working hypotheses, counterexamples and open questions.

Recording an idea here is deliberately cheaper than changing a chapter. A note may be wrong, incomplete, or abandoned later. What matters is that the evidence behind it stays attached to it.

## Lifecycle

```text
Observation
↓
Research Note
↓
Challenge / Additional Evidence
↓
Derived Principle
↓
Reusable Pattern
↓
Promote into Playbook
```

A note moves down this list only when the evidence justifies it — not when it becomes convenient.

## Maturity Labels

| Label | Meaning |
|---|---|
| `Working Hypothesis` | A plausible explanation with limited evidence. Read it as a question, not a rule. |
| `Observed Pattern` | Seen repeatedly in real work, but the cause is not yet fully understood. |
| `Derived Principle` | Supported by repeated observation and by attempts to falsify it. May become a chapter once its practical implications are clear. |

The order above is a promotion path, never an assumption. Nothing skips a step because it feels convincing.

## What a Research Note May Contain

- observations from real work
- working hypotheses
- unresolved questions
- counterexamples and failed attempts
- practical evidence (logs, measurements, incident notes)
- derived principles
- reusable patterns

## What a Research Note Is Not

Research notes are not stable methodology. Nothing here should be cited as established practice, applied as a mandatory rule, or described as production-proven.

When a research note and a published chapter disagree:

- the research note does not automatically override the chapter;
- the conflict must be recorded explicitly;
- strong new evidence should trigger a challenge to the chapter;
- until the chapter is actually revised, the published version still governs.

In short:

> **Research can challenge the Playbook, but it cannot silently rewrite it.**

## When to Promote

A note is ready to be promoted when:

- the observation has been seen in more than one context;
- attempts to falsify it have failed or have been answered;
- the practical pattern is specific enough to reuse;
- its limits and open questions are written down.

Promotion means the material moves into a chapter, the chapter is marked `Evolving` or `Stable`, and the research note is reduced to a pointer to that chapter.

The bar for opening a new note out of a chapter open question is higher: it becomes a Research Note in its own right only when the question has turned into a fairly independent object of study, has real observational sources, and is worth tracking across chapters.

An unresolved question inside a chapter already belongs to that chapter. Not every open question needs a file.

## Status

Two notes are open, both at the earliest stage:

| Note | Topic | Maturity | Language |
|---|---|---|---|
| [Parallel execution, joins and dependency-driven orchestration](parallel-execution-and-dependency-orchestration.zh-CN.md) | Joins, dependency satisfaction and state conflicts when several agents run in parallel | Working Hypothesis | Chinese only |
| [Ownership, portability and platform independence of personal context](personal-context-ownership-and-portability.zh-CN.md) | Once personal context becomes a cross-project, cross-agent and cross-model collaboration asset, who owns it, how it moves and how it is authorised | Working Hypothesis | Chinese only |

The first came out of open questions left over from Chapters 14 and 16.

The second came out of Chapter 24, where it no longer belonged to the reality feedback main line and was therefore split out as an independent research thread.

Neither has a version outside Simplified Chinese yet, and neither has produced a reusable pattern.

---

[← Playbook README](../README.md) · [Chapter template](../templates/chapter-template.md)
