# 正式候補の準備状況

確認日：2026-11-20。起点Commit：`c4412b38ff2f479b62174d551739a033c3a35d57`。これは準備状況の点検であり、正式なCandidate Manifestではない。

| 条件 | 現在の証拠・残り |
|---|---|
| 目的・利用上の主要方針 | [統合確認資料](20-consolidated-requirements.md)と判断履歴に記録。受入条件全体は未承認 |
| 対応環境 | macOSローカルは確認済み。CPUの範囲は[判断材料](26-macos-scope-decision.md)、最低OS版・ブラウザーと実行ファイル版は未固定 |
| UI・機能・データ・IFDAM | 初稿はある。データの作成元と仕事間の対応について[確認事項](../ifdam/data-provenance-review.md)が残る |
| 人間向け確認資料と構造化資料 | 個別図と確認表はあるが、条件の一部が補足に分かれる。[文言上の差](../ifdam/data-provenance-review.md)と条件・例外の意味確認、画像の再確認が残る |
| Mappingと固定Snapshot | 検討用の索引・対応表はあるが、正式Mapping・承認用Snapshotは未完成 |
| 技術の成立 | 実行管理、競合保存、両DBと両接続、IDE外実行は未実証。未実証を成功または受け入れたリスクと扱わない |
| 正式Baseline・引渡し | Candidate Package、人間の正式判断、正確なRequirement Commitと成立記録、Work Requestは未成立 |

提供対象の判断を受けても、上記の未完了事項が自動的に完了するわけではない。実装を開始する正式な入力はまだ成立していない。
