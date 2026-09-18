# 12 — Authority & Human Gates

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

**Status: Draft (chapter shell).** Maturity: **Observed Pattern** — the failure modes are well observed; the design rules are not yet settled. Ongoing evidence is tracked in the [Research Incubator](../research/README.md).

## The Question This Chapter Will Address

Which decisions must a human own, and how is that ownership enforced rather than merely stated?

## Why This Chapter Exists

A gate that exists only in documentation is a preference, not a control. Two symmetric failures appear in practice:

- **Under-gating:** autonomy without authority boundaries turns speed into risk. The agent did exactly what it was permitted to do.
- **Over-gating:** approval for everything turns capacity back into a bottleneck, and reviewers stop reading carefully.

The productive design question is therefore not "how much approval is needed". It is: which decisions are irreversible, novel, or value-laden — and therefore require a named owner?

## Concepts Expected to Belong Here

- Decision classes: reversible vs. irreversible, routine vs. novel, technical vs. value-laden
- Gate placement in a workflow, and what a gate must be able to see
- Delegated authority and its explicit limits
- Escalation, refusal, and safe stop conditions
- Gates that block vs. gates that record and continue
- Approvals as evidence: who approved, on what basis
- Failure modes of over-gating and under-gating

## Current Maturity

Failure modes are observed clearly. Gate design guidance is still qualitative and is being tested against real workflows.

---

[← 11 — Verification & Evidence](../11-verification-evidence/README.md) · [Next → 13 — Global Truth, Local Truth & Truth Projection](../13-global-local-truth/README.md)
