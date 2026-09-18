# Chapter Template

Template for chapters that are derived from research rather than from settled practice.

Chapters 01–07 were written as stable practice and do not need to follow this structure. New
chapters, and any chapter promoted from [`research/`](../research/README.md), should.

A live example of a research-stage chapter shell is
[`08-truth-governance/README.md`](../08-truth-governance/README.md).

## Usage Notes

- Keep the four kinds of content separate: **Observation**, **Principle**, **Reusable Pattern**, and
  **Limits and Open Questions**. Merging them is what turns a hypothesis into an unexamined rule.
- The `Status:` line is mandatory. Use `Stable`, `Evolving`, or `Research`.
- State the maturity label from the Research Incubator (`Working Hypothesis`, `Observed Pattern`,
  `Derived Principle`) when the chapter is not yet stable.
- Write the chapter in English (`README.md`), then provide `README.ja.md` and `README.zh-CN.md`.
  Keep placeholder or unstable content short so translation drift stays small.
- Copy the language switch line from any existing chapter, and end with the Previous / Next
  navigation line used by the other chapters, written in the chapter's own language.

---

# NN — Chapter Title

<!-- language switch line, as in every existing chapter -->

**Status:** Stable / Evolving / Research — maturity label, if applicable.

One or two sentences stating what this chapter claims, with the confidence the evidence supports.

## Problem

What situation is broken or unreliable without this chapter? Describe the failure in terms of
observed outcomes, not in terms of missing theory.

## Observation

What has actually been seen, and in what context? Prefer specific, repeatable situations over
general statements. Note where the observation came from and how often it has appeared.

## Principle

The claim this chapter makes, stated as briefly as possible. If the principle cannot be stated in
one short paragraph, it is probably two principles.

## Reusable Pattern

What a practitioner can apply, concretely. Inputs, steps, outputs, and the conditions under which
the pattern works. This section should be usable without reading the rest of the chapter.

## Practical Implications

What changes in day-to-day work if the principle holds: what to design, what to stop doing, what to
measure.

## Limits and Open Questions

Where the principle does not hold, what has not been tested, and which counterexamples remain
unanswered. This section is required. A chapter without stated limits is not ready to be `Stable`.

## Practice Note

A short note from real use — what this looked like in practice, what was tried, what failed.

---

<!-- Previous / Next navigation line, in the chapter's own language -->
