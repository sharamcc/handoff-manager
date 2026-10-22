# handoff-manager

精简项目交接入口，保留目标、约束、未完成任务与可追溯证据。支持只读审计（AUDIT）、迁移整理（MIGRATE）、增量更新（UPDATE）和完整性校验（VALIDATE）。

## 安装与使用

将本目录放入目标环境已确认的技能发现位置，保留 `SKILL.md` 与 `references/` 的相对结构，并确认技能可用。不预设特定 Agent、平台或安装目录。

使用自然语言指定项目和操作，例如：

- `使用 handoff-manager，以 AUDIT 模式检查当前项目的 HANDOFF.md。`
- `使用 handoff-manager，整理并保存当前项目交接；验证原文可恢复后执行迁移。`
- `使用 handoff-manager，根据本轮实际完成的工作更新项目交接。`
- `使用 handoff-manager，检查交接中的人工约束、未完成任务和历史追溯。`

只读模式默认在回答中报告；写入模式仅修改授权的交接文档。安装不会触发自动更新、钩子或 Git 操作。

## 文档

- [模式、共用规则与交付要求](SKILL.md)
- [迁移流程](references/MIGRATION_WORKFLOW.md) · [更新策略](references/UPDATE_POLICY.md)
- [文档分层](references/DOCUMENT_STRUCTURE.md) · [入口模板](references/HANDOFF_TEMPLATE.md)
- [校验清单](references/VALIDATION_CHECKLIST.md) · [历史验收记录](references/TEST_RESULTS.md)
