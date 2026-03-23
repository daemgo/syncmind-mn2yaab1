# 输出规则

## Markdown 展示模板

### 模式 B（迭代更新）前缀

仅在迭代模式下，在正文前插入变更摘要：

```markdown
---
### 本次更新摘要

**版本**：{oldVersion} → {newVersion}
**输入**：{新素材简述}

**变更**：
- {changeSummary 各条}
---
```

### 正文模板

```markdown
# 【销售作战指南】：{customerName}

> v{version} · {urgency}紧急度 · {timingStage} · {generatedAt}

## 1. 时机判断

**阶段**：{timingStage}
**紧急度**：{urgency}

**判断依据**：
- {analysisBasis 各条}

**切入策略**：{entryStrategy}

## 2. 竞对作战卡

[对每个竞对输出一个卡片]

### {competitor}

| 维度 | 内容 |
|------|------|
| 威胁等级 | {threat} |
| 竞对优势 | {strengths} |
| 竞对弱点 | {weaknesses} |

**应对策略**：{counterStrategy}

---

## 3. 决策链条

### 关键角色

**决策者**：
[角色、姓名（如有）、关注点、接触策略]

**影响者**：
[同上]

**潜在阻碍者**：
[风险 + 化解策略]

### 决策流程

{decisionProcess}

**审批路径**：{approvalPath，用 → 连接}
**预估周期**：{timeline}

## 4. 各阶段关注点

**首次接触**：{firstContact}
**跟进沟通**：{followUp}
**产品演示**：{demo}
**商务谈判**：{negotiation}
**签约收尾**：{closing}

### ⚠️ 禁区话题
- {avoidTopics 各条}

## 5. 快速筛选问题

| # | 问题 | 目的 |
|---|------|------|
| 1 | {question} | {purpose} |

### 收尾问题
| # | 问题 | 目的 |
|---|------|------|
| 1 | {question} | {purpose} |

## 6. 行动计划

| 优先级 | 行动 | 截止时间 | 执行人 | 状态 |
|--------|------|---------|--------|------|
| {priority} | {action} | {deadline} | {owner} | {status} |

## 7. 跟进里程碑

| 里程碑 | 触发动作 | 升级策略 |
|--------|---------|---------|
| {milestone} | {triggerAction} | {escalation} |
```

> 作战指南生成完毕。运行 `/requirements` 整理客户需求。

---

## JSON 写入规则

写入路径：`docs/customer/sales-guide.json`

### 写入策略

- **首次写入**：创建完整 JSON
- **迭代写入**：读取现有文件，只覆盖有变化的字段
- **始终更新**：metadata.generatedAt、metadata.version
- **UTF-8 编码**，JSON 缩进 2 个空格

### humanizer-zh 处理清单

| 字段路径 | 处理重点 |
|----------|---------|
| timing.entryStrategy | 具体可执行，不泛泛 |
| competitors[].counterStrategy | 像有经验的销售在教新人 |
| decisionChain.*.approachStrategy | 具体到方式和语言风格 |
| situationalHooks.* | 关注点描述，不是话术 |
| interviewGuide.*.question | 口语化，像同事聊天 |
| nextActions[].action | 具体到可执行 |
