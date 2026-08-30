# Appendix C — Cheat Sheet

[日本語](cheatsheet.ja.md) · **English** · [简体中文](cheatsheet.zh-CN.md)

## Three Core Principles

```text
1. AI is the execution layer.
2. Process creates productivity.
3. Constraints create stability.
```

## Five Rules for Task Design

| # | Rule | Question |
|---|---|---|
| 1 | One task, one objective | Are multiple outcomes mixed together? |
| 2 | Define completion | What observable evidence means done? |
| 3 | Define boundaries | What must not be changed? |
| 4 | Make it verifiable | Can the agent test or inspect its result? |
| 5 | Close the context | Is the necessary information together? |

## Minimum Task Contract

```text
summary:             desired outcome
currentAction:       work in this execution
acceptanceCriteria:  observable proof of completion
boundaries:          prohibited changes and non-goals
```

Do not hand off the task until all four fields are complete.

## Four Axes of Prompt Quality

| Axis | Check |
|---|---|
| Information density | Does every sentence affect execution? |
| Task boundaries | Are scope and non-goals explicit? |
| Context quality | Is unrelated history removed? |
| Constraint clarity | Are implicit expectations stated? |

## Context Isolation

Start a new session when responsibility changes, current state becomes hard to restate, old topics repeatedly return, or output quality declines. A handoff contains objective, decisions, specification, constraints, evidence, and acceptance criteria.

## Six Elements of Multi-Agent Management

```text
1. Roles            → who owns what
2. Constraints      → what each role must not do
3. Reporting        → changes, reasons, evidence, remaining work
4. Acceptance       → objective completion conditions
5. Failure handling → stop, record, escalate, recover
6. Handoffs         → explicit state transfer between phases
```

## Workflow Design

| Principle | Meaning |
|---|---|
| Template-driven | Follow a defined path; switch to a defined exception case |
| Compressed normal path | Replace and refine rules instead of endlessly adding them |
| Quality gates | Block transitions until evidence exists |
| Atomic rollback | Record reason, change state, and hand off together |
| Single source of truth | Keep authoritative state in one structured system |

## Verification Checklist

```text
□ Agent performed applicable self-checks
□ Changed files and diff were reviewed
□ No out-of-scope modification exists
□ Machine-verifiable checks are automated
□ Security, architecture, and business logic received human review
□ Claims are supported by primary sources or runtime evidence
□ A blocked agent stopped and produced a structured report
```

## Failure Patterns

| # | Pattern | Response |
|---|---|---|
| 1 | State first, log later | Make the transition atomic |
| 2 | Incomplete task handoff | Require the four fields |
| 3 | Everything in one session | One responsibility per session |
| 4 | Repeating rules manually | Version shared instructions |
| 5 | Working output as archive | Separate state from evidence |
| 6 | Well-intentioned scope drift | State prohibitions and non-goals |

## Final Question

```text
Can this system reproduce the same quality without me?

Yes → it is a process.
No  → it still depends on personal skill.
```

[← English README](../README.md)
