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
  - HELP
    - ヘルプをページングする方法 `git -p help -a`
    - Gitで利用できる全コマンドのリスト `git help -a`
    - すべてのGitガイドを表示 `git help -g`
    - Gitの用語集を表示 `git help glossary`

## 第4章 リポジトリの作り方と使い方
  - git logでコミットの構成をみる  
    `git log --name-only`  
    `git log --stat`
    `git log --shortstat`

## 第5章 GUIでGitを使う
  - 読み飛ばし

## 第6章 ファイルの追跡と更新
  - `gid diff`で表示される差分はhunk（ハンク）、patch（パッチ）と呼ぶ
  - gitの差分出力は `unified format` という
  - `git commit -a` は `git add .` を省略
  - ワーキングとステージングの差分 `git diff`
  - ステージングとリポジトリの差分 `git diff --staged`
  - `git add`をする前に、どのようになるかチェックする方法 `git add --dry-run .`

## 第7章 変更箇所をコミットする
  - `git add -p` で変更を部分的にステージングに追加できる
  - `git rm [ファイル名]`
  - `git mv [移動元ファイル名] [移動先ファイル名]`
  - `git reset [ファイル名]` ステージングエリアをリセットして、ファイルをコミット予定から外す
  - `git checkout [ファイル名]` ファイルのコミットを、作業ディレクトリに入れる

## 第8章 Gitというタイムマシン
  - `git log --parents` で、親のCommitのIDが表示される
  - `git log --parents --abbrev-commit` で、上記のCommitのIDが7桁と短くなる
  - `git log --patch` で、hunkを表示することができる
  - `git log --stat` で、Commitの変更ファイルの概要が表示される
  - `git log --patch-with-stat`で、patchとstatオプションの内容が同時に表示される（`git show`と同様？）
  - 他にも `git shortlog`、`git reflog`、`git blame`もある
  - タグ付け `git tag [タグ名]` or `git tag [タグ名] -m [タグメッセージ]`
  - `git rev-parse` ブランチ名、タグ名をIDに変換する

## 第9章 ブランチ（支線）を辿る
  - gitのコマンドのエイリアスを作成する `git config --global alias.lol "log --graph --decorate --pretty=oneline --all --abbrev-commit"` などで作成する
  - すべてのブランチのリストをIDをつけて表示 `git branch -v`
  - これまでに(git checkoutで)行ったブランチ切り替えのすべての記録を表示する `git reflog`

