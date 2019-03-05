# 独習Git

## 第1章 はじめに

## 第2章 Gitとバージョン管理の概要
  - repository = 倉庫
  - trunk = 幹
  - ファイルリストをみる `git ls-files`
  - ファイルの詳細をみる `git blame [ファイル名]`
  - コミット履歴をみる `git log`
  - ワンラインでコミット履歴をみる `git log --oneline`
  - 用語  
    - branch
    - checkout
    - clone
    - commit
    - distributed
    - repository
    - staging area
    - timeline
    - version control

## 第3章 Gitに馴染む
  - gitの設定の確認 `git config --list`
  - gitの設定をセット 例：名前の設定 `git config --global user.name "Johnny"`
  - gitの設定を解除 例：名前を解除 `git config --global --unset user.name "Johnny"
  - 全体の設定を行う時には `--global`をつける、リポジトリ毎に個別に行う時はつけない
  - gitのコマンド構文  
    `git [スイッチ] <コマンド> <引数>`  
    例： `git -p config --global user.name "Johnny"`
  - スイッチの短縮形には `-` を利用し、完全に記述する場合は `--` を利用する
  - コマンドリスト
    - clone  
      リポジトリを複製
    - init  
      空のリポジトリを作成
    - add  
      ファイルの内容をindexに追加
    - mv  
      ファイル／ディレクトリ／シンボリックリンクを移動・改名
    - rm  
      作業ツリーとindexから指定のファイルを削除
    - bisect  
      コミットをバイナリサーチで見つける  ← ？？？
    - grep  
      パターンにマッチする行をプリント
    - log  
      コミットログの表示
    - show  
      オブジェクトの型を表示  ← ？？？
    - status  
      作業ツリーの状態を表示
    - branch  
      ブランチのリスト／作成／削除
    - checkout  
      ブランチの切替、作業ツリーのファイルを復元
    - commit  
      変更をリポジトリに記録
    - diff  
      コミット間などの差分を表示
    - merge  
      2つ以上のヒストリーを結合
    - rebase  
      更新された上流のヘッドにフォワード  ← ？？？
    - tag  
      署名されたタグオブジェクトの作成／リスト／削除／確認
    - fetch  
      リポジトリからオブジェクトと参照をダウンロード
    - pull  
      リポジトリからfetchしてmerge
    - push  
      リモート参照と関連オブジェクトを更新   ← ？？？
  - コマンドライン効率
    - Ctrl+A  
      行の先頭に移動
    - Ctrl+E  
      行の末尾に移動
    - Ctrl+H  
      カーソルの左にある文字を削除 ＝ BACKSPACE
    - Ctrl+D  
      カーソルの右にある文字を削除 ＝ DELETE
    - Ctrl+U  
      カーソルの左側をすべて削除
    - Ctrl+K  
      カーソルの右側をすべて削除
      
## 第4章 リポジトリの作り方と使い方
## 第5章 GUIでGitを使う
## 第6章 ファイルの追跡と更新
## 第7章 変更箇所をコミットする
## 第8章 Gitというタイムマシン
## 第9章 ブランチ（支線）を辿る
## 第10章 ブランチをマージ（統合）する
## 第11章 クローン（複製）を作る
## 第12章 リモートとの共同作業
## 第13章 変更をプッシュ（送出）する
## 第14章 同期を保つ（プル）
## 第15章 ソフトウェア考古学
## 第16章 {git rebase}を理解する
## 第17章 ワークフローとブランチの規約
## 第18章 GitHubを使う
## 第19章 サードパーティ製ツールとGit
## 第20章 Gitを研ぎすませる
