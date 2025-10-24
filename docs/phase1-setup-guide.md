# Phase 1 セットアップガイド

このガイドでは、Phase 1（基本的なGitHub ActionsとIssueテンプレート）のセットアップ手順を説明します。

## 🎯 Phase 1 でできること

- ✅ GitHub Issuesでレギュレーションリクエストをテンプレートから作成
- ✅ Issue作成時に自動でコメントが返信される
- ✅ 処理中ラベルが自動で付与される
- ✅ レギュレーションドキュメントのテンプレート構造を確認

## 📋 前提条件

- GitHubアカウント
- リポジトリの作成権限
- 基本的なGit操作の知識

## 🚀 セットアップ手順

### 1. GitHubリポジトリの作成

```bash
# GitHubで新しいリポジトリを作成（Webから）
# リポジトリ名: Building-a-Scalable-DesignSystem
# 可視性: Public または Private（お好みで）
```

### 2. ローカルにファイルを配置

```bash
# このプロジェクトのファイルをリポジトリにコピー
cd Building-a-Scalable-DesignSystem

# ファイル構造を確認
tree -L 3
# .
# ├── .github/
# │   ├── workflows/
# │   │   └── issue-handler.yml
# │   └── ISSUE_TEMPLATE/
# │       └── regulation-request.yml
# ├── docs/
# │   ├── regulations/
# │   │   └── button-usage.md
# │   └── templates/
# │       └── regulation-template.md
# └── README.md
```

### 3. GitHubにプッシュ

```bash
# Gitリポジトリを初期化
git init

# ファイルをステージング
git add .

# コミット
git commit -m "Initial commit: Phase 1 setup"

# リモートリポジトリを追加
git remote add origin https://github.com/YOUR_USERNAME/Building-a-Scalable-DesignSystem.git

# プッシュ
git branch -M main
git push -u origin main
```

### 4. GitHub Actionsの有効化確認

1. GitHubリポジトリの「Actions」タブを開く
2. ワークフローが表示されていることを確認
3. もし無効になっている場合は「Enable workflows」をクリック

### 5. リポジトリ設定の確認

**Settings > Actions > General** で以下を確認：

- ✅ **Actions permissions**: Allow all actions and reusable workflows
- ✅ **Workflow permissions**: Read and write permissions
- ✅ **Allow GitHub Actions to create and approve pull requests**: チェック

## 🧪 動作テスト

### テスト1: Issueテンプレートの確認

1. リポジトリの「Issues」タブを開く
2. 「New Issue」をクリック
3. 「レギュレーション追加リクエスト」テンプレートが表示されることを確認

### テスト2: 自動応答の確認

1. Issueテンプレートを使って新しいIssueを作成
   - タイトル: `[REGULATION] テスト用レギュレーション`
   - 必須項目を適当に入力
   - 「Submit new issue」をクリック

2. 数秒後、自動でコメントが投稿されることを確認
   - 👋 挨拶メッセージ
   - 🤖 処理ステップの説明

3. ラベルに「processing」が追加されていることを確認

### テスト3: ワークフローログの確認

1. 「Actions」タブを開く
2. 実行されたワークフロー「レギュレーションリクエスト処理」をクリック
3. 各ジョブが成功（緑のチェック）していることを確認
4. ログを開いて詳細を確認

## 📝 実際に使ってみる

Phase 1では以下のような流れでテストできます：

### 実際のレギュレーションリクエストを作成

```
タイトル: [REGULATION] カラーパレットの使用基準

カテゴリー: カラー

背景・目的:
現在、各デザイナーが独自の色を使用しており、
ブランドカラーの統一性が保たれていない。
明確なカラーパレットとその使用基準を設けたい。

現在の課題:
- デザイナーによって微妙に異なる青色が使われている
- アクセシビリティを考慮した色の選択ができていない
- 背景色と文字色のコントラスト比が不十分な箇所がある

希望するレギュレーション内容（案）:
- プライマリカラー: #0066FF
- セカンダリカラー: #00CC88
- 文字色: #1A1A1A
- すべての色の組み合わせでWCAG AA基準を満たす
```

作成後、自動でコメントが返信されることを確認してください！

## 🔧 トラブルシューティング

### Issue作成時に自動コメントが投稿されない

**原因1: ラベルが正しく設定されていない**
- Issueテンプレートから作成した場合、自動で `regulation-request` ラベルが付与されます
- 手動でIssueを作成した場合は、このラベルを手動で追加してください

**原因2: GitHub Actionsが有効になっていない**
- Settings > Actions > General で Actions が有効になっているか確認

**原因3: Workflow permissionsが不足している**
- Settings > Actions > General > Workflow permissions
- 「Read and write permissions」を選択

### ワークフローが失敗する

1. Actions タブでワークフローのログを確認
2. エラーメッセージを確認
3. よくあるエラー:
   - `Resource not accessible by integration` → Permissions不足
   - `yaml: line X: mapping values are not allowed` → YAMLの文法エラー

## 📚 関連ドキュメント

- [GitHub Actions ドキュメント](https://docs.github.com/ja/actions)
- [Issue テンプレート作成ガイド](https://docs.github.com/ja/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository)
- [GitHub Script アクション](https://github.com/actions/github-script)

## 🎓 学習メモ（Rails学習者向け）

このPhase 1で触れる概念とRailsとの対応：

| GitHub Actions | Railsでの類似概念 |
|----------------|------------------|
| Workflow | Rake Task / Job |
| Trigger (on:) | Controller Action / Callback |
| Steps | メソッドの連鎖 |
| GitHub Script | Active Recordの操作 |
| YAML設定 | config/database.yml などの設定ファイル |

GitHub Actionsは「イベント駆動」の自動化ツールです。Railsでいえば：
- `after_create` コールバックでメール送信
- バックグラウンドジョブで重い処理を実行

といった概念に似ています。

## ✅ Phase 1 完了チェックリスト

- [ ] リポジトリを作成し、ファイルをプッシュした
- [ ] Issueテンプレートが表示される
- [ ] テストIssueを作成し、自動コメントが返信された
- [ ] 「processing」ラベルが自動で付与された
- [ ] Actionsタブでワークフローが成功している
- [ ] サンプルレギュレーション（button-usage.md）を確認した

## 🚀 次のステップ: Phase 2

Phase 1が完了したら、次は **Notion連携** に進みます！

Phase 2で実装すること：
- Notion APIの設定
- データベース構造の設計
- GitHub ActionsからNotionへのデータ書き込み
- レギュレーションの自動保存

---

**Phase 1 お疲れ様でした！🎉**

何か問題が発生したら、Issueを作成してフィードバックをお願いします。
