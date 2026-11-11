---
title: "第 6 课 - 使用 Playwright MCP 验证功能"
description: "在 Copilot CLI 中检查或配置 Playwright MCP，并在浏览器中探索筛选功能。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

正如前面提到的，编写代码不只是写代码。我们还要处理数据、外部服务，并让 Copilot 使用更多自动化功能。MCP 服务器可以帮助 Copilot 超越 CLI 内置功能，使用更多工具和服务。

本课将完成以下任务：

- 了解什么是 Model Context Protocol（MCP），以及 Copilot CLI 如何使用它。
- 如果尚不可用，则添加 Playwright MCP 服务器。
- 让智能体控制浏览器并探索筛选功能。

## 场景

单元测试和端到端测试很重要，但要验证 UI 更新，就必须实际与 UI 交互。你希望 Copilot 像用户一样使用正在开发的网站，进一步自动化更改过程，从而更有把握地确认更新符合预期。

## 什么是 Model Context Protocol（MCP）？

[Model Context Protocol（MCP）][mcp-blog-post]为 AI 智能体提供了与外部工具和服务通信的方式。通过 MCP，AI 智能体可以访问最新信息，并代表你执行操作。

这些工具和资源通过 MCP 服务器访问。MCP 服务器是 AI 智能体与外部工具和服务之间的桥梁。每个 MCP 服务器都提供一组不同的工具和资源，供智能体访问。

常见的 MCP 服务器包括：

- **[GitHub MCP Server][github-mcp]**：提供用于管理 GitHub 存储库、issue 和拉取请求的 API。
- **[Playwright MCP Server][playwright-mcp-server]**：提供使用 Playwright 自动化浏览器的功能。

还有许多其他 MCP 服务器。GitHub 托管了一个 [MCP 注册表][mcp-registry]，帮助用户发现并参与生态系统建设。

> [!CAUTION]
> 请像对待项目中的其他依赖项一样对待 MCP 服务器。使用前请检查源代码、确认发布者，并考虑安全影响。

## 添加 Playwright MCP 服务器

如果 Playwright MCP 服务器尚不可用，请添加它，让 Copilot 可以像用户一样与网站交互。

> [!NOTE]
> 如果 Copilot CLI 中已配置 Playwright MCP，请跳过这些设置步骤，直接继续下一部分。

1. 返回 Codespace。
2. 在 Copilot CLI 中输入以下命令，打开添加 MCP 服务器对话框：

   ```plaintext
   /mcp add
   ```

3. 在名称字段中输入 `playwright`，然后按 <kbd>Tab</kbd>。
4. 按 <kbd>Enter</kbd> 确认服务器类型为 **STDIO**，然后按 <kbd>Tab</kbd>。
5. 将以下内容粘贴到 **Command** 对话框中：

   ```plaintext
   npx -y @playwright/mcp@latest --headless --no-sandbox
   ```

6. 按 <kbd>Control</kbd>+<kbd>S</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>S</kbd>（Windows/Linux）保存新的 MCP 服务器。
7. 按 <kbd>Esc</kbd> 退出 MCP 对话框。

## 让 Copilot 使用 Playwright 探索功能

之前你已手动确认功能符合预期。现在使用 Copilot 中可用的 Playwright MCP 服务器完成同样的检查。

1. 使用以下提示，让 Copilot 通过 Playwright MCP 服务器验证功能：

   ```plaintext
   启动应用，并使用 Playwright MCP 对照 issue 和计划检查筛选功能。告诉我哪些有效、哪些无效，不要进行任何更改。完成后停止你启动的服务器。
   ```

> [!NOTE]
> 通常不必告诉 Copilot 使用 MCP 服务器，因为它一般会自行判断。不过，既然你知道要使用哪个服务器，明确指出可以让结果更一致，也能节省一些 token。

2. 查看 Copilot 在浏览器中执行的步骤，确认功能是否正常。
3. 阅读报告并确认所有行为符合预期。

Copilot 会启动服务器，使用 Playwright 与网站交互，停止服务器，然后提供报告。

## 总结和后续步骤

恭喜！你已从 Copilot CLI 使用 Playwright MCP 服务器，在真实浏览器中探索功能。回顾一下，你：

- 了解了什么是 Model Context Protocol（MCP），以及 Copilot CLI 如何使用它。
- 如果 Playwright MCP 服务器尚不可用，则添加了它。
- 让智能体控制浏览器并探索筛选功能。

接下来，你将[创建 QA 自定义智能体][next-lesson]，将 skill 和浏览器工具整合到一个专用角色中。

## 资源

- [MCP 是什么，为什么大家都在讨论它？][mcp-blog-post]
- [Microsoft Playwright MCP Server][playwright-mcp-server]
- [向 Copilot CLI 添加 MCP 服务器][add-mcp]

[previous-lesson]: ../5-agent-skills/
[next-lesson]: ../7-qa-agent/
[mcp-blog-post]: https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/
[playwright-mcp-server]: https://github.com/microsoft/playwright-mcp
[github-mcp]: https://github.com/github/github-mcp-server
[mcp-registry]: https://github.com/mcp
[add-mcp]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers
