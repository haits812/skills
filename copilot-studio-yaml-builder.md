---
name: copilot-studio-yaml-builder
description: 対話形式でMicrosoft Copilot StudioのトピックYAMLを作成する。「Copilot Studioのトピックを作りたい」「Copilot StudioのYAMLを生成して」「エージェントのダイアログを作って」などのリクエストに使用。ユーザーから要件を段階的にヒアリングし、公式ドキュメントを参照しながら正確なYAMLを生成する。
---

# Copilot Studio YAML Builder

対話形式でMicrosoft Copilot StudioのトピックYAMLを生成するスキル。

## ヒアリングプロセス

以下の順序で段階的に質問する。一度に多くの質問をせず、1-2問ずつ進める。

### Phase 1: 基本情報

1. **目的の確認**
   - 「どんなトピック（会話フロー）を作りたいですか？やりたいことを教えてください」
   
2. **トリガーの確定**
   - Phrases（トリガーフレーズ）: ユーザーの発話で起動
   - Event/Activity: 外部イベントで起動
   - Redirect: 他トピックからのリダイレクト
   - OnUnknownIntent: 不明な意図のフォールバック
   - 迷っている場合は用途から提案する

### Phase 2: 入出力の定義

3. **入力の確認**
   - 「ユーザーから何を聞き取る必要がありますか？（例：名前、注文番号、質問内容など）」
   - 変数名、型（String, Number, Boolean, Table等）を整理

4. **出力の確認**
   - 「最終的にユーザーに何を伝えたいですか？」
   - メッセージ、Adaptive Card、リンクなど

### Phase 3: 処理フローの設計

5. **処理ステップの洗い出し**
   - 「入力から出力までの間に、どんな処理が必要ですか？」
   - 箇条書きで整理してもらう

6. **条件分岐の有無**
   - 「途中で条件によって処理を分けたい場面はありますか？」

7. **外部連携の確認**
   - 「Power Automateフローの呼び出しは必要ですか？」
   - 「生成AI（SearchAndSummarize）を使いますか？」

8. **トピック遷移の確認**
   - 「他のトピックへリダイレクトする必要はありますか？」

### Phase 4: トピック構成の判断

9. **複数トピックの必要性を判断**
   - 以下に該当する場合、トピック分割を提案する：
     - 条件分岐が3つ以上ある
     - 同じ処理が複数箇所で使われる（再利用性）
     - フローが10ステップ以上になる
     - 異なるペルソナ/シナリオに対応する
   - 「このフローは複雑なので、トピックを分けたほうが管理しやすいですが、分割しますか？」

10. **トピック分割時の追加ヒアリング**
    - 「この処理は他の場面でも再利用しますか？」
    - 「どの単位でトピックを分けたいですか？（機能別/ペルソナ別/フェーズ別）」

### Phase 5: 詳細設計

11. **エンティティの確認**
    - 組み込みエンティティ（日付、数値、メールなど）
    - カスタムエンティティ（選択肢リストなど）

12. **エラーハンドリング**
    - 「ユーザーが想定外の回答をした場合どうしますか？」

## 公式ドキュメントの参照

YAML生成前に必ず公式ドキュメントを確認して最新仕様を取得する。

### 公式リソース

| リソース | URL | 用途 |
|----------|-----|------|
| トピック作成 | https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-create-edit-topics | 基本操作 |
| コードエディタ | https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/topics-code-editor | YAML仕様 |
| VS Code拡張 | https://learn.microsoft.com/en-us/microsoft-copilot-studio/visual-studio-code-extension-edit-agent-components | 構造リファレンス |
| GitHubサンプル | https://github.com/microsoft/CopilotStudioSamples | YAMLサンプル集 |

### 確認手順

1. `web_fetch`で公式ドキュメントの該当ページを取得
2. 不明点は`web_search`で「site:learn.microsoft.com Copilot Studio [検索語]」で検索
3. サンプルはGitHubリポジトリを参照

## YAML生成ルール

### 基本構造

