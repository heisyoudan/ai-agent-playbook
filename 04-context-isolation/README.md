# 04 — Context Isolation Strategy

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

## Every Conversation Accumulates Contamination

When requirements, implementation, test design, bug fixing, and unrelated discussion share one long session, the context becomes progressively less reliable.

Old assumptions remain visible. Failed approaches compete with accepted decisions. The agent has to infer which parts still matter, so output becomes less stable and rework increases.

## Why Contamination Happens

The model treats most of the current conversation as potentially relevant. Humans can often dismiss an earlier idea as obsolete without effort; a model may continue to use it unless the state is restated clearly.

Context is therefore not just a storage limit. It is an attention and responsibility boundary.

## One Session, One Responsibility

Open separate sessions and give each one a single role.

| Session | Responsibility | Include | Exclude |
|---|---|---|---|
| A | Requirements | scope, decisions, boundaries | implementation attempts |
| B | Implementation | technical contract, code, constraints | unresolved requirement debate |
| C | Testing | cases, evidence, expected behavior | implementation history |
| D | Review | acceptance, design quality, unintended changes | new feature work |

## Before and After Isolation

### Before

```text
requirements + implementation + tests + fixes = mixed context
→ unclear current responsibility
→ partial output
→ more rework
```

### After

```text
requirements session → stable decisions
implementation session → focused change
testing session → independent evidence
review session → objective evaluation
```

## Bridging Sessions

Isolation creates a handoff problem: how does the next session receive decisions without inheriting all the noise?

Use a structured bridge rather than “we discussed this earlier.”

```text
Objective: Implement sorting for the user table.
Decisions: Client-side only; server-side sorting is out of scope.
Specification: name, email, and createdAt are sortable.
Constraints: Do not change the API or add a package.
Acceptance: Ascending and descending sorting works for all three columns.
```

A bridge costs less than reconstructing lost context after a wrong implementation.

## When to Start a New Session

Consider a new context when:

1. the responsibility changes, such as requirements to implementation;
2. the number of files, unresolved decisions, or conversational turns makes current state hard to restate;
3. the discussion repeatedly returns to old topics;
4. output quality declines under otherwise comparable instructions.

Fifteen to twenty exchanges can be a warning signal, not a universal limit. Content and responsibility matter more than the raw turn count.

## Is This Extra Work?

At first it can feel slower. In practice, context isolation also organizes human thinking. Requirements remain requirements, implementation can converge, and testing can challenge the result independently.

**Context isolation is both a model-control strategy and a work-quality strategy.**

---

> **Practice note**
> Maestro separates management, development, QA, and design responsibilities. Each role has explicit authority boundaries, so context isolation is enforced by the workflow rather than remembered by the operator.

[Next → Managing Multiple Agents](../05-agent-management/README.md)
