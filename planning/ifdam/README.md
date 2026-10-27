# NyanRAD IFDAM初稿

４つの仕事について、正常・代替・例外を含む58 Interactionを整理した検討用の部分集合。

- [プロジェクト](IFDAM-NYANRAD-001/review.md)
- [フォーム・イベント](IFDAM-NYANRAD-002/review.md)
- [処理・SQL・接続](IFDAM-NYANRAD-003/review.md)
- [実行確認](IFDAM-NYANRAD-004/review.md)
- [要求・DB検証組合せとの網羅性確認](coverage-review.md)

各フォルダに構造化JSON、Mermaidソース、同じデータから生成したSVG、確認用の表を保存。
[対応表](mapping.json)は図の行・Mermaidノード・構造化JSON位置・元資料Commitを対応づける検討用の準備表。正式なMapping Manifestではない。
[検証結果](validation.json)はSchema・全IFDAM間のID一意性・参照・対応表・SVG XMLの確認。修正後の分割図７枚を目視し、凡例を追加した。55処理の表示文言をJSON・Mermaid・SVG・表で照合済み。元要件との意味の完全一致は未確認。

今回、フォーム追加・切替と既存要件のコピー・名称変更・保存失敗の不足を反映した。前回、新規作成の途中失敗、フォーム外へのはみ出し、削除Undo・保存後Undo・整列、保存失敗による実行中止、起動対象不足・ポート競合・ログ取得失敗を追加した。
SQLite・DuckDBと直接／Nyan8経由の４組は検証対象として記録し、実行は未実施。生成アプリの任意の業務画面をIDEの固定UIとして決めない。

すべての操作と例外の網羅性、Workset・正式Candidate境界、実行管理の技術成立、提供条件、承認用Snapshotは未確認・未成立。
Schema適合を要件承認・正式Baseline・引渡し可能・実装開始へ読み替えない。

Schema出典：kosaru/AI-powered-development の schemas/ifdam.schema.yaml、Blob 84b70d9377b467c28ab4aeecf620201446bb9876。コピーは検証用固定参照。

[照合・修正メモ](semantic-visual-review.md)。図は検討用に構造化データから生成したSVGであり、Mermaidから４図の一時生成を確認したが、承認用の可読性と追跡性の改善が必要。

各確認表の処理IDから、Mermaidで生成した処理単位の個別図を開ける。以前の55図について生成・XML解析と一覧画像での目視を実施。GitHubの代表１図は表示を確認したが、小さく表示された。残りのGitHub上の個別表示と詳細な可読性は未確認。詳細は[照合メモ](semantic-visual-review.md)。

[既存要件との意味の照合](requirements-semantic-audit.md)に、イベントの扱い、編集データ、履歴などの明示不足を記録。

[編集条件の補足](editing-conditions-review.md)に配置・履歴・手書き保護・編集中データの既存方針と残る未表現の流れを整理。

フォームLoad・イベント引数・手書き本文編集を独立した流れとして追加。002の管理結線と手書き本文を分けて図・対応表を更新した。更新した個別図21枚は生成・XML確認、うち５枚と全体図の３ページ目を目視。全体図のQuick Lookプレビューは一部右側が見切れたため、表示環境での全域確認が必要。元要件の完全な意味確認と技術実証は未完了。
