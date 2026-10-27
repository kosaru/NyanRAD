# NyanRAD IFDAM初稿

４つの仕事について、正常・代替・例外を含む55 Interactionを整理した検討用の部分集合。

- [プロジェクト](IFDAM-NYANRAD-001/review.md)
- [フォーム・イベント](IFDAM-NYANRAD-002/review.md)
- [処理・SQL・接続](IFDAM-NYANRAD-003/review.md)
- [実行確認](IFDAM-NYANRAD-004/review.md)
- [要求・DB検証組合せとの網羅性確認](coverage-review.md)

各フォルダに構造化JSON、Mermaidソース、同じデータから生成したSVG、確認用の表を保存。
[対応表](mapping.json)は図の行・Mermaidノード・構造化JSON位置・元資料Commitを対応づける検討用の準備表。正式なMapping Manifestではない。
[検証結果](validation.json)はSchema・全IFDAM間のID一意性・参照・対応表・SVG XMLの確認。旧版の分割図７枚は全範囲を目視した。今回修正した図の画像表示と意味の完全一致は未確認。

今回、フォーム追加・切替と既存要件のコピー・名称変更・保存失敗の不足を反映した。前回、新規作成の途中失敗、フォーム外へのはみ出し、削除Undo・保存後Undo・整列、保存失敗による実行中止、起動対象不足・ポート競合・ログ取得失敗を追加した。
SQLite・DuckDBと直接／Nyan8経由の４組は検証対象として記録し、実行は未実施。生成アプリの任意の業務画面をIDEの固定UIとして決めない。

すべての操作と例外の網羅性、Workset・正式Candidate境界、実行管理の技術成立、提供条件、承認用Snapshotは未確認・未成立。
Schema適合を要件承認・正式Baseline・引渡し可能・実装開始へ読み替えない。

Schema出典：kosaru/AI-powered-development の schemas/ifdam.schema.yaml、Blob 84b70d9377b467c28ab4aeecf620201446bb9876。コピーは検証用固定参照。

[照合・修正メモ](semantic-visual-review.md)。図は検討用に構造化データから生成したSVGであり、Mermaidからの正式レンダリングは未確認。
