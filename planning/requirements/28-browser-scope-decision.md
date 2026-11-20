# NyanRAD 初回の対応ブラウザー：判断材料

作成日：2026-11-20。状態：Aを要求者が選択済み。初回はApple SiliconのMacでローカル利用し、NyanRADはHTML・CSS・JavaScriptで構築する方針を維持する。ブラウザーの対象を指定することは、NyanPUIなどの実行ファイルを不要とする意味ではない。

## 判断したいこと

初回リリースで、画面編集・コード編集・実行確認を検証する対象ブラウザーを選ぶ。対象に含めるブラウザーごとに、操作、画面表示、生成アプリのプレビュー、保存や実行管理との連携を実際に確認する必要がある。

| 案 | 初回の対象 | 特徴 |
|---|---|---|
| A（提案） | macOS版SafariとChrome | Mac標準のSafariとChromeの両方で使えることを目指す。両方の動作確認が必要 |
| B | macOS版Safari | 初回の確認範囲を絞れる。Chromeは後続の判断対象 |
| C | macOS版Chrome | 初回の確認範囲を絞れる。Safariは後続の判断対象 |
| D | 別の範囲 | 対象ブラウザーを指定し、その範囲で確認条件を整理する |

Firefox・Edge等を初回に含めるかは選択次第であり、A〜Cでは対象に含めない提案。いずれも現時点で動作確認済みという意味ではない。

## 確認環境と残ること

2026-11-20に作業中のMacでSafari 26.6.2とChrome 158.0.8127.36のアプリを確認した。macOSは26.6.2、CPUはApple Silicon。これはインストール状況であり、NyanRADの動作試験や最低対応版の決定ではない。

選択後も、最低ブラウザー版・最低macOS版、NyanQL群の配布実行ファイルの版、実行・停止・競合保存・DBの技術成立は別途確認する。追加の専用バイナリの採用、未実証事項のリスク受入、正式Baseline・実装開始やリリースの承認を意味しない。

参照：[初回のMac対応範囲](26-macos-scope-decision.md)、[提供条件](14-delivery-conditions.md)、[実行管理の静的調査](25-runtime-capability-review.md)。

## 2026-11-20 初回の対応ブラウザー

要求者は[対応ブラウザーの選択肢](https://github.com/kosaru/NyanRAD/blob/aeb660e47cea0c3726dadd346231d531413bc10c/planning/requirements/28-browser-scope-decision.md)に対して「A」と回答した。初回リリースの対象は、Apple SiliconのMac上のSafariとChromeの両方とする。Firefox・Edge等は今回の対象に含めず、後続の判断対象とする。

最低ブラウザー版・最低macOS版、NyanQL群の実行ファイル版、両ブラウザーの実動作は未確定・未検証。HTML・CSS・JavaScriptによる構築とNyanQL群実行ファイルを使う前提は維持する。正式な要件承認、Baseline・実装開始・Releaseの判断ではない。
