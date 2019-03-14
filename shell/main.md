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
