# 08 — Truth Governance

[日本語](README.ja.md) · [English](README.md) · **简体中文**

**Status: Evolving**

---

## 为什么需要 Truth Governance

随着 AI Agent 开始承担越来越多的软件开发工作，一个新的问题逐渐变得重要：

> **Agent 到底应该相信什么？**

传统软件开发中，大量 Project Truth 并没有真正写在任何地方。

它们可能存在于：

- 某个资深开发者的记忆里
- 历史聊天记录里
- 需求会议里
- 未更新的设计文档里
- Source Code 中
- Runtime Behavior 中
- 团队长期形成的隐性共识里

Human Developer 可以在工作过程中不断补充这些缺失的信息。

他可能知道：

- 某个 Requirement 为什么这样写
- 某段代码为什么不能动
- 某个设计虽然没有写进文档，但实际上已经被团队接受
- 某个异常情况过去发生过什么
- 某个模块真正的 Ownership 在哪里

这些信息共同形成了一个持续存在的：

> **Implicit Project Model**

对于长期参与项目的人类来说，这个模型可以存在于脑中。

对于 Agent 来说，这种模式非常脆弱。

---

# Truth Drift

不同 Agent、不同模型、不同 Session，面对同一个模糊 Requirement 时，可能产生不同解释。

如果每个 Worker 都允许自己补全缺失事实：

```text
Requirement
↓
Agent Interpretation
↓
Implementation
↓
New Assumption
↓
Next Agent Interpretation
↓
More Implementation
```

系统就可能逐渐偏离最初目标。

每一步单独看都可能合理。

最终结果却可能已经建立在一组从未被正式确认的 Assumption 上。

这种现象可以称为：

> **Truth Drift**

Truth Drift 的危险之处，在于它通常不会立刻表现成明显错误。

系统可能：

- 可以 Build
- Test 全部 PASS
- Code Review 看起来合理
- Agent 之间也达成一致

但它们共同遵循的前提可能已经发生偏移。

因此：

> **Agent 的关键 Project Truth 应该显式存在于工程系统中。**

---

# Reality、Evidence 与 Truth

Truth Governance 首先需要区分三个概念：

```text
Reality
Evidence
Truth
```

它们并不等价。

## Reality

Reality 是系统真实存在的状态。

例如：

- 当前 Repository 中真实存在的代码
- Production 中真实发生的行为
- 数据库当前 Schema
- 客户真实提出的 Requirement
- 外部 API 当前真实 Contract
- Runtime 中实际出现的 Failure

Reality 并不会因为文档怎么写而改变。

---

## Evidence

Evidence 是我们用来观察和证明 Reality 的信息。

例如：

- Source Code
- Git Diff
- Test Result
- Runtime Log
- Database Schema
- Official Documentation
- Screenshot
- Monitoring Metric
- Customer Confirmation
- Reproduction Result

Evidence 可以支持一个 Claim。

但 Evidence 自己也可能：

- 不完整
- 过期
- 被错误解释
- 只覆盖局部情况

因此：

> **Evidence supports Truth, but does not automatically become Truth.**

---

## Truth

Project Truth 是：

> **当前工程系统被授权继续依赖的一组事实、约束与决策。**

例如：

```text
Payment Capture cannot exceed Authorized Amount.

Refund cannot exceed Captured Amount.

This API is owned by Payment Domain.

The customer has approved Country Override behavior.

This database field is part of the external compatibility contract.
```

这些内容会直接影响后续：

- Architecture
- Task Decomposition
- Implementation
- Verification
- Release Decision

因此 Truth 需要比普通信息拥有更明确的 Authority。

---

# Truth Candidate 与 Authorized Truth

AI 可以分析 Reality 和 Evidence。

AI 也可以提出非常好的 Architecture、Requirement Interpretation 和 Engineering Decision。

但 AI 的输出首先应该被理解为：

> **Truth Candidate**

例如：

```text
Reality
+
Requirement
+
Repository
+
Runtime Evidence
+
Technical Constraints
↓
AI Analysis
↓
Truth Candidate
```

