# 15 — Boundary Tax & Optimal Reasoning Boundary

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

**Status: Draft (chapter shell).** Maturity: **Working Hypothesis** — a useful way of framing a real cost, not yet a measured model. Tracked in the [Research Incubator](../research/README.md).

## The Question This Chapter Will Address

What does a boundary cost, and where is drawing one actually worth it?

## Why This Chapter Exists

Chapter 02 says granularity matters. Chapter 04 says isolate context. Chapter 09 says limit reasoning scope. Each of these buys control — and each charges a tax:

- handoff and re-establishment cost
- context reconstruction at every boundary
- integration and reconciliation work
- coordination overhead between scopes
- knowledge that exists only locally and never travels

The conclusion "smaller and more isolated is better" only holds if the tax is ignored. It usually is not. The useful question is where the total cost is lowest for the reliability the work actually requires.

## Concepts Expected to Belong Here

- Components of the boundary tax, named separately
- Cost of isolation vs. cost of coupling
- Optimal reasoning boundary: a candidate optimum, not a formula
- Why the optimum moves with task class, risk, and model capability
- Making the tax visible enough to argue about
- Relationship to task granularity, context isolation, and reasoning scope

## Current Maturity

Working hypothesis. The cost categories are observed in practice; no measurement method has been validated, and the "optimal" framing may prove too neat.

---

[← 14 — Workflow Runtime & Recovery](../14-workflow-runtime-recovery/README.md) · [Next → 16 — Scalable Governance & Decision Compression](../16-scalable-governance/README.md)
