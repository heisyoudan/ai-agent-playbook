# 10 — Boundaries, Contracts & Artifacts

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

**Status: Draft (chapter shell).** Maturity: **Derived Principle** — derived from the practices in Chapters 02 and 06 and repeatedly confirmed in real workflows. Not yet complete methodology. Ongoing evidence is tracked in the [Research Incubator](../research/README.md).

## The Question This Chapter Will Address

How are the limits of a task made explicit, and how is its result made usable by whoever comes next?

## Why This Chapter Exists

Chapter 02 defines the minimum task contract. That is enough to start work, but not enough to make a system reliable over time. Three things are still missing:

- **Boundaries** that cannot be crossed, not merely mentioned
- **Contracts** that state obligations on both sides, including what the receiver must provide
- **Artifacts** that carry state forward without requiring the whole conversation

Without artifacts, every subsequent session re-derives what the previous one knew. Without contracts, "done" is defined by whoever judges last.

## Concepts Expected to Belong Here

- Boundary types: scope, change, data, authority, time, budget
- Contracts as verifiable obligations, on both sides
- Artifact design: durability, minimum content, ownership, retrieval
- Working state vs. retained evidence
- Handoff artifacts and what they must contain
- Contracts between human and agent, and between agents

## Current Maturity

Derived from practical use rather than from theory. The boundary taxonomy is stable in practice; artifact conventions are still converging.

---

[← 09 — Effective Reasoning Scope](../09-effective-reasoning-scope/README.md) · [Next → 11 — Verification & Evidence](../11-verification-evidence/README.md)