如果 Decision 很重要，还可以增加：

```text
Independent AI Analysis
↓
Cross Review
↓
Challenge
↓
Evidence Comparison
↓
Convergence
```

但即使多个 AI 最终得出同一个结论：

> **AI Consensus 仍然只是 Evidence。**

因为多个模型可能拥有同一个 Shared Blind Spot。

所以更完整的流程应该是：

```text
Reality
↓
Evidence
↓
Truth Candidate
↓
Verification
↓
Human / Authorized Gate
↓
Current Authorized Truth
```

这里的关键词是：

> **Authorized**

---

# Current Authorized Truth

Project Truth 不应该被理解成永远不会改变的 Absolute Truth。

软件工程中的很多事实都会发生变化：

- Customer Requirement 改变
- Runtime Reality 暴露新问题
- Architecture 被证明存在缺陷
- External System 改变 Contract
- 新 Evidence 推翻过去的 Assumption

因此更准确的概念是：

> **Current Authorized Truth**

也就是：

> 基于当前 Evidence，工程系统当前被授权继续依赖的 Truth Version。

例如：

```text
Reality
↓
Evidence
↓
Truth Candidate
↓
Verification
↓
Authorization
↓
Project Truth v1
↓
Implementation
↓
New Evidence
↓
Truth Challenge
↓
Re-analysis
↓
Authorization
↓
Project Truth v2
```

这样 Truth 可以变化，但变化本身必须是显式、可追踪、有 Authority 的。

---

# Implementation 可以 Challenge Truth

Agent 在 Implementation 阶段可能发现：

- Requirement 和 Repository 冲突
- Design 和 Runtime 不一致
- Contract 无法实现
- Existing Architecture 与当前 Truth 不兼容
- Test 暴露了新的 Reality

这时候 Agent 不应该偷偷调整自己的理解，然后继续写代码。

更安全的流程是：

```text
Conflict Detected
↓
Stop Current Path
↓
Collect Evidence
↓
Raise Truth Challenge
↓
Re-analysis
↓
Authorized Decision
↓
Truth Version Update
↓
Task Re-derivation
↓
Resume
```

因此可以形成三条规则：

> **Code can challenge Truth.**

> **Evidence can overturn Truth.**

> **Workers cannot silently rewrite Truth.**

这三条原则非常重要。

它们把：

```text
Implementation Discovery
```

和：

```text
Truth Authority
```

明确分开。

---

# Truth 需要 Authority

如果所有 Worker 都可以随时修改 Truth，那么 Truth 本身就失去意义。

因此不同 Role 应该拥有不同 Authority。

一种可能的模型是：

```text
Dev Agent
├── Execute
├── Observe
├── Produce Evidence
└── Challenge Truth

QA Agent
├── Verify
├── Reject
├── Produce Evidence
└── Challenge Truth

Architecture / Sage Layer
├── Reconcile Conflicts
├── Analyze Impact
└── Produce Truth Candidate

Human / Authorized Owner
└── Authorize High-impact Truth Change
```

这里最重要的原则是：

> **Authority should not exceed verification capability.**

一个 Worker 或 Human 能拥有多大的 Authority，取决于它是否有能力真正验证这个 Decision。

点击 Approve 本身不会让一个 Decision 获得可信度。

---

# Multi-AI Review 的价值与边界

多个 AI 独立分析同一个问题非常有价值。

例如：

```text
AI A Analysis
AI B Analysis
AI C Analysis
↓
Cross Review
↓
Conflict
↓
Evidence
↓
Revision
↓
Convergence
```

这种方式可以显著降低：

> **Single Model Error**

但它无法自动消除：

> **Shared Blind Spot**

如果三个模型都缺少同一个 Domain Reality，它们可能共同得出一个错误但高度一致的结论。

因此：

```text
AI Agreement
≠
Objective Truth
```

更可靠的 Truth 来源应该是：

```text
AI Convergence
+
Reality Grounding
+
Evidence
+
Qualified Human Judgment
```

---

# Truth 不应该无限增长

Truth Governance 还有一个现实风险：

