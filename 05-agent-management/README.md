# 05 — Managing Multiple Agents

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

## The Problem Beyond Session Isolation

Once responsibilities are split across sessions, another cost appears: the same rules must be repeated for every agent and every conversation.

Examples include execution order, failure reporting, file boundaries, documentation rules, and when approval is required. Repeating them manually creates drift and preparation overhead.

## When the Question Changes

The question changes from “How should I prompt this agent?” to **“How should I manage several AI executors as a system?”** This is now a team-design problem.

## Six Elements to Define

### 1. Roles

Assign a clear responsibility to each role.

```text
Sage:   issue tasks, decide handoffs, handle exceptions, close work
Dev:    understand tasks, implement logic, record work, pass gates
QA:     design and run tests, judge results, report evidence
Design: implement UI with mock data, iterate visually, define interfaces
```

Design is separate because UI work is exploratory: comparison, visual judgment, and repeated adjustment are normal. Logic work is convergent: it seeks correctness, stability, closure, and verification.

Mixing these cognitive modes damages both. Design therefore avoids business logic and uses mock data; Dev connects the approved interface to real behavior.

### 2. Constraints

Define prohibited behavior as carefully as assigned work.

- Dev does not rewrite requirements.
- QA does not silently fix implementation.
- Design does not implement business logic.
- No role changes unrelated files.
- High-risk or irreversible actions require human approval.

Agents often expand scope with good intentions. Explicit non-goals make the change surface predictable.

### 3. Reporting Format

Use a stable report structure:

```text
Changed: files and behavior
Why: decision and rationale
Verified: commands, checks, and results
Remaining: risks, limits, unfinished items
Next: required handoff or action
```

A fixed format reduces the work required to understand and transfer results.

### 4. Acceptance Criteria

“Looks good” is not an acceptance criterion. Completion should be observable: a build passes, a scenario behaves as specified, a diff stays inside boundaries, or required evidence exists.

If completion cannot be judged objectively, the task was not ready to execute.

### 5. Failure Handling

Define what happens when an agent is blocked:

- stop after the retry or cost limit;
- record the error and evidence;
- list attempted approaches and changed assumptions;
- do not hide partial work behind a completion state;
- hand control to the designated role or human owner.

### 6. Handoffs

A handoff must transfer state, not conversational memory.

It should include the objective, accepted decisions, changed artifacts, evidence, remaining risks, and the exact responsibility of the receiver.

## How Rules Reach Agents

Do not rely on manually pasting the same instructions into every chat. Keep shared rules in versioned configuration or templates, then add only task-specific context.

```text
shared role and safety rules
        +
task contract and local context
        =
executable instruction
```

The shared layer should be small, stable, and platform-independent where possible.

## What This Changes

With roles, constraints, reports, acceptance, failure behavior, and handoffs defined, agent collaboration becomes less like a series of improvised conversations and more like an operating system for work.

The goal is not maximum autonomy. The goal is predictable execution, visible state, bounded authority, and recoverable failure.

---

> **Practice note**
> Maestro encodes these role and transition rules so the operator does not have to reconstruct them for each session. The methodology defines the behavior; the framework makes it executable.

[Next → Designing Workflow as a Product](../06-workflow-as-product/README.md)
