# Research Incubator

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

This directory is for ideas that are still being investigated — before they are promoted into a playbook chapter.

## Why It Exists

Chapters 01–07 are stable. Chapters 08–17 are still being written. This directory exists for what comes before both: an observation that has not yet earned a place in either.

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

When a research note and a chapter disagree, the chapter still governs — until evidence says otherwise. That is the point of keeping the two places separate.

## When to Promote

A note is ready to be promoted when:

- the observation has been seen in more than one context;
- attempts to falsify it have failed or have been answered;
- the practical pattern is specific enough to reuse;
- its limits and open questions are written down.

Promotion means the material moves into a chapter, the chapter is marked `Evolving` or `Stable`, and the research note is reduced to a pointer to that chapter.

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
