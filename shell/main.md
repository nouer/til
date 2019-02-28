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
