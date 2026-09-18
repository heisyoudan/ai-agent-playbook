# 09 — Effective Reasoning Scope

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

**Status: Draft (chapter shell).** Maturity: **Observed Pattern** — seen repeatedly in long-running work, but not yet formulated as stable methodology. Ongoing evidence is tracked in the [Research Incubator](../research/README.md).

## The Question This Chapter Will Address

How much material should an agent reason over before reliability starts to fall?

Chapter 02 controls task size. Chapter 04 isolates context. Reasoning scope is the third variable: for a given decision, which facts must an agent hold at once — and which facts actively hurt by diluting the signal?

## Why This Chapter Exists

"Provide more context" is common advice and often wrong. Beyond a certain point, additional material does not add understanding. It hides the relevant two lines inside two hundred, makes contradictions easy to overlook, and increases cost without improving the decision.

Reasoning scope is therefore a design decision, not a convenience. It determines what the agent can be expected to notice, and what it will silently ignore.

## Concepts Expected to Belong Here

- Available context vs. relevant context
- Scope per decision, not per session
- Symptoms of scope overflow: ignored contradictions, confident irrelevance, cost without improvement
- Techniques for narrowing scope before execution
- How reasoning scope relates to task granularity and context isolation
- Scope as a cost and latency driver, not only a quality factor

## Current Maturity

Observed in real workflows, but the boundary is described qualitatively. A usable way to measure an effective scope is still missing.

---

[← 08 — Truth Governance](../08-truth-governance/README.md) · [Next → 10 — Boundaries, Contracts & Artifacts](../10-boundaries-contracts-artifacts/README.md)
