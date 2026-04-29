# Hello, MkDocs from nuitsjp

## 箇条書き

### 番号なし

- Item A
- Item B

### 番号あり

1. Item 1
2. Item 2
    1. Item 2.1

## テーブル

|rows|column1|column2|
|--|--|--|
|row1|1-1|1-2|
|row2|2-1|2-2|

## 画像

![Alt text](https://picsum.photos/300/200)

## GitHub Pull Request を用いたレビューワークフロー

```mermaid
flowchart TB
  subgraph 開発者["開発者（コントリビューター）"]
    direction TB
    D1[default ブランチを最新化] --> D2[作業用ブランチを作成]
    D2 --> D3[ローカルで実装とコミット] --> D4[リモートへ push]
    D4 --> D5[GitHub 上で Pull Request を作成] --> D6[レビュアーを指名 / 下書き解除 / 再依頼]
    D6 --> D7[レビュー中は待機]
    D7 --> D8[指摘内容を反映し再 push]
    D7 --> D9[必須チェック通過と承認のあと マージ可能なら マージを実行 ※1]
    D8 --> D7
    D9 --> D10[ローカルで追従 必要なら リモートの作業ブランチを削除 ※2]
  end

  subgraph レビュアー["レビュアー（指名・CODEOWNERS 等）"]
    direction TB
    R1[通知または PR 一覧から起票の PR を開く] --> R2[差分と会話 チェック状況を確認]
    R2 --> R3{方針}
    R3 -->|追加の修正依頼| R4[コメントまたは Request changes]
    R3 -->|問題なし| R5[Approve 承認]
    R3 -->|質問| R6[会話欄に返信 必要なら解決]
    R4 --> D8
    R6 --> R2
  end

  subgraph ギ["GitHub（リポジトリ / プロジェクトホスト）"]
    direction TB
    H1[PR ベース ターゲット 会話 レビュー画面を提供] --> H2[保護ルール 必須レビュー 必須ステータスを適用] --> H3[マージ UI とマージ方針の選択] --> H4[（任意） マージ後のブランチ削除を提案] --> H5[default へ変更を取り込み]
  end

  subgraph ガ["GitHub Actions（CI ・自動化）"]
    direction TB
    A1[push または pull_request 等のイベント] --> A2[ワークフロー定義に従いジョブを実行] --> A3{ジョブは成功したか} -->|失敗| A4[失敗の詳細を Checks に掲出] -->|成功| A5[GitHub 上でステータスチェックを成功に更新]
  end

  D4 -.->|プッシュ| A1
  D5 -.->|PR 掲出| H1
  D6 -.->|依頼| R1
  A2 -.->|PR の Checks に反映| R2
  D8 -.->|再 push| A1
  A4 -.->|修正が必要| D8
  A5 -.->|必須なら| H2
  R5 -.->|承認記録| H2
  D9 -.->|マージ操作| H3
  H3 -.->|マージ| H5
  H4 -.->|掃除| D10
```

※1 多くのチームでは PR 作者やレビュアーなど **書き込み権限＋ポリシー** を満たした人がマージします。  
※2 リモートのブランチ削除は、GitHub 上の「Delete branch」やリポジトリ設定に委ねる場合もあります。

## SVG

![GitFlow](gitflow.drawio.svg)
