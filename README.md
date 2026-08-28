# Detailed Software PRD Skill V2.0.1

用于生成、审查和维护详细软件需求文档（PRD / SRS）的 Skill。

V2 不再只是“PRD 生成器”，而是定位为：

> **AI Software Requirements Engineer**

## V2 核心能力

- 完整 PRD / SRS 生成
- 单模块需求生成
- 单页面需求生成
- PRD Review / 缺陷审查
- 需求变更影响分析
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
    └── mode-f-lite.md
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

## V2.0.1 变更原则

V2.0.1 是 MODE-F Lite 专项增强版本。

MODE-A ~ MODE-E 的现有结构保持不变；此前测试中发现的通用优化项先进入后续版本 backlog，不在本版本进行大规模重构。