```yaml
kind: AdaptiveDialog
beginDialog:
  kind: [トリガータイプ]
  id: main
  [トリガー固有の設定]
  actions:
    - [アクションノード1]
    - [アクションノード2]
    ...

inputType: {}
outputType: {}
```

### 主要なトリガータイプ

| タイプ | 用途 | 設定項目 |
|--------|------|----------|
| OnRecognizedIntent | フレーズでトリガー | intent.triggerQueries |
| OnUnknownIntent | 不明意図のフォールバック | priority |
| OnRedirect | 他トピックからのリダイレクト | - |
| OnConversationStart | 会話開始時 | - |

### 主要なアクションノード（kind）

| タイプ | 用途 | 主な設定 |
|--------|------|----------|
| SendActivity | メッセージ送信 | activity（テキストまたはAdaptive Card） |
| Question | ユーザー入力を求める | prompt, variable, entity |
| SetVariable | 変数に値を設定 | variable, value |
| ConditionGroup | 条件分岐 | conditions[].condition, actions |
| SearchAndSummarizeContent | 生成AI検索 | userInput, variable, publicDataSource |
| InvokeFlow | Power Automateフロー呼び出し | flowId, inputs, outputs |
| RedirectToTopic | トピックへリダイレクト | topicId |
| EndDialog | ダイアログ終了 | clearTopicQueue |
| Foreach | ループ処理 | items, value, actions |
| ParseValue | 値のパース | valueType, value, variable |
| GotoAction | アクションへジャンプ | actionId |

### 変数参照の書式

```
Topic.VariableName      # トピック変数
System.Activity.Text    # ユーザー入力テキスト
Global.VariableName     # グローバル変数
```

### 式（Power Fx）の書式

```yaml
value: ="固定テキスト"
value: =System.Activity.Text
value: =Topic.Name & " さん"
condition: =!IsBlank(Topic.Answer)
condition: =Topic.Choice = 'topicname.main.nodeid'.OptionValue
```

## 複数トピック構成

### トピック分割の判断基準

| 条件 | 推奨アクション |
|------|----------------|
| 条件分岐が3つ以上 | 分岐先を個別トピックに |
| 同じ処理が複数箇所で使われる | 共通トピックとして切り出し |
| フローが10ステップ以上 | フェーズごとに分割 |
| 異なるユーザー種別に対応 | ペルソナ別トピック |
| エスカレーションがある | エスカレーション専用トピック |

### 複数トピック構成時の出力形式

以下の構成でファイルを生成する：

```
📁 [エージェント名]/
├── topics/
│   ├── 01_main-menu.yaml           # エントリーポイント
│   ├── 02_[機能名].yaml            # 機能別トピック
│   ├── 03_[機能名].yaml
│   ├── ...
│   └── 99_fallback.yaml            # フォールバック（必要に応じて）
└── README.md                        # 構成説明書
```

### README.mdの内容

```markdown
# [エージェント名] トピック構成

## 概要
[エージェントの目的・概要]

## トピック一覧

| No | ファイル名 | トピック名 | 役割 |
|----|------------|------------|------|
| 01 | main-menu.yaml | メインメニュー | エントリーポイント、振り分け |
| 02 | xxx.yaml | XXX | ... |

## トピック遷移図

```
[ユーザー発話]
      │
      ▼
┌─────────────┐
│ メインメニュー │
└──────┬──────┘
       │
   ┌───┼───┐
   ▼   ▼   ▼
 [A] [B] [C]
```

## 変数リレー

| 変数名 | 型 | 定義元 | 参照先 | 用途 |
|--------|-----|--------|--------|------|
| Topic.CustomerName | String | main-menu | support, billing | 顧客名 |

## 追加設定（YAML外）

- [ ] ナレッジソース設定
- [ ] Power Automateフロー作成
- [ ] 生成AIモード有効化
- [ ] チャネル公開
```

### 変数リレーの設計

トピック間で変数を受け渡す場合：

