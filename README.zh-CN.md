# AI Agent Playbook — 中文版

[日本語](README.ja.md) · [English](README.md) · **简体中文**

> 一套围绕 AI Agent 设计可靠软件工程流程的实践方法论。

这个仓库持续研究一个问题：

> **当 AI 逐渐成为软件开发的主要执行层以后，工程体系应该怎样重新设计，才能让结果依然可信、可验证、有边界、可恢复，并且始终处于可治理状态？**

---

## 这是什么

更强的模型和更好的 Prompt 可以提升执行能力，但它们不会自动形成可靠的软件工程体系。

稳定的 AI 开发依赖 Agent 周围的整个工程系统：

- 什么可以被当作 Project Truth；
- 工作应该如何切分；
- Agent 应该看到哪些 Context；
- Agent 被允许修改什么；
- Boundary 和 Contract 如何定义；
- 结果如何 Verification；
- 哪些 Evidence 必须保留；
- 谁拥有重要决策的 Authority；
- Failure、Retry 和 Handoff 如何管理。

本 Playbook 将这些问题整理成一套平台无关的 **Agentic Software Engineering** 方法论。

目标是建立一个工程环境，让越来越强的 Agent 可以高速执行，同时不丢失 Truth、Boundary、Traceability 和 Human Control。

---

## 它解决什么问题

很多看起来像模型能力不足的问题，实际上来自工程系统本身。

在局部执行层面，常见问题包括：

- Task 过大；
- Context 噪声过多或信息不足；
- Ownership 不清；
- Acceptance Criteria 太弱；
- Scope 无限制扩张；
- Handoff 缺失关键状态。

当系统规模扩大以后，还会出现更深的问题：

- Truth Drift；
- Agent Authority 失控；
- Evidence 过期或不完整；
- 多模型共享同一个 Blind Spot；
- Cross-boundary 不一致；
- Human Gate 认知过载；
- Workflow 中断以后无法可靠恢复状态。

本 Playbook 同时研究这两个层级。

---

## 适合谁

- 已经在工作中使用 AI，但结果仍然不够稳定的工程师
- 使用 Coding Agent，并在多个会话或多个角色之间协作的开发者
- 设计 AI Engineering Workflow 的技术负责人
- 准备在真实交付中引入 Agentic Software Engineering 的团队
- 研究 AI 时代 Truth、Verification、Authority 和 Workflow 应该如何变化的实践者

---

# 核心原则

这个 Playbook 最初可以用三句话概括：

```text
AI 是执行层。
流程创造生产力。
约束带来稳定性。
```

随着方法论继续演化，又形成了第二层原则：

```text
Truth 必须有 Authority。
Implementation 必须有 Boundary。
Completion 必须有 Evidence。
```

编码能力依然重要。

它支撑 Architecture、Debugging、Judgment、Verification 和 Risk Analysis。

正在快速降低稀缺性的，是常规代码生产本身。

随着执行越来越便宜，工程价值逐渐向这些区域移动：

- Truth Governance
- Reasoning Scope
- Architecture 与 Decomposition
- Verification
- Evidence
- Decision Authority
- Workflow Design

---

# 仓库结构

整个 Playbook 分为三个层级。

## Part I — Agent Collaboration Foundations

这一部分描述让单个 Agent 与 Multi-Agent Workflow 稳定工作的基础能力。

| 章节 | 主题 | 核心观点 |
|---|---|---|
| [01](01-ai-redefines-work/README.zh-CN.md) | AI 重新定义工作 | AI 改变工程价值与瓶颈所在的位置。 |
| [02](02-task-granularity/README.zh-CN.md) | Task Granularity | Task 需要落在 Agent 能可靠理解的范围内，同时闭合一个有价值的工作循环。 |
| [03](03-prompt-philosophy/README.zh-CN.md) | 复杂的极简 | 最大化相关信息，最小化噪声。 |
| [04](04-context-isolation/README.zh-CN.md) | Context Isolation | 一个 Context 承担一个主要职责，通过结构化 Handoff 传递状态。 |
| [05](05-agent-management/README.zh-CN.md) | Multi-Agent Management | 定义 Role、Constraint、Acceptance、Failure Handling 与 Handoff。 |
| [06](06-workflow-as-product/README.zh-CN.md) | Workflow as a Product | 把可重复流程、Gate、Rollback 与 Authoritative State 固化成系统。 |
| [07](07-what-really-matters/README.zh-CN.md) | 真正重要的竞争力 | 长期优势来自围绕 Agent 设计工程系统的能力。 |

---

## Part II — Governed Agentic Engineering

这一部分开始从“怎样高效使用 Agent”进入“怎样构建可靠的 Agentic Engineering System”。

