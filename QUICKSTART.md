# ⚡ クイックスタート（5分で始める）

このガイドでは、最速でPhase 1を動かす手順を説明します。

## 📦 事前準備（1分）

必要なもの：
- ✅ GitHubアカウント
- ✅ Gitがインストールされている

## 🚀 3ステップで開始

### Step 1: リポジトリを作成（1分）

1. **GitHubにログイン**
2. **画面右上の「+」→「New repository」をクリック**
3. **以下を入力:**
   - Repository name: `Building-a-Scalable-DesignSystem`
   - Public/Private: お好みで
   - ✅ **「Add a README file」はチェックしない**
4. **「Create repository」をクリック**

### Step 2: ファイルをプッシュ（2分）

```bash
# ダウンロードしたフォルダに移動
cd Building-a-Scalable-DesignSystem

# Gitリポジトリを初期化
git init

# すべてのファイルを追加
git add .

# コミット
git commit -m "Phase 1: Initial setup"

# リモートリポジトリを追加（YOUR_USERNAMEを自分のユーザー名に変更）
git remote add origin https://github.com/YOUR_USERNAME/Building-a-Scalable-DesignSystem.git

# プッシュ
git branch -M main
git push -u origin main
```

### Step 3: 動作確認（2分）

1. **GitHubリポジトリを開く**

2. **GitHub Actionsを有効化**
   - 「Settings」→「Actions」→「General」
   - 「Actions permissions」→「Allow all actions and reusable workflows」
   - 「Workflow permissions」→「Read and write permissions」にチェック
   - 「Save」をクリック

3. **テストIssueを作成**
   - 「Issues」タブを開く
   - 「New issue」をクリック
   - 「📋 レギュレーション追加リクエスト」を選択
   - 以下を入力：
     ```
     タイトル: [REGULATION] テスト用レギュレーション
     カテゴリー: コンポーネント
     背景・目的: テストです
     現在の課題: テスト中
     優先度: 低（余裕があれば）
     確認事項: すべてチェック
     ```
   - 「Submit new issue」をクリック

4. **自動コメントを確認**
   - 数秒待つ
   - 👋 自動コメントが投稿される
   - 🏷️ "processing" ラベルが追加される

## ✅ 成功！

これでPhase 1が動作しています！

## 🔍 トラブルシューティング

### 自動コメントが来ない場合

**チェック1: Actionsは有効？**
```
Settings → Actions → General
→ Workflow permissions → Read and write permissions
```

**チェック2: ワークフローは実行された？**
```
Actions タブ → 最新のワークフロー実行を確認
→ エラーがあればログを確認
```

**チェック3: ラベルは正しい？**
```
Issue に "regulation-request" ラベルが付いているか確認
```

## 📚 次のステップ

✅ Phase 1が動いたら:
1. **[PHASE1_REPORT.md](./PHASE1_REPORT.md)** で詳細を確認
2. **[docs/phase1-setup-guide.md](./docs/phase1-setup-guide.md)** で深く学ぶ
3. **Phase 2** に進む（Notion連携）

## 💬 サポート

問題が発生したら:
1. GitHub Issuesで報告
2. [セットアップガイド](./docs/phase1-setup-guide.md)のトラブルシューティングを確認
3. Actions のログを確認

---

**Happy Coding! 🎉**
