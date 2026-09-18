# AI Agent Playbook

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

> A practical methodology for designing reliable software engineering workflows around AI agents.

This repository explores a simple question:

> **As AI becomes the execution layer of software development, how should engineering itself be redesigned so that the result remains reliable, verifiable, bounded, and governable?**

---

## What This Is

Stronger models and better prompts can improve execution, but they do not automatically create reliable engineering.

Reliable AI-assisted development depends on the system around the agent:

- what is treated as project truth;
- how work is decomposed;
- what context an agent is allowed to see;
- what an agent is allowed to change;
- how boundaries and contracts are defined;
- how results are verified;
- what evidence is retained;
- who has authority to approve important changes;
- how failures, retries, and handoffs are managed.

This playbook organizes those concerns into a platform-independent methodology for **Agentic Software Engineering**.

The goal is to design an engineering environment in which increasingly capable agents can move quickly without losing truth, boundaries, traceability, or human control.

---

## What Problem This Solves

Many AI failures that appear to be model failures are actually engineering-system failures.

At the execution level, common problems include:

- tasks that are too large;
- noisy or incomplete context;
- unclear ownership;
- weak acceptance criteria;
- uncontrolled scope expansion;
- missing handoff state.

At the system level, deeper problems appear:

- Truth Drift;
- unbounded agent authority;
- stale or incomplete evidence;
- shared blind spots across multiple models;
- cross-boundary inconsistency;
- human approval overload;
- workflow state that cannot be reconstructed after interruption.

This playbook studies both levels.

---

## Who It Is For

- Engineers already using AI but struggling to achieve consistent results
- Developers building with coding agents across multiple sessions or roles
- Technical leads designing AI-assisted engineering workflows
- Teams introducing Agentic Software Engineering into real delivery
- Practitioners researching how truth, verification, authority, and workflow should change in the AI era

---

# Core Principles

The original foundation of this playbook can be summarized in three lines:

```text
AI is the execution layer.
Process creates productivity.
Constraints create stability.
```

As the methodology evolved, a second layer became equally important:

```text
Truth must have authority.
Implementation must have boundaries.
Completion must have evidence.
```

Coding skill still matters. It supports architecture, debugging, judgment, verification, and risk analysis.

What is becoming less scarce is routine code production itself.

As execution becomes cheaper, engineering value increasingly moves toward:

- Truth Governance
- Reasoning Scope
- Architecture and Decomposition
- Verification
- Evidence
- Decision Authority
- Workflow Design

---

# Repository Structure

The playbook is organized into three layers.

## Part I — Agent Collaboration Foundations

These chapters describe the practical foundations required to make individual agents and multi-agent workflows reliable.

| Chapter | Topic | Main Idea |
|---|---|---|
| [01](01-ai-redefines-work/README.md) | AI Redefines Work | AI changes where engineering value and bottlenecks sit. |
| [02](02-task-granularity/README.md) | Task Granularity | A task must fit the agent's reasoning capability while still closing a useful loop. |
| [03](03-prompt-philosophy/README.md) | Complex Minimalism | Maximize relevant information while minimizing noise. |
| [04](04-context-isolation/README.md) | Context Isolation | One responsibility per context; transfer state through structured handoffs. |
| [05](05-agent-management/README.md) | Multi-Agent Management | Define roles, constraints, acceptance, failure handling, and handoffs. |
| [06](06-workflow-as-product/README.md) | Workflow as a Product | Encode reusable procedures, gates, rollback, and authoritative state. |
| [07](07-what-really-matters/README.md) | What Really Matters | Durable advantage comes from engineering the system around the agent. |

---

## Part II — Governed Agentic Engineering

These chapters move from effective agent collaboration toward reliable engineering governance.

