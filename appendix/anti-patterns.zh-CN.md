# 附录A — 常见失败模式

[日本語](anti-patterns.ja.md) · [English](anti-patterns.md) · **简体中文**

以下是实际 Agent 工作流中反复出现的失败，以及怎样从结构上预防它们。

本附录是这个 Playbook 的**失败模式导航**，由两部分组成：

- 六个高频基础失败模式，来自较早期实践，至今仍然成立；
- 一个按 Part 组织的跨章节失败模式索引。

每个章节正文中的失败模式是**权威定义位置**。本附录不复制它们。

---

## 反模式1：先改状态，之后再写日志

### 症状

任务先被标记为完成，工作记录和证据准备之后再补。

### 后果

系统中出现了没有原因的状态变化。下一个角色只能询问或猜测。如果需要回滚，也找不到可追溯的判断依据。

### 对策

**让状态变更成为一次原子状态转换（Atomic Transition）。** 记录原因和证据、修改状态、生成下一步交接必须作为一次操作完成，不允许只成功其中一部分。

## 反模式2：任务定义不完整就交接

### 症状

Agent 收到“差不多把这个功能做一下”之类的模糊请求。

### 后果

Agent 会用看似合理的假设填补空白。真实意图与实现的差异直到审查时才出现，造成不必要返工。

### 对策

交接前强制具备四项：

- 目标；
- 本次动作；
- 验收标准；
- 边界或非目标。

缺少任何一项，任务都还没有准备好。

## 反模式3：在一个会话中完成所有事情

### 症状

需求、实现、测试和缺陷修复共用同一个会话。

### 后果

上下文被污染。已确认决策、假设和失败尝试混合在一起，对话越长，输出越不稳定。

### 对策

**一个会话，一个职责。** 会话之间只传递结构化决策、约束、证据和下一步动作。

## 反模式4：每次手工教 Agent 规则

### 症状

每个新会话都要重新说明 Agent 可以做什么、不可以做什么。

### 后果

措辞变化导致规则漂移，准备成本上升，不同会话中的行为也不一致。

### 对策

把共享规则放进有版本管理的配置、模板或系统指令中，统一注入，并与任务特定上下文分开。

## 反模式5：把工作测试输出当作永久档案

### 症状

旧测试输出持续堆积在 Agent 用于理解当前状态的同一文件中。

### 后果

Agent 无法区分最新结果和历史快照，过期证据会污染当前判断。

### 对策

**分离工作状态与长期证据。** Agent 的运行上下文只保留最新结果；发布、法规或事故调查所需证据，应按时间、版本、环境、结果和审批人另行保存。不要保存所有噪声，也不要删除必要的审计证据。

## 反模式6：放任善意的范围扩张

### 症状

Agent 修改无关文件、增加未要求的文档，或执行不属于任务的重构。

### 后果

变更范围不可预测，审查成本上升。意外修改往往很晚才被发现，也更难追踪。

### 对策

明确禁止事项和非目标。可预测的边界，通常比“自由改进所有相关内容”更有价值。

## 失败模式索引

各章节是失败模式的权威定义位置。下面是按 Part 的导航。

### Part I — 个人 AI 工程（01–07）

任务粒度失衡、上下文污染、角色与职责混淆、工作流过度依赖人工纪律等。

→ [02](../02-task-granularity/README.zh-CN.md) · [03](../03-prompt-philosophy/README.zh-CN.md) · [04](../04-context-isolation/README.zh-CN.md) · [05](../05-agent-management/README.zh-CN.md) · [06](../06-workflow-as-product/README.zh-CN.md) · [07](../07-what-really-matters/README.zh-CN.md)

### Part II — 可靠 Agent 软件工程（08–17）

真相漂移、错误前提、证据不足、共享盲区、权限越界、投影陈旧、错误重试、恢复失败、边界协调成本、治理膨胀、能力误判等。

→ [08](../08-truth-governance/README.zh-CN.md) · [09](../09-effective-reasoning-scope/README.zh-CN.md) · [10](../10-boundaries-contracts-artifacts/README.zh-CN.md) · [11](../11-verification-evidence/README.zh-CN.md) · [12](../12-authority-human-gates/README.zh-CN.md) · [13](../13-global-local-truth/README.zh-CN.md) · [14](../14-workflow-runtime-recovery/README.zh-CN.md) · [15](../15-boundary-tax/README.zh-CN.md) · [16](../16-scalable-governance/README.zh-CN.md) · [17](../17-capability-boundaries/README.zh-CN.md)

### Part III — Human × AI 长期协作（18–24）

长期上下文污染、推断升级为事实、陈旧目标、过度个性化、决策替代、授权越界、错误归因、负复利等。

→ [18](../18-from-tool-to-long-term-collaborator/README.zh-CN.md) · [19](../19-persistent-personal-context/README.zh-CN.md) · [20](../20-personal-truth-and-memory-governance/README.zh-CN.md) · [21](../21-contextual-decision-support/README.zh-CN.md) · [22](../22-human-ai-decision-boundaries/README.zh-CN.md) · [23](../23-from-decision-to-agent-execution/README.zh-CN.md) · [24](../24-reality-feedback-and-long-term-evolution/README.zh-CN.md)

---

## 总结

这些失败具有同一个根源：依赖人的注意力和记忆。

“下次小心”不是控制措施。**应当用结构预防重复失败。**

---

[附录B → 验证策略](verification-strategies.zh-CN.md) · [附录C → 实战速查表](cheatsheet.zh-CN.md) · [附录E → 概念权威地图](concept-index.zh-CN.md) · [← 中文README](../README.md)
