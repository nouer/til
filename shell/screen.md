# screen til
## screen で Permission denied が表示される
  - .bashrc に以下を追記
    `export SCREENDIR=$HOME/.screen`

## 基本
  - 名前付きのセッションを開始 `screen -S <セッション名>`
  - セッションとスクリーンのリスト表示 `screen -ls`
  - セッションにアタッチ `screen -x`
  - 名前付きセッションにアタッチ `screen -r <セッション名>`
  - 名前付きセッションをデタッチ `screen -d <セッション名>`

## 抜ける・デタッチ
  - デタッチ `Ctrl-a d`
  - デタッチしてログアウト `Ctrl-a D D`
  - スクリーンを抜ける `Ctrl-a :`
  - 強制的に抜ける（推奨されない） `Ctrl-a C-\`

## ヘルプ
  - Ctrl-a ?

## Window操作
  - ウインドウを作成 `Ctrl-a c`
  - 最後に訪れたウインドウへ変更 `Ctrl-a Ctrl-a`
  - 番号を指定してウインドウを変更 `Ctrl-a <番号>`
  - 番号か名前を指定してウインドウを変更 `Ctrl-a ' <番号 または　ウインドウ名>`
  - 次のウインドウへ変更 `Ctrl-a n` or `Ctrl-a <スペース>`
  - 前のウインドウへ変更 `Ctrl-a p` or `Ctrl-a <バックスペース>`
  - ウインドウのリストを表示 `Ctrl-a "`
  - ウインドウバーを表示 `Ctrl-a w`
  - 現在のウインドウ名を変更 `Ctrl-a A`
