# NyanRAD IFDAM初稿

2026-10-27作成。UI工程の４つのWorkset候補に対応する、22 Interactionの検討用の部分集合。

- [プロジェクト](IFDAM-NYANRAD-001/review.md)
- [フォーム・イベント](IFDAM-NYANRAD-002/review.md)
- [処理・SQL・接続](IFDAM-NYANRAD-003/review.md)
- [実行確認](IFDAM-NYANRAD-004/review.md)

各フォルダに構造化JSON、Mermaidソース、同じデータから生成したSVG、確認用の表を保存した。JSONは正本のIFDAM Schemaに適合する。
[対応表](mapping.json)に図の行・Mermaidノード・構造化JSON位置・元資料Commitを対応づけた。正式なMapping Manifestではない。
[検証結果](validation.json)はSchema・ID・参照・対応表・SVG XMLの形式確認。画像としての表示検証、全操作の網羅性、意味の完全一致はまだ確認していない。

競合後の３選択、未保存実行の３選択、コピー・名称変更・行選択等の個別Interactionは補完が必要。既存実行ファイルによる常駐管理の技術成立、提供条件と正式な候補境界も未確定。
Schema適合を、要件承認・正式Baseline・引渡し可能・実装開始へ読み替えない。

Schema出典：kosaru/AI-powered-development の schemas/ifdam.schema.yaml、Blob 84b70d9377b467c28ab4aeecf620201446bb9876。コピーは検証のための固定参照でありプロセスの正本を変更しない。
