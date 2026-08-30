# AI Agent Playbook — English Overview

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

> A practical methodology for AI-agent collaboration, distilled from two years of production use in large-scale payment systems.

> This is the English overview. The detailed chapters currently remain in Japanese; the operational-readiness appendix is also available in English.

---

## What This Is

AI collaboration does not become reliable merely because a stronger model or a better prompt is available.

The durable advantage comes from designing the work around the model: choosing the right task size, isolating context, making constraints explicit, verifying outputs, and turning a successful workflow into a repeatable system.

This playbook organizes those practices into a platform-independent methodology.

## Who It Is For

- Engineers using AI at work but not yet getting consistent results
- Practitioners who feel that managing an agent can cost more than doing the work themselves
- Technical leaders introducing AI-assisted delivery at team or organization level
- Interviewers and candidates discussing practical AI collaboration

## Core Principles

```text
AI is the execution layer.
Process creates productivity.
Constraints create stability.
```

Coding skill still matters: it supports judgment, debugging, design, and verification. What is changing is the scarcity of producing routine code by hand. The goal is not to discard engineering fundamentals, but to combine them with task design, context management, verification, and workflow engineering.

## Contents

| Chapter | Topic | Main idea |
|---|---|---|
| [01](01-ai-redefines-work/README.md) | AI Redefines Work *(Japanese)* | AI changes where engineering value and bottlenecks sit. |
| [02](02-task-granularity/README.md) | Task Granularity *(Japanese)* | A task must be small enough to finish independently and large enough to close one useful loop. |
| [03](03-prompt-philosophy/README.md) | “Complex Minimalism” *(Japanese)* | Maximize relevant information while minimizing noise. |
| [04](04-context-isolation/README.md) | Context Isolation *(Japanese)* | One session, one responsibility; bridge sessions with structured handoffs. |
| [05](05-agent-management/README.md) | Multi-Agent Management *(Japanese)* | Define roles, constraints, reporting, acceptance, failure handling, and handoffs. |
| [06](06-workflow-as-product/README.md) | Workflow as a Product *(Japanese)* | Encode repeatable procedures, gates, rollback, and a single source of truth. |
| [07](07-what-really-matters/README.md) | What Really Matters *(Japanese)* | The long-term advantage is system design, not attachment to one tool. |

### Appendices

| Appendix | Topic |
|---|---|
| [A](appendix/anti-patterns.md) | Common failure patterns *(Japanese)* |
| [B](appendix/verification-strategies.md) | Verification strategies *(Japanese)* |
| [C](appendix/cheatsheet.md) | Cheat sheet *(Japanese)* |
| [D](appendix/operational-readiness.en.md) | Operational readiness and governance *(English)* |

## The Method in One Loop

1. **Classify risk.** Decide what the agent may do, what requires approval, and what must remain human-owned.
2. **Define one objective.** State the intended outcome, current action, acceptance criteria, and boundaries.
3. **Provide a closed context.** Include only the files, facts, decisions, and constraints needed for the task.
4. **Let the agent execute and self-check.** Require builds, tests, linting, or other applicable evidence.
5. **Review the delta.** Inspect changed files, unintended scope, high-risk logic, and the evidence behind claims.
6. **Record and hand off.** Persist decisions and evidence in a structured source of truth, then start a clean context for the next responsibility.
7. **Measure and improve.** Track rework, escaped defects, review time, cost, and exceptions—not output volume alone.

## Minimum Task Contract

```text
summary:             What outcome should be achieved?
currentAction:       What should be done in this execution?
acceptanceCriteria:  What observable checks define completion?
boundaries:          What must not be changed or attempted?
```

If one of these fields is missing, the task is not ready to delegate.

## Scope and Responsibility

An agent proposes and executes; it does not remove human accountability. Security, authorization, payment behavior, privacy, compliance, production release, destructive operations, and irreversible external actions need explicit owners and approval rules.

Model agreement is not evidence. Verify factual claims against primary documentation, source code, tests, runtime output, or measurements. Keep short-lived working state separate from audit and release evidence that must be retained.

## Reading Paths

| Situation | Suggested path |
|---|---|
| Limited time | Chapters 01 and 07, then Appendix D |
| Starting in practice | Chapters 02–04, then the minimum task contract above |
| Managing several agents | Chapters 05–06 and Appendix B |
| Organization rollout | Chapter 06 and [Appendix D](appendix/operational-readiness.en.md) |

## Background

The methods in this playbook were shaped through production and personal-development use, including an agent-collaboration framework that encodes task contracts, context isolation, quality gates, and structured handoffs. The aim is to describe the underlying method without binding it to one model or platform.

## License

[MIT](LICENSE)