**渡す側（親トピック）**
```yaml
- kind: RedirectToTopic
  id: redirectToSupport
  topicId: crf00_technicalSupport
  inputs:
    - name: CustomerName
      value: =Topic.CustomerName
    - name: IssueCategory
      value: =Topic.Category
```

**受け取る側（子トピック）**
```yaml
inputType:
  properties:
    CustomerName:
      displayName: 顧客名
      type: String
    IssueCategory:
      displayName: 問題カテゴリ
      type: String
```

**返す側（子トピック）**
```yaml
outputType:
  properties:
    TicketNumber:
      displayName: チケット番号
      type: String

# アクション内で
- kind: SetVariable
  id: setOutput
  variable: Topic.TicketNumber
  value: ="TKT-12345"

- kind: EndDialog
  id: endWithOutput
```

**受け取る側（親トピック）**
```yaml
- kind: RedirectToTopic
  id: redirectToSupport
  topicId: crf00_technicalSupport
  inputs:
    - name: CustomerName
      value: =Topic.CustomerName
  outputs:
    - name: TicketNumber
      variable: Topic.TicketNumber
```

## サンプルYAML

### 基本的なQ&Aトピック

```yaml
kind: AdaptiveDialog
beginDialog:
  kind: OnRecognizedIntent
  id: main
  intent:
    triggerQueries:
      - 営業時間を教えて
      - 何時まで営業

  actions:
    - kind: SendActivity
      id: sendMessage1
      activity: 営業時間は平日9:00〜18:00です。土日祝日はお休みです。

inputType: {}
outputType: {}
```

### 質問と条件分岐

```yaml
kind: AdaptiveDialog
beginDialog:
  kind: OnRecognizedIntent
  id: main
  intent:
    triggerQueries:
      - 問い合わせ
      - サポート

  actions:
    - kind: Question
      id: askCategory
      interruptionPolicy:
        allowInterruption: true
      prompt: お問い合わせの種類を選択してください。
      variable: init:Topic.Category
      entity:
        kind: EmbeddedEntity
        definition:
          kind: ClosedListEntity
          items:
            - id: technical
              displayName: 技術的なご質問
            - id: billing
              displayName: 請求について
            - id: other
              displayName: その他

    - kind: ConditionGroup
      id: categoryCondition
      conditions:
        - id: technicalBranch
          condition: =Topic.Category = 'main.askCategory'.technical
          actions:
            - kind: RedirectToTopic
              id: redirectTech
              topicId: crf00_technicalSupport

        - id: billingBranch
          condition: =Topic.Category = 'main.askCategory'.billing
          actions:
            - kind: RedirectToTopic
              id: redirectBilling
              topicId: crf00_billingInquiry

      elseActions:
        - kind: SendActivity
          id: otherMessage
          activity: その他のお問い合わせは support@example.com までご連絡ください。

inputType: {}
outputType: {}
```

### 生成AI検索（Generative Answers）

```yaml
kind: AdaptiveDialog
beginDialog:
  kind: OnUnknownIntent
  id: main
  priority: -1
  actions:
    - kind: SearchAndSummarizeContent
      id: searchContent
      userInput: =System.Activity.Text
      variable: Topic.Answer
      moderationLevel: Medium
      additionalInstructions: 回答は日本語で、丁寧な口調で応答してください。
      publicDataSource:
        sites:
          - "docs.example.com/"
      sharePointSearchDataSource: {}

    - kind: ConditionGroup
      id: hasAnswerCondition
      conditions:
        - id: hasAnswer
          condition: =!IsBlank(Topic.Answer)
          actions:
            - kind: EndDialog
              id: endTopic
              clearTopicQueue: true

      elseActions:
        - kind: SendActivity
          id: noAnswerMessage
          activity: 申し訳ございません。ご質問への回答が見つかりませんでした。

inputType: {}
outputType: {}
```

## 複数トピック構成サンプル

### 問い合わせ対応エージェント（3トピック構成）

