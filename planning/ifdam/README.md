# NyanRAD IFDAM初稿

2026-10-27更新。UI工程の４つのWorkset候補について、正常・代替・例外を含む43 Interactionを整理した検討用の部分集合。

- [プロジェクト](IFDAM-NYANRAD-001/review.md)
- [フォーム・イベント](IFDAM-NYANRAD-002/review.md)
- [処理・SQL・接続](IFDAM-NYANRAD-003/review.md)
- [実行確認](IFDAM-NYANRAD-004/review.md)

各フォルダに構造化JSON、Mermaidソース、同じ構造化データから生成したSVG、確認用の表を保存。
[対応表](mapping.json)に図の行・Mermaidノード・構造化JSON位置・元資料Commitを対応づけた。正式なMapping Manifestではない。
[検証結果](validation.json)はSchema・全IFDAM間のID一意性・内部参照・対応表・SVG XMLの形式確認を記録。Quick Lookで４図の画像生成を確認し、004・003はプレビューの一部を目視した。全領域の目視と意味の完全一致は未確認。

今回、競合後の３選択と再変更、未保存の切替・実行の選択、コピー・名称変更・一覧表の行選択・ログ表示クリア等を追加。
すべての操作と例外の網羅性、Workset・正式Candidate境界、実行管理の技術成立、提供条件、承認用Snapshotはまだ確認・成立していない。
Schema適合を要件承認・正式Baseline・引渡し可能・実装開始へ読み替えない。

Schema出典：kosaru/AI-powered-development の schemas/ifdam.schema.yaml、Blob 84b70d9377b467c28ab4aeecf620201446bb9876。コピーは検証用固定参照。
