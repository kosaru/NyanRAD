# NyanRAD IFDAMと要求の網羅性確認（初稿）

確認日：2026-10-27／確認元Commit：`1157fd02b0012b31f0383af3d9c5919b8b9e920a`

要求一覧・受入条件とIFDAMを照合し、43件へ10件の正常・代替・例外を補足した。
「対応あり」は処理の記載があるという意味であり、実装・テスト成功、仕様の詳細確定、正式承認を示さない。

## 要求一覧との対応

| 要求 | 対応箇所・確認結果 | 残る確認 |
|---|---|---|
| 01 ブラウザIDE | 全Worksetの画面と操作 | 動作環境・提供条件は未固定 |
| 02 通常ソース | 001 OPEN／SAVE、004 EXPORT | 出力方式・対応版の実証 |
| 03 macOSローカル | 004実行確認の前提 | 最低OS版・CPU・ブラウザ・実行ファイル版 |
| 04 プロジェクト | 001 CREATE／OPEN／SAVEと既存・失敗・競合 | 途中失敗の復旧手順と技術成立 |
| 05 フォーム | 002 FORMADD／FORMSWITCH／EDITとプロジェクト読込 | 名称変更の詳細と各操作の分岐 |
| 06 部品配置 | 002 EDIT／INVALID／CLIP／ALIGN | 部品種類ごとの表示・操作詳細 |
| 07 プロパティ・Undo | 002 EDIT／UNDO／UNDODELETE／UNDOAFTERSAVE | 保存後のRedo等の詳細確認 |
| 08 イベント | 002 EVENT／COPY／RENAME／DELETE | Load等の対象別イベントと引数の扱い |
| 09 Nyan8 | 003 OPEN／EDIT／ERROR | 処理・API設定ごとの条件と検証 |
| 10 NyanQLのSQL・設定 | 003 OPEN／EDIT／ERROR | SQL・DB設定と実行結果の個別確認 |
| 11 両接続 | 003 EDIT、004 START | 直接／Nyan8経由の検証証拠。生成アプリの動的な画面を固定UIとして扱わない |
| 12 SQLite・DuckDB | 003 EDIT、004 START | 両DB・両経路・CRUDの検証組合せが未実行 |
| 13 実行・停止 | 004 START／STOP／RESTART等 | プロセス管理の技術成立が未実証 |
| 14 ログ・エラー | 004 LOG／CLEAR／LOGFAIL等 | ログの取得上限・保持方式と実証 |
| 15 手書き保護・再編集 | 001競合分岐、002 COPY／RENAME／DELETE／UNSUPPORTED | 対応構文・参照検出限界・部分保存整合 |
| 16 IDE外利用 | 004 EXPORT | 対応実行ファイルで実際に実行できる証拠 |

## DBと接続の検証組合せ

| DB | 直接接続 | Nyan8経由 |
|---|---|---|
| SQLite（既定） | 基本CRUD・接続失敗・不正SQLを確認予定 | 基本CRUD・接続失敗・不正SQLを確認予定 |
| DuckDB | 基本CRUD・接続失敗・不正SQLを確認予定 | 基本CRUD・接続失敗・不正SQLを確認予定 |

４組すべて未実施。各CRUDの入力・実データ・結果は後の正式なテストで具体化する。
同じSQL・同じDBファイルを両製品で使えるという保証は追加しない。
生成アプリの任意の業務画面を、NyanRAD固定の画面仕様として勝手に定義しない。

## 表示・形式の確認

構造化IFDAM４件、53 Interactionについて、Schema、IDの一意性、参照、対応表のJSON位置、Mermaidノード、SVG XMLを検証。
SVGをQuick Lookで画像生成し、プレビューを確認する。サムネイルは大きい図の一部を切るため、全領域の目視を完了したとは扱わない。
図・表・JSONは同一データから生成したが、技術的生成の一致と、人間が要件の意味を確認したことは区別する。

## 残る正式資料の作業

図の全領域の可読性、全ての要件・主要例外の追跡、部分保存の整合条件、イベントの利用上の詳細、提供条件を確認する。
Workset・IFDAM・Interactionの最終境界、人間向け固定Snapshot、正式Mapping、Schema以外の意味一致検証をそろえる。
技術成立T03と提供条件P01〜P03を管理し、Blockingな不明を放置して正式Candidate完成とはしない。
この表はレビューの初稿。正式な受入・Baseline・実装開始ではない。

参照：[要求一覧](../requirements/05-requirements-list.md)、[受入条件](../requirements/18-acceptance-criteria.md)、[IFDAM一覧](README.md)

## 追記：同期修正後

フォーム追加・切替を追加し、全体は55 Interactionとなった。旧版の分割図７枚は全領域を目視したが、修正版の画像表示確認、Mermaidからの正式レンダリングおよび意味の完全一致は未完了。[照合・修正メモ](semantic-visual-review.md)参照。

## 追記：修正後の表示と表現の確認

修正後の７分割図を目視し、図の凡例の欠落を修正。55処理のJSON・Mermaid・SVG・表の対応文言を照合して差分なし。Mermaidから４図を一時生成したが、横幅・Interaction ID・種別・終了Interfaceの表示が承認用の課題として残る。これは要求と例外の網羅性の完了や技術的な動作実証を意味しない。[照合メモ](semantic-visual-review.md)参照。