| 章节 | 主题 | 核心问题 |
|---|---|---|
| [08](08-truth-governance/README.zh-CN.md) | Truth Governance | Agent 可以依赖什么作为 Truth，谁有权限改变它？ |
| [09](09-effective-reasoning-scope/README.zh-CN.md) | Effective Reasoning Scope | AI 在一次有效推理中究竟能可靠理解多大的问题？ |
| [10](10-boundaries-contracts-artifacts/README.zh-CN.md) | Decomposition、Boundary 与 Contract | 如何切分复杂系统，同时控制边界协调成本？ |
| [11](11-verification-evidence/README.zh-CN.md) | Verification 与 Evidence | 什么样的证据足以让一个 Completion Claim 获得可信度？ |
| [12](12-authority-human-gates/README.zh-CN.md) | Authority、Human Gate 与 Decision Compression | 哪些决策必须交给 Human，以及如何避免 Human 成为系统瓶颈？ |
| [13](13-global-local-truth/README.zh-CN.md) | Global Truth、Local Truth 与 Truth Projection | 当 Agent 无法读取整个系统时，如何保持局部执行与全局一致？ |

---

## Part III — Scaling Agentic Engineering

这一层目前仍处于持续研究阶段。

当前研究方向包括：

- Workflow Runtime
- Retry、Resume 与 Re-execution
- Persistent Execution State
- Boundary Tax
- Optimal Reasoning Boundary
- Scalable Governance
- Decision Compression
- Capability Boundaries
- Runtime Verification
- Truth Change Propagation

这一层中的一部分内容已经以草稿章节的形式存在，并被标注为研究，而不是稳定方法论：[14](14-workflow-runtime-recovery/README.zh-CN.md) Workflow Runtime 与 Recovery、[15](15-boundary-tax/README.zh-CN.md) Boundary Tax 与 Optimal Reasoning Boundary、[16](16-scalable-governance/README.zh-CN.md) Scalable Governance 与 Decision Compression、[17](17-capability-boundaries/README.zh-CN.md) Capability Boundaries。

这些内容会先进入 Research 阶段。

当 Observation、Evidence 和 Principle 足够成熟以后，再提升为正式章节。

详见 [Research Incubator](research/README.zh-CN.md)。

---

### 附录

| 附录 | 主题 |
|---|---|
| [A](appendix/anti-patterns.zh-CN.md) | 常见失败模式 |
| [B](appendix/verification-strategies.zh-CN.md) | AI 产出验收策略 |
| [C](appendix/cheatsheet.zh-CN.md) | 速查表 |
| [D](appendix/operational-readiness.zh-CN.md) | 生产就绪与治理检查表 |

# 研究成熟度

仓库中的内容并不处于同一个成熟阶段。

当前使用三种状态：

### Observed Pattern

在真实 Workflow 或工程实践中反复观察到的现象。

### Derived Principle

从多个 Observation 中抽象出的更一般化原则。

### Working Hypothesis

目前看来有解释力，但仍然需要更多 Evidence、Challenge 或实践验证的理论模型。

这个区分非常重要。

新的想法不会因为被写进仓库就自动成为工程 Truth。

---

# Engineering Loop

当前方法论可以抽象成：

```text
Reality
↓
Evidence
↓
Truth Candidate
↓
Authorization
↓
Current Authorized Truth
↓
Scope / Boundary
↓
Agent Execution
↓
Verification
↓
Evidence
↓
Decision
├── Continue
├── Rework
└── Truth Challenge
```

这个循环具有递归性。

新的 Evidence 可能证明当前 Truth 仍然成立，也可能发现 Implementation Defect，还可能直接挑战当前 Truth。

---

# Practical Execution Loop

日常工作中，可以缩减为七个步骤。

1. **划分风险。** 明确 Agent 可以直接执行什么，什么需要审批，什么必须由 Human 负责。
2. **定义单一 Objective。** 写清预期结果、本次 Action、Acceptance Criteria 与 Boundary。
3. **提供 Bounded Context。** 只提供完成当前 Task 所需要的文件、事实、决策、Contract 与 Constraint。
4. **执行并自检。** 要求 Build、Test、Lint、Static Analysis 或其他适用检查。
5. **独立 Verification。** 检查 Delta、Relevant Behavior、越界修改，以及重要 Claim 背后的 Evidence。
6. **记录并 Handoff。** 将 Decision、Artifact、Evidence 与 Remaining Risk 写入 Authoritative System。
7. **度量并改进。** 关注 Rework、Escaped Defect、Review Cost、Exception 与 Workflow Cost。

---

# Minimum Task Contract

一个 Local Execution Task 至少应该包含：

```text
summary:             要达成什么结果？
currentAction:       本次具体执行什么？
acceptanceCriteria:  哪些可观察检查代表完成？
boundaries:          哪些内容不得修改或尝试？
```

任何一项缺失，都说明这个 Task 可能还没有进入可以可靠委托的状态。

需要注意：

这个 Contract 代表的是 **Local Execution Boundary**。

它不能替代 Project Truth、Architecture、System Invariant 与更高层 Authority。

整体关系更接近：

```text
Project Truth
↓
Architecture / Boundary
↓
Task Contract
↓
Agent Execution
↓
Verification
↓
Evidence
```

---

## 从模糊请求到可执行 Task

