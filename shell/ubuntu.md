# ubuntu til

## すべてのコマンドのパスワード入力を省略する  
  - `sudo visudo` コマンドで、`sudoers`ファイルに以下の行を追加する  
    `[ユーザ名] ALL=NOPASSWD: ALL`

  - 特定のコマンドのみ省略したい場合は、コマンドを指定する  
    `[ユーザ名] ALL=NOPASSWD: /sbin/shutdown`

## screen で Permission denied が表示される
  - .bashrc に以下を追記
    `export SCREENDIR=$HOME/.screen`

## pipのインストール
  - `curl -kL https://bootstrap.pypa.io/get-pip.py | sudo python`
  - `pip -V`