> **Truth 本身也有维护成本。**

如果每一个 Implementation Detail 都升级为 Project Truth，工程系统会被文档与同步成本拖垮。

因此需要区分不同级别的信息。

一种简单模型：

```text
Global / Critical Truth
├── System Invariants
├── Architecture Boundaries
├── Ownership
├── Critical Contracts
└── High-risk Decisions

Local Truth
├── Current Module Decisions
├── Local Contracts
└── Task-relevant Constraints

Ephemeral Working Information
├── Temporary Investigation Notes
├── Intermediate Reasoning
└── Short-lived Execution State
```

治理强度应该与 Truth Drift 的影响相匹配。

可以形成一条原则：

> **Governance intensity should be proportional to drift impact.**

例如：

资金账本规则、Authentication、Security、Data Migration 等高风险区域，需要更严格的 Truth Governance。

普通 UI 调整、局部实现细节和低风险 Experiment，可以拥有更宽松的流程。

---

# Truth Rot

即使 Truth 曾经正确，它也可能随着时间失效。

例如：

```text
Truth v1
↓
Code Changes
↓
Dependency Changes
↓
Runtime Changes
↓
Requirement Changes
↓
Truth Document unchanged
```

此时就产生：

> **Truth Rot**

所以 Truth 不能只被创建。

它还需要：

- Version
- Provenance
- Change History
- Dependency Awareness
- Periodic Challenge
- Runtime Feedback

如果 Reality 已经变化，旧 Truth 仍然继续被 Agent 使用，就会产生系统性的错误。

---

# Truth 与 Documentation

在传统开发中，Documentation 经常被理解成：

> 给 Human 阅读的说明书。

在 Agentic Engineering 中，它还承担另一个重要角色：

> **Persistent Project Truth**

原因很简单。

系统中的 Worker 可能持续变化：

```text
Different Model
Different Session
Different Agent
Different Developer
Different Tool
```

但 Project 仍然需要维持连续性。

因此：

> **Workers are replaceable. Project Truth persists.**

这意味着关键 Engineering Decision 应尽量脱离某个 Worker 的长期记忆，进入可以持续被读取、验证和挑战的 Artifact。

---

# Truth 与 Task

Task 不应该自己重新定义世界。

更合理的关系是：

```text
Project Truth
↓
Architecture / Boundary
↓
Relevant Truth Projection
↓
Task Contract
↓
Agent Execution
↓
Verification
↓
Evidence
```

Task Contract 负责告诉 Agent：

- 当前目标是什么
- 当前允许做什么
- 当前不能做什么
- 怎样证明完成

Project Truth 负责告诉整个系统：

- 当前世界是什么
- 哪些事实已经被授权
- 哪些 Invariant 必须保持
- 哪些 Boundary 不允许被局部 Worker 随意改变

---

# Truth 与 Evidence 的闭环

Truth Governance 最终应该形成一个持续循环。

```text
Reality
↓
Evidence
↓
Truth Candidate
↓
Verification
↓
Authorization
↓
Current Authorized Truth
↓
Implementation
↓
Runtime / Test / Review
↓
New Evidence
↓
├── Truth Still Holds
│      ↓
│   Continue
│
└── Conflict
       ↓
   Truth Challenge
       ↓
   Re-analysis
       ↓
   Truth vNext
```

这使 Truth 成为一个可以持续被 Reality 校正的系统。

---

# Practical Pattern

一个最小可复用的 Truth Governance Pattern 可以写成：

```text
1. Observe Reality

2. Collect Evidence

3. Produce Truth Candidate

4. Challenge with independent reasoning

5. Identify unresolved uncertainty

6. Send high-impact decision to authorized owner

7. Record Current Authorized Truth

8. Derive bounded tasks from that truth

9. Verify implementation

10. Feed new evidence back into truth evaluation
```

---

# Failure Pattern: Silent Truth Rewrite

一个常见失败模式：

```text
Task says A
↓
Agent finds A difficult
↓
Agent assumes B
↓
Agent implements B
↓
Tests are written against B
↓
Everything PASS
```