| Chapter | Topic | Main Question |
|---|---|---|
| [08](08-truth-governance/README.md) | Truth Governance | What can an agent safely treat as true, and who may change it? |
| [09](09-effective-reasoning-scope/README.md) | Effective Reasoning Scope | How large a problem can an agent reliably understand at once? |
| [10](10-boundaries-contracts-artifacts/README.md) | Decomposition, Boundaries & Contracts | How should complex work be divided without creating excessive coordination cost? |
| [11](11-verification-evidence/README.md) | Verification & Evidence | What makes a completion claim trustworthy? |
| [12](12-authority-human-gates/README.md) | Authority, Human Gates & Decision Compression | Which decisions require human authority, and how can human attention scale? |
| [13](13-global-local-truth/README.md) | Global Truth, Local Truth & Truth Projection | How can local agents remain consistent with a system they cannot read in full? |

---

## Part III — Scaling Agentic Engineering

This layer is still under active research.

Current research directions include:

- Workflow Runtime
- Retry, Resume, and Re-execution
- Persistent Execution State
- Boundary Tax
- Optimal Reasoning Boundaries
- Scalable Governance
- Decision Compression
- Capability Boundaries
- Runtime Verification
- Truth Change Propagation

Draft chapter shells for part of this layer are being written, and are labelled as research rather than as stable methodology: [14](14-workflow-runtime-recovery/README.md) Workflow Runtime & Recovery, [15](15-boundary-tax/README.md) Boundary Tax & Optimal Reasoning Boundary, [16](16-scalable-governance/README.md) Scalable Governance & Decision Compression, and [17](17-capability-boundaries/README.md) Capability Boundaries.

These topics will be promoted into stable chapters only after the underlying observations and principles become sufficiently mature.

See the [Research Incubator](research/README.md).

---

### Appendices

| Appendix | Topic |
|---|---|
| [A](appendix/anti-patterns.md) | Common failure patterns |
| [B](appendix/verification-strategies.md) | Verification strategies |
| [C](appendix/cheatsheet.md) | Cheat sheet |
| [D](appendix/operational-readiness.md) | Operational readiness and governance |

# Research Maturity

Not every idea in this repository has the same maturity level.

The playbook distinguishes three levels:

### Observed Pattern

A behavior repeatedly observed in real workflows or engineering practice.

### Derived Principle

A more general principle extracted from one or more observed patterns.

### Working Hypothesis

A theoretical model that appears useful but still requires more evidence, challenge, or practical validation.

This distinction matters.

The repository should not present every new idea as established engineering truth.

---

# The Engineering Loop

The broader methodology can be represented as:

```text
Reality
↓
Evidence
↓
Truth Candidate
↓
Authorization
↓
Current Authorized Truth
↓
Scope / Boundary
↓
Agent Execution
↓
Verification
↓
Evidence
↓
Decision
├── Continue
├── Rework
└── Truth Challenge
```

The loop is intentionally recursive.

New evidence may validate the current truth, reveal an implementation defect, or challenge the assumptions on which the work was based.

---

# Practical Execution Loop

For day-to-day work, the process can be reduced to seven steps.

1. **Classify risk.** Decide what the agent may execute, what requires approval, and what must remain human-owned.
2. **Define one objective.** State the intended outcome, current action, acceptance criteria, and boundaries.
3. **Provide a bounded context.** Include the files, facts, decisions, contracts, and constraints required for the task.
4. **Execute and self-check.** Require builds, tests, linting, static analysis, or other applicable checks.
5. **Verify independently.** Review the delta, relevant behavior, unintended scope, and evidence supporting important claims.
6. **Record and hand off.** Persist decisions, artifacts, evidence, and remaining risks in an authoritative system.
7. **Measure and improve.** Track rework, escaped defects, review effort, exceptions, and workflow cost.

---

# Minimum Task Contract

A local execution task should at least define:

```text
summary:             What outcome should be achieved?
currentAction:       What should be done in this execution?
acceptanceCriteria:  What observable checks define completion?
boundaries:          What must not be changed or attempted?
```

If one of these fields is missing, the task may not yet be ready for reliable delegation.

This contract represents the **local execution boundary**.

It does not replace project truth, architecture, system invariants, or higher-level authority.

Conceptually:

```text
Project Truth
↓
Architecture / Boundary
↓
Task Contract
↓
Agent Execution
↓
Verification
↓
Evidence
```

---

## Example: From a Vague Request to an Executable Task

