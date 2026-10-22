# NyanRAD 進捗一覧

最終更新：2026-10-22

## 現在地

要件定義着手済み（DR-NYANRAD-001：approved-for-requirements）。「要件定義、その前に」を記録し、「企画を確認する」の初稿を作成。NyanQL群をVB6のように使う目的、ソースコードを生成物とする前提、直接接続とNyan8経由、内蔵DBを使う方向を記録済み。

## 追跡する作業

| 作業 | 状態 | 記録 |
|---|---|---|
| 初期構想・判断の保存 | 完了 | [議論の整理](requests/DR-NYANRAD-001/discussion-summary.md)、[判断履歴](requests/DR-NYANRAD-001/decision-log.md) |
| VB6とNyanQL群の対応調査 | 比較資料作成済み | [対応資料](requests/DR-NYANRAD-001/vb6-nyan-mapping.md) |
| 初期範囲・対象外の比較と着手判断材料 | 着手判断記録済み | [Issue #2](https://github.com/kosaru/NyanRAD/issues/2) |
| 人間向け要件定義 | 着手済み・企画確認書初稿作成 | [準備編 Issue #3](https://github.com/kosaru/NyanRAD/issues/3) |
| 正式Baseline・実装引渡し | 未着手 | 要件定義と正式判断の後 |
| 設計・実装・テスト・内部レビュー | 未着手 | 正式なWork Requestの後 |
| 初回正式リリース | 未着手 | 人間の正式受入の後 |

全体の追跡：[Issue #1](https://github.com/kosaru/NyanRAD/issues/1)

## 次に進める内容

[初期範囲の比較案](requests/DR-NYANRAD-001/initial-scope-options.md)を作成済み。初回候補と後続候補を検討の軸とする人間の了承を記録済み。
対象利用者・困り事・改善方向の人間確認を反映済み。要件定義着手の明示判断を記録済み。[企画確認書](requirements/01-project-brief.md)を材料に、次は「全体像を描く」へ進める。

## 更新方法

- 作業開始時にIssueへ目的、次の作業、完了条件を記録する。
- まとまった作業が終わったら、成果物・Commit・PR・確認結果と残る作業をIssueと本一覧へ反映する。
- 判断待ちの場合は、判断対象と影響する作業を明示する。
- 正式な要件・Gate・Release等の状態は、それぞれの正式記録へリンクする。
- 手順の正本は[kosaru/AI-powered-development](https://github.com/kosaru/AI-powered-development)。本一覧は進捗の入口とする。

## 作業履歴

- 2026-10-22：既存記録を確認し、全体追跡Issueと次の作業Issue、進捗一覧を作成。資料の既存状態はCommit `5efc52027aa263c16b0e23ba6208166943819223`で確認。

- 2026-10-22：Issue #2の範囲比較資料を作成（`e1b98fa49946ae428afc81eecd275d0f77e684bd`）。初回候補・後続候補と影響を提示。受付状態はexploringを維持。

- 初期範囲の検討方針への人間の了承を判断履歴へ保存。残る受付事項の確認へ進む。

- 2026-10-22：利用者・困り事・改善方向の人間確認を反映。受付条件を評価しcandidateへ移行。要件定義着手は判断待ち。

- 2026-10-22：人間の明示指示で要件定義着手。開始資料と企画確認書初稿を作成。