从 Implementation 角度看，整个流程非常成功。

从 Engineering 角度看，系统已经发生 Truth Drift。

因此：

> **A successful implementation against unauthorized assumptions is still a failed engineering outcome.**

---

# Failure Pattern: Perfect Verification Against Wrong Truth

另一个危险情况：

```text
Wrong Truth
↓
Correct Task Derivation
↓
Correct Implementation
↓
Correct Tests
↓
Correct QA
↓
PASS
```

每一层都按照输入正确工作。

最终整个系统仍然错误。

这说明：

> **Verification can prove conformity to Truth. It cannot automatically prove that the Truth itself is correct.**

因此 Verification Architecture 和 Truth Governance 必须同时存在。

---

# Failure Pattern: Over-governed Truth

Truth Governance 也可能走向另一个极端：

```text
Every Decision
↓
Truth Update
↓
Cross Review
↓
Human Approval
↓
Documentation Update
↓
Implementation
```

如果所有局部变化都经过最高级别治理，Human 很快会成为整个系统的 Throughput Bottleneck。

因此真正可扩展的系统需要：

```text
Low-risk Local Decision
→ Local Authority

Medium-impact Contract Decision
→ Independent Verification

High-impact Global Truth
→ Qualified Human Gate
```

Truth Governance 的目标是保护高价值 Truth。

并不要求所有信息都拥有同样强度的流程。

---

# Open Questions

本章主干已经相对稳定，但以下课题仍处于研究阶段，尚不足以写成确定的机制：

- **Truth Versioning** —— Truth 的版本应该以什么粒度存在，如何与 Code、Contract、Architecture 的变化对应
- **Truth Change Propagation** —— 一次 Truth 更新之后，哪些下游产物（任务、实现、测试、文档）必须重新验证
- **Truth Rot Detection** —— 如何在不依赖人工定期巡检的前提下发现已经失效的 Truth
- **Human Authority Scaling** —— 当 Truth 数量增长时，如何避免 Human Gate 成为吞吐瓶颈

这些问题会在 [Research Incubator](../research/README.zh-CN.md) 中继续跟踪，成熟之后再补入本章。

---

# Core Principles

本章可以浓缩成以下原则。

> **Truth must have authority.**

Truth 必须拥有明确的 Authority。

---

> **AI consensus is evidence, not proof.**

多个模型达成一致可以提高 Confidence，但不能自动成为 Truth。

---

> **Code can challenge Truth. Evidence can overturn Truth. Workers cannot silently rewrite Truth.**

Implementation 可以发现问题，Evidence 可以推翻旧 Truth，但 Worker 不能自行改写世界。

---

> **Governance intensity should be proportional to drift impact.**

Truth Drift 的影响越大，治理强度越高。

---

> **Workers are replaceable. Project Truth persists.**

Worker 可以替换，Project Truth 必须持续存在。

---

# Closing Thought

AI Agent 的能力正在快速提升。

它们可以写更多代码、阅读更多文件、执行更长的 Workflow，也可以自主完成越来越复杂的 Task。

但执行能力越强，一个问题就越重要：

> **它正在基于什么世界做决定？**

如果这个世界来自：

- 随机 Context
- 历史聊天
- 模糊 Requirement
- 未经授权的 Assumption
- Agent 自己临时补全的解释

那么更强的执行能力可能只会让错误传播得更快。

因此 Agentic Engineering 的一个核心任务，是建立一个能够回答这些问题的系统：

```text
什么是当前被授权的 Truth？

这个 Truth 基于什么 Evidence？

谁有权改变它？

什么情况下必须 Challenge 它？

哪些 Worker 只能执行，哪些 Worker 可以裁决？

Truth 变化以后，哪些下游结果需要重新验证？
```

当这些问题可以被明确回答时，Agent 才真正进入一个可以被工程化治理的世界。

---

[← 07 — 真正的竞争力在哪里](../07-what-really-matters/README.zh-CN.md) · [下一章 → 09 — 有效推理范围](../09-effective-reasoning-scope/README.zh-CN.md)
