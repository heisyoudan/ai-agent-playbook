# 14 — Workflow Runtime & Recovery

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

**Status: Draft (chapter shell).** Maturity: **Observed Pattern** — the problem is observed consistently; the recovery mechanisms are still being tested. Ongoing evidence is tracked in the [Research Incubator](../research/README.md).

## The Question This Chapter Will Address

How does a workflow know where it is, and how does it resume after being interrupted?

## Why This Chapter Exists

Multi-step workflows fail in the middle: a session ends, a tool times out, an agent produces something unusable, or a gate rejects the current state.

If runtime state exists only inside a conversation, recovery means re-deriving context from scratch — usually the most expensive and least reliable option available. Worse, it is invisible: nobody records it as a failure because work eventually continues.

Recovery should be a designed capability, in the same way verification is. That means the workflow must be able to state its position, its last valid checkpoint, and what it must not repeat.

## Concepts Expected to Belong Here

- Run state: what the workflow must be able to answer about itself
- Checkpoints, and what makes one valid
- Resume vs. restart vs. rollback
- Idempotent re-execution and protecting irreversible steps
- Partial failure and its visible state
- Retry limits, escalation, and safe stop conditions
- Recovery evidence: proving what was re-run and what was skipped

## Current Maturity

The problem is consistently observed in real workflows. Concrete recovery mechanisms are still being compared, and no single approach is established.

---

[← 13 — Global Truth, Local Truth & Truth Projection](../13-global-local-truth/README.md) · [Next → 15 — Boundary Tax & Optimal Reasoning Boundary](../15-boundary-tax/README.md)
