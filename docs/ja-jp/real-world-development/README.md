---
title: "実践的な開発"
slug: ja-jp/real-world-development
authors:
  - geektrainer
lastUpdated: 2026-09-16
---

現実的なシナリオ、完成したアプリケーション、共有バックログを使って、ソフトウェア開発ライフサイクル全体で GitHub Copilot を活用しましょう。変更を計画し、コードを作成し、動作をテストし、pull request をレビューし、エージェントを使って作業を管理します。

## シナリオ

あなたは、開発者をテーマにしたボード ゲームのクラウドファンディングを提供する架空の会社、Tailspin Toys の新しい開発者です。チームのバックログは GitHub issue として登録されており、すぐに着手できます。フィルタリングやページネーションなどの機能開発に加えて、アクセシビリティやコーディング標準などの品質改善も含まれています。

## 環境を選ぶ

GitHub Copilot は、どの環境でも利用できます。開発方法に合った環境を選択してください。それぞれのワークショップは個別のセットアップから始まり、共通の Tailspin Toys シナリオを使用します。

### [GitHub Copilot CLI][cli]

ターミナルでエージェント型アシスタントを使います。Plan モードと Autopilot モード、指示、スキル、カスタム エージェント、Playwright MCP、Agent Merge、便利なスラッシュ コマンドを活用します。

### [GitHub Copilot アプリ][app]

エージェント セッションを並行して実行し、セッション モードを切り替え、Canvas で共同作業を行い、デスクトップ アプリで GitHub issue と pull request を管理します。

### [Copilot クラウド エージェント][cloud]

GitHub issue を非同期エージェントに割り当て、その作業をガイドし、進行状況を監視して、作成された pull request をレビューします。

### [Visual Studio Code][vscode]

Visual Studio Code と GitHub Codespaces で GitHub Copilot を使います。エディターを離れずに、Copilot Chat のエージェント モード、MCP サーバー、カスタム エージェントを活用します。

[cli]: cli/
[app]: app/
[cloud]: cloud/
[vscode]: vscode/
