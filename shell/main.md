# shell関係
## 環境変数
### 設定
  - `export aaa=1`

### 削除
  - `unset aaa`  
  - `export -n aaa`  
    `export aaa=""` などでは削除はできない  
    変数名前には `$` はつけない

### 取得
  - `env`

## コマンド
### ls
 - ファイル名のみリスト  
   `ls -1`
 - 再帰  
   `ls -R`
 - カンマ区切りで表示  
   `ls -m`
 - 容量表示  
   `ls -s`
 - 読みやすい単位で容量表示  
   `ls -sh`
 - パターンにマッチする対象は表示しない  
   `ls -I *dummy*`

### find
 - ファイル名のみ
   `find -type f`

### 変数
 - ハイフンは変数名に使えない
 - 先頭に数字は使えない
 - 変数作成時の＝の前後にスペースを入れることはできない（左辺をコマンドとして、＝と右辺を引数として実行しようとする）
 - スペースやタブを含む場合は''または""で囲む
 - 変数の参照には$を利用する
 - 代入時には$をつけないことに注意
 - 文字列と結合する場合は、{}で明示する  
   `item=pen`  
   `echo I have ${item}s`

### 環境変数
  - 現在のシェルからコマンドへ引き継がれる変数
  - 環境変数は子プロセスから参照できる
  - 現在の設定されている環境変数は `printenv` で確認できる
  - 環境変数の設定はexportコマンドを利用する  
    例1：
    `CONFIG_NAME=private_config`  
    `export CONFIG_NAME`  
    例2：  
    `export CONFIG_NAME=private_config`
  - コマンドの前に変数への代入を指定すると、その1回のプロセスだけで有効な環境変数になる  
    `CONFIG_NAME=private_config ./test.sh`
  - 特殊なシェル変数
    - HOME  
      ホームディレクトリ
    - PWD  
      カレントディレクトリ
    - SHELL  
      ログインシェル
    - BASH  
      bashコマンドのフルパス
    - BASH_VERSION  
      bashコマンドのバージョン
    - LINENO  
      現在実行しているシェルスクリプトの行番号
    - LANG  
      ローケル
    - PATH
      シェルがコマンドを探すディレクトリ
    - IFS
      シェルの区切り文字
