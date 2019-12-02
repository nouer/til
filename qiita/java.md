# 進捗
- 2016/10/04 作成開始
- 2016/10/04 作成中

---

# 環境設定
- [Windows7/10](http://qiita.com/nouernet/items/d9e6c4317fc0c3905356)
- Mac OS
- Amazon Linux

---

# Hello world
```helloworld.java
public class HelloWorld
{
    public static void main(String[] args)
    {
        System.out.println("Hello world");
    }
}
```

---

# コンパイル
```
$ javac HelloWorld.java
```

# 実行
```
$ java HelloWorld
```

---

# コメント
- 単行

```
// コメント
```

- ブロック

```
/* コメント*/
```

---

# 変数/定数
```
public class HelloWorld
{

    // privateメンバ変数
    private int private_hoge;

    // publicメンバ変数
    public int public_hoge;
    public String public_moji;

    // protectedメンバ変数
    protected int protected_hoge;

    // static変数
    public static int static_hoge = 100;

    // 定数
    public static final String static_final_moji = "定数";

    public HelloWorld(String moji)
    {
        this.public_moji = moji;
    }

    public static void main(String[] args)
    {
        System.out.println("Hello world");
        System.out.println(HelloWorld.static_hoge);
        HelloWorld hw = new HelloWorld("axaxa");
        System.out.println(hw.public_moji);
        System.out.println(HelloWorld.static_final_moji);
    }

}
```

# 文字列操作
- 文字列定義

```
```

- 長さの取得

```
```

- 空設定

```
```

- 空判定

```
```

- 一部の取得

```
```

- 置換

```
```

- 比較

```
```

- 検索

```
```

- 正規表現

```
```

# 数値操作
- 2進数 / 10進数 / 16進数

```
```

- 四則演算

```
```

- 余り

```
```

- 大きい数字

```
```

- 四捨五入

```
```

- 小数点切捨て／切上げ

```
```

# 時間操作
- 時間の加減（年／月／日／時／分／秒）

```
```

- UTC/Local

```
```

# null

- 定義

```
```

- 判定

```
```

# 乱数

- 文字列　⇔　数字　（フォーマット）

```
``` 

```
カンマ
```

```
ZeroPadding
```


- 文字列　⇔　日付　（フォーマット）

```
```

```
元号
```

- 文字列　⇔　配列

```
```


# 型判定

```
```

# 制御構造

- if

```
```

- select/case

```
```

- for

```
```

- while

```
```

- 可変長引数

```
```

# 配列
- リスト / マップ

```
```

- 数える

```
```

- 削除 / 追加 / 挿入

```
```

- 検索

```
```

- ソート

```
```

- 並び替え

```
```

# ペア／タプル

```
```

# 標準I/O

- 標準入力

```
```

- 標準出力

```
```

- 標準エラー出力

```
```

# ファイルI/O
- ファイルI/O（テキスト）

```
```

- ファイルI/O（バイナリ）

```
```

- ファイルシステム操作

```
```


```
ファイル属性
```


```
ファイル名
```


ディレクトリ走査
```
```

# ロギング

```
```

# HTTP/HTTPSクライアント
- GET

```
```

- POST

```
```

- ファイルアップロード

```
```

# HTTP/HTTPSサーバ
- GET

```
```

- POST

```
```

- ファイルアップロード

```
```

# ネットワーク
- DNS

```
```

- サーバソケット

```
```

- クライアントソケット

```
```

- ネットワークI/O

```
```

# JSON I/O	
- 文字列　⇔　JSONオブジェクト

```
```

# エラーハンドリング

# オブジェクト指向
- オブジェクト生成

```
```

- オブジェクト破棄

```
```

- 継承

```
```

- インターフェイス

```
```

- リフレクション

```
```

- シングルトン

```
```

# DB接続
- Connect/Disconnect

```
```

- SELECT

```
```

- INSERT

```
```

- UPDATE

```
```

- DELETE

```
```

- ロック

```
```

# 暗号化

```
```

# 圧縮

```
```

# マルチスレッド
- スレッド作成

```
```

- スレッドスリープ

```
```

- スレッド終了

```
```

- スレッド待機

```
```

- 排他制御

```
```

- ロック

```
```

- 非同期処理

```
```

プログラミング言語別HOWTO Java編 環境設定

# Windows7/10における設定
## cygwin設定
- PATHを通す

```
環境変数→システム環境変数「PATH」
C:\cygwin\cygdrive\c\jdk1.7\bin\;
```

- cygwinの文字エンコーディングを設定

```
cygwinの上部で右クリック→options→text→character set →UTF-8
```

- 環境変数で文字エンコーディングを設定

```..bashrc
alias javac='javac -J-Dfile.encoding=UTF-8'
alias java='java -Dfile.encoding=UTF-8'
```