**構成図**
```
[ユーザー発話]
      │
      ▼
┌─────────────────┐
│ 01_main-menu    │ ← エントリー、カテゴリ選択
└────────┬────────┘
         │
    ┌────┼────┐
    ▼    ▼    ▼
┌──────┐┌──────┐┌──────┐
│ 02_  ││ 03_  ││ else │
│tech  ││billing││→終了 │
└──────┘└──────┘└──────┘
```

**01_main-menu.yaml**
```yaml
kind: AdaptiveDialog
beginDialog:
  kind: OnRecognizedIntent
  id: main
  intent:
    triggerQueries:
      - 問い合わせ
      - サポート
      - 困っている

  actions:
    - kind: Question
      id: askCategory
      interruptionPolicy:
        allowInterruption: true
      prompt: お問い合わせの種類を選択してください。
      variable: init:Topic.Category
      entity:
        kind: EmbeddedEntity
        definition:
          kind: ClosedListEntity
          items:
            - id: technical
              displayName: 技術的なご質問
            - id: billing
              displayName: 請求について
            - id: other
              displayName: その他

    - kind: ConditionGroup
      id: categoryBranch
      conditions:
        - id: techBranch
          condition: =Topic.Category = 'main.askCategory'.technical
          actions:
            - kind: RedirectToTopic
              id: redirectTech
              topicId: crf00_technicalSupport

        - id: billingBranch
          condition: =Topic.Category = 'main.askCategory'.billing
          actions:
            - kind: RedirectToTopic
              id: redirectBilling
              topicId: crf00_billingInquiry

      elseActions:
        - kind: SendActivity
          id: otherMessage
          activity: その他のお問い合わせは support@example.com までご連絡ください。

inputType: {}
outputType: {}
```

**02_technical-support.yaml**
```yaml
kind: AdaptiveDialog
beginDialog:
  kind: OnRedirect
  id: main
  actions:
    - kind: Question
      id: askIssue
      prompt: 技術的な問題の内容を教えてください。
      variable: init:Topic.IssueDetail
      entity:
        kind: EmbeddedEntity
        definition:
          kind: RegexEntity
          pattern: ".*"

    - kind: SearchAndSummarizeContent
      id: searchKnowledge
      userInput: =Topic.IssueDetail
      variable: Topic.Answer
      moderationLevel: Medium
      additionalInstructions: 技術サポートとして、問題解決に役立つ回答をしてください。

    - kind: ConditionGroup
      id: hasAnswer
      conditions:
        - id: answered
          condition: =!IsBlank(Topic.Answer)
          actions:
            - kind: SendActivity
              id: sendAnswer
              activity: "{Topic.Answer}"
      elseActions:
        - kind: SendActivity
          id: escalateMessage
          activity: 担当者にエスカレーションします。しばらくお待ちください。

inputType: {}
outputType: {}
```

**03_billing-inquiry.yaml**
```yaml
kind: AdaptiveDialog
beginDialog:
  kind: OnRedirect
  id: main
  actions:
    - kind: Question
      id: askOrderNumber
      prompt: ご注文番号を入力してください（例：ORD-12345）
      variable: init:Topic.OrderNumber
      entity:
        kind: EmbeddedEntity
        definition:
          kind: RegexEntity
          pattern: "ORD-\\d{5}"

    - kind: SendActivity
      id: confirmOrder
      activity: ご注文番号 {Topic.OrderNumber} を確認しました。請求担当よりご連絡いたします。

inputType: {}
outputType: {}
```

## 生成フロー

1. ヒアリング完了後、要件を箇条書きで確認
2. **トピック分割が必要か判断し、必要なら構成を提案**
3. ユーザーの承認を得る
4. 必要に応じて公式ドキュメントをweb検索で確認
5. YAML生成（複数トピックの場合は全ファイル生成）
6. **複数トピックの場合はREADME.md（構成図・変数リレー）も生成**
7. 生成したYAMLの説明を添える
8. **YAMLだけでは対応できない設定がある場合、必ず設定方法を併記する**
9. ファイルとして出力

