# Google Workspaceのチーム運用事例集

更新：2026-11-26（JST）

Google Workspaceでチームの知識を集め、作業を管理し、LLMが参照しやすくするための公開事例集です。AIエージェントを置かずに始められる部分を優先しますが、追加ツールや許可が必要な事例も、参考になる手順があれば収録します。事例に登場する構成と、ここで提案する小さな試し方は別です。

## 優先テーマ：Geminiとチームが同じ前提で仕事をする

手順書を検索できるだけでは、今の仕事をGeminiに任せられない。必要なのは、**チームの目的と制約、案件の現在地、判断した理由**を、別の担当者が開いた新しいチャットでも渡せること。個人のチャット履歴をチームの正本にしない。

- **チームの前提（Docs）**：なぜこの業務をするか、誰がどこまで判断するか、優先順位、変更できない制約。
- **動いている案件（Sheets）**：いまの状態、担当、未解決の論点と必要な情報、次の行動。既存の台帳を使い、Gemini用の進捗表は別に作らない。
- **前提が変わった記録（Docsまたは台帳のリンク先）**：いつ・何を決めたか、なぜか、何が変われば見直すか。会議やチャットからは確定した内容と必要な保留事項だけを戻す。

**実務の参考：** [Attache](https://workspace.google.com/blog/customer-stories/attache-transforming-menial-magical-gemini-google-workspace?hl=en)では、会議の議題をもとに、Geminiでフォローアップや作業事項を残すための型を作った。これは情報を残す入口の事例で、チーム単位で新しいチャットに継続的な文脈を渡せたことまで示すものではない。

**検証案：** 架空の案件1件で、チームの前提・台帳・判断記録を用意する。別の担当者が経緯を口頭で補足せず、新しいGeminiチャットで「今の優先事項は何か、なぜその順か、次に誰が何を確認するか」を聞く。元資料を示せるか、不足を言えるか、台帳の状態を変えた後に旧版と取り違えないかを見る。最初は資料を明示して試す。共有Gemは共通指示を渡す比較候補で、利用可否と添付資料の権限は別に確認する。[共有Gemの仕様](https://support.google.com/gemini/answer/16504957?hl=en)

## 1. チームのコンテキストを集めて更新する

| 公開事例 | 実際の運用 | そのまま使わずに取り入れる点 |
| --- | --- | --- |
| [HK01](https://workspace.google.com/customers/hk01/) | エンジニアリング部門がDriveの社内手順書をSitesから探せるようにした。申請処理にはJiraとSlackも利用。 | Sitesは入口にし、手順書の正本はチームのDriveに置く。申請ツールは別の判断。 |
| [GlobalLogic](https://cloud.google.com/customers/globallogic) | 散在した技術資料を社内ポータルに集め、チームが新しい案件の計画段階で既存の解決策を探す。ポータル全体はSitesに加えてGoogle Cloud等を使用。 | 新しい作業を始める前に「同じ問題の過去例」を調べる。高度な検索や自動タグ付けは前提にしない。 |
| [Google SRE](https://sre.google/workbook/postmortem-culture/) | 振り返りをDocsの共通様式にまとめ、フォローアップの担当を明確にする。公開された例は障害対応の運用。 | 記録の責任者と、各対応項目の担当を区別する。障害対応の規模や公開範囲はそのまま真似しない。 |

**最小運用の案：** Sitesから「手順」「判断記録」「対応中」へリンクする。作業完了時に再利用できる発見、方針決定時に理由と根拠、手順変更時に正本の改訂を残す。例えば判断記録は「日付／何を決めた／なぜ／根拠／担当／何が変わったら見直す」の6項目。記録の有効性は別の人がSitesから探し、同じ判断の理由までたどれるかで確かめる。新しい定例は作らず、既存の定例で更新が必要なものだけを見る。[共有ドライブの仕様](https://support.google.com/a/users/answer/7212025)・[判断記録の書き方](https://docs.cloud.google.com/architecture/architecture-decision-records)

## 2. LLMが参照しやすい正本を作る

- [リーフラス](https://workspace.google.com/blog/ja/customer-stories/generative-ai-paving-the-way-for-regional-futures?hl=ja)：過去の練習メニューをNotebookLMで再利用し、指導員が新しいメニューを考える際に利用。
- [Docusign](https://workspace.google.com/blog/customer-stories/docusign-rapidly-scales-its-ai-strategy-by-enabling-its-global-workforce-with-gemini)：Driveを資料の中心に据え、良い回答例を集めてGeminiの指示を改善。

**最小検証の案：** 承認済みの手順書2〜3本を用意し、冒頭に対象・適用範囲・更新日・担当をそろえる。本文は通常手順、例外、判断例と根拠。許可された組織内LLMで、根拠のある質問と、情報不足で結論が出せない質問を各1件聞く。現行版を引用できるか、推測を断定しないか、旧版に差し替えたときに違いを判別できるかを見る。権限・更新反映は実際の利用者ごとに確認する。[Notebookの資料仕様](https://support.google.com/gemininotebook/answer/16215270?hl=en)・[Geminiのデータ参照条件](https://support.google.com/a/users/answer/17010577)

## 3. Issueに相当する作業を管理する

- [グッデイ](https://workspace.google.com/blog/ja/customer-stories/google-google-2017-01?hl=ja)：各店舗の入力をForms、集計をSheetsに分け、個別Excelの取りまとめを省いた事例。
- [マルトノマ郡](https://workspace.google.com/customers/multnomah-county/)：Formsから入った案件をSheetsへ集め、対応が必要なものを絞り込む。通知も使うが、その部分は初回の前提にしない。

**試作：** [Issue台帳の作り方と架空データ](../experiments/01-issue-tracker/README.md)。ID、担当、期限、状態、次の行動、根拠を1行で管理する。台帳を直接編集しない人から起票が必要ならFormsを足す。GitHub Issuesのコメントスレッドや細かな権限・監査まで、同じようにできるという意味ではない。

## 4. LLMに一工程を任せる候補

人が資料と対象範囲を指定し、LLMに一次分類・根拠・追加確認事項を案出しさせ、人が確定する。公開アドバイザリと架空の機器表なら「対象と版が確定」「製品名は合うが版が不明」「名称が似た別製品」を並べ、どこで保留すべきかを見る。自動通知・自動確定は対象外。これは試作案であり、導入済みの事例ではない。

## 5. Excel出力を人の仕上げに近づける候補

[フードハブ・プロジェクト](https://workspace.google.com/blog/ja/customer-stories/generative-ai-paving-the-way-for-regional-futures?hl=ja)はGeminiをSheetsの関数処理や献立の分析に利用。Excelでの表示・印刷品質が確認された事例ではない。

**試し方：** 完成見本1枚をもとに、書式・式・印刷範囲はテンプレートとして固定し、LLMには入力セルの値だけ出させる。同じ架空データで、数式・値、日付やゼロの表示、折り返し・改ページ、Excelで開いた結果、手直し時間を人の作成物と比べる。[Gemini in Sheetsの仕様](https://support.google.com/docs/answer/14356410)

## 利用前の確認

- 導入可否を確認する前でも、事例と必要条件は収録する。記事だけで自組織の契約・管理者設定・個別権限を確認済みとはしない。
- 手順を試すなら1業務・2人・1週間を目安に、起票→担当→判断と根拠の記録→別の人または許可されたLLMが根拠を探す、まで1回通す。
- 本ページは公開事例・一般手順・架空データのみ。公開リポジトリは閲覧・ダウンロード用で、利用先の情報・検証ログ・実データは載せない。
