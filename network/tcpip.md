# TCP/IP

## IP アドレス

- ネットワーク部とホスト部に分かれる。
  - ネットワーク部の値列でネットワークを特定する。
  - ホスト部の値列でホストを特定する。
  - ネットマスク（例: 255.255.255.0）を元に分けられる。
- ネットワークアドレス。
  - ネットワークを示すアドレスのこと。
  - ホスト部がすべて 0 (例: 192.168.10.0) の値列が使われる。
- ブロードキャストアドレス。
  - ネットワーク内の全ホストを示すアドレスのこと。
  - ホスト部がすべて 1 (例: 192.168.10.255) の値列が使われる。

## 通信

- 同一ネットワーク内のホストは直接通信できる。
  - ネットワークアドレスをもとに調べる。
- 異なるネットワークのホストへはルータを介して通信する。
  1. ホストはルータに転送を依頼する。
  2. ルータはあて先に近い（と思われる）ルータに転送を依頼する。
  3. 目的のネットワークに着くまで転送を繰り返す。

## ルーティング

- 通信経路を選択する処理のこと。
- 各通信機器はルーティングテーブルを元にこれを決める。
  - 特定のアドレスあて（Destination）のパケットを、  
    どこのルータ（Gateway）に送信すれば良いかという情報を管理している。
  - 登録状況は route コマンドで確認できる。
    ```
    $ route -n
    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    10.131.23.0     0.0.0.0         255.255.255.0   U     0      0        0 br0-2502
    10.146.13.0     0.0.0.0         255.255.255.0   U     0      0        0 br1
    172.19.64.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
    0.0.0.0         172.19.64.1     0.0.0.0         UG    0      0        0 eth0
    ```
  - Gateway が 0.0.0.0 と登録されているのは、ルーティングを無効にするため。
    - Destination がホストのいるネットワークを指しているはず。
  - Destination, Genmask が 0.0.0.0 の登録は、デフォルトゲートウェイを有効にしている。
    - 他の登録に該当しないパケットはすべてこのルーティングが適用される。

