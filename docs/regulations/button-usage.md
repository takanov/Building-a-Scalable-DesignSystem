# プライマリボタンとセカンダリボタンの使い分け

> **カテゴリー**: コンポーネント  
> **最終更新**: 2025-10-24  
> **ステータス**: Approved

## 📋 概要

ボタンは情報アーキテクチャにおいて最も重要なインタラクション要素の一つです。このレギュレーションでは、プライマリボタンとセカンダリボタンの適切な使い分けについて定義します。

## 🎯 目的

このレギュレーションは以下の目的で設定されています：

- UIの視覚的階層を明確にし、ユーザーが迷わず主要なアクションを実行できるようにする
- デザインの一貫性を保ち、チーム全体で統一された基準を持つ
- アクセシビリティを向上させ、すべてのユーザーにとって使いやすいインターフェースを実現する

## ⚠️ 解決する課題

現状、以下の問題が発生しています：

- 1つの画面に複数のプライマリボタンが配置され、どれが主要なアクションか不明確
- 重要度の低いアクション（キャンセル、戻る等）にプライマリボタンが使用されている
- デザイナーによってボタンの使い方が異なり、一貫性がない
- セカンダリボタンの視認性が低すぎるという指摘がある

## ✅ ルール

### 基本原則

**1. 1画面につきプライマリボタンは1つまで**
- 例外: モーダル内と親画面でそれぞれ1つずつは許可される

**2. プライマリボタンは最も重要なアクションにのみ使用**
- ページやフローの主目的となるアクション
- ユーザーが最も実行する可能性が高いアクション

**3. セカンダリボタンはプライマリに次ぐ重要度のアクション**
- プライマリをサポートする代替アクション
- 破壊的でない補助的なアクション

### 具体的な使用基準

| シーン | プライマリボタン | セカンダリボタン |
|--------|-----------------|------------------|
| フォーム送信 | 「保存」「送信」「登録」 | 「キャンセル」「下書き保存」 |
| 確認ダイアログ | 「削除」「実行」 | 「キャンセル」 |
| ページ遷移 | 「次へ」「完了」 | 「戻る」 |
| データ操作 | 「作成」「追加」 | 「インポート」「テンプレートから作成」 |

## 📐 実装例

### ✅ Good Examples

**フォーム画面**
```jsx
<form>
  {/* フォーム要素 */}
  
  <ButtonGroup>
    <Button variant="secondary" onClick={handleCancel}>
      キャンセル
    </Button>
    <Button variant="primary" type="submit">
      保存
    </Button>
  </ButtonGroup>
</form>
```

**確認モーダル**
```jsx
<Modal>
  <ModalTitle>本当に削除しますか?</ModalTitle>
  <ModalContent>この操作は取り消せません。</ModalContent>
  
  <ModalActions>
    <Button variant="secondary" onClick={handleCancel}>
      キャンセル
    </Button>
    <Button variant="primary" variant="destructive" onClick={handleDelete}>
      削除
    </Button>
  </ModalActions>
</Modal>
```

### ❌ Bad Examples

**悪い例1: プライマリボタンが複数**
```jsx
❌ NG
<ButtonGroup>
  <Button variant="primary">保存</Button>
  <Button variant="primary">送信</Button>
  <Button variant="primary">下書き保存</Button>
</ButtonGroup>

✅ OK
<ButtonGroup>
  <Button variant="secondary">下書き保存</Button>
  <Button variant="primary">送信</Button>
</ButtonGroup>
```

**悪い例2: キャンセルがプライマリ**
```jsx
❌ NG
<ButtonGroup>
  <Button variant="primary">キャンセル</Button>
  <Button variant="secondary">保存</Button>
</ButtonGroup>

✅ OK
<ButtonGroup>
  <Button variant="secondary">キャンセル</Button>
  <Button variant="primary">保存</Button>
</ButtonGroup>
```

## 🔍 チェックリスト

実装時には以下を確認してください：

- [ ] 1画面にプライマリボタンは1つのみ配置されているか
- [ ] プライマリボタンはそのページで最も重要なアクションに使用されているか
- [ ] キャンセルや戻るなどの消極的アクションはセカンダリボタンになっているか
- [ ] ボタンの配置順序は正しいか（一般的に、左: キャンセル / 右: 実行）
- [ ] 破壊的なアクション（削除など）には適切な警告スタイルが適用されているか
- [ ] モバイル表示でもボタンの階層が明確に伝わるか

## 📚 参考資料

- [Material Design - Buttons](https://material.io/components/buttons)
- [Apple Human Interface Guidelines - Buttons](https://developer.apple.com/design/human-interface-guidelines/buttons)
- [Nielsen Norman Group - Primary vs Secondary Actions](https://www.nngroup.com/articles/call-to-action-buttons/)
- 社内Notion: デザイン原則 > ビジュアル階層

## 💡 補足・注意事項

### ボタンの配置順序について

一般的な配置パターン：
- **左揃え**: セカンダリ（キャンセル） | プライマリ（実行）
- **右揃え**: プライマリ（実行） | セカンダリ（キャンセル）

我々のシステムでは **左揃えパターン** を採用しています。

### 破壊的アクションの扱い

削除や取り消せない変更などの破壊的アクションは、プライマリボタンであっても赤色など警告色を使用します：

```jsx
<Button variant="primary" color="destructive">
  削除
</Button>
```

### リンクとボタンの使い分け

- **ボタン**: アクションを実行（データ送信、状態変更など）
- **リンク**: 別のページへ移動

移動のみが目的の場合は、ボタンではなくリンクを使用してください。

---

## 📊 メタ情報

- **Issue**: #1
- **提案者**: @designer-user
- **承認者**: @lead-designer, @lead-engineer
- **関連レギュレーション**: 
  - アイコンボタンの使用基準
  - フォームデザインパターン
  - カラーシステム

## 📝 変更履歴

| 日付 | 変更内容 | 変更者 |
|------|---------|--------|
| 2025-10-24 | 初版作成 | @designer-user |
| 2025-10-24 | レビューフィードバック反映 | @designer-user |
| 2025-10-24 | 承認 | @lead-designer |
