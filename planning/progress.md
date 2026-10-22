# NyanRAD 進捗一覧

最終更新：2026-10-22

## 現在地

構想整理中（DR-NYANRAD-001：exploring）。NyanQL群をVB6のように使う目的、ソースコードを生成物とする前提、直接接続とNyan8経由、内蔵DBを使う方向を記録済み。

## 追跡する作業

| 作業 | 状態 | 記録 |
|---|---|---|
| 初期構想・判断の保存 | 完了 | [議論の整理](requests/DR-NYANRAD-001/discussion-summary.md)、[判断履歴](requests/DR-NYANRAD-001/decision-log.md) |
| VB6とNyanQL群の対応調査 | 比較資料作成済み | [対応資料](requests/DR-NYANRAD-001/vb6-nyan-mapping.md) |
| 初期範囲・対象外の比較と着手判断材料 | 次の作業 | [Issue #2](https://github.com/kosaru/NyanRAD/issues/2) |
| 人間向け要件定義 | 未着手 | 着手判断後、正本の工程順に進める |
| 正式Baseline・実装引渡し | 未着手 | 要件定義と正式判断の後 |
| 設計・実装・テスト・内部レビュー | 未着手 | 正式なWork Requestの後 |
| 初回正式リリース | 未着手 | 人間の正式受入の後 |

全体の追跡：[Issue #1](https://github.com/kosaru/NyanRAD/issues/1)

## 次に進める内容

VB6を手本に、プロジェクト作成、画面配置、プロパティ・イベント編集、Nyan8／NyanQLとの接続、実行、保存・再編集の一巡を初期範囲案として比較する。
初期範囲と対象外は提案として示し、未決定事項を明記して人間の判断材料にする。

## 更新方法

- 作業開始時にIssueへ目的、次の作業、完了条件を記録する。
- まとまった作業が終わったら、成果物・Commit・PR・確認結果と残る作業をIssueと本一覧へ反映する。
- 判断待ちの場合は、判断対象と影響する作業を明示する。
- 正式な要件・Gate・Release等の状態は、それぞれの正式記録へリンクする。
- 手順の正本は[kosaru/AI-powered-development](https://github.com/kosaru/AI-powered-development)。本一覧は進捗の入口とする。

## 作業履歴

- 2026-10-22：既存記録を確認し、全体追跡Issueと次の作業Issue、進捗一覧を作成。資料の既存状態はCommit `5efc52027aa263c16b0e23ba6208166943819223`で確認。
