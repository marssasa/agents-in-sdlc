---
title: "第 8 课 - 创建并合并功能 PR"
description: "一起检查筛选功能、说明、skill 更新、QA 配置文件和测试，然后创建 PR 并使用 Agent Merge。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

筛选功能实现、说明更新、skill 更新、质量保证（QA）配置文件和测试都保存在同一个分支中。现在可以一起检查这些内容并创建拉取请求。上一次你亲自合并了星级评分拉取请求（PR）；这次将让 **Agent Merge** 管理合并流程。

> [!NOTE]
> 通常会将功能、说明更新、skill 更新和 QA 智能体拆分到几个 PR 中。为了简化工作坊，你将完整的筛选与质量工作流保留在同一个对话和分支中，并将所有更改放入这个 PR。

本课将完成以下任务：

- 了解什么是 Agent Merge，以及它如何自动管理 PR 合并生命周期。
- 检查完整的功能更改和验证证据。
- 创建筛选功能 PR。
- 仅在检查完成后启用 Agent Merge，并确认 PR 已合并。

## 场景

在筛选工作流中，你使用 Copilot 规划、实现并验证了一项功能。Tailspin Toys 现在希望自动完成剩余的 PR 工作，同时由开发者控制合并授权。

## 了解 Agent Merge

**Agent Merge** 会自动完成合并拉取请求所需的剩余工作。启用后，Copilot 会处理阻碍 PR 合并的问题，例如修复失败的持续集成（CI）检查、回复审查意见，以及在需要时进行变基。如果存储库允许，它还会启用 GitHub 自动合并。

之前都是由你亲自选择 **Merge pull request**。Agent Merge 可以接手这项工作。启用它之前，请先检查更改并确认已准备就绪。

## 使用 Agent Merge 管理 PR

所有代码都已创建完成，现在一起检查更改、创建 PR，并让 Agent Merge 管理剩余流程。

1. 返回 Codespace。
2. 输入 `/agent` 打开智能体对话框。
3. 从选项列表中选择 **Default**，然后按 <kbd>Enter</kbd>。
4. 使用命令 `/pr create` 创建新的 PR。
5. 使用 `/pr agentmerge` 启用 Agent Merge。
6. Copilot 会监视 PR 的持续集成流程。所有检查成功后，它会执行合并。
7. 确认 Copilot 显示类似“PR #14 was squash-merged successfully”的消息。

> [!IMPORTANT]
> Agent Merge 不会绕过必需的审批、分支保护、合并队列、存储库设置或缺失的权限。如果操作受阻，请查看报告的原因，并在存储库允许时手动完成已检查的合并。

## 总结和后续步骤

你已自动化开发流程中的多个部分，包括代码生成、代码测试和验证，以及拉取请求流程。本课中，你：

- 了解了什么是 Agent Merge，以及它如何自动管理 PR 合并生命周期。
- 检查了完整的功能更改和验证证据。
- 创建了筛选功能 PR。
- 仅在检查完成后启用了 Agent Merge，并确认 PR 已合并。

接下来，你将[探索其他实用的 Copilot CLI 斜杠命令][next-lesson]，用于管理上下文、模型、共享和可选的云端委派。

## 资源

- [使用 Copilot CLI 管理拉取请求][manage-prs]
- [Copilot CLI 命令参考][cli-reference]

[previous-lesson]: ../7-qa-agent/
[next-lesson]: ../9-cli-power-tools/
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
