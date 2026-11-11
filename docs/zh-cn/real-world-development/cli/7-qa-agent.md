---
title: "第 7 课 - 创建并使用 QA 智能体"
description: "创建一个 QA 自定义智能体，将 issue 要求、quality-checks skill 和 Playwright MCP 结合起来。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

你已使用 `quality-checks` skill 执行自动检查，并使用 Playwright MCP 在浏览器中观察筛选体验。现在将这些能力整合到一个具有明确 QA 流程的自定义智能体中。

本课将完成以下任务：

- 了解自定义智能体如何与说明、skills 和 MCP 工具协作。
- 创建并检查可复用的质量保证配置文件。
- 选择 QA 智能体，并根据筛选 issue 检查它的发现。

## 场景

在创建拉取请求（PR）之前，Tailspin Toys 希望一致地检查要求、代码质量、自动检查、测试覆盖率和浏览器行为。自定义智能体可以协调 QA 流程并提供可复用的报告。

## 什么是自定义智能体？

自定义智能体是在 Markdown 配置文件中定义的 Copilot 专用版本。配置文件描述智能体的用途、说明和可用工具。在本工作坊中，你将在 `.github/agents/qa.agent.md` 中定义 QA 角色，并在 Copilot CLI 中选择它。

你使用的自定义功能各有不同用途。存储库说明描述团队标准。`quality-checks` skill 包含可重复执行的检查。Playwright MCP 提供浏览器工具。QA 配置文件告诉 Copilot 如何使用这些能力评估要求并报告发现。它不会替代其他功能，也不需要另开对话。

## 创建 QA 配置文件

创建功能 PR 前，让 Copilot 创建一个可复用的 QA 配置文件。配置文件将定义 QA 执行的检查和必须遵循的界限。

1. 返回 Codespace，确认筛选对话处于 Interactive 模式。
2. 请求默认智能体创建新的自定义智能体：

   ```plaintext
   在 .github/agents/qa.agent.md 中创建一个名为 QA 的自定义智能体。它应根据 issue 和已达成一致的要求检查功能，遵循存储库说明，运行 quality-checks skill，使用 Playwright MCP 验证行为，并在测试覆盖不足时添加测试。

   它应将每项要求报告为通过、失败或受阻，并提供支持证据。修改实现代码前必须先询问，而且不得提交更改或创建拉取请求。

   目前只创建配置文件，供我检查。
   ```

## 检查配置文件

使用新智能体之前，先检查配置文件，确认 Copilot 已记录预期的 QA 工作流和界限。这样可以避免不完整或范围过大的智能体修改本来只想验证的功能。

1. 输入 `/diff` 并打开 `.github/agents/qa.agent.md`。
2. 阅读 frontmatter。`description` 是必需项；`name` 是可选项，但添加后可以为智能体提供清晰的显示名称。
3. 阅读配置文件说明，确认 QA 从要求开始，遵循存储库说明，运行 `quality-checks` skill 并使用 Playwright MCP。
4. 确认 QA 会提供支持证据、修改实现代码前会先询问，并且不会提交更改或创建拉取请求。
5. 如果生成的配置文件缺少任何职责或界限，请让默认智能体先修改，再继续。

## 根据 issue 执行 QA

Copilot CLI 会在对话开始时加载项目智能体。创建配置文件后，恢复同一个筛选对话并选择 QA，让它使用对话中的 issue 和规划决定。

1. 使用以下提示启用智能体：

   ```plaintext
   /agent QA
   ```

> [!NOTE]
> 刚创建的智能体可能不会立即出现在可用智能体列表中，但上述命令仍会启用它。

2. 使用以下提示让 QA 智能体检查功能：

   ```plaintext
   根据 issue 和我们计划中的决定检查筛选功能。它是否已准备好创建 PR？
   ```

3. QA 智能体会开始工作。
4. 完成后阅读它提供的报告。

## 总结和后续步骤

你为工作流添加了一个可复用的专用角色，并检查了它的工作结果。本课中，你：

- 了解了自定义智能体如何与说明、skills 和 MCP 工具协作。
- 创建并检查了可复用的质量保证配置文件。
- 选择了 QA 智能体，并根据筛选 issue 检查它的发现。

实现、skill 更新、QA 配置文件、测试和验证报告都已准备好供审核。接下来，你将[把它们整合到功能 PR 中，并使用 Agent Merge][next-lesson]。

## 资源

- [为 Copilot CLI 创建自定义智能体][create-agents]
- [自定义智能体配置][agent-config]

[previous-lesson]: ../6-mcp-playwright/
[next-lesson]: ../8-create-pull-request/
[create-agents]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/create-custom-agents-for-cli
[agent-config]: https://docs.github.com/copilot/reference/custom-agents-configuration
