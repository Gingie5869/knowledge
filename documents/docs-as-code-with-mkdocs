# MkDocs公開方式の比較検討メモ

## 背景

Markdownを正本としてGitHubで構成管理しながら、顧客にはHTML形式で閲覧してもらいたい。

検討ポイントは以下。

- MarkdownをGitHubで管理したい
- 顧客はブラウザで閲覧したい
- レビューコメントを残したい
- 設計書とレビュー履歴を紐付けたい
- 将来的な構成管理も実施したい

---

# 公開方式候補

## パターン1: GitHub Pages + GitHub Issues

### 構成

```text
Repository
↓
MkDocs
↓
GitHub Pages
↓
Issueでレビュー
```

### メリット

- GitHubだけで完結
- 導入コストが低い
- 構成管理とレビュー履歴を一元管理できる
- 変更履歴が自動で残る

### デメリット

- コメントがページ上に表示されない
- 非ITユーザーには少し分かりづらい
- Issueと設計書を行き来する必要がある

### レビューイメージ

```text
SCR-001 受注登録

↓ 指摘

Issue作成

タイトル:
SCR-001 コメント

内容:
代引商品のパターン追加希望
```

---

# パターン2: GitHub Pages + Discussions

### 構成

```text
Repository
↓
MkDocs
↓
GitHub Pages
↓
GitHub Discussions
```

### メリット

- Q&A形式で議論できる
- 顧客が参加しやすい
- スレッド形式で会話できる
- Issueよりも心理的ハードルが低い

### デメリット

- 設計書との関連付けルールが必要
- Discussion運用ルールが必要

### カテゴリ例

```text
業務フロー
画面設計
帳票設計
インターフェース
権限管理
```

---

# パターン3: MkDocs + ページコメント機能

### 構成

```text
Repository
↓
MkDocs
↓
HTMLサイト
↓
giscus
↓
GitHub Discussions
```

### 特徴

設計書ページの下部にコメント欄を表示できる。

利用者からは通常のWebサイトと同じ感覚になる。

### イメージ

```text
受注登録設計

業務フロー
画面設計
入力項目

----------------

コメント

顧客:
代引商品のケースも必要です

設計者:
対応します

顧客:
確認しました
```

### メリット

- ページを見ながらコメントできる
- Wordコメントに近い体験
- 顧客が利用しやすい
- コメントはGitHub上で管理可能

### デメリット

- 初期セットアップが少し必要

---

# パターン4: Azure Static Web Apps

### 構成

```text
GitHub
↓
MkDocs
↓
Azure Static Web Apps
```

### メリット

- Microsoft Entra ID認証が利用可能
- 顧客単位でアクセス制御可能
- HTTPS標準対応
- Azureとの親和性が高い

### デメリット

- Azure環境の準備が必要
- 運用コストが増える

### 向いているケース

- 顧客向け公開が前提
- セキュリティ要件が高い
- 外部ユーザー管理が必要

---

# パターン5: SharePoint

### 構成

```text
GitHub
↓
MkDocs
↓
HTML生成
↓
SharePoint
```

### メリット

- 顧客が慣れている
- M365認証利用可能
- アクセス制御が容易
- 社内利用との親和性が高い

### デメリット

- GitHubとの連携設計が必要
- デプロイ運用を考える必要がある

---

# 個人的な推奨案

## 第一候補

```text
Private Repository
↓
MkDocs Material
↓
GitHub Pages
↓
giscus
↓
GitHub Discussions
```

### 理由

設計書の閲覧とレビューが一体化できるため。

顧客の利用イメージは、

```text
設計書を見る
↓
そのままコメントを書く
↓
回答を確認する
```

となる。

Wordのコメント機能に近い体験を提供できる。

---

# 将来の構成管理まで考慮した運用

設計要素ごとにIDを付与する。

例

```text
SCR-001 受注登録
SCR-002 受注変更
SCR-003 出荷指示
```

レビューコメントにもIDを付与する。

例

```text
DISC-001 代引商品対応
DISC-002 配送先変更対応
```

### トレーサビリティ例

```text
要件
↓
Discussion
↓
Issue
↓
Commit
↓
Pull Request
↓
設計書
↓
ソースコード
```

これにより、

- なぜ仕様変更されたのか
- 誰が指摘したのか
- いつ対応したのか

を追跡できる。

---

# 現時点でのおすすめ方針

案件の前提

- Markdownを正本化したい
- GitHubを利用中
- 顧客レビューが必要
- AI活用したい
- 将来的に構成管理を強化したい

上記を踏まえると、まずは以下が現実的。

```text
Private Repository
↓
Markdown管理
↓
MkDocs Material
↓
GitHub Pages
↓
giscus
↓
GitHub Discussions
```

これにより、

- Docs as Code
- AI活用
- 顧客レビュー
- 構成管理
- トレーサビリティ

を比較的低コストで実現できる。
