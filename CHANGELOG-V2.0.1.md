# V2.0.1 Changelog

## 目标
本版本只做一件主线事情：让能力较弱的 AI 能够根据已开发系统，分步骤反向整理可信 PRD。

## 新增
- MODE-F Lite：现有系统反向 PRD
- `references/reverse-prd-lite.md`
- `references/page-lite.md`
- `references/reverse-quality-lite.md`
- `tests/mode-f-lite.md`

## SKILL.md 小范围增强
- Skill 目录默认只读
- 用户指定文件白名单为硬边界
- “没有提到”不等于 Out of Scope
- 实现事实与已确认需求冲突时并列记录，不互相覆盖
- MODE-F Lite 四级事实标签与四级实现状态

## 暂不处理
MODE-C / MODE-D / MODE-E 等此前测试发现的通用优化项进入后续版本 backlog，不在 V2.0.1 大改。
