# 11 — Verification & Evidence

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

**Status: Draft (chapter shell).** Maturity: **Derived Principle** — derived from practical verification work, with several mechanisms still under test. Ongoing evidence is tracked in the [Research Incubator](../research/README.md).

[Appendix B](../appendix/verification-strategies.md) lists concrete verification strategies. This chapter asks the design question underneath them.

## The Question This Chapter Will Address

What must be true before a claim is accepted?

## Why This Chapter Exists

"Done" is not evidence, and a confident explanation is not evidence either. Two distinctions carry most of the value:

- Verification designed **before** execution is control. Verification produced **after** execution is inspection.
- Evidence that can be re-checked by someone else is evidence. Evidence that exists only as a narrative is testimony.

Chapter 02 already requires acceptance criteria. This chapter asks what those criteria must produce, who can reproduce them, and how long they remain valid.

## Concepts Expected to Belong Here

- Evidence classes: test output, runtime behavior, measurement, primary documentation
- Verification designed before execution, and matched to the claim being made
- Independent reproduction vs. self-report
- Falsification over confirmation: what would prove this wrong?
- Which evidence to retain, for how long, and for whose use
- Cost of verification vs. cost of an escaped defect
- Reusing evidence across sessions without inflating it into truth

## Current Maturity

Built on long-running practice; the evidence taxonomy and retention rules are still evolving.

---

[← 10 — Boundaries, Contracts & Artifacts](../10-boundaries-contracts-artifacts/README.md) · [Next → 12 — Authority & Human Gates](../12-authority-human-gates/README.md)
