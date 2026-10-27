# IFDAM と要件資料の参照整理

確認対象：NyanRAD の Commit `ec00ea33ff5cab9708141ca2677217a0fa326750`。状態：検討用。正式なMapping ManifestやSnapshotではない。

## 今回の確認

| 対象 | 処理数 |
|---|---:|
| プロジェクト | 16 |
| フォーム・イベント | 21 |
| 処理・SQL・接続 | 3 |
| 実行確認 | 18 |
| 合計 | 58 |

58処理について、構造化資料と確認表・処理単位のMermaidのID、開始・終了画面、イベント、機能、データとCRUD、結果の対応を点検した。既存の対応表は各処理の元資料とCommitを示すが、元資料内の参照箇所を特定していなかった。

[要件参照索引](source-index.json)に各処理から辿れる関連節を追加し、[検討用対応表](mapping.json)から参照できるようにした。105件の参照について、固定した上記Commitに対象ファイル・節・指定した行の目印が存在することを確認した。関連節は確認を始めるための入口であり、単独で条件・結果の全てを裏付ける証拠ではない。従来の元資料Commitの参照も維持している。

例として、コピー・Undo・イベント等は[編集操作の細目](https://github.com/kosaru/NyanRAD/blob/ec00ea33ff5cab9708141ca2677217a0fa326750/planning/requirements/13-editing-details.md)、実行・停止は[実行管理の方針](https://github.com/kosaru/NyanRAD/blob/ec00ea33ff5cab9708141ca2677217a0fa326750/planning/requirements/16-run-lifecycle.md)、イベント雛形は[選択肢とA案](https://github.com/kosaru/NyanRAD/blob/ec00ea33ff5cab9708141ca2677217a0fa326750/planning/requirements/24-event-handler-options.md)を参照する。

## 残る確認

- 各操作の条件・結果・例外が、人間向け要件の意味を過不足なく表しているか、参照先を使って確認する。
- SVGの今回の表示や全ての意味の一致は、この参照先の存在確認だけでは確認できない。
- 正式なMapping Manifest、固定Snapshot、Candidateの範囲と不足を整える。実行管理・DBの技術実証も未完了。
- 正式BaselineおよびWork Requestは未成立であり、実装着手を意味しない。
