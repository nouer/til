# データ分析ツール Jupyter入門
## 目次
<pre>
Chapter 1 Jupyterを利用する
1.1 Jupyterの基本とAnacondaのセットアップ
Pythonと数値処理
Jupyterとは？
Pythonについて
JupyterとIPython
Anacondaディストリビューション
Anacondaをインストールする（Windows）
Anacondaをインストールする（macOS）
Anacondaのソフトウェア
1.2 アプリケーションを利用する
Anaconda Navigatorを起動する
Home表示について
仮想環境の構築
仮想環境を作る
仮想環境にアプリケーションを追加する
Notebookを使う
ノートブックを作成する
セルについて
カーネルの管理
ノートブックのメニューとツールバー
「File」メニューについて
「Edit」メニューについて
「View」メニューについて
「Insert」メニューについて
「Cell」メニューについて
「Kernel」メニューについて
「Widgets」以降のメニュー
キーボードショートカットについて
ツールバーについて
1.3 JupyterLabを使う
JupyterLabとは？
JupyterLabのインストール
JupyterLabを起動する
画面の基本的な役割について
各タブの働き
Labで追加されたメニューについて
「Settings」メニューについて
設定の編集エディタについて
Google Colaboratoryについて
Google Colaboratoryの基本画面
Google Colaboratoryの特徴
もう1つのJupyter環境

Chapter 2 Markdownによるドキュメント記述
2.1 Markdownの基本
Markdownについて
ドキュメントの記述
タイトルと見出し
Markdownのエディット機能について
スタイルの設定
テキストの引用
ソースコードの記述
仕切り線の表示
リンクの作成
イメージの表示
2.2 リストとテーブル
箇条書きリストについて
階層化されたリスト
ナンバリングされたリスト
定義リストについて
テーブルの作成
&lt;table&gt;タグは使える？
2.3 TeX記法による数式
数式の基本は「$」記号
数式を記述する
べき乗の記述
分数の記述
三角関数について
ルート（平方根）
総和について
対数について
極限について
微分について
積分について
行列について
equationとeqnarray
スタイルとカラー
数式への番号付け

Chapter 3 numpyによるベクトルと行列演算
3.1 ベクトルと行列
numpyとscipyについて
numpyとscipyをインストールする
numpyのimportについて
ベクトル値の作成
ベクトルと数値の演算
ベクトルどうしの演算
行列の作成
非正方の単位行列
そのほかの対角行列
ベクトルから行列への変換
転置について
3.2 ベクトル・行列の演算
ベクトルの結合
ベクトルの内積・外積
行列の四則演算
行列の積
行列の結合
行列の分割
総和の計算
最大値・最小値
統計計算
linalgについて
逆行列と行列式
テキストファイルからデータを読み込む
load/saveもある
ソートについて
ビューとスライス

Chapter 4 sympyによる代数計算
4.1 sympyの基本
sympyと代数計算
sympyのインストール
整数・実数・分数
intとIntegerの違い
分数について
N、evalfによる実数換算
定数（π、e、無限大）について
階乗について
平方根について
変数とシンボル
4.2 式を操作する
式の単純化
式の展開
多項式の因数分解
シンボルに値を代入する
方程式を解く
２元方程式を解く
連立方程式を解く
y = x は？
極限について
微分について
積分について

Chapter 5 scikit-learnによる機械学習
5.1 scikit-learnによる機械学習
A.I.と機械学習
scikit-learnとは
scikit-learnをインストールする
学習モデルの種類
irisデータについて
学習用と予測用のデータを用意
5.2 さまざまなモデルを使う
K近傍法で学習する
予測を行う
ロジスティック回帰を利用する
パーセプトロンの利用
MLP（多層パーセプトロン）
SVM（Support Vector Machine）
教師なし学習「K平均法」
5.3 さまざまなデータを利用する
digitsデータについて
digitsをロードする
K近傍法を利用する
そのほかの学習を利用する
教師なし学習を行う
mnistを利用する
SVMで予測する
教師なし学習を試す

Chapter 6 pandasによるデータ分析
6.1 DataFrameの基礎
pandasとは？
pandasをインストールする
追加モジュールについて
DataFrameについて
DataFrameを作成する
列データについて
列を追加する
行を追加する
1行ずつ追加するには？
インデックスの変更
locとiloc
行列の反転
6.2 DataFrameのデータを活用する
ユニークなデータの取得
Seriesについて
Seriesの演算
Seriesの統計メソッド
DataFrameのソート
グループについて
各グループの平均点を得る
合計点数でソートする
aggで集計する
特定のグループを取り出す
条件で検索する
ピボットテーブルについて
6.3 DataFrameとファイルアクセス
スプレッドシート・データの用意
CSVファイルを読み込む
CSVファイルに保存する
Excelファイルを利用する
Excelファイルに保存する
タブ区切りデータについて

