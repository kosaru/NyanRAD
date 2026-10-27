# IFDAMで確認する編集条件（検討用）

既存の人間向け要件に記載された条件を、関連する処理へ対応づけた補足。図の短い表示だけで判断せず、この表と各確認表を併せて確認する。既存合意を新たな正式Baselineへ変更したものではない。

| 対象 | 関連する既存の方針 | 確認先 |
|---|---|---|
| 配置・不正値 | 位置と寸法は整数CSSピクセル。位置は0以上、幅・高さは1以上。不正値は以前の値を保ち理由を示す | [002 EDIT・INVALID](IFDAM-NYANRAD-002/review.md)、[操作上の決定](../requirements/22-operation-decisions.md) |
| Undo・Redo・履歴 | 配置等の履歴とコード編集の履歴は分ける。同じ編集セッションの保存後も履歴を保持し、再読込・プロジェクト切替で区切る。保存済みファイルは自動で巻き戻さない | [002 UNDO・UNDOAFTERSAVE](IFDAM-NYANRAD-002/review.md)、[編集細目](../requirements/13-editing-details.md) |
| 名前変更・削除・削除Undo | 管理対象の識別・CSS・結線の変更と、手書き本文の保持を区別する。名前変更では手書き本文への参照の影響を示す。削除Undoで本文を二重生成しない | [002 RENAME・DELETE・UNDODELETE](IFDAM-NYANRAD-002/review.md)、[編集細目](../requirements/13-editing-details.md) |
| サーバー処理・SQL・設定の編集 | 元の保存済みソースと、編集中の本文・設定・変更状態を区別する。編集の表示自体を保存済みファイルの書換えと扱わない | [003 EDIT](IFDAM-NYANRAD-003/review.md)、[データ検討](../requirements/10-data.md) |

## 追加した流れと残る確認

[002 CODEEDIT](IFDAM-NYANRAD-002/diagrams/19.svg)はIDE上の手書き本文の編集、[002 FORMLOAD](IFDAM-NYANRAD-002/diagrams/20.svg)と[002 EVENTARGS](IFDAM-NYANRAD-002/diagrams/21.svg)は生成アプリの実行時の流れとして整理した。LoadはDOMとIDE管理の結線が利用可能になった後に一度呼ぶ。イベント引数の具体的な署名・値型は引き続き未決定。

構造化データと図では、IDE管理のイベント対応・結線と手書きイベント処理本文を分け、名前変更・削除・Undoのデータ操作から区別できるようにした。編集時の本文更新は保存済みファイルへの書込みを意味しない。イベント処理の初回雛形を開く場合に、どの段階で何を作成するかは整理が必要。

図と表の内容は検討用。全図の表示確認、元要件と主要例外の意味一致、技術成立、人間の確認は残る。正式な承認、Baseline、実装開始は未成立。