```text
Bad:

Fix the authentication system.

Better:

summary:
Fix the refresh-token failure after access-token expiration.

currentAction:
Trace the refresh flow and patch only the token-renewal path.

acceptanceCriteria:
- an expired access token is renewed successfully
- the existing login flow still passes
- tests cover refresh success and failure

boundaries:
- do not change the user schema
- do not modify OAuth provider configuration
```

The second task creates a smaller and more inspectable reasoning world.

The agent can execute without inventing unrelated product or architecture decisions.

---

# Truth, Verification, and Authority

Several rules apply across the entire playbook.

### Model agreement is not proof

Multiple agents can reduce single-model error, but they cannot automatically eliminate shared blind spots.

AI consensus should be treated as evidence, not as truth by itself.

### Evidence must remain connected to reality

Important claims should be grounded in sources such as:

- repository state;
- primary documentation;
- tests;
- runtime behavior;
- measurements;
- production evidence;
- explicit human decisions.

### Authority should not exceed verification capability

A person or agent should only authorize decisions they are capable of meaningfully evaluating.

High-risk architecture, payment behavior, authentication, security, privacy, compliance, data migration, destructive operations, and irreversible actions require stronger ownership and verification.

### State, evidence, and truth are different concepts

```text
State
= where execution currently is

Evidence
= what supports a claim about what happened

Truth
= what the project is currently authorized to rely on
```

Confusing these concepts creates fragile workflows.

---

# Global and Local Reasoning

Large systems introduce a special problem.

An agent may be unable to reliably reason over the entire repository, all design documents, all dependencies, and all historical decisions at once.

The goal therefore is not to give every worker the entire world.

The goal is to provide the **complete relevant world for the current decision**.

Conceptually:

```text
Global Truth
├── System Invariants
├── Architecture Boundaries
├── Critical Contracts
└── Dependency Relationships
        ↓
Current Task
        ↓
Truth Projection
        ↓
Local Truth
+
Relevant Global Constraints
+
Relevant Dependencies
        ↓
Agent Reasoning
```

This is one of the central directions of the evolving methodology.

---

# Reading Paths

| Situation | Suggested Path |
|---|---|
| Limited time | 01 → 07 → 08 |
| Starting with AI-assisted development | 02 → 03 → 04 |
| Managing several agents | 05 → 06 → 11 |
| Designing reliable agent workflows | 06 → 08 → 11 → 12 |
| Understanding task decomposition deeply | 02 → 09 → 10 |
| Working on large systems | 09 → 10 → 13 |
| Interested in governance and verification | 08 → 11 → 12 |
| Following active research | [Research Incubator](research/README.md) |

---

# Relationship with Maestro

The methodology in this repository is platform-independent.

**Maestro** is one executable framework used to operationalize and test parts of the methodology.

The relationship is:

```text
Agentic Engineering Principles
↓
AI Agent Playbook
↓
Reference Patterns
↓
Maestro
```

The Playbook defines and evolves the methodology.

Maestro explores how parts of that methodology can be encoded into task contracts, role boundaries, gates, state transitions, structured handoffs, and workflow execution.

The Playbook should remain useful even if the implementation framework, model provider, or agent platform changes.

---

# Background

This playbook grew from sustained AI-assisted engineering practice across large-scale payment-system work, personal software development, multi-agent workflows, and real delivery environments.

Some concepts come directly from repeated production practice.

Some are abstractions derived from observing larger engineering systems.

Some are still active research hypotheses.

The repository intentionally keeps those maturity levels separate.

The long-term goal is to build a methodology that survives changes in models, tools, and platforms.

---

# Closing Thought

As AI becomes increasingly capable of producing implementation, engineering does not disappear.

Its center of gravity changes.

The difficult questions become:

```text
What is true?

What is the boundary?

What can this worker safely change?

What evidence is required?

Who has authority to decide?

How do we know the system still agrees with itself?
```

The strongest Agentic Engineering system is not the one that delegates the most work.

It is the one that allows powerful workers to move quickly inside a world that remains understandable, verifiable, bounded, recoverable, and governed.

---

## License

`MIT`
