# 🎨 自律的に成長するデザインシステム

GitHub Issues、Claude Code、Notionを活用した、自動でレギュレーションを生成・管理するデザインシステムです。

## 🌟 特徴

- **GitHub Issues でリクエスト**: ボタンの使い分けなど、デザインルールの追加をIssueで起票
- **自動でレギュレーション生成**: Claude Codeが既存のドキュメントと理論を参照し、自動でドキュメントを作成
- **Notionに自動蓄積**: 生成されたレギュレーションはNotionデータベースに自動保存
- **レビューとフィードバック**: PRでチーム全体がレビューし、品質を担保

## 🏗️ システム構成

```
1. GitHub Issuesで起票
   ↓
2. GitHub Actionsがトリガー
   ↓
3. Claude Codeがレギュレーション生成
   ↓
4. PRを自動作成
   ↓
5. レビュー＆マージ
   ↓
6. Notionに自動保存
```

## 📁 ディレクトリ構造

```
.
├── .github/
│   ├── workflows/              # GitHub Actionsのワークフロー
│   └── ISSUE_TEMPLATE/         # Issueテンプレート
├── docs/
│   ├── regulations/            # 生成されたレギュレーション
│   └── templates/              # レギュレーションのテンプレート
└── README.md
```

## 🚀 セットアップ

### ⚡ クイックスタート（5分で始める）

最速で動かしたい方は **[QUICKSTART.md](./QUICKSTART.md)** をご覧ください。

### 📖 詳細なセットアップ

#### Phase 1の詳細レポート

Phase 1で実装した内容の詳細は **[PHASE1_REPORT.md](./PHASE1_REPORT.md)** をご覧ください。

### 1. リポジトリのクローン

```bash
git clone https://github.com/YOUR_USERNAME/Building-a-Scalable-DesignSystem.git
cd Building-a-Scalable-DesignSystem
```

### 2. GitHub Secretsの設定

以下のSecretをリポジトリに設定してください：

- `GITHUB_TOKEN`: GitHub Actions用（自動で利用可能）
- `NOTION_API_KEY`: Notion API キー（Phase 2で設定）
- `NOTION_DATABASE_ID`: NotionデータベースID（Phase 2で設定）

### 3. Issue テンプレートから起票

リポジトリの「Issues」タブから「New Issue」をクリックし、「レギュレーション追加リクエスト」テンプレートを選択してください。

## 📝 使い方

1. **レギュレーションの追加をリクエスト**
   - GitHub Issuesで新しいレギュレーションをリクエスト
   - テンプレートに従って必要事項を記入

2. **自動処理を待つ**
   - GitHub Actionsが自動でPRを作成
   - Claude Codeがレギュレーションドキュメントを生成

3. **レビュー**
   - 作成されたPRを確認
   - 必要に応じて修正をコメント

4. **マージ**
   - 承認後、マージすると自動でNotionに保存

## 🛠️ 技術スタック

- **GitHub Issues**: レギュレーションリクエストの管理
- **GitHub Actions**: 自動化ワークフロー
- **Claude Code**: レギュレーション生成
- **Notion API**: ドキュメントの永続化
- **Markdown/MDX**: ドキュメント形式

## 📖 ドキュメント

### スタートガイド
- **[⚡ クイックスタート](./QUICKSTART.md)** - 5分で始める
- **[📋 Phase 1 セットアップガイド](./docs/phase1-setup-guide.md)** - 詳細な手順
- **[📊 Phase 1 完了レポート](./PHASE1_REPORT.md)** - 実装内容とシステム設計

### テンプレート
- [レギュレーションテンプレート](./docs/templates/regulation-template.md)
- [サンプル：ボタンの使い分け](./docs/regulations/button-usage.md)

### その他
- **[📝 Zenn記事ドラフト](./zenn-article-draft.md)** - 完成後に投稿予定

## 🤝 コントリビューション

このプロジェクトは開発中です。フィードバックやコントリビューションを歓迎します！

## 📄 ライセンス

MIT License

---

**Built with ❤️ for designers and developers**
