# Appendix D — Operational Readiness and Governance

[日本語](operational-readiness.md) · [简体中文](operational-readiness.zh-CN.md)

Good task design is not enough for production. Permissions, data handling, accountability, evaluation, and stop conditions must also be explicit. This checklist extends the playbook from individual practice to team and organizational use.

---

## 1. Classify Risk First

| Risk | Examples | Default treatment |
|---|---|---|
| **Low** | Drafts, explanations, local refactoring | May run automatically; review the delta and automated checks |
| **Medium** | Dependency changes, database migrations, user-visible behavior | Human review before and after execution; prepare rollback |
| **High** | Authentication, payments, personal data, regulation, production release | Human owns design and final decision; require independent review and evidence |
| **Prohibited** | Unapproved production deletion, secret exfiltration, irreversible external action | Do not grant the capability |

Classify by impact and reversibility, not by confidence in the model.

## 2. Minimize Data and Permissions

- Provide only the files and data required for the task.
- Do not paste secrets, personal information, or customer data into prompts or logs.
- Treat read, write, network, and production access as separate permissions.
- Use short-lived credentials restricted by scope and expiration.
- Check retention, training, and transfer terms for every model, service, and plugin.

Give the minimum authority needed to finish the current task, not the maximum authority that makes the agent convenient.

## 3. Define Human Approval Points

Require explicit approval before:

- production changes;
- deletion, overwrite, or migration of data;
- payments, purchases, publication, messages, or other external side effects;
- changes to authentication, authorization, cryptography, or payment logic;
- adding an external dependency, service, or plugin;
- legal, privacy, or compliance decisions.

The approver reviews the delta, impact, verification evidence, and recovery plan—not merely the agent’s confidence.

## 4. Measure Outcomes

| Dimension | Example metrics |
|---|---|
| **Speed** | Lead time to acceptance, review wait time |
| **Quality** | Rework rate, escaped defects, reopen rate, out-of-scope changes |
| **Verification** | Human review time, automated-check coverage, missing-evidence rate |
| **Economics** | Model cost per accepted task, retries, compute time |
| **Operations** | Human intervention rate, exception rate, rollback rate, recovery time |

Capture a baseline before rollout and compare on a limited task type. Faster output with more rework or incidents is not a success.

## 5. Separate Working State from Evidence

Keep the context used by an agent compact. Retain the following separately when required for release, audit, or incident response:

- approved requirements and decisions;
- changed files and target version;
- tests, environment, timestamp, and results;
- gate decisions and approvers;
- exception, rejection, and rollback reasons;
- model and tool identifiers where relevant.

Reading only the latest state does not mean deleting historical evidence.

## 6. Define Stop, Degrade, and Recovery Conditions

Stop autonomous execution and return control to a human when:

- the same failure repeats without a new hypothesis;
- time, cost, or retry limits are exceeded;
- changes expand outside the approved scope;
- specifications, tests, and runtime evidence disagree;
- a privacy, secret, or security concern appears;
- rollback cannot be confirmed.

At stop time, hand off a structured report containing background, current state, evidence, attempted approaches, and unfinished work.

## 7. Roll Out Gradually

```text
Choose one low-risk task type
  ↓
Record baseline and success criteria
  ↓
Run a two-to-four-week pilot
  ↓
Review quality, speed, cost, and exceptions
  ↓
Adjust gates and permissions
  ↓
Expand to the next task type
```

Do not automate the whole lifecycle first. Limit scope until exception patterns and verification cost are understood.

## Pre-Launch Checklist

```text
□ Risk class and accountable owner are defined
□ Agent permissions follow least privilege
□ Secret and personal-data handling is defined
□ Operations requiring prior approval are listed
□ Acceptance criteria and rollback procedure exist
□ Speed, quality, and cost baselines are recorded
□ Working state and retained evidence use separate stores
□ Stop conditions and escalation owners are defined
```

---

[English overview](../README.md) · [Japanese appendix](operational-readiness.md) · [Chinese appendix](operational-readiness.zh-CN.md)
