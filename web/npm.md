# node/npm til

## nodeのインストール  
  1. nodebrewをインストール
    curl -L git.io/nodebrew | perl - setup
    export PATH=$HOME/.nodebrew/current/bin:$PATH
    source ~/.bashrc
  1. nodeの最新をインストール  
    nodebrew install-binary latest
  1. インストールされているnodeのリストを表示
    nodebrew ls
  1. 使用するバージョンの切り替え  
    nodebrew use latest
  1. 

## npmでpermission denied
  1. グローバルインストールのためのディレクトリを作成する  
    `mkdir ~/.npm-global`
  1. 新しいディレクトリを使う設定をnpmで行う  
    `npm config set prefix '~/.npm-global'`
  1. ~/.profileを開くか作成し，以下の行を追加する  
    `export PATH=~/.npm-global/bin:$PATH`
  1. 3の変更を反映する  
    `source ~/.profile`

## npm install でエラー
  - node_modules の削除をためしてみる  
    `rm -rf node_modules`
  - npm のキャッシュごとクリアしてみる
    `npm cache clean`

## 該当パッケージを、sourceからnpm installを行う  
  - `npm install sqlite3 --build-from-source`

## npm/node のパスの確認
  - node_modulesの場所  
    npm root -g
  - binの場所
    npm bin -g

## npm config をresetする
  - user  
    echo "" > $(npm config get userconfig)  
    npm config edit
  - global  
    echo "" > $(npm config get globalconfig)  
    npm config --global edit  
  - sudoが必要な場合  
    sudo sh -c 'echo "" > $(npm config get globalconfig)'
    
## npmのバージョンを上げる
  - `npm install -g npm`
