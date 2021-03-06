# fzf のナレッジ

https://github.com/junegunn/fzf

## fzf の概要

- ファジー検索をインタラクティブな UI で提供する CLI ツール。
- Kakao（Kakao Talk とか作ってる会社）にお勤めの [Junegunn さん](https://github.com/junegunn) による個人開発。
- ドキュメントは README.md。
- インストールスクリプトによるインストールが案内されているが、
  これはバイナリのダウンロードとキーバインド等の導入を自動化したもので、
  バイナリ単体であればダウンロードしてきたものを PATH を通った位置におくだけで終わり。

## preview 機能がすばらしい

- ファイラのプレビュー機能みたいなことをやるためのもの。
- ls | fzf --preview 'cat {}' で、選択されたファイルの内容をプレビュー用の窓に表示しつつ選べる。

## その他、Tips など

- なぜか Ctrl-T のバインドを上書きしてくる。（transpose-chars ってメジャーじゃないのか？）  
  ```~/.fzf/shell/key-bindings.bash``` のバインド処理をコメントアウトして対処した。
- 初めは気にならなかったが、期待した出力と逆順にリストアップされるので、  
  そうならないためにデフォルトで --reverse の方がいい気がしてきた。
- Ctrl-V, Alt-V でページダウン/アップできないかしら。

## 環境変数設定例

```bash
# ~/.bashrc

export FZF_DEFAULT_OPTS="--reverse --inline-info --select-1 --exit-0"
```


