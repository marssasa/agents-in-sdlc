---
slug: ja-jp/real-world-development/cloud
title: "GitHub Copilot クラウド エージェント"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

**[GitHub Copilot クラウド エージェント](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent)**を使うと、GitHub Copilot がクラウドで非同期に作業できます。GitHub で作業を割り当てると、クラウド エージェントがバックグラウンドでリポジトリを調査して変更を加え、pull request を開きます。その間、ほかの作業を続けられます。

各演習では、まずクラウド エージェントが従うカスタム指示を追加し、GitHub issue を割り当てて実装を依頼します。カスタム エージェントを確認して使い、アプローチを調整する方法を学びます。エージェント ダッシュボードからセッションを監視して方向付けし、最後に pull request をレビューして作業を反復します。

## 演習

| 演習 | トピック | 説明 |
|----------|-------|-------------|
| [0. 前提条件][ex0] | セットアップ | リポジトリと Codespace を作成する |
| [1. カスタム指示][ex1] | コンテキスト | クラウド エージェントが従うカスタム指示を追加する |
| [2. クラウド エージェント][ex2] | 非同期エージェント | Copilot クラウド エージェントに issue を割り当てる |
| [3. カスタム エージェント][ex3] | 専門エージェント | カスタム エージェントを確認して使用する |
| [4. エージェントの管理][ex4] | 監視 | エージェントのセッションを監視して方向付ける |
| [5. 反復][ex5] | レビュー | PR をレビューし、Copilot の作業を反復して、次の手順を選ぶ |

## 前提条件

このワークショップに参加する前に、次の準備をしてください。

- [ ] **Copilot Student、Pro、Pro+、Business、Enterprise** のいずれかが有効な GitHub アカウント
- [ ] アカウントまたは組織で Copilot クラウド エージェントが有効になっていること

> [!TIP]
> 有料プランを利用していませんか? 認証済みの学生は [GitHub Education][callout-student-plan-education] を通じて GitHub Copilot を無料で利用できます。**Copilot Student** プランには、このワークショップで使うエージェント、MCP、コード レビュー、Copilot CLI の機能が含まれているため、すべてのハーネスを完了できます。

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> クラウド エージェントは **Copilot Student、Pro、Pro+、Business、Enterprise** で利用できます。Copilot Free では利用できません。Copilot Business または Enterprise の場合、管理者が組織で有効にする必要があります。

> [!NOTE]
> このハーネスでは MCP を扱いません。Copilot で MCP サーバーを使う方法については、[CLI ハーネス](../cli/)または [VS Code ハーネス](../vscode/)を参照してください。

## 始める

**[演習 0: 前提条件から始める →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/
