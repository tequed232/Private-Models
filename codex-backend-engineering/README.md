# Codex Backend Engineering Playbook

一套面向 OpenAI Codex 的后端工程规范、可复用 Skill、任务 Prompt 与自主开发工作流。内容综合 Anthropic 的 Claude Code / Prompt Engineering / Autonomous Coding 实践，并按 Codex 的 `AGENTS.md` 与 Skills 机制重新组织。

> 这不是 Anthropic 官方发布的 Codex 模板，也不是把 Claude 专属命令直接搬过来；它是面向 Codex 的跨模型工程化整理。具体技术栈和命令必须以目标仓库实际情况为准。

## 目录

- [AGENTS.md](./AGENTS.md)：项目级长期工程约束模板
- [Backend Engineering Skill](./.agents/skills/backend-engineering/SKILL.md)：可复用后端工程工作流
- [Feature Implementation](./prompts/feature-implementation.md)：新功能端到端实现
- [Architecture Review](./prompts/architecture-review.md)：架构审查与重构决策
- [Security Audit](./prompts/security-audit.md)：安全审计
- [Performance Audit](./prompts/performance-audit.md)：性能分析与优化
- [Code Review](./prompts/code-review.md)：变更审查
- [Autonomous Development](./workflows/autonomous-development.md)：跨会话自主开发与进度持久化
- [Official Resources](./references/official-resources.md)：官方资料与适用边界

## 推荐使用方式

1. 将 `AGENTS.md` 中适合目标项目的内容复制到目标仓库根目录；补充实际技术栈、构建命令、测试命令、目录约定。
2. 将 `.agents/skills/backend-engineering/SKILL.md` 放入目标仓库的同路径，或按当前 Codex 版本支持的 Skills 目录进行安装。
3. 每次具体任务从 `prompts/` 选择模板，填入目标、约束、验收标准。
4. 大型任务采用 `workflows/autonomous-development.md`，把计划、测试清单和进度写入仓库文件，避免只依赖聊天上下文。
5. 要求 Agent 提供实际执行的命令、测试结果和 Git diff 证据；不能把“看起来正确”当作验证通过。

## 设计原则

- 先调查，再设计，再实现；复杂任务不要一上来就改代码。
- 先理解仓库现有架构，优先延续已验证的项目约定。
- 测试用于验证通用正确性，不是诱导硬编码或绕过需求的目标。
- 安全、数据一致性和兼容性是设计要求，不是上线前补丁。
- 性能优化应基于可复现的指标、Profile 或查询证据。
- 变更保持聚焦；不擅自覆盖用户改动或执行破坏性操作。
- 结论必须可追溯：区分已验证事实、推断、假设和未完成事项。

## 重要说明

- `AGENTS.md` 应保持精简，存放长期有效的项目规则；细分流程放进 Skills 或单次 Prompt。
- 示例中的技术组件（例如 PostgreSQL、JWT、Redis、Express）不是强制选型。
- 不要求所有任务都经过完整五阶段流程。小改动应直接执行，复杂改动才使用完整规划和验证流程。
- 不要将密钥、生产数据、个人信息或内部凭据写入文档、Prompt、日志或提交记录。
