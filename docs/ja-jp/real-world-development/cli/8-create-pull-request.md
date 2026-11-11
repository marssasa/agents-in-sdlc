---
title: "レッスン 8 - 機能の PR を作成してマージする"
description: "フィルタリング、指示、スキルの更新、QA プロファイル、テストをまとめてレビューし、PR を作成して Agent Merge を使用します。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

フィルタリングの実装、指示の更新、スキルの更新、品質保証 (QA) プロファイル、テストはすべて 1 つのブランチに保存されています。まとめてレビューし、pull request を開きましょう。星評価の PR は自分でマージしましたが、今回は **Agent Merge** にプロセスを任せます。

> [!NOTE]
> 通常は、機能、指示、スキルの更新、QA エージェントを複数の PR に分割します。ワークショップを効率化するため、フィルタリングと品質のワークフロー全体を 1 つの会話とブランチで進め、この PR にまとめました。

このレッスンでは、次の操作を行います。

- Agent Merge とは何か、PR のライフサイクルをどのように自動化するかを学びます。
- 機能の変更全体と検証の根拠を確認します。
- フィルタリングの PR を作成します。
- レビュー後にのみ Agent Merge を有効にして、PR がマージされたことを確認します。

## シナリオ

フィルタリングの作業を通して、Copilot で機能の計画、実装、検証を行いました。Tailspin Toys では、マージを許可する権限は開発者の管理下に置きながら、PR の残りの作業を自動化したいと考えています。

## Agent Merge とは

**Agent Merge** は、pull request をマージするために必要な残りの作業を自動化します。有効にすると、Copilot は PR のブロック要因 (継続的インテグレーション (CI) チェックの失敗、レビュー コメント、必要なリベースなど) に対処し、リポジトリで許可されている場合は GitHub の自動マージを有効にします。

これまでは **Merge pull request** を自分で選択していました。Agent Merge にその作業を任せることもできます。Agent Merge を有効にする前に、作業をレビューし、準備ができていることを確認してください。

## Agent Merge で PR を管理する

コードの作成が終わったら、全体をレビューして PR を作成し、残りの作業を Agent Merge に任せましょう。

1. Codespace に戻ります。
2. `/agent` を入力してエージェントのダイアログを開きます。
3. オプションの一覧から **Default** を選択して <kbd>Enter</kbd> を押します。
4. `/pr create` コマンドを実行して PR を新規作成します。
5. `/pr agentmerge` を実行して Agent Merge を有効にします。
6. Copilot は PR の継続的インテグレーションを監視します。すべてのチェックに成功すると、マージを実行します。
7. Copilot が「PR #14 was squash-merged successfully」のようなメッセージを表示することを確認します。

> [!IMPORTANT]
> Agent Merge は、必須の承認、ブランチ保護、マージ キュー、リポジトリ設定、または不足している権限を回避しません。ブロックされた場合は報告された理由を確認し、リポジトリで許可されていればレビュー済みの変更を手動でマージしてください。

## まとめと次のステップ

コード生成、テストと検証、pull request のプロセスなど、開発プロセスの複数の部分を自動化しました。具体的には、次の操作を行いました。

- Agent Merge とは何か、PR のライフサイクルをどのように自動化するかを学びました。
- 機能の変更全体と検証の根拠を確認しました。
- フィルタリングの PR を作成しました。
- レビュー後にのみ Agent Merge を有効にし、PR がマージされたことを確認しました。

次は、コンテキスト、モデル、共有、クラウドへの任意の委任に使える[便利な Copilot CLI のスラッシュ コマンド][next-lesson]を確認します。

## リソース

- [Copilot CLI で pull request を管理する][manage-prs]
- [Copilot CLI コマンド リファレンス][cli-reference]

[previous-lesson]: ../7-qa-agent/
[next-lesson]: ../9-cli-power-tools/
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
