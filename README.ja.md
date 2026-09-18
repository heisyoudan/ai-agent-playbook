# AI Agent Playbook

**日本語** · [English](README.md) · [简体中文](README.zh-CN.md)

> AI Agent を前提とした、信頼できるソフトウェアエンジニアリング・ワークフローを設計するための実践的方法論。

このリポジトリでは、ひとつの問いを継続的に研究している。

> **AI がソフトウェア開発の主要な実行層になっていくとき、成果を信頼可能・検証可能・境界付き・回復可能・統治可能な状態に保つために、エンジニアリングそのものをどのように再設計すべきか。**

---

## これは何か

より強いモデルや、より良い Prompt は実行能力を高める。

しかし、それだけで信頼できるソフトウェアエンジニアリング体系が生まれるわけではない。

安定した AI 開発には、Agent を取り巻く工程全体の設計が必要になる。

たとえば：

- 何を Project Truth として扱うのか
- 作業をどのように分解するのか
- Agent にどの Context を渡すのか
- Agent が何を変更してよいのか
- Boundary と Contract をどう定義するのか
- 成果をどう Verification するのか
- どの Evidence を保持するのか
- 重要な判断を誰が承認できるのか
- Failure、Retry、Handoff をどう扱うのか

本 Playbook は、これらを **Agentic Software Engineering** のための、プラットフォーム非依存な方法論として整理する。

目標は、より強力になる Agent が高速に作業しても、Truth、Boundary、Traceability、Human Control が失われないエンジニアリング環境を作ることである。

---

## この Playbook が解決する問題

AI の失敗に見える問題の多くは、実際にはエンジニアリング・システムの問題である。

局所的な実行では、次のような問題が起こりやすい。

- Task が大きすぎる
- Context にノイズが多い、または必要情報が不足している
- Ownership が曖昧
- Acceptance Criteria が弱い
- Scope が無制限に拡大する
- Handoff に必要な状態が残っていない

システム規模が大きくなると、さらに深い問題が現れる。

- Truth Drift
- Agent Authority の肥大化
- Evidence の陳腐化や不足
- 複数モデルが同じ Blind Spot を共有する
- Cross-boundary inconsistency
- Human Gate の認知過負荷
- Workflow 中断後に状態を再構築できない

本 Playbook は、この両方を対象とする。

---

## 対象読者

- すでに AI を業務で使っているが、結果がまだ安定していないエンジニア
- 複数 Session や複数 Role で Coding Agent を運用している開発者
- AI Engineering Workflow を設計するテクニカルリード
- 実際の Delivery に Agentic Software Engineering を導入したいチーム
- AI 時代に Truth、Verification、Authority、Workflow がどう変わるべきかを研究している実践者

---

# Core Principles

この Playbook の初期段階は、次の3行で表現できる。

```text
AI is the execution layer.
Process creates productivity.
Constraints create stability.
```

方法論が発展する中で、もうひとつ重要な層が加わった。

```text
Truth must have authority.
Implementation must have boundaries.
Completion must have evidence.
```

Coding skill は今でも重要である。

Architecture、Debugging、Judgment、Verification、Risk Analysis を支える基礎だからである。

一方で、Routine Code Production の希少性は急速に低下している。

Execution が安価になるほど、エンジニアリング価値は次の領域へ移動していく。

- Truth Governance
- Reasoning Scope
- Architecture と Decomposition
- Verification
- Evidence
- Decision Authority
- Workflow Design

---

# Repository Structure

Playbook は3つの層に分かれている。

## Part I — Agent Collaboration Foundations

単体 Agent と Multi-Agent Workflow を安定させるための基礎。

| 章 | タイトル | Main Idea |
|---|---|---|
| [01](01-ai-redefines-work/README.ja.md) | AI Redefines Work | AI によってエンジニアリング価値とボトルネックの位置が変わる。 |
| [02](02-task-granularity/README.ja.md) | Task Granularity | Task は Agent が信頼して推論できる範囲に収まりつつ、意味のある一つの Loop を閉じる必要がある。 |
| [03](03-prompt-philosophy/README.ja.md) | Complex Minimalism | 必要情報を最大化し、ノイズを最小化する。 |
| [04](04-context-isolation/README.ja.md) | Context Isolation | 一つの Context に一つの主要責務を持たせ、構造化された Handoff で状態を渡す。 |
| [05](05-agent-management/README.ja.md) | Multi-Agent Management | Role、Constraint、Acceptance、Failure Handling、Handoff を定義する。 |
| [06](06-workflow-as-product/README.ja.md) | Workflow as a Product | 再利用可能な手順、Gate、Rollback、Authoritative State を仕組みにする。 |
| [07](07-what-really-matters/README.ja.md) | What Really Matters | 長期的な強みは Agent の周囲にあるエンジニアリング・システムを設計する能力にある。 |

---

## Part II — Governed Agentic Engineering

Agent を効率よく使う段階から、信頼できる Agentic Engineering System を構築する段階へ進む。

