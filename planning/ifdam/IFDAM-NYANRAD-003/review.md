# サーバー処理・SQLと接続を編集する：IFDAM確認用初稿

![処理フロー 1/1](flow-01.svg)

[全体図](flow.svg)（分割図の重複行は見切れ防止のため）

各処理のIDを選ぶと、開始画面・操作・機能・データ・結果・終了画面を示す個別図を開けます。条件は下表をご覧ください。

| Interaction | 種別 | 条件 | 返す結果 |
|---|---|---|---|
| [INT-NYANRAD-003-OPEN](diagrams/01.svg) | normal | 対象を読み込める | 製品・実行場所・ソースを表示する |
| [INT-NYANRAD-003-EDIT](diagrams/02.svg) | normal | 編集可能な対象を開いている | 編集内容と未保存状態を表示する |
| [INT-NYANRAD-003-ERROR](diagrams/03.svg) | exception | 設定不正・非対応表現等 | 対象と問題を示し元ソースを保持する |

検討中の部分集合。未実証の技術成立や提供条件を含み、正式候補・Baseline・実装開始は未成立。DB動作やIDE外実行の検証組合せは[網羅性確認表](../coverage-review.md)で追跡。

関連する既存の編集条件・データの区別は[編集条件の補足](../editing-conditions-review.md)を参照。フォームLoad等の未表現の流れも同補足で追跡する。
