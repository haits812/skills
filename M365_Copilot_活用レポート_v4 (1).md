# Microsoft 365 Copilot 活用レポート

## このレポートのポイント

1. **国内大手企業で月間10,000時間以上の業務時間削減**、年間12億円のコスト削減を実現した事例あり
   - 出典: [住友商事「コスト削減効果は年間約12億」](https://www.sumitomocorp.com/ja/jp/enrich/contents/0095) / [住友商事「AIとパワーナップから考える働き方の未来」](https://www.sumitomocorp.com/ja/jp/enrich/contents/0088) / [日経クロステック](https://xtech.nikkei.com/atcl/nxt/column/18/03085/013000002/) / [ITmedia](https://www.itmedia.co.jp/business/articles/2504/14/news001.html)

2. **Teams会議の議事録自動作成**が最も即効性が高く、導入効果を実感しやすい機能
   - 出典: [yjk365「TeamsのMicrosoft 365 Copilotを使ってみた」](https://yjk365.jp/jirei/how-to-use-teamscopilot/) / [Microsoft公式サポート](https://support.microsoft.com/ja-jp/office/microsoft-teams-会議で-copilot-を使用する-0bf9dd3c-96f7-44e2-8bb8-790bedf066b1)

3. 月額約4,500円/人だが、月12時間の時間削減で**投資回収率約800%**を達成可能
   - 出典: [Microsoft Customer Stories - デンソー（月12時間削減実績）](https://www.microsoft.com/ja-jp/customers/story/19426-denso-corporation-microsoft-365-copilot) / [Microsoft 365 Copilot価格](https://www.microsoft.com/ja-jp/microsoft-365/copilot/enterprise)

4. 「**たたき台を作り、人が確認・修正する**」という協働型のワークフローが成功の鍵
   - 出典: [住友商事 浅田氏インタビュー「副操縦士」発言](https://www.sumitomocorp.com/ja/jp/enrich/contents/0088) / 太田浩史『Microsoft 365 Copilot 踏み込み活用術』（インプレス、2026年）

---

## 1. Microsoft 365 Copilotとは

### 製品の概要

Microsoft 365 Copilotは、OpenAI/AnthropicのLLM（大規模言語モデル）とMicrosoft Graph（組織内のメール・カレンダー・ドキュメント）を組み合わせて動作するAIアシスタント。

### 「副操縦士」という位置づけ

Copilotという名前には「副操縦士（Co-Pilot）」という意味がある。操縦士は利用する私たち人間であり、Copilotはあくまで操縦士を支援してくれる存在。完成品を一発で生成するのではなく、「たたき台」を作成し、それを人が確認・修正するという協働型のワークフローが基本となる。

### 対応アプリケーション

| アプリ | 主な機能 |
|--------|----------|
| Teams | 会議の自動要約・議事録作成、アクションアイテム抽出 |
| Word | 文書作成・要約・書き換え、コーチング機能 |
| Excel | 数式補完、データ分析・グラフ作成 |
| Outlook | メール要約・返信ドラフト生成 |
| PowerPoint | スライド自動生成、翻訳（40言語対応） |
| OneNote / Loop / Forms / SharePoint | 各種支援機能 |

### 料金体系（2025年1月時点）

| プラン | 料金 | 備考 |
|--------|------|------|
| Microsoft 365 Copilot | 約4,500円/人/月 | M365契約が前提 |
| Copilot Chat（基本機能） | 無料 | Entraアカウント保有者 |
| Copilot Studio | 従量課金 | Azure契約が必要 |

---

## 2. 消費者向けCopilotとの違い

「Copilot」という名前のサービスは複数存在するため、混同しやすい。

| 製品名 | 対象 | 特徴 | 料金 |
|--------|------|------|------|
| **Microsoft Copilot**（旧Bing Chat） | 一般消費者 | Web検索ベースのチャットAI。bing.com/chatやWindows標準搭載 | 無料 |
| **Copilot Pro** | 個人ユーザー | 上記＋Office連携。個人向けM365契約者向け | 約3,200円/月 |
| **Microsoft 365 Copilot** | 法人 | **本レポートの対象**。組織データ連携、エンタープライズセキュリティ | 約4,500円/人/月 |
| **Copilot Chat** | 法人 | M365 Copilotの基本機能。Entraアカウントがあれば無料 | 無料 |

### 重要な違い

- 消費者向けCopilotは**インターネット上の情報**を参照
- Microsoft 365 Copilotは**組織内のデータ（メール・ファイル・会議）** を参照
- 法人版はデータがAI学習に使用されない（エンタープライズデータ保護）

本レポートでは、法人向けの**Microsoft 365 Copilot**について解説する。

### Copilot ChatとMicrosoft 365 Copilotの違い

法人向けには「Copilot Chat（無料）」と「Microsoft 365 Copilot（有料）」の2つがある。**2025年8月〜10月のアップデートで無料版の機能が大幅に拡充された**ため、追加料金を払うかどうかの判断ポイントが変わっている。

#### 機能比較（2026年1月時点）

| 機能 | Copilot Chat（無料） | M365 Copilot（約4,500円/人/月） |
|------|---------------------|-------------------------------|
| **Webブラウザでのチャット** | ✅ | ✅ |
| **Web検索** | ✅ | ✅ |
| **Word内でのCopilot利用** | ✅（基本機能） | ✅（全機能） |
| **Excel内でのCopilot利用** | ✅（基本機能） | ✅（全機能＋高度分析） |
| **PowerPoint内でのCopilot利用** | ✅（基本機能） | ✅（全機能） |
| **Outlook内でのCopilot利用** | ✅（基本機能） | ✅（全機能） |
| **OneNote内でのCopilot利用** | ✅（基本機能） | ✅（全機能） |
| **Teams会議の要約・議事録** | ❌ | ✅ |
| **Teamsチャットの要約** | ❌ | ✅ |
| **組織データ（SharePoint等）の検索** | 一部（開いているファイルのみ） | ✅（組織全体を横断検索） |
| **Researcher/Analystエージェント** | ❌ | ✅ |

出典：[Microsoft 365 Copilot プランと価格](https://www.microsoft.com/ja-jp/microsoft-365-copilot/pricing/enterprise) / [Microsoft 365 アプリで Copilot Chat を使用する](https://support.microsoft.com/ja-jp/office/microsoft-365-アプリで-copilot-chat-を使用する)

#### 2025年8月〜10月のアップデートで変わったこと

**無料のCopilot Chatでもできるようになったこと：**
- Word/Excel/PowerPoint/Outlook/OneNote内でCopilotを利用可能に
- 開いているファイルの要約・質問応答
- 基本的な文書作成支援

**引き続き有料版（M365 Copilot）が必要なこと：**
- **Teams会議の議事録自動生成**（最も即効性の高い機能）
- **組織全体のデータを横断検索**（「〇〇プロジェクトの資料を探して」など）
- **高度なExcel分析**（Agent Mode、複雑なデータ処理）
- **Researcher/Analystエージェント**

#### 判断のポイント

**Copilot Chat（無料）で十分なケース：**
- 開いているファイルの要約や質問がメイン
- 基本的な文書作成・推敲支援で十分
- Teams会議の議事録は手動で対応できる

**M365 Copilot（有料）が必要なケース：**
- **Teams会議の議事録を自動生成したい**（これが最大の差別化ポイント）
- **組織内の情報を横断検索したい**（「先月の営業会議の資料は？」など）
- **高度なデータ分析を行いたい**（Analyst、複雑なExcel処理）

#### 実務での違いの例

| やりたいこと | Copilot Chat（無料） | M365 Copilot（有料） |
|-------------|---------------------|---------------------|
| 「開いているWordの要点を教えて」 | ✅ できる | ✅ できる |
| 「この文章をフォーマルに書き換えて」 | ✅ できる | ✅ できる |
| 「会議の議事録を自動で作りたい」 | ❌ 自分でメモ → 後からチャットで整理 | ✅ Teams会議中に自動要約 → 議事録生成 |
| 「先月の〇〇プロジェクトの資料を探して」 | ❌ 自分でSharePointを検索 | ✅ Copilotが組織全体から検索 |
| 「このデータを深く分析して」 | △ 基本的な分析のみ | ✅ Agent Mode、高度な推論 |

**結論：Teams会議の議事録自動生成と、組織データの横断検索が必要かどうか**が最大の判断ポイント。特にTeams会議の議事録自動生成は、有料版でないと利用できない最も価値の高い機能。

※機能は頻繁にアップデートされるため、最新情報は[Microsoft公式](https://www.microsoft.com/ja-jp/microsoft-365-copilot/pricing)を確認してください。

#### ブラウザ版（Web版）とデスクトップ版の違い

Copilot Chatの機能は、ブラウザ版とデスクトップ版で異なる場合がある。

| 観点 | ブラウザ版（Web版） | デスクトップ版 |
|------|-------------------|---------------|
| **新機能の提供** | 先行して提供される | 遅れて提供される場合あり |
| **更新チャネルの影響** | なし | 「半期エンタープライズチャネル」では機能制限あり |
| **管理者設定の影響** | 比較的少ない | ピン留め解除等で無効化される場合あり |

**推奨：新機能をいち早く使いたい場合はブラウザ版（Web版）を利用**

出典：[キーマンズネット - M365 Copilotの最新機能を早く使うなら「ブラウザ版」が良い理由](https://kn.itmedia.co.jp/kn/articles/2508/01/news006.html)

デスクトップ版でCopilotが表示されない場合は、以下を確認：
- 更新チャネルが「最新チャネル」または「月次エンタープライズチャネル」になっているか
- 管理者がCopilot Chatのピン留めを解除していないか
- M365サブスクリプションが対象ライセンスか

---

## 3. 導入効果・メリット

### 国内企業の導入効果（実績値）

| 企業名 | 時間削減効果 | その他成果 | 出典 |
|--------|--------------|------------|------|
| 住友商事 | 月間10,560時間削減 | 年間12億円コスト削減、利用率75% | [Microsoft公式事例](https://customers.microsoft.com/ja-jp/story/1839340739329724-sumitomo-corporation-microsoft-copilot-for-microsoft-365-professional-services-ja-japan) |
| デンソー | 1人あたり月12時間削減 | 設計品質向上、3万人展開予定 | [Microsoft公式事例](https://customers.microsoft.com/ja-jp/story/1892831961143-denso-corporation-manufacturing-microsoft-365-copilot-ja-japan) |
| 東芝 | 1人あたり月5.6時間削減 | 95%が実務活用、1万人展開決定 | [Microsoft公式事例](https://customers.microsoft.com/ja-jp/story/1824605500134070586-toshiba-discrete-manufacturing-microsoft-365-copilot-ja-japan) |
| JCB | 1人あたり月6時間削減 | 月間利用率83%、全社員展開予定 | [Microsoft公式事例](https://customers.microsoft.com/ja-jp/story/1858630175736658656-jcb-banking-and-capital-markets-microsoft-365-copilot-ja-japan) |
| 学情 | 3か月で5,004時間削減 | アクティブユーザー率100%達成 | [Microsoft公式事例](https://customers.microsoft.com/ja-jp/story/1811604158453438567-gakujo-professional-services-microsoft-365-copilot-ja-japan) |

### ROI試算

月額約4,500円/人の投資に対し、月12時間の業務時間削減が実現できれば、時給3,000円の社員で月36,000円相当の効果 → **投資回収率 約800%**

### 主要メリット

#### ① 日常業務での即効性

- 全社員が日常利用するMicrosoft 365に組み込まれており、特定業務ではなく全社員が利用可能
- 使い慣れたWord、Excel、PowerPoint、Teams、Outlookにそのまま統合
- 新しいツールの学習コストが低い

#### ② セキュリティ・ガバナンス

- 各企業のMicrosoft 365環境（テナント）内で閉じた形で動作
- SharePointなどのアクセス権設定がそのまま適用
- 入力データはAI学習に使用されない（エンタープライズデータ保護）
- [Copilot Copyright Commitment](https://www.microsoft.com/ja-jp/licensing/news/microsoft-copilot-copyright-commitment)により、知的財産権侵害リスクはMicrosoftが法的責任を負う

#### ③ 品質向上への貢献

デンソーの事例では、設計部門においてCopilotから社内に蓄積されたデータを基に、これまで気づかなかった注意点などのアドバイスを得ることができ、設計品質の向上が図れた。

---

## 4. こんな時に使える（アプリ別活用シーン）

### Copilot Chat（汎用的な質問・調べもの）

| シーン | 使い方 | 効果 |
|--------|--------|------|
| 何か調べたい時 | 「〇〇について教えて」と質問 | Web検索＋組織データを統合して回答 |
| 社内情報を探したい時 | 「〇〇プロジェクトの資料はどこ？」 | SharePoint/OneDrive内を検索して回答 |
| ちょっとした相談 | 「この文章をもっとカジュアルにして」 | 簡単な推敲や言い換えに対応 |

### Teams（最も効果が出やすい機能）

| シーン | Copilotの使い方 | 効果 |
|--------|-----------------|------|
| 会議に遅刻した | 「これまでの内容は？」と質問 | 議論の流れを即座にキャッチアップ |
| 会議後の議事録作成 | 会議終了後に要約を生成→Wordにエクスポート | 議事録作成時間を大幅短縮 |
| 長いチャット履歴の確認 | 「このチャットの要点は？」と質問 | スレッドを読み返す時間を削減 |
| 会議室での対面会議 | Teams会議として接続しCopilotを有効化 | 対面会議でも自動議事録作成が可能 |

※前提条件：文字起こし（トランスクリプト）を有効化する必要あり

### Outlook（メール処理の効率化）

| シーン | Copilotの使い方 | 効果 |
|--------|-----------------|------|
| 長いメールスレッドの把握 | 「このスレッドを要約して」 | 経緯を素早く把握 |
| 返信文の作成 | 「丁寧なトーンで返信を作成して」 | メール作成時間を短縮 |
| 自分のメールの改善 | 下書きに対して「アドバイスをもらう」 | 送信前に品質チェック |

### Word（文書作成・推敲）

| シーン | Copilotの使い方 | 効果 |
|--------|-----------------|------|
| 報告書の草案作成 | 「〇〇プロジェクトの月次報告書を作成して」 | ゼロから書く手間を削減 |
| 文章が浮かばない時 | 書きかけの文章に対して「続きを書いて」 | ライターズブロックを解消 |
| 文章の品質向上 | 「読みやすく整えて」「フォーマルに書き換えて」 | 推敲時間を短縮 |

### Excel（データ分析・数式作成）

| シーン | Copilotの使い方 | 効果 |
|--------|-----------------|------|
| 数式エラーの解決 | エラーセルを選択し「このエラーを解説して」 | エラー原因の理解と修正方法の把握 |
| 複雑な集計式の作成 | 「部門別・月別の売上合計を計算して」 | 関数を調べる手間を削減 |
| 条件付き書式の設定 | 「目標未達の行を赤くハイライトして」 | 書式設定の手順を覚える必要なし |

### PowerPoint（プレゼン資料作成）

| シーン | Copilotの使い方 | 効果 |
|--------|-----------------|------|
| プレゼン資料の新規作成 | 「〇〇についてのプレゼンを作成して」 | 構成から考える手間を削減 |
| 発表準備 | 「このプレゼンの想定問答を作成して」 | 質疑応答への備えを効率化 |
| 海外向け資料の準備 | 「このプレゼンを英語に翻訳して」 | デザインを維持したまま40言語対応 |

---

## 5. エージェント活用ガイド

### エージェントとは

「エージェント」とは、**特定の目的に特化したAIアシスタント**のこと。通常のCopilotが汎用的な質問応答をするのに対し、エージェントは特定のタスクや業務領域に最適化されている。

| 概念 | 説明 | 例 |
|------|------|-----|
| **Copilot** | 汎用AIアシスタント | 「このメールを要約して」「資料を作って」 |
| **エージェント** | 特定目的に特化したAI | 「営業リードを育成するエージェント」「社内FAQ対応エージェント」 |

### なぜエージェントが重要か

1. **専門性**: 汎用AIより特定タスクの精度が高い
2. **効率性**: 毎回同じ指示を入力する手間が省ける
3. **一貫性**: 同じ基準で処理されるため品質が安定
4. **拡張性**: 外部システム（Salesforce、ServiceNow等）と連携可能

### エージェントの種類

| 種類 | 説明 | 作成方法 | 難易度 |
|------|------|----------|--------|
| **Microsoft製エージェント** | Microsoftが提供する汎用エージェント | 最初から利用可能 | ★☆☆ |
| **SharePointエージェント** | 特定のSharePointサイトの情報を参照 | SharePointサイトから数クリックで作成 | ★☆☆ |
| **定型業務エージェント** | よくやる作業をプロンプトごと保存して再利用 | Copilot Chatから作成 | ★★☆ |
| **カスタムエージェント** | 組織独自の業務に特化 | Copilot StudioまたはAgent Builderで作成 | ★★★ |
| **サードパーティエージェント** | ISVが提供するエージェント | エージェントストアから追加 | ★☆☆ |

---

### SharePointエージェント

SharePointサイトに蓄積された情報を参照して回答するエージェント。**数クリックで作成可能**で、最も手軽に始められる。

#### 作成手順

1. SharePointサイトを開く
2. 右上の「Copilot」アイコンをクリック
3. 「エージェントを作成」を選択
4. 参照するライブラリやフォルダを指定
5. 名前と説明を設定して保存

#### 活用例

| 用途 | 参照先 | 効果 |
|------|--------|------|
| プロジェクトFAQ | プロジェクトサイトの全ドキュメント | 新メンバーの質問対応を自動化 |
| 部署ナレッジ検索 | 部署のSharePointライブラリ | マニュアルや過去資料をAIで検索 |
| 製品情報回答 | 製品カタログ・仕様書フォルダ | 営業からの製品問い合わせに即答 |

#### ポイント

- エージェントはSharePointのアクセス権を継承するため、見せたくない情報が含まれるサイトでは注意
- 定期的に情報を更新しないと古い情報を回答する可能性あり

---

### 定型業務の再利用（プロンプトのエージェント化）

よく使うプロンプトをエージェントとして保存し、毎回同じ指示を入力する手間を省く。

#### 作成手順

1. Copilot Chatで定型業務のプロンプトを作成・テスト
2. 「このプロンプトをエージェントとして保存」を選択
3. 名前と説明を設定
4. 必要に応じて入力項目（変数）を設定
5. 保存してピン留め

#### 活用例

| エージェント名 | プロンプト内容 | 入力項目 |
|---------------|---------------|----------|
| 日英翻訳（ビジネス調） | 「以下の文章をビジネス英語に翻訳してください。丁寧すぎず、簡潔で明確な表現を使ってください。」 | 翻訳したい文章 |
| 議事録フォーマッター | 「以下の会議メモを、日付・参加者・議題・決定事項・アクションアイテムの形式に整理してください。」 | 会議メモ |
| メール返信下書き | 「以下のメールに対して、丁寧だが簡潔な返信を作成してください。相手の質問に明確に答え、次のアクションを提案してください。」 | 受信メール |
| 週次報告生成 | 「以下の作業ログから、今週の成果・課題・来週の予定をまとめた週次報告を作成してください。」 | 作業ログ |

#### ポイント

- プロンプトの品質がエージェントの品質を決める。最初にしっかりテストすること
- チームで共有すれば、品質の標準化にもつながる

---

### Microsoft製エージェント

Microsoftが提供する汎用エージェント。ライセンスがあれば追加設定なしで利用可能。

| エージェント名 | 機能 | GA状況 |
|---------------|------|--------|
| **Researcher** | 複雑な調査タスクを実行。競合分析や市場調査を自動化 | 2025年5月GA |
| **Analyst** | データ分析。o3-miniモデルによる推論でExcelデータを深堀り | 2025年5月GA |
| **Facilitator** | Teams会議の進行支援。議題管理・時間配分の自動化 | GA済 |
| **Surveys Agent** | アンケート作成・配信・分析を一貫して実行 | 2025年10月GA |
| **Employee Self-Service Agent** | HR/IT問い合わせへの自動回答 | 2025年11月GA |
| **People Agent** | 人物情報統合、スキル・協業者検索 | Frontier |
| **Learning Agent** | スキル開発・LinkedIn Learning連携 | Frontier |
| **Sales Development Agent** | 営業パイプライン自動化、リード育成 | Frontier |

参考：[Microsoft Copilot Studio](https://www.microsoft.com/ja-jp/microsoft-copilot/microsoft-copilot-studio)

---

### 自律型エージェント

2025年以降、Copilotのエージェントは「指示を受けて動く」だけでなく、**自律的にタスクを実行**できるようになった。

#### 従来型との違い

| 観点 | 従来のエージェント | 自律型エージェント |
|------|-------------------|-------------------|
| 起動方法 | ユーザーの指示を待って動作 | トリガー（時間・イベント）で自動起動 |
| タスク範囲 | 単一タスクを実行 | 複数ステップを計画・実行・検証 |
| 人の介在 | 人が結果を確認して次へ | 必要に応じて人に確認を求める |

#### 具体例：Sales Development Agent

1. **トリガー**: CRMで新規リードが登録される
2. **計画**: リードの業種・規模を分析し、アプローチ方法を決定
3. **実行**: パーソナライズされたフォローアップメールを作成・送信
4. **検証**: 開封率・返信率をモニタリングし、次のアクションを判断
5. **確認依頼**: 商談化の可能性が高いリードは営業担当に通知

#### 利用可能な自律型エージェント（2026年1月時点）

| エージェント | 機能 | 状況 |
|-------------|------|------|
| Sales Development Agent | リード育成・フォローアップ自動化 | Frontier |
| Workflows Agent | スケジュール/イベントベースの自動化 | Frontier |
| Copilot Studio自律エージェント | 独立動作するカスタムエージェント構築 | 2025年6月GA |

---

### エージェントの作り方

| 作成方法 | 難易度 | 向いているケース |
|----------|--------|-----------------|
| SharePointエージェント | ★☆☆ | 特定サイトの情報を参照するFAQ |
| Copilot Chatからプロンプト保存 | ★★☆ | 定型的なプロンプトの再利用 |
| Agent Builder（自然言語） | ★★☆ | コーディング不要でカスタムエージェント作成 |
| Copilot Studio | ★★★ | 外部システム連携、複雑なワークフロー |

#### Copilot Studioでの作成概要

1. [Copilot Studio](https://copilotstudio.microsoft.com/)にアクセス
2. 「新しいエージェント」を選択
3. エージェントの名前・説明・指示を設定
4. ナレッジソース（SharePoint、Dataverse等）を追加
5. トピック（会話フロー）を設計
6. 外部コネクタ（Salesforce、ServiceNow等）を接続（必要に応じて）
7. テスト・公開

参考：[Microsoft Copilot Studio](https://www.microsoft.com/ja-jp/microsoft-copilot/microsoft-copilot-studio)

---

## 6. 注意点・課題

### 情報整備が前提

AIが参照するデータが整理されていないと、古い情報や誤った情報をもとに成果物が作られる可能性。SharePointやOneDriveの情報整理が導入前の重要なステップ。

### 出力の確認は必要（ハルシネーション）

生成AIは時に、間違った情報をもっともらしく答えることがある（ハルシネーション）。これは現時点の生成AIでは避けられない制約であり、人の目による確認は避けられない。Copilotは「たたき台」を作成するものであり、最終的な品質保証は人間が行う必要がある。

### 定着施策が必須

導入しても現場で使われなければ投資が無駄になる。「社内で聞ける人がいる」「失敗しても大丈夫」という安心感を醸成し、人と仕組みの両面からのサポート体制を整えることが重要。

### コストの検討

月額約4,500円/人という価格は決して安価ではない。投資に見合う効果が得られるか、まずは一部の部署でスモールスタートし、具体的な業務での時間削減効果を測定した上で全社展開を検討することが現実的。

---

## 7. 部署内で活用を広げるポイント

### ① まずは自分が使ってみる

Copilotは「正解の型」があるツールではない。**1日1回はCopilotに話しかけてみる**、うまくいったことや失敗したことをメモしておく、といった小さな行動の積み重ねが、Copilotとの距離を縮める。

### ② ユースケース集の横展開

「何にどう使ったらいいのかわからない」という声に対応するため、利用事例集を整備し、プロンプトと回答例をコピー＆ペーストで使える形で提供することが効果的。

### ③ 成功事例の共有

デンソー、東芝、住友商事など成功企業はすべてパイロット導入から開始。IT部門や有志から始め、成功事例を作ってから全社展開するアプローチが有効。部署内でも同様に、まず数人が使い込んで「これは便利」という事例を作ることが重要。

### ④ 段階的な教育プログラム

学情では3か月間6回のトレーニングを実施し、各回200〜250名が参加。アプリケーションごとの活用方法を実業務に即した具体的なユースケースで説明することが重要。

### ⑤ トップダウンの支援

JCBでは社長メッセージを社員向けポータルで発信し、週次Tips配信との相乗効果で利用率向上を実現。経営層や部署長のコミットメントが定着の鍵。

### ⑥ 試行錯誤を楽しむ文化

うまくいったことや失敗したことをチームで共有する。「こんな風に使ったらうまくいった」「これは期待はずれだった」という情報交換が、チーム全体のスキルアップにつながる。

---

## 8. リリースチャネルと今後の機能

Microsoft 365 Copilotでは、新機能が段階的にリリースされる。管理者が各チャネルを有効化することで、最新機能を先行利用できる。

### リリース段階の種類

| 段階 | 説明 | 有効化場所 |
|------|------|-----------|
| **Private Preview** | 招待制。MSと契約した特定企業のみ | 招待のみ |
| **Public Preview** | 公開プレビュー。管理者有効化で利用可 | 機能により異なる |
| **Frontier** | Copilot専用の早期アクセスプログラム | M365管理センター > Copilot > 設定 > Copilot Frontier |
| **GA (General Availability)** | 正式リリース。テナントで利用可能に | 機能により異なる |

### GAでも管理者設定が必要な機能

**注意：GAになっても自動的に全員が使えるわけではない。** 以下の機能は管理者による有効化や設定が必要。

| 機能 | デフォルト状態 | 設定場所 |
|------|---------------|----------|
| Copilotライセンス自体 | 手動割当が必要 | M365管理センター > ライセンス |
| Web検索（Web grounding） | オン（無効化可能） | Cloud Policy / M365管理センター |
| 画像生成 | オフ（要有効化） | M365管理センター > Copilot > 設定 |
| Teams会議の文字起こし・要約 | オフ（要有効化） | Teams管理センター > 会議ポリシー |
| 外部LLMプロバイダー（Anthropic等） | オフ（要有効化） | M365管理センター > Copilot > 設定 > LLMプロバイダー |
| エージェントの利用許可 | 制限可能 | M365管理センター > Copilot > エージェント |
| Copilot Studioでのエージェント作成 | 要Power Platform設定 | Power Platform管理センター |

### 2025年にGAになった主要機能

| 機能 | GA時期 | 以前の状態 | 概要 |
|------|--------|-----------|------|
| M365 Copilotアプリ刷新 | 5月 | Preview | 新UI、ナビゲーション改善 |
| Copilot Pages | 5月 | Preview | AIとの共同作業キャンバス |
| Copilot Notebooks | 5月 | Preview | 長文コンテンツ生成・整理 |
| Create体験 | 5月 | Preview | 画像・デザイン生成機能 |
| **Researcher** | 5月30日 | Frontier | 深層リサーチエージェント（OpenAI deep research） |
| **Analyst** | 5月30日 | Frontier | データ分析エージェント（o3-mini推論） |
| DLP for Copilot | 6月 | Public Preview | 機密ラベル付きファイルのCopilot処理ブロック |
| Copilot Studio自律エージェント | 6月 | Preview | 独立動作するエージェント構築 |
| Harmful Content Protection | 9月 | Preview | 有害コンテンツ保護の管理者制御 |
| WhatsAppチャネル（Copilot Studio） | 9月 | Preview | WhatsAppへのエージェント展開 |
| Code Interpreter（Copilot Studio） | 9月 | Preview | Python実行機能 |
| Agent pinning | 10月 | Preview | 管理者がエージェントをユーザーに固定表示 |
| Surveys Agent | 10月 | Preview | アンケート作成・分析エージェント |
| Employee Self-Service Agent | 11月 | Preview | HR/IT問い合わせ対応エージェント |
| GPT-5 Chat（Copilot Studio） | 11月 | Preview | EU/US向けGPT-5モデル |
| **Agent Mode（Excel）** | 12月 | Frontier | 複数ステップのデータ処理自動化 |
| **GPT-5（Copilot Chat全体）** | 12月 | Frontier/Preview | デフォルトモデルがGPT-5に |

### 現在Frontierにある機能（2026年1月時点）

| 機能 | 概要 | 備考 |
|------|------|------|
| People Agent | 人物情報統合、スキル・協業者検索 | 2025年11月〜 |
| Learning Agent | スキル開発・LinkedIn Learning連携 | 2025年11月〜 |
| Workforce Insights Agent | 組織分析・リーダー向けインサイト | 2025年12月〜 |
| Sales Development Agent | 営業パイプライン自動化、リード育成 | 2025年12月〜 |
| Office Agents（Chat経由） | CopilotチャットからWord/Excel/PPT生成 | Anthropic Claude有効化必須 |
| App Builder | 自然言語でアプリ作成 | |
| Workflows Agent | スケジュール/イベントベース自動化 | 2025年10月〜 |
| Sora 2（Create） | AI動画生成 | |
| Project Opal | 次世代プロジェクト管理 | |
| Multi-tab Reasoning（Edge） | 複数タブを跨いだ推論 | Coming soon |
| GPT-Image-1.5 | 画像生成モデル強化版 | 2026年1月展開中 |
| Notebook動画サマリー | NotebookLM風の動画自動生成 | |

### 現在Public Previewにある機能（2026年1月時点）

| 機能 | 概要 | GA予定 |
|------|------|--------|
| Teams Mode | CopilotチャットをTeamsグループチャット化 | 未定 |
| Copilot in Outlook（音声） | 音声でメール/カレンダー操作 | 未定 |
| Action Segments | ユーザー行動ベースでターゲットメッセージ | 2026年3月 |
| Email delivery channel | 組織メッセージをメール配信 | 2026年3月 |
| Computer Use（Copilot Studio） | エージェントがUIを直接操作 | 米国のみ |
| Copilot Chat for Outlook拡張 | 受信トレイ全体＋カレンダー理解 | 2026年1〜3月 |
| Agent Mode（Copilot Chatユーザー向け） | ライセンスなしでもOffice Agent利用 | 2026年1〜3月 |
| Purview DLP for Copilot prompts | プロンプト内機密データをブロック | 未定 |
| AI Observability（DSPM） | 全エージェントの可視化 | 未定 |
| Agent 365 | エージェント統合管理プレーン | 未定 |

### Frontier有効化の注意点

Office Agents（Word/Excel/PowerPointエージェント）を利用するには、Frontier有効化に加えて**Anthropicモデル（Claude）の有効化が必須**。

- 設定場所: M365管理センター > Copilot > 設定 > LLMプロバイダー > Anthropic
- テナント全体への有効化が必要（個人/グループ単位では不可）
- Anthropicモデルで処理されるデータはMicrosoft管理外となる点に注意

参考：[Microsoft Adoption - Frontier Program](https://adoption.microsoft.com/ja-jp/copilot/frontier-program/)

---

## まとめ

Microsoft 365 Copilotは、Microsoft 365を業務基盤としている企業にとって、以下の理由から最適なAIアシスタントの選択肢：

1. **使い慣れたアプリ内で完結** — 新ツール学習コストゼロで即座に業務効率化を開始可能
2. **社内データとの連携** — SharePoint/OneDriveのファイルを自然に参照し、組織の文脈を理解した回答を生成
3. **エンタープライズセキュリティ** — 既存のM365セキュリティ設定を継承し、データがAI学習に使用されない
4. **Teams会議との統合** — 議事録作成の自動化で即効性があり、導入効果を実感しやすい
5. **拡張性** — Copilot Studioで業務特化のカスタムエージェント構築が可能

国内大手企業の事例が示すように、適切な導入・定着施策を講じることで、**月間10,000時間以上の業務時間削減、年間12億円規模のコスト削減**も実現可能。

---

## 出典・参考リンク

### Microsoft公式

- [Microsoft 365 Copilot 製品ページ](https://www.microsoft.com/ja-jp/microsoft-365/copilot/enterprise)
- [Microsoft Copilot Studio](https://www.microsoft.com/ja-jp/microsoft-copilot/microsoft-copilot-studio)
- [Copilot Copyright Commitment](https://www.microsoft.com/ja-jp/licensing/news/microsoft-copilot-copyright-commitment)
- [Microsoft Adoption - Frontier Program](https://adoption.microsoft.com/ja-jp/copilot/frontier-program/)

### 国内企業導入事例（Microsoft Customer Stories）

- [住友商事](https://customers.microsoft.com/ja-jp/story/1839340739329724-sumitomo-corporation-microsoft-copilot-for-microsoft-365-professional-services-ja-japan)
- [デンソー](https://customers.microsoft.com/ja-jp/story/1892831961143-denso-corporation-manufacturing-microsoft-365-copilot-ja-japan)
- [東芝](https://customers.microsoft.com/ja-jp/story/1824605500134070586-toshiba-discrete-manufacturing-microsoft-365-copilot-ja-japan)
- [JCB](https://customers.microsoft.com/ja-jp/story/1858630175736658656-jcb-banking-and-capital-markets-microsoft-365-copilot-ja-japan)
- [学情](https://customers.microsoft.com/ja-jp/story/1811604158453438567-gakujo-professional-services-microsoft-365-copilot-ja-japan)

### その他

- [住友商事「コスト削減効果は年間約12億」](https://www.sumitomocorp.com/ja/jp/enrich/contents/0095)
- [住友商事「AIとパワーナップから考える働き方の未来」](https://www.sumitomocorp.com/ja/jp/enrich/contents/0088)
- [日経クロステック](https://xtech.nikkei.com/atcl/nxt/column/18/03085/013000002/)
- [ITmedia](https://www.itmedia.co.jp/business/articles/2504/14/news001.html)
- [日経ビジネス Special](https://special.nikkeibp.co.jp/atclh/ONB/24/microsoft0628/)
- [yjk365「TeamsのMicrosoft 365 Copilotを使ってみた」](https://yjk365.jp/jirei/how-to-use-teamscopilot/)
- [Microsoft公式サポート - Teams会議でCopilotを使用する](https://support.microsoft.com/ja-jp/office/microsoft-teams-会議で-copilot-を使用する-0bf9dd3c-96f7-44e2-8bb8-790bedf066b1)

### 書籍

- 太田浩史『Microsoft 365 Copilot 踏み込み活用術』（インプレス、2026年1月）

---

*2025年1月作成 / 2026年1月更新（構成変更、エージェント活用ガイド拡充）*
