# 既存要件とIFDAMの意味の照合（作業中）

対象Commit：`2ec69f3039ad71f9ff3b4e446c3053045d4338ca`。人間が既に了承した方針と55件のIFDAM初稿を比較した。記載があることと、条件・結果・例外まで完全に表現されていることは分けて扱う。要件の新規採用・正式承認ではない。

| 既存の方針 | IFDAMで確認できる対応 | 追加確認・同期が必要なこと |
|---|---|---|
| 保存競合時に差分を示し、再読込・明示上書き・中止を選ぶ | 001 CONFLICT／RELOAD／OVERWRITE／CANCEL／RECHECK | 他の保存・切替時との整合と全例外の網羅 |
| 未保存時の実行と部分保存 | 004 UNSAVED／RUNSAVE／RUNSAVED／RUNCANCEL／RUNSAVEFAIL／BLOCK、001 SAVEFAIL | 部分保存の解消条件と実際の実行管理能力は未実証 |
| コピー・名称変更・削除と手書き本文 | 002 COPY／RENAME／DELETE／UNDODELETE | 002のデータは「イベント対応・手書き本文」をまとめており、名前変更・削除でUを示すだけでは管理結線の変更と本文を保持する範囲が図から区別しにくい。データ表現と図を明確にする |
| 配置・不正値・はみ出し | 002 EDIT／INVALID／CLIP | 整数CSSピクセル、座標0以上、幅・高さ1以上の具体条件は個別図・確認表に明示されず、統合要件と併読が必要。対象部品ごとの詳細も未整理 |
| Undo／Redoと履歴 | 002 UNDO／UNDODELETE／UNDOAFTERSAVE／ALIGN | 図だけではコード履歴との分離、同一セッションで保存後も履歴を保持し、再読込・プロジェクト切替で区切る条件を追いきれない |
| フォームとイベント | 002 FORMADD／FORMSWITCH／EVENT | フォームLoadをDOM・IDE管理の結線が利用可能になった後に一度呼ぶ方針と、明示的なイベント引数の方針は個別Interactionから明確に追えない。手書き本文を編集する操作もEVENTの「開く」だけでは直接示されない。署名・値型を新たに決めずに同期する |
| 一覧表の行選択 | 002 ROWKEY／ROWINDEX／ROWDUP／ROWRELOAD | 取得する行データ、行キーと再読込の範囲が要求どおりか、関連画面の具体化時に再確認 |
| サーバー・SQL・接続編集 | 003 OPEN／EDIT／ERROR | 元の通常ソースは読み取り、編集中の本文は編集状態に保持する解釈が可能だが、003の「編集状態」の説明が抽象的で、元資料の現在の本文・設定を含むことが図から分かりにくい。保存済みファイルへの直接書換えと区別して明確化する |
| 起動・停止・不明状態・ログ | 004 START／PARTIAL／STOP／UNKNOWN／STOPFAIL／LOG／CLEAR／LOGFAIL | 一部起動失敗時の停止対象、状態不明の扱い、ログの省略等は記載。実行管理・ログ取得の成立は別途実証 |
| 両DB・両接続、IDE外利用 | 003 EDIT、004 START／EXPORT | ４組の基本CRUDとIDE外利用は未実施。生成アプリの任意画面をIDEの固定UIとして追加しない |

参照：[統合要件](../requirements/20-consolidated-requirements.md)、[機能](../requirements/09-functions.md)、[データ](../requirements/10-data.md)、[編集細目](../requirements/13-editing-details.md)、[操作の決定](../requirements/22-operation-decisions.md)、[受入条件案](../requirements/18-acceptance-criteria.md)、[網羅性確認](coverage-review.md)。

次は、上記の明示不足を既存合意と資料の範囲で同期し、表・構造化資料・Mermaid・図・対応表の整合性を再確認する。未決定のイベント署名や提供条件、技術成立を推測で確定しない。
