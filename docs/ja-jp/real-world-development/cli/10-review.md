---
title: "レッスン 10 - 振り返りと次のステップ"
description: "Copilot CLI のワークフロー、2 つの pull request、再利用可能なカスタマイズ、追加リソースを振り返ります。"
authors:
  - geektrainer
lastUpdated: 2026-09-29
---

Tailspin Toys の一連のワークフローで GitHub Copilot CLI を使用しました。具体的には、次の操作を行いました。

- Codespace を準備し、Copilot CLI をインストールし、プロジェクトを確認して、フィルタリング issue を見つけました。
- 星評価を追加し、転送されたブラウザーで結果を確認して、最初の pull request (PR) を手動でマージしました。
- フィルタリング issue から始めて、Plan モードでアプローチを定義し、Autopilot モードで実装し、Interactive モードでレビューしました。
- カスタム指示でエージェントをガイドし、既存の `quality-checks` スキルをカスタマイズして、単体テスト、lint、型チェックを実行しました。
- Playwright Model Context Protocol (MCP) サーバーを追加し、実際のブラウザーでフィルタリングを確認しました。
- 要件、カバレッジ、スキルの結果、ブラウザーの根拠を評価するため、品質保証 (QA) カスタム エージェントを作成して選択しました。
- フィルタリングの変更全体をレビューし、フィルタリング PR に Agent Merge を許可しました。
- コンテキスト、モデル、共有、任意のクラウド委任に使うスラッシュ コマンドを確認しました。

## 実装した内容

このワークショップでは、更新済みの `main` からそれぞれ作成した別々のブランチで、2 つの PR を作成します。

1. **星評価:** 既存の `starRating` と未評価であることを示す明確な状態を、ゲーム カードに表示します。
2. **フィルタリングと品質ワークフロー:** フィルタリングを実装し、指示を更新して機能に適用し、`quality-checks` レポートをカスタマイズし、QA プロファイルを作成して、関連するテストを含めます。

フィルタリングの計画から PR の作成まで、同じ会話とブランチを使用しました。ワークショップを簡略化するため、これらの作業を 1 つの PR にまとめました。

## さまざまな検証方法

自動テスト、自分で行うブラウザーの確認、MCP 経由の Copilot によるブラウザー操作など、複数の方法でコードを確認しました。`quality-checks` スキルは単体テスト、lint、型チェックを実行し、新しい形式で報告しました。QA はこれらの結果と要件およびテスト カバレッジのレビューをまとめてから PR を作成しました。

追加するテストでは、実際の不足を解消してください。QA の実行で新しいテストが必要ない場合もあります。マージを許可する前にコードと根拠をレビューし、変更後は影響を受ける根拠を更新します。

## ベスト プラクティス

Copilot に与えるコンテキストやツールは、Copilot の作業に影響します。このワークショップでは、指示を更新し、スキルをカスタマイズし、QA プロファイルを作成し、MCP サーバーを構成しました。これらのカスタマイズは会話をまたいで再利用し、チームのニーズに合わせて調整できます。指示は標準を設定し、スキルは繰り返し可能なタスクを定義し、カスタム エージェントは専門的な役割を定義し、MCP サーバーは外部ツールに接続します。エージェントの要約だけでなく、実際の変更とツールの結果を確認してください。

タスクに合った**モードとモデル**を選びます。実装前に方法を検討するときは **Plan**、目的を絞った変更に関与し続けるときは **Interactive**、範囲が明確なタスクには **Autopilot** を使います。定型的な編集には高速なモデルを、複雑な作業にはより高性能なモデルを選択します。

インフラストラクチャと同じくらい、コンテキストも重要です。*何を*作りたいか、*なぜ*必要か、*どのように*作るかを明確に説明すると、結果が大きく変わります。

## さらに確認する

主要なワークフローは完了しました。Copilot CLI には、次のような機能もあります。

- `/review` でコード レビュー エージェントに変更を分析してもらいます。
- `/rubber-duck` で問題を説明し、別の視点からの意見を得ます。
- `/fleet` で独立したサブタスクを並列に調整します。
- `/worktree` で個別のタスクを分離します。
- `/delegate` で Copilot クラウド エージェントにタスクを送信します。

## 次のステップ

どのツールでも、上達する一番の方法は使い続けることです。本番コード、個人のコード、あるいは何年も作ろうと思いながら手をつけていなかった小さなアプリで活用してみましょう。チームに学んだことを共有し、ほかのメンバーから学ぶことも大切です。そして、ドキュメントも確認してください。

ターミナルから Tailspin Toys を拡張したい場合は、任意の [Foundry Backer Concierge シリーズ][foundry]に進みます。ほかの環境と比較するには、[VS Code ワークショップ][vscode]、[GitHub Copilot アプリのワークショップ][app]、または [Copilot クラウド エージェントのワークショップ][cloud]を確認してください。

## リソース

- [GitHub Copilot CLI について][about-cli]
- [Copilot CLI コマンド リファレンス][cli-reference]
- [Copilot CLI をカスタマイズする][customize-cli]
- [Copilot CLI で pull request を管理する][manage-prs]

[previous-lesson]: ../9-cli-power-tools/
[foundry]: ../8-foundry-agent/
[vscode]: ../../vscode/
[app]: ../../app/
[cloud]: ../../cloud/
[about-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[customize-cli]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
