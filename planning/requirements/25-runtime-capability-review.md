# NyanQL群の保存・実行管理：現在のソース確認

確認日：2026-10-27。NyanRADの要件資料はCommit `54472621cff77c7a3d3517b1cba20c6e33388869` を参照。NyanQL群の各リポジトリのmainを確認し、以下のCommitに固定してソースを読んだ。これは**静的な調査**であり、配布実行ファイルやmacOSでの動作試験ではない。

| 製品 | 調査対象のCommit |
|---|---|
| NyanPUI | [`ebc4ddee`](https://github.com/NyanQL/NyanPUI/tree/ebc4ddee7dffa84fb25688cbff0ba16746d42dfd) |
| NyanQL | [`d513c4d9`](https://github.com/NyanQL/NyanQL/tree/d513c4d9bca77b62bdd5a9335c61d26cd9f107cf) |
| Nyan8 | [`88c1b37b`](https://github.com/NyanQL/Nyan8/tree/88c1b37bbed0c1133933f86923834c9ae8540abf) |

３つとも、前回の[静的調査](04a-local-feasibility.md)で示したCommitと同じだった。実行ファイルの実際の版がこれらと一致するかは未確認。

## 読込・保存

NyanPUIのサーバーJavaScriptには、読込・保存・削除の関数が登録されている。保存は対象と同じディレクトリに一時ファイルを作り、書込み・同期・クローズの後に名前を変更する。これらは**１ファイルの処理**として確認できる。[関数登録](https://github.com/NyanQL/NyanPUI/blob/ebc4ddee7dffa84fb25688cbff0ba16746d42dfd/main.go#L2853)、[読込・保存](https://github.com/NyanQL/NyanPUI/blob/ebc4ddee7dffa84fb25688cbff0ba16746d42dfd/main.go#L3133)

保存関数の対象部分には、読込時の版と現在の保存先を比較してから書く処理は見当たらない。複数ファイルを一括で保存・復元する処理も、この関数からは確認できない。したがって、競合表示・途中失敗・部分保存の扱いは、NyanRAD側の要件と技術検証として残る。外部変更が比較後に発生する場合の扱いも検証対象。

NyanPUIは `nyanSaveFile(path, content)`、NyanQLは `nyanSaveFile(base64, path)` の形で登録され、戻り値も異なる。引数や戻り値が３製品で共通と仮定しない。[NyanQLの保存登録](https://github.com/NyanQL/NyanQL/blob/d513c4d9bca77b62bdd5a9335c61d26cd9f107cf/main.go#L9311)

NyanPUIのパス解決は絶対パスをそのまま使い、相対パスは設定ファイル基準のディレクトリへ結合する。プロジェクト外への書込みをNyanRAD側がどう制限するかは別途設計・検証する。[パス解決](https://github.com/NyanQL/NyanPUI/blob/ebc4ddee7dffa84fb25688cbff0ba16746d42dfd/main.go#L3123)

## 起動・停止・ログ

３製品の `nyanHostExec` は、macOSを含むWindows以外でシェル経由のコマンドを実行し、終了結果を返す。NyanPUIは標準出力・標準エラーの読取り終了とコマンド終了を待ち、NyanQL・Nyan8はコマンドの実行終了を待つ。[NyanPUI](https://github.com/NyanQL/NyanPUI/blob/ebc4ddee7dffa84fb25688cbff0ba16746d42dfd/main.go#L2955)、[NyanQL](https://github.com/NyanQL/NyanQL/blob/d513c4d9bca77b62bdd5a9335c61d26cd9f107cf/main.go#L8369)、[Nyan8](https://github.com/NyanQL/Nyan8/blob/88c1b37bbed0c1133933f86923834c9ae8540abf/main.go#L5885)

この関数が返すコマンドの終了結果だけでは、生成アプリの常駐サービスの準備完了、IDEによる所有、後からの停止、ログの継続取得は確認できない。NyanPUIの読取り完了待ちから、起動した子プロセスが出力先を保持し続ける場合に呼出しが返らない可能性も考えられるが、これはソースからの推論でありmacOSで未実証。

| 確認したいこと | 既存コードからの現状 | 後の実証で見ること |
|---|---|---|
| 起動後もIDEが応答できる | コマンド終了と出力読取りを待つ | 対象の常駐中にも要求が返り、起動成否と準備完了を区別できるか |
| 対象を識別する | コマンド結果だけで長期の所有情報は確認できない | 起動した対象と外部サービス、PIDの再利用、IDE再起動後を区別できるか |
| 自分の対象だけ止める | 停止要求と終了確認を行う機能の成立は未確認 | 所有を確認できない場合に別サービスを停止せず、不明を表示できるか |
| 起動に一部失敗 | 起動結果と対象の対応づけは別途必要 | 今回起動したものだけを停止し、停止失敗を表示できるか |
| ログを表示 | 実行コマンドの出力収集はある | 対象別の継続ログ、取得失敗、表示上限、既存ファイル保持を満たせるか |
| 外部変更と保存 | １ファイルの読込・一時保存・名前変更はある | 差分確認後の再変更、部分保存、未保存保持を要求どおり扱えるか |

## 現時点の判断

NyanPUIの既存のファイル関数と、３製品のコマンド機能は候補になる。**既存の機能だけでNyanRADの実行管理が成立するとはまだ判断できない。** 逆に、追加バイナリが必須とも判断しない。

初回macOS・HTML/CSS/JavaScript・提供されるNyanQL群の実行ファイルという前提は維持する。実機検証・実装は正式BaselineとWork Request成立後に進め、満たせない条件や新しい残存リスクが見つかれば人間へ提示する。正式な要件承認、リスク受入、Baseline・実装開始・リリースは成立していない。