## YAMLだけでは対応できない設定

以下の設定はYAMLのみでは完結せず、追加の設定手順が必要。YAML生成時に該当する場合は、必ず設定方法を併記すること。

### スケジュール起動（時間トリガー）

YAMLのトリガーはユーザー発話やイベント起点のみ。定期実行にはPower Automateとの連携が必要。

**設定方法：**
1. Power Automateで「スケジュール済みクラウドフロー」を作成
2. トリガー「繰り返し」で実行間隔を設定（例：毎日9:00）
3. アクション「Microsoft Copilot Studio」→「エージェントにメッセージを送信」を追加
4. 対象トピックのトリガーフレーズを送信メッセージに設定
5. 応答を受け取ってTeams/メール等に転送

```
[Power Automate フロー構成]
┌─────────────────────────┐
│ トリガー: 繰り返し       │
│ (毎日 9:00 JST)         │
└───────────┬─────────────┘
            ▼
┌─────────────────────────┐
│ Copilot Studioに        │
│ メッセージ送信          │
│ 「生成AIニュース」      │
└───────────┬─────────────┘
            ▼
┌─────────────────────────┐
│ 応答をTeamsチャネルに   │
│ 投稿 / メール送信       │
└─────────────────────────┘
```

### ナレッジソースの設定

`SearchAndSummarizeContent`で参照するナレッジソースの一部はYAMLで指定できるが、以下はUI設定が必要。

**UI設定が必要な項目：**
- SharePointサイトの接続・認証
- アップロードファイル（PDF、Word等）
- Dataverseテーブル
- カスタムコネクタ経由のデータ

**設定方法：**
1. Copilot Studio → エージェント設定 → 「ナレッジ」
2. 「ナレッジソースを追加」から種類を選択
3. 認証情報・接続先を設定

### Power Automateフローの連携

`InvokeFlow`ノードで呼び出すフローは事前に作成・公開が必要。

**設定方法：**
1. Power Automateで「インスタントクラウドフロー」を作成
2. トリガー「Microsoft Copilot Studio からフローを実行する」を選択
3. 入出力パラメータを定義
4. フローを保存・公開
5. Copilot Studio側で「アクションを呼び出す」からフローを選択
6. YAMLでは`flowId`に該当フローのIDを記載

```yaml
- kind: InvokeFlow
  id: callMyFlow
  flowId: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx  # Power AutomateのフローID
  inputs:
    inputParam1: =Topic.UserInput
  outputs:
    outputParam1: Topic.FlowResult
```

### 認証設定

エージェントの認証方式（Azure AD、手動認証など）はYAMLでは設定不可。

**設定方法：**
1. Copilot Studio → エージェント設定 → 「セキュリティ」
2. 「認証」から認証方式を選択
3. Azure ADの場合はアプリ登録情報を入力

### チャネル公開

Teams、Webサイト、LINE等へのチャネル公開はUI操作が必要。

**設定方法：**
1. Copilot Studio → 「公開」→ 「公開」ボタン
2. 「チャネル」から公開先を選択
3. 各チャネル固有の設定を完了

### 生成AI機能の有効化

`SearchAndSummarizeContent`（生成AI回答）を使用するには、エージェントの生成AIモードを有効化する必要がある。

**設定方法：**
1. Copilot Studio → エージェント設定 → 「生成AI」
2. 「生成」または「クラシック + 生成」を選択
3. コンテンツモデレーションレベルを設定

---

## 注意事項

- ノードIDは小文字キャメルケースまたはスネークケースを推奨（例：`sendMessage1`, `ask_name`）
- 変数名は`Topic.`プレフィックス + パスカルケースを推奨（例：`Topic.CustomerName`）
- エンティティの選択肢参照は `'topicname.main.nodeid'.OptionId` 形式
- 複雑なフローは図解説明を添える
- 生成後は「Copilot Studioのコードエディタに貼り付けて動作確認してください」と案内
- Power Fxの式は `=` で始める
