---
title: "レッスン 4 - カスタム指示で Copilot をガイドする"
description: "リポジトリの指示を確認し、ドキュメントの標準を追加して、フィルタリング コードに適用します。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

生成 AI を使うときは、コンテキストが重要です。タスクを特定の方法で実行する必要がある場合、そのガイダンスを Copilot が利用できるようにします。[指示ファイル][instruction-files]では、必要なコードだけでなく、コードの構成方法も指定できます。フィルタリング機能を作成したので、Copilot が参照した指示を確認し、ドキュメントの標準を追加してコードに適用しましょう。

このレッスンでは、次の操作を行います。

- リポジトリの指示とパス固有の指示ファイルがエージェントに読み込まれる方法を確認します。
- コーディング標準に従うよう、指示ファイルを更新します。
- 指示ファイルがコードに与える影響を確認します。

## シナリオ

Tailspin Toys には、優れた開発チームと同じように、開発プラクティスに関するガイドラインと要件があります。具体的には、次のとおりです。

- コメントではコードを繰り返すのではなく、意図や自明でない判断を説明します。
- `db/` と `src/lib/` のエクスポート関数では、インジェクション可能な `db` 引数がある場合はそれも含め、目的、パラメーター、戻り値を TSDoc/JSDoc で説明します。
- 再利用可能な Astro コンポーネントでは `Props` コントラクトを説明し、関連コードが変更されたときにコメントも更新します。
- 既存のフォーマットと lint のガイダンスを維持します。

指示ファイルを使うと、Copilot がこれらのプラクティスに沿ってタスクを実行するための情報を提供できます。

## 指示ファイル

カスタム指示では、Copilot にコンテキストや設定を伝え、コーディング スタイルや要件を理解しやすくできます。適切な提案やコード スニペットを得るために役立つ機能です。好みのコーディング規約、ライブラリ、コードに含めるコメントの種類などを指定できます。リポジトリ全体に適用する指示や、特定のファイルの種類に適用する指示を作成できます。

指示ファイルには、次の 2 種類があります。

- `.github/copilot-instructions.md`: リポジトリ内の **すべて** の要求で Copilot に送信される単一の指示ファイルです。多くの要求に関係するプロジェクト レベルの情報を記載します。
- `.github/instructions/*.instructions.md`: 特定の言語、ファイルの種類、またはタスクに関するガイドラインを記載するファイルです。

> [!NOTE]
> ほかの形式の指示とそのサポート状況は、環境によって異なります。特定の形式に依存する前に、[カスタム指示のサポートに関するリファレンス][custom-instructions-support]を確認してください。

## プロジェクトのカスタム指示ファイルを確認する

スターター プロジェクトには、すでに指示ファイルが含まれています。変更を加える前に、ファイルを確認して指示の効果を見てみましょう。

1. Codespace に戻ります。
2. Codespaces エディターで (ターミナルではなく) `.github/copilot-instructions.md` を開きます。
3. ファイルを確認し、プロジェクトの簡単な説明とコーディング ガイダンスを見つけます。この指示は、リポジトリ内で Copilot と行うすべてのやり取りに適用されます。
4. `.github/instructions` フォルダーを開いて、ファイルを確認します。Astro ファイル、Drizzle データ レイヤー、テストなどの指示が含まれています。
5. `.github/instructions/unit-tests.instructions.md` を開きます。先頭の `applyTo` フィールドが、指示を適用するファイルを決める glob であることを確認します。
6. `.github/instructions/drizzle.instructions.md` を開き、ほかの指示ファイルや既存のプロジェクト ファイルへのリンクを確認します。これにより、大きな指示セットを小さく再利用可能なファイルに分割し、Copilot に参照してほしい例を示せます。

## チームのガイダンスに合わせて指示ファイルを更新する

既存のファイルはよい出発点ですが、まだ改善できます。新しく生成する TypeScript に TSDoc コメントが追加されるよう、中心となる `copilot-instructions.md` を変更します。

1. `.github/copilot-instructions.md` で、35 行目付近にある **Code formatting guidance** セクションを探します。
2. 最後の項目として、次の行を追加します。

   ```markdown
   - 新しい TypeScript には、ドキュメント用の TSDoc コメントを含める必要があります。
   ```

ファイルは自動的に保存されます。

## 更新したガイダンスを使う

Copilot CLI は会話の開始時にリポジトリの指示を読み込みます。更新した指示を保存したら、フィルタリングの会話を終了して再開します。これにより機能のコンテキストを保ったまま、新しい指示が読み込まれます。

1. フィルタリングの会話が開いている場合は、`/exit` を入力して閉じます。Copilot CLI は会話を自動的に保存します。
2. リポジトリのルートから、`game-filters-cli` ブランチで保存済みの会話を再開します。

   ```bash
   copilot --resume
   ```

   選択を求められた場合は、フィルタリングの会話を選び、`game-filters-cli` ブランチがチェックアウトされていることを確認します。
3. 更新したガイダンスをコードに適用するよう Copilot に依頼します。

   ```plaintext
   先ほど指示とコードのガイダンスを更新しました。生成したコードをガイダンスに従うように更新してください。
   ```

4. `/diff` を入力して、変更された TypeScript ファイルを確認します。新しい TSDoc コメントが追加され、コードを正確に説明していることを確認します。

## まとめと次のステップ

指示ファイルから Copilot がコンテキストを取得する方法を確認し、機能に新しい標準を適用しました。具体的には、次の操作を行いました。

- リポジトリの指示とパス固有の指示ファイルがエージェントに読み込まれる方法を確認しました。
- コーディング標準に従うよう、指示ファイルを更新しました。
- 指示ファイルがコードに与える影響を確認しました。

次は、再利用可能な `quality-checks` スキルを[カスタマイズして実行し][next-lesson]、lint とテストが一貫して実行されるようにします。

## リソース

- [Copilot CLI にカスタム指示を追加する][instruction-files]
- [カスタム指示のサポート][custom-instructions-support]
- [カスタム指示を作成するためのベスト プラクティス][instructions-best-practices]
- [Awesome Copilot: 指示ファイルなどのリソース集][awesome-copilot]

[instruction-files]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions
[instructions-best-practices]: https://docs.github.com/copilot/concepts/prompting/response-customization#writing-effective-custom-instructions
[awesome-copilot]: https://awesome-copilot.github.com/
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support
[previous-lesson]: ../3-agent-modes/
[next-lesson]: ../5-agent-skills/