## 第10章 ブランチをマージ（統合）する
  - ２つのブランチの違いを表示 `git diff [ブランチ名1]...[ブランチ名2]` 順番が大事
  - n個まえのコミットの概要を表示する、`git log -[n]`
  - マージの際にベースとなるコミットを表示する `git merge-base [ブランチ名1] [ブランチ名2]

## 第11章 クローン（複製）を作る
  - リポジトリのクローンを作成する `git clone [複製元] [クローンを作成するディレクトリ]`
  - ブランチごとのファイルリストを表示 `git ls-tree [ブランチ名|ID|タグ]`

## 第12章 リモートとの共同作業
  - 現在のリポジトリにあるリモートの名前を表示する `git remote`
  - リモートの名前を対応するURLと同時に表示する `git remote -v show`
  - リモートを追加する `git remote add [リモート名] [ローカルリポジトリ]`
  - リモートのリファレンスを表示する `git ls-remote`

## 第13章 変更をプッシュ（送出）する
  - masterブランチをoriginという名前のリモートにプッシュする `git push origin master`
  - 現在のブランチをデフォルトリモート追跡ブランチにプッシュする `git push`
  - デフォルトリモート追跡ブランチを設定する `git push --set-upstream [ブランチ名]`
  - 正規表現を使って設定を表示する `git config --get-regexp [正規表現]`
  - ローカルブランチを削除する `git branch -d [ブランチ名]`
  - リモートブランチを削除する `git push origin :[ブランチ名]`
  - タグを付ける `git tag -a [タグ名] -m [タグメッセージ] [コミットID]`
  - リモートにタグをプッシュする `git push origin [タグ名]`
  - すべてのタグをデフォルトのリモートにプッシュする `git push --tags`
  - ローカルのタグを削除する `git tag -d [タグ名]`
  - リモートのタグを削除する `git push origin :[タグ名]`
  - プッシュの方式にはsimpleと、matching等が存在する
    - nothing  
      sourceとdestinationの指定が必須
    - current  
      カレントブランチをプッシュして、同名のブランチを更新する
    - upstream  
      currentと同様の動作
    - simple  
      upstreamと同様、ブランチ名が上流のブランと同一かどうかチェックする
    - matching  
      リモートに同名のブランチを持つ全てのブランチをプッシュする
  - プッシュの方式を設定する `git config push.default [プッシュ方式]`

## 第14章 同期を保つ（プル）
  - ローカルリポジトリをリモートリポジトリ（複製元）と同期させる、git fetchとgit mergeで構成される `git pull`
  - ローカルリポジトリにリモートリポジトリから新しいコミットを取り込む、リモート追跡ブランチが更新される `git fetch`
  - FETCH_HEADからの新しいコミットを、カレントブランチにマージする `git merge FETCH_HEAD`
  - FETCH_HEADがカレントブランチの子孫（Fast-Forward）である場合に限りマージする `git pull --ff-only`

## 第15章 ソフトウェア考古学
  - マージの結果であるコミットのリストを表示 `git log --merges`
  - 正規表現で文字列を含んでいるコミットのリストを表示 `git log --grep=[文字列]`
  - 2つの日付の間に作られたコミットのリストを表示 `git log --since MM/DD/YYYY --until MM/DD/YYYY`
  - 著者名によるコミットの要約を表示 `git shortlog`
  - 同時にEメールも表示 `git shortlog -e`
  - 著者を指定してコミットのリストを表示 `git log --author=[著者名]`
  - すべてのブランチを絡む表示 `git branch --column`
  - ブランチIDから名前の表示 `git name-rev [ブランチID]`
  - 指定したコミットIDを含むブランチの表示 `git branch -r -contains [コミットID]`
  - 正規表現で文字列を含むファイルを探し出す `git grep [文字列]`
  - blame出力でファイルを表示 `git blame [ファイル名]`

## 第16章 {git rebase}を理解する
  - ブランチ間のログを表示 `git log [ブランチID]..[ブランチID]`
  - ブランチを最新のコミットにリベース `git rebase [ブランチID]`
  - HEADの変更をすべて記録したreflogを表示 `git reflog`
  - ステージングも作業ディレクトリ両方を、コミットIDの内容でリセットする `git reset --hard [コミットID]`
  - リベースを対話型で行う `git rebase --interactive [コミットID]`
  - 指定のコミットをカレントブランチにコピーする `git cherry-pick [コミットID]`

## 第17章 ワークフローとブランチの規約
  - ファイルの追加なしにコミットする `git commit --allow-empty -m [コミットメッセージ]`
  - 指定のブランチをカレントブランチに、たとえFast-Forwardであったとしても、マージコミットを作成する `git merge --noff [ブランチID]`
  - git flowを利用する（詳しくはgit flowのTIL参照）

## 第18章 GitHubを使う
  - 読み飛ばし

## 第19章 サードパーティ製ツールとGit
  - 読み飛ばし

## 第20章 Gitを研ぎすませる
  -  ローカルのGitの設定をリストで表示 `git config --local --list`
  -  グローバルのGitの設定をリストで表示 `git config --global --list`
  -  システムのGitの設定をリストで表示 `git config --system --list`
  -  相対的日付表示でログを表示 `git -c log.date=relative log`
  -  ローカルのGitの設定をエディタで開く `git config --local --edit`
  -  グローバルのGitの設定をエディタで開く `git config --global --edit`
  -  システムのGitの設定をエディタで開く `git config --system --edit`
