# ソケット通信

## ソケット・インタフェース

- ソケット通信の終点。
- ファイル・インタフェースを拡張したもの。
  - ファイル操作用のシステムコールでは固定長のデータの扱いしかできないため。
  - ソケットも read(), write() で読み書きする。
  - ソケットも子プロセスに引き継がれる。
  - ソケットも i ノードで管理される。

## ドメイン

- いくつかの通信プロトコルを抽象化したもの。
  - INET ドメイン（インターネットドメイン）: インターネット通信で利用される。
  - UNIX ドメイン: プロセス間通信で利用される。

## ソケット通信の流れ（サーバ）

1. ソケットを作成する。(socket())
  - このタイミングでドメインを指定する。
2. ソケットに名前をつける。(bind())
  - UNIX ドメインソケットの場合はファイル名（パス）が名前になる。
3. ソケットキューを作成する。(listen())
  - 接続要求を待ち受けるためのキュー。
4. 接続を待ち受ける。(accept())
  - ソケットキューの先頭のひとつを受け付ける。
  - 別の通信用のソケットを作成する。
5. 以降はファイル操作と同様。

## ソケット通信の流れ（クライアント）

1. ソケットを作成する。(socket())
2. 接続を要求する。(connect())
5. 以降はファイル操作と同様。

## 資料

- [Linuxカーネルの基本機能 - 第12回　ソケット･インタフェース：ITpro](http://itpro.nikkeibp.co.jp/article/COLUMN/20080520/303014/?P=2)
  - すごくわかりやすいんだけど、もっと権威のあるテキストはないものか。
