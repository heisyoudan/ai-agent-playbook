# 16 — Scalable Governance & Decision Compression

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

**Status: Draft (chapter shell).** Maturity: **Working Hypothesis** — the scaling problem is observed; the proposed mechanism is not yet validated. Tracked in the [Research Incubator](../research/README.md).

## The Question This Chapter Will Address

How can governance grow with a project without becoming its bottleneck?

## Why This Chapter Exists

Governance that depends on a human reviewing every decision does not scale. It also degrades quietly: reviewers approve by pattern, and the review stops being a real control.

**Decision compression** means encoding a repeated judgment once — as a rule, default, template, or checklist — so that it does not need to be re-argued every time, while keeping the reasoning behind it recoverable. This resembles how engineering teams already use standards and conventions, but applied deliberately to agent-produced work.

The risk is obvious and is part of the hypothesis: a compressed decision that is never revisited becomes an unreviewed rule, and rules that nobody remembers the reason for are hard to correct.

## Concepts Expected to Belong Here

- Repeated decisions as compression candidates
- Rules, defaults, templates, checklists as compressed decisions
- Delegating precedent, with explicit scope
- Recording the rationale, so compression stays revisable
- Triggers that require a compressed decision to be re-opened
- Governance cost per change, and how it changes as the project grows

## Current Maturity

Working hypothesis. Related to Chapter 12 (Authority & Human Gates) and Chapter 06 (workflow as a product). The mechanism is being applied in practice but not yet measured.

---

[← 15 — Boundary Tax & Optimal Reasoning Boundary](../15-boundary-tax/README.md) · [Next → 17 — Capability Boundaries](../17-capability-boundaries/README.md)
