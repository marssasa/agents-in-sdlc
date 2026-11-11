---
title: "第 3 课 - 智能体模式：Plan 和 Autopilot"
description: "使用 Plan 确定实施方案，使用 Autopilot 根据 issue 实现筛选功能，并在 Interactive 模式下检查结果。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

我们先为项目添加了一项小功能，但更大的改动需要更完善的流程。GitHub Copilot CLI 可以配合组织现有的工作流，帮助我们用合适的方式构建合适的功能。本课是一系列课程中的第一课，你将遵循常见的智能体驱动开发流程：从 issue 开始实现新功能，确认代码有效、功能符合预期，最后成功合并到项目中。

> [!NOTE]
> 在继续完成此功能的工作流时，你会使用同一个对话和分支。通常，不同文件类型的工作会放在不同分支或 PR 中，但这里会简化流程，以便聚焦核心概念。

本课将完成以下任务：

- 从 GitHub issue 开始新的 Copilot 对话。
- 在 Plan 模式下定义要求。
- 使用 Autopilot 模式实现新功能。
- 检查代码。
- 在转发的浏览器中手动验证功能。

继续开发此功能时，你还会更新存储库说明、自定义现有的 `quality-checks` skill、添加 MCP 验证、创建 QA 智能体并打开功能 PR。

## 场景

Tailspin Toys 的目录不断扩大，访问者需要按类别和发行商筛选游戏。积压 issue 描述了这项功能，但在开始编码前，必须先确定类别组合等细节。你将使用 Plan 模式达成这些决定，然后授权 Autopilot 在限定范围内实施。

## 背景

将 AI 编程智能体引入开发流程并不会改变基本原则，反而会让这些原则更加重要。大多数开发者遵循类似的流程：

1. 从描述待办事项的已创建 issue 开始。
2. 规划需要构建的内容。
3. 编写并检查代码。
4. 运行测试以验证代码。
5. 手动验证新功能。
6. 创建拉取请求（PR）。
7. 代码通过检查并且持续集成流程成功后，合并代码。

> [!NOTE]
> 具体步骤会因团队和组织而异，但大多数流程都与上述主题类似。

遵循这种标准流程，可以确保 AI 生成的代码满足要求，并经过与手动编写的代码相同的审核。

## 对话模式

**对话模式**控制智能体的自主程度。按 <kbd>Shift</kbd>+<kbd>Tab</kbd> 可在模式之间切换：

- **Interactive**：你与智能体协作。智能体提出更改建议，并等待你输入后再继续。
- **Plan**：智能体先创建计划，且不能编辑项目文件。
- **Autopilot**：智能体自主工作，编写代码、运行测试并不断迭代，直到任务完成。

先在 Plan 模式下检查计划，再使用 Autopilot 实施。

## 从 issue 开始

开始筛选功能前，返回 Codespace，确认存储库和终端已准备就绪。

1. 返回 Codespace。如果它已停止，请先重新启动。
2. 确认星级评分 PR 已合并。
3. 如果终端尚未打开，请按 <kbd>Control</kbd>+<kbd>\`</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>\`</kbd>（Windows/Linux）。
4. 更新 `main`，然后为筛选工作创建分支：

   ```bash
   git checkout main
   git pull --ff-only
   git checkout -b game-filters-cli
   ```

5. 启动 Copilot CLI：

   ```bash
   copilot --yolo
   ```

6. 按两次 <kbd>Tab</kbd> 打开 **Issues** 选项卡。
7. 按 <kbd>A</kbd> 显示所有 issue。
8. 使用方向键选中标题为 **Allow users to filter games by category and publisher** 的 issue。
9. 按 <kbd>C</kbd> 将 issue 添加到提示中，然后返回 **Session** 选项卡。

请注意，提示现在以 `#7`（或类似编号）开头。`#` 可以将 GitHub issue 或拉取请求（PR）添加到上下文中。

## 规划筛选功能

规划可以让你在将功能实现或任务执行交给 Copilot 之前，先确定采用的方法。处理复杂任务时，花一些时间规划总是有帮助的。现在切换到 Plan 模式，让 Copilot 创建计划。

1. 按 <kbd>Shift</kbd>+<kbd>Tab</kbd> 切换到 Plan 模式。确认提示下方的模式指示器显示 **Plan**。
2. 在上一步添加的 issue 引用后输入以下提示：

   ```plaintext
   为实现此功能创建计划。
   ```

Copilot 会开始探索项目，并确定最合适的方法，从而制定计划。

3. Copilot 可能会询问筛选功能的具体行为。根据自己的偏好回答，没有错误答案。
4. 计划完成后，按 <kbd>Control</kbd>+<kbd>E</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>E</kbd>（Windows/Linux）展开计划。
5. 上下滚动检查计划。
6. 如果计划中的某项内容与你的决定不符，请让 Copilot 修改。

## 批准 Autopilot

计划已经编写并检查完毕，现在可以开始实施了。使用 Autopilot 让 Copilot 执行工作。

Autopilot 会让 Copilot 不断处理问题，直到它认为任务已经完成。

1. 选择 **Accept plan and build on autopilot (recommended)**，或已安装版本中名称相似的选项。
2. 确认提示下方的模式指示器显示 **Autopilot**。
3. 查看 Copilot 如何按计划迭代、生成代码并运行测试。

> [!NOTE]
> 批准后可能会立即开始实施，因此请先检查计划。如果 Copilot 报告缺少依赖项或端口冲突，请先解决设置问题，再将检查视为已完成。

## 检查并验证实现

与其他代码一样，生成的代码也必须在合并前检查。现在检查代码并运行网站，确认一切正常。

1. 按 <kbd>Shift</kbd>+<kbd>Tab</kbd> 进入 Interactive 模式。确认模式指示器不再显示 **Plan** 或 **Autopilot**。
2. 输入 `/diff`，检查筛选功能的实现和测试。
3. 将结果与 issue 以及规划时做出的决定进行比较。
4. 检查完成后，按 <kbd>Esc</kbd> 退出差异视图。
5. 查看项目检查的结果，并让 Copilot 修复任何失败项。

## 试用新功能

代码看起来没问题，但能否正常运行？像之前一样启动应用，通过 Codespaces 转发的端口打开网站。

1. 请 Copilot 启动应用：

   ```plaintext
   启动应用，让我在浏览器中试用筛选功能。告诉我 URL，并让服务器保持运行。
   ```

2. 当 Codespaces 报告端口 `4321` 可用时，选择 **Open in Browser**。
3. 尝试按类别筛选、按发行商筛选，以及计划中确定的组合。
4. 确认重置和无结果时的行为符合 issue 和你的决定。
5. 返回 Codespace，请 Copilot 停止它启动的开发服务器。

## 总结和后续步骤

你使用不同的对话模式构建并检查了功能。本课中，你：

- 从 GitHub issue 开始新的 Copilot 对话。
- 在 Plan 模式下定义要求。
- 使用 Autopilot 模式实现新功能。
- 检查代码。
- 在转发的浏览器中手动验证功能。

接下来，我们将深入了解代码的生成过程，并通过[使用自定义说明][next-lesson]确保代码遵循记录的实践。

## 资源

- [GitHub Copilot CLI 中的 Autopilot][autopilot]
- [Copilot CLI 命令参考][cli-reference]

[autopilot]: https://docs.github.com/copilot/concepts/agents/copilot-cli/autopilot
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[previous-lesson]: ../2-add-star-rating/
[next-lesson]: ../4-custom-instructions/
