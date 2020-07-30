# Connection
データ転送等。

## Python
- `subprocess`でSSH接続の実施を伴うコマンド(e.g. `rsync`)を実行する場合、設定ファイル`~/.ssh/config`が勝手に用いられる。Pythonプログラム上で設定ファイルを読み込む必要はない。
- Python上でSSH接続を実施する場合(e.g. Paramiko, Fabric)、SSH接続の設定ファイルを明示的に読み込む必要がある。