Chapter 7 matplotlibによる視覚化
7.1 matplotlibの基礎
matplotlibとは？
matplotlibのインストール
pyplotでグラフを描く
plotとshow
sin曲線を描く
複数のグラフを描く
凡例を表示する
グラフ表示に関する設定
グリッド表示について
グラフの表示エリア
グラフの形状
7.2 グラフを使いこなす
Axesの分割
FigureにAxesを追加する
テキストを追加する
矢印の追加
注釈を付ける
線の描画
一定の幅で塗りつぶす
指定領域の塗りつぶし
7.3 さまざまなグラフ
棒グラフを作る
グラフを重ねる
棒グラフを横に並べる
円グラフを描く
ヒストグラムの作成
確率密度曲線を描く
複数データの利用
散布図の作成
カラーメッシュを描く
3Dグラフの描画

Chapter 8 pillowによるイメージ処理
8.1 pillowの基礎
pillowとは？
pillowをインストールする
イメージを読み込む
イメージの情報を得る
ファイル保存とフォーマット変換
ファイルの例外処理について
サイズの変更
イメージの回転
反転と回転
RGBとグレースケールの変換
8.2 イメージ処理の機能
フィルターについて
ブラー処理を行う
GaussianBlurについて
BoxBlurでぼかしをかける
アンシャープマスクをかける
UnsharpMaskクラスについて
モルフォロジー変換
RankFilterについて
pointと輝度調整
8.3 イメージの描画と合成
新しいイメージの作成
ImageDrawについて
直線の描画
四角形の描画
ellipseによる円の描画
テキストの描画
イメージを重ねて描く
イメージを切り抜いてペーストする
イメージのブレンド
RGBの分離とマージ
イメージのセピア化
8.4 ImageOps/ImageChops
オートコントラスト
イメージの反転
イメージの輝度反転
グレースケール化
ポスタライズ
ソラリゼーション
カラーライズ
平均化
ImageChopsモジュールについて
darker/lighter
addによる合成
multiplyによる合成
subtractによる合成
differenceによる合成
compositeによる合成

Chapter 9 Jupyter機能拡張ウィジェットの活用
9.1 ipyleafletの利用
モジュールとウィジェット
ipyleafletとは？
Mapクラスを使う
マーカーを追加する
マーカークラスタについて
円形マーカー
直線の描画
四角形の描画
円の描画
イメージを表示する
描画コントロールの利用
設定をスライダーで操作する
イベントを利用する
リアルタイムに情報を表示する
9.2 ipywidgets
ipywidgetsとは？
Labelによるテキスト表示
interactウィジェット
ボタンとイベント
入力フィールド関連のクラス
スライダー関係コントロール
真偽値のコントロール
複数項目からの選択
そのほかの複数項目選択コントロール
複数の項目を選択する
Boxコンテナについて
Accordionによるアコーディオン表示
Tabsによるタブパネル
コンテナを組み合わせ、更に複雑に！

Chapter 10 Jupyterのカスタマイズ
10.1 JavaScriptカーネルを利用する
カーネルについて
IJavascriptカーネルを準備する
カーネルを変更する
IJavascriptカーネルを利用する
アウトプットとコンソール出力
Node.jsのパッケージを利用する
HTMLを出力する
JPEGイメージを出力する
10.2 機能拡張RISEによるスライドショウ
RISEによるスライドショウ機能
スライドの設定について
スライドの作成と実行
サブスライドについて
フラグメントについて
10.3 Jupyter contrib nbextensions
Jupyter contrib nbextensionsについて
nbextensionsメニューについて
LaTeX environments for Jupyter
Autopep8
AutosaveTime
Cell Filter
Code Font Size
Code folding
Equation Auto Numbering
Hide Input/Hide Input All
Live Markdown Preview
nbTranslate
Printview
Python Markdown
Scratchpad
Snippets
Table of Contents (2)
Tree Filter
Variable Inspector
10.4 Jupyter設定ファイル
設定ファイルの作成
jupyter_notebook_config.pyの中身
パスワードを設定する
HTTPSを利用する
</pre>
## メモ