| 章 | タイトル | Main Question |
|---|---|---|
| [08](08-truth-governance/README.ja.md) | Truth Governance | Agent は何を Truth として信頼でき、誰がそれを変更できるのか。 |
| [09](09-effective-reasoning-scope/README.ja.md) | Effective Reasoning Scope | AI は一度の有効な推論で、どの程度の問題空間を信頼して理解できるのか。 |
| [10](10-boundaries-contracts-artifacts/README.ja.md) | Decomposition, Boundaries & Contracts | 複雑なシステムを、調整コストを増やしすぎずにどう分割するか。 |
| [11](11-verification-evidence/README.ja.md) | Verification & Evidence | Completion Claim を信頼できる状態にするには、どの Evidence が必要か。 |
| [12](12-authority-human-gates/README.ja.md) | Authority, Human Gates & Decision Compression | どの Decision を Human に委ねるべきか。また Human Attention をどう Scale させるか。 |
| [13](13-global-local-truth/README.ja.md) | Global Truth, Local Truth & Truth Projection | Agent がシステム全体を読めない状況で、局所実行と全体整合性をどう維持するか。 |

---

## Part III — Scaling Agentic Engineering

この層は現在も Research 中である。

主な研究テーマ：

- Workflow Runtime
- Retry、Resume、Re-execution
- Persistent Execution State
- Boundary Tax
- Optimal Reasoning Boundary
- Scalable Governance
- Decision Compression
- Capability Boundaries
- Runtime Verification
- Truth Change Propagation

この層の一部は、すでに草稿の章として存在し、安定した方法論ではなく Research として明示している：[14](14-workflow-runtime-recovery/README.ja.md) Workflow Runtime & Recovery、[15](15-boundary-tax/README.ja.md) Boundary Tax & Optimal Reasoning Boundary、[16](16-scalable-governance/README.ja.md) Scalable Governance & Decision Compression、[17](17-capability-boundaries/README.ja.md) Capability Boundaries。

これらは最初に Research として記録される。

Observation、Evidence、Principle が十分に成熟した段階で、正式な Chapter へ昇格する。

詳しくは [Research Incubator](research/README.ja.md) を参照。

---

### 付録

| 付録 | タイトル | 概要 |
|---|---|---|
| [A](appendix/anti-patterns.ja.md) | **よくある失敗パターン** | 実戦で踏んだ地雷と、その対処法。 |
| [B](appendix/verification-strategies.ja.md) | **AI 出力の検収戦略** | AI の成果物を効率的に検証するための実践手法。 |
| [C](appendix/cheatsheet.ja.md) | **早見表（Cheat Sheet）** | 全章の核心原則を1枚にまとめた早見表。 |
| [D](appendix/operational-readiness.ja.md) | **実運用・ガバナンスチェックリスト** | リスク、データ、承認、計測、監査、停止条件を運用に落とす。 |

---

# Research Maturity

このリポジトリ内のすべての考え方が、同じ成熟度にあるわけではない。

現在は3つのレベルを区別する。

### Observed Pattern

実際の Workflow やエンジニアリング実務で繰り返し観察された現象。

### Derived Principle

複数の Observation から抽象化された、より一般的な Principle。

### Working Hypothesis

現時点では説明力があるが、さらに Evidence、Challenge、実践検証を必要とする理論モデル。

新しいアイデアが Repository に書かれたという理由だけで、Engineering Truth になることはない。

---

# The Engineering Loop

現在の方法論は、次の Loop として表現できる。

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

この Loop は再帰的である。

新しい Evidence は、現在の Truth を支持することもあれば、Implementation Defect を発見することもあり、既存の Truth 自体を Challenge することもある。

---

# Practical Execution Loop

日々の実務では、7つの Step に圧縮できる。

1. **Risk を分類する。** Agent が直接実行できること、Approval が必要なこと、Human が所有すべきことを決める。
2. **一つの Objective を定義する。** Outcome、Current Action、Acceptance Criteria、Boundary を明示する。
3. **Bounded Context を渡す。** Task に必要な File、Fact、Decision、Contract、Constraint のみを含める。
4. **実行と Self-check を行う。** Build、Test、Lint、Static Analysis など適用可能な確認を要求する。
5. **Independent Verification を行う。** Delta、Relevant Behavior、Scope Violation、重要な Claim を支える Evidence を確認する。
6. **記録して Handoff する。** Decision、Artifact、Evidence、Remaining Risk を Authoritative System に残す。
7. **Measure and Improve.** Rework、Escaped Defect、Review Cost、Exception、Workflow Cost を追跡する。

---

# Minimum Task Contract

Local Execution Task は最低限、次の情報を持つべきである。

```text
summary:             何を達成するか
currentAction:       今回何を実行するか
acceptanceCriteria:  どの観測可能な確認をもって完了とするか
boundaries:          何を変更・実行してはいけないか
```

いずれかが欠けている場合、その Task はまだ信頼して委譲できる状態ではない可能性がある。

この Contract は **Local Execution Boundary** を表す。

Project Truth、Architecture、System Invariant、高位 Authority を置き換えるものではない。

概念的には：

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

