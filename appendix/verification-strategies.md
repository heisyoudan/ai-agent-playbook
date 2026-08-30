# Appendix B — Verification Strategies for AI Output

[日本語](verification-strategies.ja.md) · **English** · [简体中文](verification-strategies.zh-CN.md)

## Why Verification Matters

AI can generate thousands of lines faster than a human can review them. Verification therefore becomes the bottleneck and the control surface of AI-assisted delivery.

**Productivity is limited not only by execution speed, but by the speed at which trustworthy acceptance can be reached.**

---

## Strategy 1: Require Self-Verification

Ask the agent to execute applicable checks, not merely suggest them.

```text
Implement sorting for the user table. Before reporting completion:
- build the project;
- run the existing test suite;
- add and run ascending/descending tests for all three columns;
- confirm that TypeScript strict mode reports no error.
```

“Write tests” leaves execution to the reviewer. “Write, run, and report the results” produces evidence.

Self-verification is a first line of defense, not independent acceptance. The agent may misread its own output or omit a relevant check.

## Strategy 2: Review the Delta

Do not reread the whole repository. Start with the declared and actual change surface.

```text
1. Require a list of changed files and a purpose for each change.
2. Inspect the diff and compare it with the task boundaries.
3. Check for unexpected files, dependencies, generated artifacts, and formatting churn.
4. Review high-risk logic in full, even if the diff is small.
```

Diff review compresses the inspection surface, but it does not prove that an unchanged dependency or assumption is correct.

## Strategy 3: Use an Independent Review Context

Review implementation in a separate session or role.

```text
Purpose: [task objective]
Changed files: [list]
Acceptance criteria: [checks]

Review for:
- satisfaction of acceptance criteria;
- consistency with existing architecture;
- out-of-scope changes;
- security, privacy, and failure behavior;
- missing tests or evidence.
```

A separate context avoids inheriting all implementation justifications and failed attempts. Independence improves challenge, but a second model is still not a source of truth.

## Strategy 4: Automate Quality Gates

Machines should decide what machines can decide.

| Check | Typical mechanism | Human judgment? |
|---|---|---|
| Build succeeds | build command / CI | No |
| Existing tests pass | test runner | No |
| Lint and type checks pass | linter / compiler | No |
| No unapproved dependency | lockfile or manifest diff | No |
| Design intent is correct | review | Yes |
| User experience is appropriate | inspection and testing | Yes |
| Business behavior is valid | domain owner | Yes |

Automate deterministic checks so human attention can focus on intent, tradeoffs, and risk.

## Strategy 5: Verify in Stages

Do not wait for a large feature to finish before checking it.

```text
data model → verify
API behavior → verify
UI integration → verify
end-to-end behavior → verify
```

Small gates reduce the amount of invalid work built on top of an early mistake. Stage boundaries should match meaningful responsibilities, not arbitrary tiny edits.

## Strategy 6: Know What Requires Human Judgment

### Suitable for Delegated Execution

- established implementation patterns;
- test generation and routine automation;
- rule-based refactoring;
- documentation drafts;
- deterministic error handling.

### Requires Explicit Human Ownership

- **Security:** authentication, authorization, secrets, and threat models;
- **Architecture:** decisions that constrain the whole system;
- **Business correctness:** whether code reflects real domain rules;
- **Performance:** claims that require measurement under representative load;
- **Legal and compliance:** interpretation and accountability;
- **Irreversible external actions:** production deletion, payment, publication, or communication.

The line is not “AI can” versus “AI cannot.” It is whether failure impact, uncertainty, and responsibility can be delegated safely.

## Strategy 7: Escalate Stalled Problems

Stop repeated execution when:

- several attempts fail without a new hypothesis;
- output references facts or APIs that do not exist;
- the problem requires an architectural decision;
- several viable directions exist and the choice depends on tradeoffs outside the task.

### Structured Stop Report

```text
Background:       intended outcome
Current state:    progress and exact blocking point
Relevant code:    files and locations
Observed problem: errors, contradictions, or unexpected behavior
Attempts:         approaches tried and why they failed
Unfinished work:  acceptance criteria not yet met
Evidence:         logs, tests, documentation, measurements
```

### Multi-Model Deliberation

A difficult problem can be presented to more than one reasoning model. One proposes a solution, another critiques its assumptions, and the first revises it. The human moderates the debate and decides when it has converged enough to test.

```text
structured problem report
  ↓
model A proposes
  ↓
model B attacks assumptions and failure modes
  ↓
model A revises
  ↓
human selects a testable direction
  ↓
working agent validates it against code and evidence
```

Agreement between models does not establish truth. Models can share the same mistaken premise. Verify APIs, security requirements, legal claims, and performance assertions against primary documentation, source code, tests, and measurement.

## Three Acceptance Questions

1. **Are all predeclared acceptance criteria satisfied with evidence?**
2. **Did the change remain inside the approved scope?**
3. **Is enough state recorded for the next phase or future investigation?**

Keep the agent’s working state compact, but retain release and audit evidence separately with the relevant version and environment.

## Summary

Reliable verification combines:

1. self-checks;
2. delta review;
3. independent review context;
4. automated gates;
5. staged acceptance;
6. human ownership of high-risk judgment;
7. structured escalation.

The goal is not to read every generated line. It is to construct an evidence chain strong enough to justify acceptance.

---

[Appendix A → Failure Patterns](anti-patterns.md) · [Appendix C → Cheat Sheet](cheatsheet.md) · [← English README](../README.md)
