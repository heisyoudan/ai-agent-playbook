# 03 — The Prompt Philosophy of “Complex Minimalism”

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

## What Prompt Engineering Really Is

Prompt engineering is often treated as a collection of phrases, templates, and tricks that supposedly unlock better output.

My view is different.

**A strong prompt is neither complicated for its own sake nor extremely short. It practices “complex minimalism.”**

## What “Complex Minimalism” Means

A high-quality prompt satisfies two competing conditions at the same time.

**1. Enough complexity to provide a complete working context**

The agent needs the project structure, technology choices, conventions, purpose of the change, boundaries, and acceptance criteria. Without them, it produces something generally plausible but locally wrong.

**2. Enough simplicity to remove irrelevant noise**

More information is not automatically better. Old discussions, unrelated design notes, failed attempts, and artifacts from other tasks compete for attention and gradually distort the result.

## Four Axes of Prompt Quality

### 1. Information Density

Remove politeness and filler that do not affect execution. Increase the amount of relevant meaning per sentence.

```text
Bad:  “If possible, could you perhaps adjust the styling a little?”

Good: “In UserTable, change the header background to #f5f5f5 and the font
       size to 14px. Do not change other styles.”
```

### 2. Task Boundaries

Describe both what to do and what not to do.

```text
Implement client-side sorting only.
Do not add server-side sorting or change the API response shape.
```

### 3. Context Quality

Provide only information that directly affects the current task. Remove resolved bugs, unrelated features, abandoned proposals, and conversational leftovers.

### 4. Constraint Clarity

Turn implicit expectations into explicit rules.

```text
Keep existing tests passing. Follow TypeScript strict mode.
Do not add dependencies.
```

## A Prompt Is an Execution Interface

A prompt is not ordinary prose written to impress a human reader. It is an interface through which a model receives a task.

That makes the following useful:

- remove ceremonial introductions;
- keep background only when it changes execution;
- use lists and explicit structure;
- prefer stated constraints to assumed intent.

The most important operation in prompt design is converting implicit expectations into explicit, testable constraints.

## A Practical Review

Before sending a task, ask:

1. **Can the agent begin using only this prompt and the referenced files?** If not, context is missing.
2. **Does the prompt contain information unrelated to this task?** If so, remove the noise.
3. **Where can the agent make an interpretation that would materially change the result?** Replace it with a decision, boundary, or question.

When these three checks pass, the prompt approaches complex minimalism.

---

> **Practice note**
> Maestro uses a task-contract template to enforce a minimum information structure. Required fields and placeholder checks move prompt quality from personal attention into the workflow itself.

[Next → Context Isolation Strategy](../04-context-isolation/README.md)
