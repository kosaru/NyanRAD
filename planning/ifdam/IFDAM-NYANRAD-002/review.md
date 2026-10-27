# フォームと画面イベントを編集する：IFDAM確認用初稿

![処理フロー](flow.svg)

| Interaction | 種別 | 条件 | 返す結果 |
|---|---|---|---|
| INT-NYANRAD-002-EDIT | normal | 入力が有効 | 変更と未保存状態を表示する |
| INT-NYANRAD-002-EVENT | normal | 対象イベントを選択 | 既存本文または初回の雛形を開く |
| INT-NYANRAD-002-DELETE | normal | 対象部品を選択 | 部品を削除し手書き本文を保持する |
| INT-NYANRAD-002-UNDO | normal | 対象操作の履歴がある | 編集状態を更新し保存済みファイルは自動巻戻ししない |
| INT-NYANRAD-002-INVALID | exception | 名前重複・規則違反・不正な座標等 | 以前の値を保持し理由を表示する |
| INT-NYANRAD-002-UNSUPPORTED | alternative | 非対応または解析できない表現がある | ソースを保持し編集制限の範囲と理由を示す |


UI工程のWorkset候補を使用。正式な境界・Baselineは未成立。図は同じ構造化データから生成したSVGとMermaidソースを併記。Schema適合と要件の承認は別。
各行の条件と結果、データ操作は検討用。競合の各選択や細かな編集操作等をすべて分解した完全なInteraction一覧ではない。次の範囲確認で補完する。
