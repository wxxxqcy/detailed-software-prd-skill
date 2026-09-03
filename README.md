# Detailed Software PRD Skill V2.1.0

用于生成、审查和维护详细软件需求文档（PRD / SRS）的 Skill。

V2 不再只是“PRD 生成器”，而是定位为：

> **AI Software Requirements Engineer**

## V2 核心能力

- 完整 PRD / SRS 生成
- 单模块需求生成
- 单页面需求生成
- PRD Review / 缺陷审查
- 需求变更影响分析
- Interactive Requirement Intake：交互式需求澄清 / 需求访谈
- MODE-F Lite：已开发系统反向 PRD
- 需求缺口发现
- Mermaid 功能架构 / 信息架构 / Sitemap / 流程 / 状态机 / ER 图
- ASCII Page / Modal / Drawer / Empty / Loading / Error 原型
- 页面字段、列表、按钮、交互、跳转、状态、异常
- 页面权限 / 操作权限 / 数据权限 / 字段权限
- 业务对象生命周期与状态机
- Given / When / Then 验收标准
- 需求编号与可追踪性
- Mermaid / ASCII / 正文一致性检查
- Open Questions 管理

## 目录

```text
detailed-software-prd-v2/
├── SKILL.md
├── README.md
├── references/
│   ├── interactive-requirement-intake.md
│   ├── prd-template.md
│   ├── requirement-analysis.md
│   ├── page-specification.md
│   ├── ascii-wireframe.md
│   ├── mermaid.md
│   ├── business-rules.md
│   ├── permissions.md
│   ├── state-machine.md
│   ├── acceptance-criteria.md
│   ├── prd-review.md
│   ├── change-impact.md
│   ├── quality-checklist.md
│   ├── reverse-prd-lite.md
│   ├── page-lite.md
│   └── reverse-quality-lite.md
├── examples/
│   ├── crm/
│   ├── ecommerce/
│   └── admin-system/
└── tests/
    ├── basic-prd.md
    ├── complex-workflow.md
    ├── regression-checklist.md
    ├── mode-f-lite.md
    └── interactive-intake.md
```

## 推荐调用方式

显式调用：

```text
@detailed-software-prd

生成一个完整的企业合同管理系统 PRD。
```

单模块：

```text
@detailed-software-prd

只设计订单管理模块。
```

单页面：

```text
@detailed-software-prd

只生成 P-023 客户列表页，要求完整 ASCII 原型、字段、按钮、交互、权限和验收标准。
```

Review：

```text
@detailed-software-prd

Review 下面这份 PRD，找出遗漏、冲突、不可开发和不可测试的地方。
```

变更影响：

```text
@detailed-software-prd

现有合同系统增加“续签”功能，请分析受影响的功能、页面、流程、状态、权限、数据和验收标准。
```

## Interactive Requirement Intake：交互式需求澄清

V2.1.0 新增跨模式交互式需求访谈能力。

它不是 MODE-G，而是可以和 MODE-A ~ MODE-F 组合使用。

### 标准调用

```text
@detailed-software-prd

开启 Interactive Intake。
我要做一个供应商管理系统。
先不要生成 PRD，先把必须确认的信息跟我问清楚。
达到生成门槛后再执行 MODE-A。
```

Skill 会：

```text
读取已有需求
→ 提取已确认事实
→ 找出真正缺口
→ 每轮询问 3～5 个问题
→ 接收简写答案
→ 更新需求事实
→ 达到生成门槛
→ 再进入目标 MODE
```

支持直接回答：

```text
1C
2B，48小时
3 待确认
4 就按你的建议
```

### 快速澄清

```text
@detailed-software-prd

Interactive Intake / 快速。
只问会阻塞核心流程的问题。
信息足够后直接生成 MODE-A 第一版。
```

### MODE-F + Interactive Intake

```text
@detailed-software-prd

MODE-F Lite + Interactive Intake。

先读取当前系统。
代码能确认的不要问我。
只把会阻塞流程、测试或交付的问题拿来确认。
```

核心原则：

> 先取证，后提问。

> AI 建议不是正式需求，只有需求人员明确接受后才能转为已确认需求。

## GitHub 部署

将整个目录提交到 GitHub，而不是只提交单个 `SKILL.md`。

推荐：

```bash
git add .
git commit -m "Add V2 software PRD skill"
git push
```

## 版本策略

建议：
- `main`：稳定版本
- `dev`：开发版本
- Tag：`v2.0.0`、`v2.1.0`

## 说明

V2 的关键变化是把长规则拆入 `references/`，由 `SKILL.md` 负责调度。这样更容易维护，也能避免一个文件过长导致规则执行不稳定。


## MODE-F Lite：现有系统反向 PRD

适合“系统已经做了大部分，现在需要根据真实实现补 PRD”的场景。

核心原则：

> 看得到就记录，看不到就【待确认】，不猜。

> 一次一个 STEP；页面详细整理时一次最多 5 页。

### STEP-1：单端页面盘点

```text
@detailed-software-prd

MODE-F Lite / STEP-1

只盘点当前商城 A 端。
不要猜 A 端的业务含义。

以当前页面、路由、代码和我明确提供的信息为事实来源。
看得到的写【现有实现】；
我明确要求的写【已确认需求】；
无法确认的写【待确认】；
AI 优化想法只能写【建议】。

本轮只输出：
1. 页面清单
2. 页面入口/路由
3. 已发现主要功能
4. 页面跳转
5. 实现状态
6. 待确认问题

完成后停止，不进入下一 STEP。
```

B 端、C 端分别新开任务，用同样方式盘点。

### STEP-2：核心流程

```text
MODE-F Lite / STEP-2

根据已经确认的页面清单，只还原当前系统真实存在的核心业务流程。
禁止为了流程完整而增加新状态、新按钮或新业务规则。
完成后停止。
```

### STEP-3：页面详细需求

```text
MODE-F Lite / STEP-3

本轮只整理 P-A-001 ~ P-A-005。
一次不超过 5 个页面。

按 page-lite.md 输出。
不要重新设计页面。
完成后停止。
```

### STEP-4：三端关系检查

```text
MODE-F Lite / STEP-4

基于已确认的 A/B/C 页面与流程，检查三端之间的数据、状态、操作结果和权限是否能对应。
只报告真实关系、差异和待确认项，不重新设计系统。
完成后停止。
```

### STEP-5：测试与缺口

```text
MODE-F Lite / STEP-5

只针对当前已实现能力和已确认需求整理核心测试场景、已知缺口、测试阻塞项和客户演示风险。
【待确认】不得写成正式验收条件。
完成后停止。
```

### STEP-6：合并最终 PRD

```text
MODE-F Lite / STEP-6

把前面已经确认的内容合并为最终 PRD。
只合并，不重新推理，不新增功能、状态、角色或页面。
执行 reverse-quality-lite.md 最终检查。
```

## V2.1.0 变更原则

V2.1.0 的核心新增能力是 **Interactive Requirement Intake / 交互式需求澄清**。

本版本重点：
- 不把交互问答做成新的 MODE-G，而是作为 MODE-A ~ MODE-F 的跨模式前置能力。
- 默认先提取已有信息，再提问，避免重复问需求人员。
- 每轮 3～5 个高价值问题，支持简写回答与“待确认 / 跳过 / 请给建议”。
- 建立需求事实状态：已确认 / 部分确认 / 待确认 / 已延期 / 存在冲突。
- MODE-F 与 Intake 联动时坚持“先取证、后提问”。
- 行业常见检查项只用于发现问题，不再作为默认需求来源。

MODE-A ~ MODE-F 的主要工作模式保持兼容，不进行大规模重构。
