---
title: "第 4 课 - 使用自定义说明引导 Copilot"
description: "查看存储库说明，添加文档标准，并将其应用于筛选代码。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

使用生成式 AI 时，上下文至关重要。如果任务需要以特定方式完成，应让 Copilot 获得相应指导。[说明文件][instruction-files]不仅描述你需要*什么*代码，还描述代码应*如何*组织。现在筛选功能已经完成，你将查看 Copilot 使用的说明、添加文档标准并将其应用于代码。

本课将完成以下任务：

- 了解存储库说明和路径范围说明文件如何提供给智能体。
- 更新说明文件，确保遵循编码标准。
- 查看说明文件对代码的影响。

## 场景

与其他优秀的开发团队一样，Tailspin Toys 有一套开发实践指南和要求，包括：

- 注释应解释意图和不明显的决策，而不是重复代码。
- `db/` 和 `src/lib/` 中导出的函数应使用 TSDoc/JSDoc 说明用途、参数和返回值（如果存在可注入的 `db` 参数，也要说明）。
- 可复用的 Astro 组件应说明其 `Props` 契约；相关代码更改时，注释也应保持更新。
- 保留现有格式与 lint 指南。

借助说明文件，你可以确保 Copilot 获得正确的信息，并按照这些实践执行任务。

## 说明文件

自定义说明可以为 Copilot 提供上下文和偏好，帮助它理解你的编码风格和要求。它可以让 Copilot 给出更相关的建议和代码片段。你可以指定偏好的编码约定、库以及希望代码包含的注释类型。你可以为整个存储库创建说明，也可以为特定文件类型创建说明，以提供任务级上下文。

说明文件有两种：

- `.github/copilot-instructions.md`：单个说明文件，会随存储库中的**每个**请求发送给 Copilot。文件应包含与大多数请求相关的项目级信息。
- `.github/instructions/*.instructions.md` 文件：为特定语言、文件类型或任务提供指南。

> [!NOTE]
> 其他说明格式及其支持情况因环境而异。依赖特定格式前，请先查看[自定义说明支持参考][custom-instructions-support]。

## 查看此项目的自定义说明文件

入门项目中已包含一组说明文件。进行更改之前，先查看现有文件并了解其作用。

1. 返回 Codespace。
2. 在 Codespaces 编辑器（而不是终端）中打开 `.github/copilot-instructions.md`。
3. 查看文件，注意其中简要的项目说明和编码指南。这些说明适用于在此存储库中与 Copilot 的所有交互。
4. 打开 `.github/instructions` 文件夹并查看其中的文件。这里有针对 Astro 文件、Drizzle 数据层、测试等内容的说明。
5. 打开 `.github/instructions/unit-tests.instructions.md`。查看顶部的 `applyTo` 字段，它设置了用于确定说明适用文件的 glob。
6. 打开 `.github/instructions/drizzle.instructions.md`，查看它指向其他说明文件和现有项目文件的链接。这样可以将较大的说明集拆分成更小、可复用的文件，并为 Copilot 提供参考示例。

## 根据团队指南更新说明文件

现有文件是不错的起点，但仍有缺漏。修改核心文件 `copilot-instructions.md`，确保新生成的 TypeScript 添加 TSDoc 注释。

1. 在 `.github/copilot-instructions.md` 中找到 **Code formatting guidance** 部分，该部分应位于第 35 行附近。
2. 在该部分最后添加以下项目：

   ```markdown
   - 所有新编写的 TypeScript 都应包含用于文档说明的 TSDoc 注释。
   ```

文件会自动保存。

## 使用更新后的指南

Copilot CLI 会在对话开始时加载存储库说明。保存更新后的说明后，退出并恢复筛选对话，让 Copilot 在保留功能上下文的同时加载新指南。

1. 如果筛选对话仍处于打开状态，请输入 `/exit` 将其关闭。Copilot CLI 会自动保存对话。
2. 在存储库根目录的 `game-filters-cli` 分支中恢复已保存的对话：

   ```bash
   copilot --resume
   ```

   如果系统提示，请选择筛选对话，并确认当前检出的是 `game-filters-cli` 分支。
3. 请 Copilot 应用更新后的指南：

   ```plaintext
   我们刚刚更新了说明和代码指南。请更新你生成的代码，使其符合这些指南。
   ```

4. 输入 `/diff` 并查看更改过的 TypeScript 文件。注意新生成的 TSDoc 注释，并确认它们准确描述代码。

## 总结和后续步骤

你了解了 Copilot 如何从说明文件中获取上下文，并将新的标准应用于功能。具体来说，你：

- 了解存储库说明和路径范围说明文件如何提供给智能体。
- 更新说明文件，确保遵循编码标准。
- 查看了说明文件对代码的影响。

接下来，你将[自定义并运行可复用的 quality-checks skill][next-lesson]，确保一致地执行 lint 和测试。

## 资源

- [向 Copilot CLI 添加自定义说明][instruction-files]
- [自定义说明支持][custom-instructions-support]
- [创建自定义说明的最佳实践][instructions-best-practices]
- [Awesome Copilot：说明文件和其他资源集合][awesome-copilot]

[instruction-files]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions
[instructions-best-practices]: https://docs.github.com/copilot/concepts/prompting/response-customization#writing-effective-custom-instructions
[awesome-copilot]: https://awesome-copilot.github.com/
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support
[previous-lesson]: ../3-agent-modes/
[next-lesson]: ../5-agent-skills/
