# データ分析ツール Jupyter入門
## 目次
<pre>
Chapter 1 Jupyterを利用する
  1.1 Jupyterの基本とAnacondaのセットアップ
  1.2 アプリケーションを利用する
Chapter 2 Markdownによるドキュメント記述
  2.1 Markdownの基本
  2.2 リストとテーブル
  2.3 TeX記法による数式
Chapter 3 numpyによるベクトルと行列演算
  3.1 ベクトルと行列
  3.2 ベクトル・行列の演算
Chapter 4 sympyによる代数計算
  4.1 sympyの基本
  4.2 式を操作する
Chapter 5 scikit-learnによる機械学習
  5.1 scikit-learnによる機械学習
  5.2 さまざまなモデルを使う
  5.3 さまざまなデータを利用する
Chapter 6 pandasによるデータ分析
  6.1 DataFrameの基礎
  6.2 DataFrameのデータを活用する
  6.3 DataFrameとファイルアクセス
Chapter 7 matplotlibによる視覚化
  7.1 matplotlibの基礎
  7.2 グラフを使いこなす
  7.3 さまざまなグラフ
Chapter 8 pillowによるイメージ処理
  8.1 pillowの基礎
  8.2 イメージ処理の機能
  8.3 イメージの描画と合成
  8.4 ImageOps/ImageChops
Chapter 9 Jupyter機能拡張ウィジェットの活用
  9.1 ipyleafletの利用
  9.2 ipywidgets
Chapter 10 Jupyterのカスタマイズ
  10.1 JavaScriptカーネルを利用する
  10.2 機能拡張RISEによるスライドショウ
  10.3 Jupyter contrib nbextensions
  10.4 Jupyter設定ファイル
</pre>
## メモ
   - 扱うモジュール  
     - numpy ナムパイ 行列
     - sympy シムパイ 代数計算
     - scikit-learn サイキットラーン 機械学習
     - pandas パンダス データ分析
     - matplotlib マットプロットリブ 視覚化
     - pillow ピロウ イメージ処理
   - JupyterはIPythonから派生したプロジェクト
   - Pythonの種類
     - CPython オリジナル
     - IronPython .NET Framework
     - JPython JVM/JRE
   - Jupyter Lab
   - Amazon SageMaker と Google Colaboratory
   - ベクトル値
      ```Python
        変数 = np.array(リスト)
      ```
     - ゼロのベクトル
      ```Python
        変数 = np.zeros(要素数)
      ```
     - 1のベクトル
      ```Python
        変数 = np.ones(要素数)
      ```
     - 等差数列
       - ステップ数で作成
        ```Python
          変数 = np.arange(開始数, 終了数, ステップ)
        ```
       - 分割数で作成
        ```Python
          変数 = np.linspace(開始数, 終了数, 分割数)
        ```

  
