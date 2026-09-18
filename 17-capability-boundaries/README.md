# 17 — Capability Boundaries

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

**Status: Draft (chapter shell).** Maturity: **Working Hypothesis** — the problem is observed; the method for establishing capability is still being developed. Tracked in the [Research Incubator](../research/README.md).

## The Question This Chapter Will Address

What can an agent be trusted to do, and what evidence supports that trust?

## Why This Chapter Exists

Capability is usually inferred from something that is not evidence about the work at hand:

- one successful result, treated as a general property
- a public benchmark on someone else's tasks
- the confidence expressed in the output itself

None of these describe what this agent can do in this repository, on this task class, under these constraints. Capability boundaries are more useful when they are established per task class from observed results, and revised when models, tools, or context change.

A related confusion is worth separating carefully: **capability is not authority.** Chapter 12 covers what an agent is allowed to decide. This chapter covers what it can be relied on to do well — two different questions that are often merged into one.

## Concepts Expected to Belong Here

- Claimed capability vs. demonstrated capability
- Per-task-class evidence rather than general impressions
- Calibration: how confidence compares to outcomes
- Degradation over long horizons, repeated edits, or unfamiliar code
- Capability drift as models, tools, and context change
- The distinction between capability and authority

## Current Maturity

Working hypothesis. The distinction is clear; a repeatable way to establish a capability boundary is not yet established.

---

[← 16 — Scalable Governance & Decision Compression](../16-scalable-governance/README.md) · [Research Incubator →](../research/README.md)
