# Appendix A — Common Failure Patterns

[日本語](anti-patterns.ja.md) · **English** · [简体中文](anti-patterns.zh-CN.md)

Failures seen in real agent workflows, and how to prevent them structurally.

---

## Anti-Pattern 1: Change State First, Write the Log Later

### Symptom

A task is marked complete before the work record and evidence are written.

### What Happens

The system contains a state transition without a reason. The next role must ask what happened or guess. If rollback is needed, the decision has no traceable basis.

### Response

**Make the transition atomic.** Record the reason and evidence, change state, and generate the next handoff as one operation. Do not allow only one part to succeed.

## Anti-Pattern 2: Hand Off an Incomplete Task Definition

### Symptom

An agent receives a vague request such as “roughly implement this feature.”

### What Happens

The agent fills the gaps with reasonable-looking assumptions. The difference from the real intent appears only during review, creating avoidable rework.

### Response

Require four fields before handoff:

- objective;
- current action;
- acceptance criteria;
- boundaries or non-goals.

If one is missing, the task is not ready.

## Anti-Pattern 3: Do Everything in One Conversation

### Symptom

Requirements, implementation, tests, and bug fixes share one session.

### What Happens

Context becomes contaminated. Accepted decisions, hypotheses, and failed attempts are mixed together, and output becomes less stable as the conversation grows.

### Response

**One session, one responsibility.** Transfer only structured decisions, constraints, evidence, and next actions between sessions.

## Anti-Pattern 4: Teach Every Agent the Rules Manually

### Symptom

Every new conversation starts by rewriting what the agent may and may not do.

### What Happens

Wording changes, rules drift, preparation cost grows, and behavior differs between sessions.

### Response

Store shared rules in versioned configuration, templates, or system instructions. Inject them consistently and keep task-specific context separate.

## Anti-Pattern 5: Treat Working Test Output as a Permanent Archive

### Symptom

Old test output accumulates in the same file the agent uses to understand the current state.

### What Happens

The agent cannot distinguish the latest result from historical snapshots. Stale evidence contaminates current decisions.

### Response

**Separate working state from retained evidence.** Keep only the latest result in the agent’s operational context. Store evidence required for releases, regulation, or incident response separately with timestamp, version, environment, result, and approver. Do not preserve all noise, and do not delete required audit evidence.

## Anti-Pattern 6: Allow Well-Intentioned Scope Expansion

### Symptom

The agent changes unrelated files, adds unrequested documentation, or performs a refactor that was not part of the task.

### What Happens

The change surface becomes unpredictable and review cost rises. Unexpected edits are discovered late and are difficult to trace.

### Response

Define prohibitions and non-goals explicitly. A predictable boundary is often more valuable than an open-ended instruction to “improve anything relevant.”

## Summary

These failures share one cause: they depend on human attention and memory.

“Be careful next time” is not a control. **Prevent recurring failure with structure.**

---

[Appendix B → Verification Strategies](verification-strategies.md) · [Appendix C → Cheat Sheet](cheatsheet.md) · [← English README](../README.md)
