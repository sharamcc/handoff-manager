# handoff-manager

`handoff-manager` 帮助维护 Agent 项目的交接文档：让下一轮工作能快速找到当前目标、必须遵守的约束、未完成任务和可追溯证据。它适用于审计、迁移、增量更新和完整性校验，不会因为安装了技能就自动改写项目文档。

## 安装

1. 克隆本仓库，或下载仓库文件：

   ```sh
   git clone https://github.com/sharamcc/handoff-manager.git
   ```

2. 按当前 Agent 宿主的技能安装说明，将仓库目录放入其可发现的技能目录，并保留 `SKILL.md` 与 `references/` 的相对结构。不同宿主的安装位置和发现方式可能不同；请以该宿主的文档为准。
3. 在宿主提供的技能列表或调用入口中确认 `handoff-manager` 可用。

## 选择工作模式

在请求中指定项目或交接文档，并选择以下模式。若不指定，Agent 会根据请求意图选择；写入范围不明确时采用只读模式。

| 模式 | 用途 | 是否写入 |
| --- | --- | --- |
| `AUDIT` | 检查文档体积、结构、冲突、过期状态和敏感信息风险，并提出整理建议 | 否 |
| `MIGRATE` | 在明确授权后整理或压缩现有交接文档，并保留完整恢复依据和迁移映射 | 仅交接相关文档 |
| `UPDATE` | 根据已完成工作、决定和验证证据，增量更新交接 | 仅授权的交接文档 |
| `VALIDATE` | 检查重要要求、任务、决定和历史证据是否仍可追溯 | 否 |

## 使用示例

将示例中的 `当前项目` 或 `HANDOFF.md` 换成实际路径或项目名称：

- 只读审计：`使用 handoff-manager，以 AUDIT 模式检查当前项目的 HANDOFF.md，并列出冲突和未核实项。`
- 迁移整理：`使用 handoff-manager，以 MIGRATE 模式整理当前项目的 HANDOFF.md；先确认原文可恢复，再按原文逐项建立迁移映射。`
- 日常更新：`使用 handoff-manager，以 UPDATE 模式根据本轮实际完成的工作和验证结果更新当前项目交接。`
- 完整性检查：`使用 handoff-manager，以 VALIDATE 模式检查当前项目交接中的人工约束、未完成任务和历史追溯。`

## 工作边界

- `AUDIT` 和 `VALIDATE` 只读；检查结果默认在对话中报告。
- `MIGRATE` 和 `UPDATE` 只修改明确授权的交接文档。不会自动修改业务代码、配置、凭据或部署环境，也不会删除旧文档。
- 迁移前检查敏感信息并验证原文恢复方式。发现秘密且没有受保护的恢复方案时，会暂停受影响内容的复制或覆盖。
- 将已验证事实、历史记录、AI 建议和待核实假设分开记录。提交或测试通过不能单独证明功能已部署。
- 不自动安装钩子、提交、推送、重置或改写 Git 历史；这些动作需要单独授权。

## 参考文档

- [技能行为、模式选择与权限](SKILL.md)
- [迁移流程与恢复要求](references/MIGRATION_WORKFLOW.md)
- [增量更新策略](references/UPDATE_POLICY.md)
- [交接文档结构建议](references/DOCUMENT_STRUCTURE.md)
- [交接入口模板](references/HANDOFF_TEMPLATE.md)
- [审计与校验清单](references/VALIDATION_CHECKLIST.md)
- [历史验收记录及其适用范围](references/TEST_RESULTS.md)
