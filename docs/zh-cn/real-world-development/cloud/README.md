---
slug: zh-cn/real-world-development/cloud
title: "GitHub Copilot 云端智能体"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

**[GitHub Copilot 云端智能体](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent)**可以让 GitHub Copilot 在云端异步工作。你在 GitHub 上分配任务后，云端智能体会在后台执行，包括探索存储库、进行更改和创建拉取请求，而你可以继续处理其他事务。

在这些练习中，你将添加云端智能体会遵循的自定义说明，然后分配 GitHub issue 让它实现功能。你将查看并使用自定义智能体来引导工作方式，通过智能体仪表板监控和指导会话，最后审查它创建的拉取请求并继续迭代。

## 练习

| 练习 | 主题 | 说明 |
|----------|-------|-------------|
| [0. 先决条件][ex0] | 设置 | 创建存储库和 Codespace |
| [1. 自定义说明][ex1] | 上下文 | 添加云端智能体会遵循的自定义说明 |
| [2. 云端智能体][ex2] | 异步智能体 | 将 issue 分配给 Copilot 云端智能体 |
| [3. 自定义智能体][ex3] | 专用智能体 | 查看并使用自定义智能体 |
| [4. 管理智能体][ex4] | 监控 | 监控并指导智能体会话 |
| [5. 迭代][ex5] | 审查 | 审查 PR、迭代 Copilot 的工作并选择后续步骤 |

## 先决条件

参加本工作坊前，请确认你具备以下条件：

- [ ] 拥有有效的 **Copilot Student、Pro、Pro+、Business 或 Enterprise** 计划的 GitHub 帐户
- [ ] 已为帐户或组织启用 Copilot 云端智能体

> [!TIP]
> 没有付费计划？经过验证的学生可以通过 [GitHub Education][callout-student-plan-education] 免费使用 GitHub Copilot。**Copilot Student** 计划包含本工作坊所用的智能体、MCP、代码审查和 Copilot CLI 功能，因此可完成所有练习。

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> 云端智能体适用于 **Copilot Student、Pro、Pro+、Business 和 Enterprise**，但不适用于 Copilot Free。使用 Copilot Business 或 Enterprise 时，管理员必须为组织启用该功能。

> [!NOTE]
> 本练习不涉及 MCP。要了解如何在 Copilot 中使用 MCP 服务器，请参阅 [CLI 练习](../cli/)或 [VS Code 练习](../vscode/)。

## 开始

**[从练习 0：先决条件开始 →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/
