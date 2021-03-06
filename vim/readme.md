# VIM TIL

## [vimrc読書会](https://vim-jp.org/reading-vimrc/)

## モード移動
 - i
 - o
 - R
 - v
 - <C-v>
 - <Shift-v>
 - ESC
 - <C-[> 
 - I 行頭へ移動して編集モードへ
 - S 行を削除して編集モードへ
 - C 右側を削除して編集モードへ
 

## カーソル移動
### ノーマルモードのカーソル移動
  - H 画面の最上部行
  - M 画面の真ん中行
  - L 画面の最下部行
  - gg 最初の行
  - G 最終の行
  - {n}g {n}行
  - w 単語の先頭にジャンプ（区切り文字をまで）
  - W 単語の先頭にジャンプ（区切り文字を含めない）
  - e 単語の最後にジャンプ（区切り文字をまで）
  - E 単語の最後にジャンプ（区切り文字を含めない）
  - b 単語の先頭に戻る（区切り文字まで）
  - B 単語の先頭に戻る（区切り文字を含めない）
  - f
  - F
  - t
  - T
  - zz
  - <C-o> 古いカーソル位置に戻る
  - <C-i> 新しいカーソル位置に戻る
  - <C-u> 半画面分上へ移動
  - <C-d> 半画面分下へ移動
  - <C-f> 一画面分上へ移動
  - <C-b> 一画面分下へ移動
  - <C-y> 一行上へスクロール
  - <C-e> 一行下へスクロール
  - g; 変更箇所を辿って戻る
  - g, 変更箇所を辿って進む
  - gj 折り返しがあっても行単位で下に移動
  - gk 折り返しがあっても行単位で上に移動
  - <Shift-[> 下方の空行に移動
  - <Shift-]> 上方の空行に移動
  - % 対応するカッコに移動

### 編集モードのカーソル移動
  - <C-o> で一旦ノーマルモードに移って、カーソル移動後、自動的に戻る
  
## 編集
### ノーマルモードからの編集
  - = インデントを合わせる
### インデント
### ノーマルモードからのインデント操作
  - `>>` インデントを増やす
  - `<<` インデントを減らす
#### 編集モードからのインデント操作
  - `<C-t>` インデントを増やす 
  - `<C-d>` インデントを減らす 
### 数字操作
  - `<C-a>` 数字を増やす
  - `<C-x>` 数字を減らす

## その他
### ハイライト操作
  - ハイライト消去 `:nohlsearch`
  - ハイライト消去 :noh
  
### ウインドウ操作
  - :sp
  - :vs
  - ウインドウの幅を増やす `<C-w> >`
  - ウインドウの幅を減らす `<C-w> <` 
  - ウインドウの高さを増やす `<C-w> +`
  - ウインドウの高さを減らす `<C-w> -`

### レジスタ
  - ノーマルモードで
    - レジスタ内容を表示 `:reg`
    - レジスタ操作を開始 `"`
      - レジスタ操作をaという名前で開始 `"a`
        - レジスタ操作をaという名前で開始して、aに行をヤンク `"ayy`
        - レジスタ操作をaという名前で開始して、aをペースト `"ap`
      
  - 編集モードで
    - レジスタ操作を開始　`<C-r>`
      - レジスタ操作をaという名前で開始して、aをペースト `<C-r> a`
  
  - 参照  
    [vimのレジスタ](https://qiita.com/0829/items/0b3f63798b6910623efc)

### コマンドライン
  - `:` でコマンドラインを開始  
   コマンドラインで利用するコマンドをことをExコマンドという
   - 主要なExコマンド
     - `e` ファイルを開く
     - `tabnew` 新規タブを開く
     - `r` 入力をバッファに挿入する
     - `w` 現在のバッファを開いているファイルにwriteする
     - `q` 現在のバッファを終了する、すべてのバッファが終了したらvimを終了する
     - `wq` w+q
     - `q!` 編集内容があっても`q`を実行
     - `reg` レジスタ内容を表示
     - `his` コマンドライン履歴を表示
  - コマンドラインモードでのカーソル移動
    - `<S-→>`
    - `<S-←>`
    - `<C-w>`
    - `<C-u>`
    - `<C-e>`
    - `<C-b>`
    - `<C-p>`
    - `<C-n>`
    - `<C-f>`
    - `<C-r>`
  - 参照  
    [Vimのコマンドラインモードでできること](https://qiita.com/gorilla0513/items/f4a5fd835201cf49fda1)

### 入力
  - 標準入力を挿入する `:r [コマンド]`
        - レジスタ操作をaという名前で開始して、aをペースト `"ap`
  
### 出力
  - 標準出力にバッファを渡す  
    `:w !xargs echo`








