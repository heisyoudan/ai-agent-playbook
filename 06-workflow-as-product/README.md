# 06 — Designing Workflow as a Product

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

## Why a Workflow Is Necessary

Task design, context isolation, and role definitions improve individual sessions. But if people must remember and reconstruct those practices every time, quality still depends on personal discipline.

A workflow turns the method into an executable system. It determines how tasks enter, which role acts, what evidence is required, when state may change, and how failure returns to a safe point.

## Why I Built Maestro

I wanted the principles in this playbook to survive beyond a successful conversation. Maestro began as a way to encode task contracts, role boundaries, structured handoffs, quality gates, and recoverable transitions.

The relationship is simple:

```text
Playbook = methodology and operating principles
Maestro  = executable workflow framework
```

The framework is not the source of the methodology. It is a practical environment in which the methodology is exercised, tested, and refined.

## Template-Driven Execution

### Free Interpretation vs. Templates

| Mode | Behavior | Risk |
|---|---|---|
| **Free interpretation** | The agent invents the procedure from general instructions. | Decisions drift and output varies. |
| **Template-driven** | The agent follows a defined normal path and switches to a defined exception path. | Behavior is constrained and inspectable. |

```text
normal template
  ↓ exception detected
case template
  ↓ case complete
explicit handoff to the next phase
```

### Main Template

Each role and state needs:

- **Objective** — what this phase achieves;
- **Procedure** — steps to perform;
- **Completion conditions** — evidence required to leave the phase;
- **Allowed cases** — exceptions that may interrupt the normal path.

### Case Template

Each exception needs:

- **Trigger** — the condition that activates it;
- **Applicability** — roles and states in which it is valid;
- **Procedure** — how to handle the exception;
- **Completion** — when the case is resolved;
- **Handoff** — who acts next and with what state.

## Compress the Normal Path; Explain Exceptions

The normal path should become shorter as the workflow matures. Add a rule only when it measurably reduces ambiguity, error, or communication cost.

- Replace outdated rules instead of stacking new ones indefinitely.
- Remove duplicate templates and expired operational knowledge.
- Keep unusual and dangerous paths explicit, because that is where improvisation is costly.

**Rules are not a collection to grow. They are a product to refine.**

## Quality Gates

A gate determines whether a phase may transition.

```text
Dev
  ↓ Gate: journal exists; build and required checks pass
QA
  ↓ Gate: test results and evidence are recorded
Sage / closure
```

If a condition fails, the next phase cannot begin. A gate converts quality from an intention into a structural requirement.

## Atomic Rollback

When work is rejected or returned, three things must happen together:

```text
1. Record the reason and evidence.
2. Change the state.
3. Generate the next handoff.
```

If state changes before the reason is recorded, the next role sees an unexplained transition. Treating these steps as one operation prevents that gap.

## Single Source of Truth

Chat history is not a reliable task database. It is incomplete, difficult to query, and full of competing interpretations.

Keep authoritative state in one structured system:

```text
current task state     → tasks
execution history      → journal entries
gate evidence          → gate runs
transition history     → transition requests
supplemental context   → task notes
```

Agents should read the authoritative data, not depend on someone retelling the conversation.

## Workflow as a Reusable Product

Once encoded, the workflow can be reused across projects, agents, and platforms.

```text
platform-independent core templates
                 ↓ derive
Codex / Copilot / other platform-specific instructions
```

Platform files are delivery formats, not the source of truth. Maintain the core method and derive adapters from it.

## Command-Driven Work in Practice

### Without a Workflow System

The human repeatedly reconstructs background, collects files, lists constraints, explains completion, summarizes results, and prepares the next handoff. Each cycle adds explanation and transmission cost.

### With a Workflow System

```text
Sage issues a task
  ↓ structured task and Dev instruction are generated
Dev executes and records evidence
  ↓ QA instruction is generated
QA verifies independently
  ↓ exception is recorded or task is closed
```

The human remains responsible for decisions and high-risk approval, but no longer has to manually rebuild ordinary context at every transition.

### What the Difference Means

The value is not automation by itself. It is **fixing the methodology into an executable structure and reducing friction between humans and agents**.

Task contracts, isolated responsibilities, explicit constraints, templates, gates, and structured handoffs make a command-driven workflow possible. Without those foundations, a new tool merely moves the same explanation cost elsewhere.

---

> **Practice note**
> Maestro applies this architecture by deriving platform-specific instructions from a shared workflow core. The platform can change while the operating method remains stable.

[Next → Where the Real Competitive Advantage Lies](../07-what-really-matters/README.md)
