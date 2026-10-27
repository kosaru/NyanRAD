# プロジェクトを作成・再開する：IFDAM確認用初稿

![処理フロー](flow.svg)

| Interaction | 種別 | 条件 | 返す結果 |
|---|---|---|---|
| INT-NYANRAD-001-CREATE | normal | 作成先に既存ファイルがない | 作成したプロジェクトを表示する |
| INT-NYANRAD-001-OPEN | normal | 対象ソースを読み込める | 内容と再編集可能範囲を表示する |
| INT-NYANRAD-001-SAVE | normal | 競合がなく保存できる | 対象別の保存結果を表示する |
| INT-NYANRAD-001-CONFLICT | exception | 外部で対象が変更された | 差分と再読込・明示上書き・中止の選択を示す |
| INT-NYANRAD-001-SAVEFAIL | exception | 全部または一部の保存が失敗 | 未保存内容と失敗対象を保持して表示し新規実行を止める |
| INT-NYANRAD-001-EXISTS | exception | 作成先に既存ファイルがある | 生成せず別の場所・中止を示す |


UI工程のWorkset候補を使用。正式な境界・Baselineは未成立。図は同じ構造化データから生成したSVGとMermaidソースを併記。Schema適合と要件の承認は別。
各行の条件と結果、データ操作は検討用。競合の各選択や細かな編集操作等をすべて分解した完全なInteraction一覧ではない。次の範囲確認で補完する。