## 曖昧な依頼から実行可能な Task へ

```text
悪い例:

認証システムを修正する。

良い例:

summary:
Access Token 失効後に発生する Refresh Token 障害を修正する。

currentAction:
Refresh Flow を追跡し、Token Renewal Path のみを修正する。

acceptanceCriteria:
- 失効した Access Token が正常に更新される
- 既存の Login Flow が引き続き成功する
- Refresh Success / Failure の Test が存在する

boundaries:
- User Schema を変更しない
- OAuth Provider Configuration を変更しない
```

後者は、より小さく、観測可能で、境界が明確な Reasoning World を作る。

Agent は余計な Product Decision や Architecture Decision を発明せずに作業を開始できる。

---

# Truth, Verification, and Authority

Playbook 全体で、いくつかの基本ルールを共有する。

### Model Agreement は Proof ではない

複数 Agent は Single Model Error を減らすことができる。

しかし、Shared Blind Spot を自動的に消すことはできない。

AI Consensus は Evidence にはなり得るが、それだけで Truth になるわけではない。

### Evidence は Reality と接続される必要がある

重要な Claim は、可能な限り次の Source に Grounding されるべきである。

- Repository State
- Primary Documentation
- Test
- Runtime Behavior
- Measurement
- Production Evidence
- Explicit Human Decision

### Authority は Verification Capability を超えるべきではない

Human や Agent が持てる Authority は、その Decision を意味のある形で検証できる能力によって制限される。

Architecture、Payment Behavior、Authentication、Security、Privacy、Compliance、Data Migration、Destructive Operation、Irreversible Action などの高リスク領域では、より強い Ownership と Verification が必要になる。

### State、Evidence、Truth は分離する

```text
State
= Execution が現在どこにいるか

Evidence
= 何が起きたかという Claim を何が支えるか

Truth
= Project が現在どの前提を信頼して進んでよいか
```

これらを混同すると、Workflow は脆くなる。

---

# Global and Local Reasoning

大型システムには特有の問題がある。

Agent は一度の推論で、次のすべてを安定して理解できるとは限らない。

- Repository 全体
- すべての Design Document
- すべての Dependency
- すべての Historical Decision

目標は、各 Worker に世界全体を読ませることではない。

重要なのは：

> **現在の Decision に必要な Relevant Reality を完全に見せること。**

概念的には：

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

これは現在進化中の方法論における中心的テーマの一つである。

---

# Reading Paths

| 状況 | 推奨パス |
|---|---|
| 時間がない | 01 → 07 → 08 |
| AI Assisted Development を始めたい | 02 → 03 → 04 |
| 複数 Agent を管理したい | 05 → 06 → 11 |
| 信頼できる Agent Workflow を設計したい | 06 → 08 → 11 → 12 |
| Task Decomposition を深く理解したい | 02 → 09 → 10 |
| 大型システムを扱う | 09 → 10 → 13 |
| Governance と Verification に関心がある | 08 → 11 → 12 |
| 進行中の Research を追いたい | [Research Incubator](research/README.ja.md) |

---

# Maestro との関係

本 Playbook の Methodology は Platform Independent である。

**Maestro** は、この方法論の一部を実行可能な形で試し、検証するための Framework の一つである。

関係は次のように整理できる。

```text
Agentic Engineering Principles
↓
AI Agent Playbook
↓
Reference Patterns
↓
Maestro
```

Playbook は Methodology を定義し、継続的に進化させる。

Maestro は、その一部を次のような実行可能構造へ変換する方法を検証する。

- Task Contract
- Role Boundary
- Gate
- State Transition
- Structured Handoff
- Workflow Execution

将来 Model、Provider、Agent Platform、Framework が変わっても、Playbook 自体は有効であるべきだと考えている。

---

# Background

この Playbook は、長期的な AI Assisted Engineering の実践から生まれた。

対象には、大規模決済システムに関わる業務、個人ソフトウェア開発、Multi-Agent Workflow、実際の Project Delivery が含まれる。

内容の一部は、繰り返し実践された経験から得られている。

一部は、大規模エンジニアリング・システムの観察から抽象化されたものである。

また、一部は現在も Research と Validation の途中にある。

この Repository では、それらの成熟度を意識的に区別する。

長期的な目標は、Model、Tool、Platform が変化しても残り続けるソフトウェアエンジニアリング方法論を作ることである。

---

# Closing Thought

AI が Implementation を生成する能力を高めても、Software Engineering 自体が消えることはない。

その中心が変化する。

より重要になる問いは：

```text
何が Truth なのか。

Boundary はどこにあるのか。

現在の Worker は何を変更できるのか。

Completion を証明する Evidence は何か。

誰が Decision Authority を持つのか。

システム全体が今も整合していると、どう証明するのか。
```

成熟した Agentic Engineering System の価値は、最も多くの仕事を委譲できることではない。

強力な Worker が高速に動きながら、その工程世界全体が理解可能・検証可能・境界付き・回復可能・統治可能な状態を保てること。

そこに本当の価値がある。

---

## License

`MIT`
