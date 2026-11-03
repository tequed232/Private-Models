# Official Resources and Source Notes

本手册是对公开资料的工程化归纳。以下链接用于核对原始方法与工具行为。

## Anthropic

### Claude Code: Best Practices for Agentic Coding
- https://www.anthropic.com/engineering/claude-code-best-practices
- 重点：先读相关文件、先制定计划再编码；复杂任务可使用子代理进行独立调查；测试驱动迭代；使用清单/草稿文件维持长任务进度；频繁校正方向。
- 适用迁移：把“先调查—再规划—再实现—再验证”的工作节奏用于 Codex。
- 注意：Claude Code 专属命令、快捷键和模型思考档位不能直接视为 Codex 功能。

### Claude Code Best Practices (Research)
- https://www.anthropic.com/research/claude-code-best-practices
- 重点：迭代开发、TDD、视觉验证、上下文管理、自动化工作流。

### Prompting Best Practices
- https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices
- 重点：明确直接的指令、定义输出格式和约束、提供结构化上下文、要求通用解法而不是硬编码、先检查代码再作判断。
- 适用迁移：用于编写清晰的任务 Prompt 和验收标准。
- 注意：模型特定技巧需要针对 Codex 当前模型重新评估，不应照搬模型专属提示技巧。

### Claude Quickstarts — Autonomous Coding Agent
- https://github.com/anthropics/claude-quickstarts/tree/main/autonomous-coding
- 重点：Initializer Agent 先将规格拆成可测试功能清单；后续 Coding Agent 每次完成一部分，并把进度持久化到文件/Git。
- 适用迁移：采用初始化规划 + 分阶段编码 + 持久化进度的两阶段模式。
- 注意：示例使用 Claude Agent SDK；此处借鉴的是工作流思想，不是 SDK 兼容性。

## OpenAI / Codex

### Codex customization
- https://developers.openai.com/codex
- Codex 的项目指令、Skills、MCP 和子代理等定制能力入口。具体行为以当前官方文档为准。

### AGENTS.md project instructions
- https://learn.chatgpt.com/docs/agent-configuration/agents-md
- 说明 Codex 如何发现并组合全局与项目级指令，以及如何使用嵌套指令。
- 推荐：把长期、普遍适用的规则放入 AGENTS.md；具体工作流程放入 Skill 或任务 Prompt，避免根指令过长。

### Iterating Development Workflows with Codex
- https://developers.openai.com/cookbook/examples/codex/iterating-development-workflows-with-codex
- 重点：通过 GOALS/PLANS/PROMPTS、阶段文件、上下文记录和 build log 管理迭代式开发。
- 适用迁移：为跨会话工作建立可恢复的仓库内状态。

## How to interpret these sources

- Anthropic 的实践文章是方法论参考，不代表其内容是可直接导入 Codex 的官方模板。
- OpenAI 的 Codex 文档决定 Codex 指令文件和 Skills 的实际发现/加载方式；如果路径或配置发生变化，以当前官方文档为准。
- 本仓库模板是经过整合的建议起点，不保证适用于所有语言、框架、架构或合规环境。
- 安全审计、性能评估和测试深度应根据真实威胁模型、流量和业务风险调整。
