# Deep Learning ディープラーニング G検定 対策: 2019

## 目次

<pre>
G 検定 の 特徴 と 合格 マインド セット
  G 検定 の 特徴
  G 検定 の 不都合 な 真実
人工 ニューラルネットワーク（ANN）
  単純 パーセプトロン
  線形 回帰
  ロジスティック 回帰
  多層 パーセプトロン
深層 ニューラルネットワーク（DNN）
  インターネット の 普及
  GPGPU の 普及
  勾配 消失 問題 の 解決
  画像認識 コンペティション での 圧倒的 な 成果
  深層 学習 ライブラリ の オープン ソース 化
  勾配 降下 法 の 概説
  勾配 降下 法 の 種類
  確率 的 勾配 降下 法（SGD） の 進化
深層 ニューラルネットワーク の 種類
  畳み込み ニューラルネットワーク（CNN）
  再帰 型 ニューラルネットワーク（RNN）
  LSTM/ GRU
  自己 符号化 器（オート エンコーダ： Auto Encoder)
  敵対 生成 ネットワーク（GAN）
  変 分 オート エンコーダ（VAE）
  Deep Q Network(DQN)
  コラム
自然言語処理 における 応用（Word 2 Vec/ fastText/ GloVe/ ELMo/ BERT）
  形態素解析(Morphological Analysis) と 前 処理
  BoW（Bag of Words)
  Word 2 Vec
  fastText
  GloVe
  ELMo
  BERT
試験 力 強化

</pre>

### ANN
  - 人口ニューラルネットワーク(ANN)
  - 単純パーセプトロン
    - 内積  
      要素同士を掛け算して、それをすべて足し合わせる計算
    - 活性化関数  
      f(u)=1の状態を発火、活性化しているといい  
      f(u)=0の状態を非活性という。
    - ステップ関数
    - 学習  
      単純パーセプトロンの重みである w を 最適な値を最終的な出力の値が正しいかどうかによって調整していくこと
    - 分類問題  
      入力ベクトルから離散的な値を出力し、出力値をラベルと紐づけることで、入力値から出力ラベル（または属するクラス）を予測する問題のこと
    - 線形回帰  
      価格、株価などの連続値をとる変数を、ほかの関連する観測データから予想すること
    - 目的変数  
      線形回帰において、予想したい対象の変数のこと
    - 説明変数  
      線形回帰において、予測に使われる変数のこと
    - 単回帰分析  
      説明変数ひとつのときの回帰分析のこと
    - 重回帰分析  
      説明変数が複数のときの回帰分析のこと
    - 多重共線性  
      重回帰分析の際に、説明変数同士の相関係数の絶対値が１に近い、強い相関がある場合、正しく推計できないような悪影響が生じること。
    - 恒等関数
      どのような入力変数に対しても、入力値がそのまま出力となる関数
    - パーセプトロンの限界
      線形分離可能な問題、つまり、直線で予測可能な問題のみしか解けない
    - ロジスティック回帰
- 誤差  
  最終的な出力値と正解の差分、この誤差が少なくなるように調整することを学習という
- シグモイド関数  
  ロジスティック関数の別名
- ロジット関数
  ロジスティック関数の逆関数


   