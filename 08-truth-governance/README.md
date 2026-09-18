# 08 — Truth Governance

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

**Status: Evolving.** Maturity: **Observed Pattern** — see the [Research Incubator](../research/README.md) for the maturity labels. The full text of this chapter is currently published in [Simplified Chinese](README.zh-CN.md); this page is still an outline of the same chapter.

In this repository, *truth* means a fact that is supported by evidence and can be used as the basis for a decision.

## The Question This Chapter Will Address

Agents rarely fail because they cannot produce output. They fail because they act on facts that are outdated, incomplete, or simply invented — and because nothing in the workflow is responsible for noticing.

So: how does a project decide what counts as true, where that truth lives, and who keeps it current?

## Why This Chapter Exists

Chapters 01–07 make the work around an agent reliable: smaller tasks, closed context, explicit constraints, verification, and handoffs. Those practices assume that the facts an agent receives are trustworthy.

That assumption breaks down as soon as a project runs longer than a single session. The same question is answered differently in three places. A decision recorded last month is no longer reflected in the code. An agent fills a gap with a plausible invention, and the next agent inherits it as fact.

Truth Governance treats project truth as something that must be produced, owned, and invalidated — not as background context that happens to be available.

## Concepts Expected to Belong Here

- Reality, project truth, and the gap between them
- Facts, decisions, assumptions, and open questions as distinct types
- Truth sources, ownership, and the authority to change them
- Evidence attached to a fact, and what happens when that evidence expires
- Staleness, invalidation, and how drift becomes visible
- Conflicting truths across documents, code, and conversation
- Truth as an input to every task context, not a separate activity

## Current Maturity

Observed in real workflows; the vocabulary is not yet stable. Some of the mechanisms that make truth governable are still being tested.

---

[← 07 — Where the Real Competitive Advantage Lies](../07-what-really-matters/README.md) · [Next → 09 — Effective Reasoning Scope](../09-effective-reasoning-scope/README.md)
