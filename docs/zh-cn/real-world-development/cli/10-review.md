---
title: "第 10 课 - 回顾和后续步骤"
description: "回顾 Copilot CLI 工作流、两个拉取请求、可复用的自定义设置和更多资源。"
authors:
  - geektrainer
lastUpdated: 2026-09-29
---

你在 Tailspin Toys 的完整工作流中使用了 GitHub Copilot CLI。你：

- 准备了 Codespace、安装了 Copilot CLI、探索了项目并找到了预先创建的筛选 issue。
- 添加了星级评分，在转发的浏览器中检查结果，并手动合并了第一个拉取请求（PR）。
- 从筛选 issue 入手，在 Plan 模式下确定方案，在 Autopilot 模式下实现，并在 Interactive 模式下检查。
- 使用自定义说明引导智能体，随后自定义现有的 `quality-checks` skill，并使用它运行单元测试、lint 和类型检查。
- 添加了 Playwright Model Context Protocol（MCP）服务器，并用它在真实浏览器中探索筛选功能。
- 创建并选择了质量保证（QA）自定义智能体，用于评估要求、覆盖率、skill 结果和浏览器证据。
- 检查了完整的筛选更改，并授权 Agent Merge 合并筛选 PR。
- 探索了用于上下文、模型、共享和可选云端委派的斜杠命令。

## 已交付的内容

本工作坊包含两个 PR 里程碑，每个里程碑都在从更新后的 `main` 创建的独立分支中完成：

1. **星级评分：** 在游戏卡片中显示现有的 `starRating`，并明确显示尚未评分的状态。
2. **筛选和质量工作流：** 实现筛选，更新说明并将其应用于功能，自定义 `quality-checks` 报告，创建 QA 配置文件并添加相关测试。

从规划筛选功能到创建 PR，你一直使用同一个对话和分支。为了简化工作坊，这些工作合并到一个 PR 中。

## 不同类型的验证

你通过多种方式检查了代码：自动化测试、自己在浏览器中检查，以及 Copilot 通过 MCP 探索浏览器。`quality-checks` skill 运行了单元测试、lint 和类型检查，并按新格式报告结果。创建 PR 前，QA 将这些结果与要求和测试覆盖率检查结果结合起来。

新增测试应解决实际缺口；QA 运行不需要添加测试也可能是正确的。授权合并前先检查代码和证据，并在更改后更新受影响的证据。

## 最佳实践

提供给 Copilot 的上下文和工具会影响它的工作。在本工作坊中，你更新了说明、自定义了 skill、创建了 QA 配置文件并配置了 MCP 服务器。可以在其他对话中复用这些自定义设置，并根据团队需求调整。说明设定标准，skills 描述可重复执行的任务，自定义智能体定义专用角色，MCP 服务器连接外部工具。请检查实际更改和工具结果，而不只是智能体的总结。

根据任务选择**模式和模型**。开始构建前用 **Plan** 考虑方案，用 **Interactive** 参与专注的更改，对范围明确的任务使用 **Autopilot**。日常编辑时选择速度更快的模型，复杂任务则选择能力更强的模型。

上下文与基础设施同样重要。清晰说明要构建*什么*、*为什么*构建以及*如何*构建，会显著影响结果。

## 继续探索

核心工作流已经完成。还可以了解以下 CLI 功能：

- 使用 `/review` 请求代码审查智能体分析更改。
- 使用 `/rubber-duck` 讨论问题并获得另一种观点。
- 使用 `/fleet` 并行协调独立子任务。
- 使用 `/worktree` 隔离单独的任务。
- 使用 `/delegate` 将任务发送给 Copilot 云端智能体。

## 后续步骤

提升任何工具使用能力的最佳方法就是继续使用它。将它用于生产代码、个人项目，或那个想了很多年却一直没开始的小应用。与团队分享经验，也向团队成员学习。最后，别忘了继续阅读文档。

如果想在终端中扩展 Tailspin Toys，请继续学习可选的 [Foundry Backer Concierge 系列][foundry]。要比较其他环境，可以探索 [VS Code 工作坊][vscode]、[GitHub Copilot 应用工作坊][app]或 [Copilot 云端智能体工作坊][cloud]。

## 资源

- [关于 GitHub Copilot CLI][about-cli]
- [Copilot CLI 命令参考][cli-reference]
- [自定义 Copilot CLI][customize-cli]
- [使用 Copilot CLI 管理拉取请求][manage-prs]

[previous-lesson]: ../9-cli-power-tools/
[foundry]: ../8-foundry-agent/
[vscode]: ../../vscode/
[app]: ../../app/
[cloud]: ../../cloud/
[about-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[customize-cli]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
