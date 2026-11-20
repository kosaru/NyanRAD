# NyanQL群のmacOS配布物とローカル管理の確認

確認日：2026-11-20。NyanRAD要件の確認対象：`ba342a71adb865c445b1fff560b7ba2bd2b5e2ce`。調査で実行ファイルを起動していない。以下はGitHub公開配布物・ソースの静的確認であり、動作成功や安全性の保証ではない。

## Apple Silicon向け配布物

３製品のGitHub Releasesの最新公開版を取得し、配布ページに示されたSHA-256と照合した。いずれも一致。ZIP中の実行ファイルのMach-Oヘッダーはすべてarm64だった。

| 製品・公開版 | 配布物 | SHA-256 | 実行ファイルに記録された最低macOS版 |
|---|---|---|---|
| [NyanPUI v1.0.17](https://github.com/NyanQL/NyanPUI/releases/tag/v1.0.17) | NyanPUI_macos-latest.zip | `9ecc365b23a9c32f507dca105b6b153719027950f7dd27e060e14dab68dd76df` | 26.0 |
| [Nyan8 v1.0.21](https://github.com/NyanQL/Nyan8/releases/tag/v1.0.21) | Nyan8_macos-latest.zip | `c2a79f1bd7ea5af6992655a67b6b8cf588bb1ffa0ae04bde4ef33d632b57c4c2` | 12.0 |
| [NyanQL v1.0.24](https://github.com/NyanQL/NyanQL/releases/tag/v1.0.24) | NyanQL_macos-latest.zip | `45c7fe0982ee463127b5570b02622ee6c8a78a03e0bc36b1727ee22fa61e98c2` | 26.0 |

最低版は各実行ファイルの `LC_BUILD_VERSION` に記録された値であり、実際にそのOSで起動・動作した証拠ではない。配布ページのタグと調査対象を記録したもので、NyanRADでこれらの版を正式採用したものではない。古い版や異なるビルドが旧macOSで利用可能かは未確認。macOS 26未満も初回対象とする場合は、対応する３製品の配布版または別ビルドの有無と実動作の確認が別途必要になる。

## ローカル管理機能のアクセス範囲

[NyanPUIの該当ソース](https://github.com/NyanQL/NyanPUI/blob/ebc4ddee7dffa84fb25688cbff0ba16746d42dfd/main.go#L974)ではHTTPサーバーの待受先をポートのみで指定している。READMEも全インターフェースで待ち受け、localhostのURLでアクセスしても公開範囲が限定されるわけではないと説明している。[運用上の前提](https://github.com/NyanQL/NyanPUI/blob/ebc4ddee7dffa84fb25688cbff0ba16746d42dfd/README.md)

通常API向けには[CORSで全Originを許可する処理](https://github.com/NyanQL/NyanPUI/blob/ebc4ddee7dffa84fb25688cbff0ba16746d42dfd/main.go#L2438)があり、[paramCheckによるAPI実行前の判定](https://github.com/NyanQL/NyanPUI/blob/ebc4ddee7dffa84fb25688cbff0ba16746d42dfd/main.go#L1610)と[要求ヘッダー取得](https://github.com/NyanQL/NyanPUI/blob/ebc4ddee7dffa84fb25688cbff0ba16746d42dfd/main.go#L2769)が実装されている。NyanPUI自体のこれらの機能が、NyanRADで必要なアクセス制御を満たすことは未検証。

NyanRADはローカル利用を前提とし、将来的にファイル保存などの管理操作を持つ。このため、管理APIの公開範囲・認証・意図しない呼出しの防止を技術的に確認する必要がある。単にURLがlocalhostであることや、CORSだけを根拠に保護済みと判定しない。今回、NyanRADのAPIは未実装であり、外部からの呼出し・認証回避等の実験は行っていない。対処方法の採用、リスク受入、既存フレームワークの変更を決定したものではない。

## 次の作業

- 初回の最低macOS版を[判断材料](30-minimum-macos-decision.md)として確認する。
- 選択対象の実行ファイルの版・互換性・設定、SafariとChromeでの利用可能性を正式な検証対象として固定する。
- 管理APIの公開・認証・ファイル操作・実行管理を区別し、既存機能の成立を確認する。設計・実装・動作試験は正式な入力成立後に行う。
- 既存の前提で実現できない場合や新たな残存リスクが生じる場合は、事実と選択肢を人間に提示する。今回の記録はリスク受入を意味しない。
