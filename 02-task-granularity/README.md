# 02 — Task Granularity Determines Everything

[日本語](README.ja.md) · **English** · [简体中文](README.zh-CN.md)

## Task Design Matters More Than Agent Performance

Discussions about AI development often focus on which agent or tool is strongest. Once the environment is installed and connected, however, the more common limitation is not a lack of model capability.

**Even an excellent agent cannot produce reliable results from a poorly designed task.**

What is usually missing is a task shape that lets the agent understand, execute, verify, and finish the work without losing focus.

## When a Task Is Too Large

“Build the entire administration backend” sounds efficient, but it hides requirements, boundaries, interfaces, screen behavior, constraints, and acceptance decisions.

The context needed to make such a task safe can cost more than the implementation itself. As context expands, the agent loses focus, output becomes inconsistent, rework grows, and a human eventually has to reconstruct the whole effort.

## When a Task Is Too Small

Over-fragmentation creates a different problem. Work that could close in one interaction requires three or four handoffs. Communication and decision overhead become larger than the work.

Splitting a task is itself a design activity. If every tiny edit becomes a separate task, the human starts serving the workflow instead of benefiting from it.

## Finding the Right Granularity

The right task is both:

- **Small enough** for the agent to complete independently and self-verify.
- **Large enough** to close one useful loop in a single session.

| Size | Example | Result |
|---|---|---|
| **Too large** | “Build the whole admin screen.” | Context expands; scope drift and rework become likely. |
| **Appropriate** | “Implement the user-table component with sorting and pagination using the following API contract.” | The task can finish and be verified as one loop. |
| **Too small** | “Create the header,” then “create the body,” then “add pagination.” | Handoffs dominate execution. |

## The Shift in Question

I used to ask, “Can AI do this task?”

Now I ask, **“How should I design this task so that AI can complete it reliably?”**

The focus moves from judging the model to designing the work. Agent capability matters, but the human controls the objective, boundaries, context, and evidence required for completion.

## Five Practical Rules

1. **One task, one objective** — do not combine unrelated outcomes.
2. **Define completion** — state what observable evidence means “done.”
3. **Define boundaries** — state what is out of scope and must not change.
4. **Make it verifiable** — choose a unit the agent can test or inspect.
5. **Close the context** — place the required information together.

---

> **Practice note**
> Maestro requires four fields before a task can execute: `summary`, `currentAction`, `acceptanceCriteria`, and `boundaries`. They represent the outcome, this execution, the proof of completion, and the non-goals. An incomplete task contract is rejected before work begins.

[Next → The Prompt Philosophy of “Complex Minimalism”](../03-prompt-philosophy/README.md)
