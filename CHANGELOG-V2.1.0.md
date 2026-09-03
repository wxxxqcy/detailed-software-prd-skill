
# CHANGELOG V2.1.0

## 版本主题

**Interactive Requirement Intake / 交互式需求澄清**

V2.1.0 让 `detailed-software-prd` 从“需求文档生成器”进一步变成可以主动做需求访谈的 AI Software Requirements Engineer。

---

## 新增

### 1. 跨模式 Interactive Intake

新增：

- `references/interactive-requirement-intake.md`
- `tests/interactive-intake.md`

Interactive Intake 不是 MODE-G，可与 MODE-A ~ MODE-F 任意组合。

---

### 2. 需求事实表

交互过程中区分：

- ✅ 已确认
- 🟡 部分确认
- ⚪ 待确认
- ⏸ 已延期
- ⚠️ 存在冲突

避免 AI 把未回答、建议或行业常识误写成正式需求。

---

### 3. 逐轮提问机制

默认：

- 每轮 3～5 个问题
- P0 阻塞项优先
- 已知信息不重复问
- 支持选择题 + 自定义回答
- 支持 `1C 2B 3待确认`
- 支持“不知道 / 先跳过 / 你给建议”

---

### 4. 生成门槛

新增 Readiness Gate。

达到“目标、范围、角色、核心对象、主流程、关键规则”基本可成立后，即可进入第一版 PRD，不用等待所有 P1/P2 细节全部回答。

---

### 5. MODE-F 联动

MODE-F + Interactive Intake 强制：

> 先取证，后提问。

代码和页面已经能回答的问题不得再次询问需求人员。

当需求人员的【已确认需求】与【现有实现】冲突时：
- 两者并列
- 记录实现差异
- 不相互覆盖

---

## 调整

### requirement-analysis.md

明确：
- 行业常见检查项只用于发现提问线索
- 不能直接转成正式需求
- Interactive Intake 中优先使用已确认事实

### reverse-prd-lite.md

新增与 Interactive Intake 的联动规则。

### SKILL.md

新增跨模式调度规则、读取策略、交互安全边界和最终一致性检查。

---

## 兼容性

- MODE-A ~ MODE-F 保持兼容。
- V2.0.1 的 MODE-F Lite 核心执行方式不变。
- 本版本不引入 AUTO 全自动模式，也不重构旧模式，避免扩大变更范围。
