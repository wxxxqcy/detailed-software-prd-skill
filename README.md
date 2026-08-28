# Detailed Software PRD Skill V2

用于生成、审查和维护详细软件需求文档（PRD / SRS）的 Skill。

V2 不再只是“PRD 生成器”，而是定位为：

> **AI Software Requirements Engineer**

## V2 核心能力

- 完整 PRD / SRS 生成
- 单模块需求生成
- 单页面需求生成
- PRD Review / 缺陷审查
- 需求变更影响分析
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
│   └── quality-checklist.md
├── examples/
│   ├── crm/
│   ├── ecommerce/
│   └── admin-system/
└── tests/
    ├── basic-prd.md
    ├── complex-workflow.md
    └── regression-checklist.md
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