```text
差：

修复认证系统。

更好：

summary:
修复 Access Token 过期以后 Refresh Token 失败的问题。

currentAction:
追踪 Refresh Flow，只修改 Token Renewal Path。

acceptanceCriteria:
- 过期的 Access Token 可以成功续期
- 原有 Login Flow 继续通过
- 测试覆盖 Refresh Success 与 Failure

boundaries:
- 不修改 User Schema
- 不修改 OAuth Provider Configuration
```

第二个 Task 创建了一个更小、边界清晰、可以独立观察的 Reasoning World。

Agent 可以执行当前工作，同时不需要自行发明额外的 Product Decision 或 Architecture Decision。

---

# Truth、Verification 与 Authority

整个 Playbook 都遵循几个基础规则。

### Model Agreement 不代表 Proof

多个 Agent 可以降低 Single Model Error。

它们无法自动消除 Shared Blind Spot。

AI Consensus 可以成为 Evidence，但它本身不能自动升级为 Truth。

### Evidence 必须连接 Reality

重要 Claim 应该尽量回到这些来源：

- Repository State
- Primary Documentation
- Test
- Runtime Behavior
- Measurement
- Production Evidence
- Explicit Human Decision

### Authority 不应超过 Verification Capability

Human 或 Agent 能够拥有多大 Authority，取决于它是否拥有足够能力验证这个 Decision。

Architecture、Payment Behavior、Authentication、Security、Privacy、Compliance、Data Migration、Destructive Operation 和 Irreversible Action 等高风险区域，需要更强的 Ownership 和 Verification。

### State、Evidence 与 Truth 应保持分离

```text
State
= 当前 Execution 位于哪里

Evidence
= 什么信息支持“发生了什么”的 Claim

Truth
= 当前 Project 被授权继续依赖什么
```

把这三者混在一起，会让 Workflow 逐渐失去可靠性。

---

# Global 与 Local Reasoning

大型系统会出现一个特殊问题。

Agent 可能无法在一次推理中可靠理解：

- 整个 Repository
- 所有 Design Document
- 所有 Dependency
- 所有 Historical Decision

因此目标不应该是让每个 Worker 阅读整个世界。

更合理的目标是：

> **让 Agent 看清完成当前 Decision 所需要的完整 Relevant Reality。**

可以抽象成：

```text
Global Truth
├── System Invariants
├── Architecture Boundaries
├── Critical Contracts
└── Dependency Relationships
        ↓
Current Task
        ↓
Truth Projection
        ↓
Local Truth
+
Relevant Global Constraints
+
Relevant Dependencies
        ↓
Agent Reasoning
```

这也是当前方法论继续演化的重要方向之一。

---

# 推荐阅读路径

| 场景 | 建议 |
|---|---|
| 时间有限 | 01 → 07 → 08 |
| 开始 AI Assisted Development | 02 → 03 → 04 |
| 管理多个 Agent | 05 → 06 → 11 |
| 设计可靠 Agent Workflow | 06 → 08 → 11 → 12 |
| 深入理解 Task Decomposition | 02 → 09 → 10 |
| 处理大型系统 | 09 → 10 → 13 |
| 关注 Governance 与 Verification | 08 → 11 → 12 |
| 跟踪正在进行的研究 | [Research Incubator](research/README.zh-CN.md) |

---

# 与 Maestro 的关系

本 Playbook 的方法论保持 Platform Independent。

**Maestro** 是用于实践和验证这套方法论的一种可执行 Framework。

两者关系可以理解为：

```text
Agentic Engineering Principles
↓
AI Agent Playbook
↓
Reference Patterns
↓
Maestro
```

Playbook 用于定义和持续演化 Methodology。

Maestro 用来探索怎样把其中一部分原则编码成：

- Task Contract
- Role Boundary
- Gate
- State Transition
- Structured Handoff
- Workflow Execution

即使未来 Model、Provider、Agent Platform 或具体 Framework 发生变化，Playbook 本身仍然应该成立。

---

# 背景

本 Playbook 来自长期 AI Assisted Engineering 实践，包括大型支付系统相关工作、个人软件开发、Multi-Agent Workflow 与真实项目交付。

其中有些内容来自长期反复实践。

有些内容来自对大型工程系统的观察与抽象。

也有一些内容仍处于研究与验证阶段。

仓库会明确区分这些成熟度。

长期目标，是形成一套能够跨越 Model、Tool 与 Platform 变化的软件工程方法论。

---

# 结语

随着 AI 越来越擅长生产 Implementation，软件工程本身不会消失。

它的重心正在变化。

越来越重要的问题会变成：

```text
什么是真的？

Boundary 在哪里？

当前 Worker 有权改变什么？

什么 Evidence 才足以证明完成？

谁拥有 Decision Authority？

怎样证明整个系统仍然保持自洽？
```

一个成熟的 Agentic Engineering System，价值不在于能够委托最多的工作。

真正重要的是：

让强大的 Worker 可以高速执行，同时整个工程世界依然保持可理解、可验证、有边界、可恢复，并且始终处于可治理状态。

---

## License

`MIT`
