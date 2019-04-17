# Git TIL
## インストールした際にすること
  - vimをデフォルトエディタにする
    - nanoを削除するのが早い
  - ユーザ情報を設定
  
## Commiterの変更方法
  - 新しい環境からgitにコミットしたらCommiterを間違えていた場合等
  - リポジトリ直下の`.gitconfig`を修正する  
     `git config --local user.name Johnny`   
     `git config --local user.email johnny@hoge.com`
  - 現在のCommitに適応する場合、`git --amend`で情報を変更する

## Authorの変更方法
  - 新しい環境からgitにコミットしたらAuthorを間違えていた場合等
  - `git --amend --author`で修正する  
     git commit --amend --author="Johnny <johnny@hoge.com>"
     git log --pretty=full

## addのやり忘れ
  - 追加する場合  
    `git add` したあと、`git commit --amend` でコミットを修正する
  - commit自体をなかったコトにする場合  
    `git reset --soft HEAD^`
  - commitも変更もなかったことにする場合  
    `git reset --hard HEAD^`
  - いくつか前のコミットからやりなおす  
    `git rebase -i [コミットID]`

## コミットメッセージの変更方法
  - `git commit --amend`

## `git rebase` メモ
  - rebaseの指定するIDのコツ  
    `git rebase -i [コミットID]` で指定するコミットIDは、リベースしたい箇所の一つ前を使う。  
    以下の3つのコミットが存在していて、`commit_3`を, `commit_2`にリベースする場合は、コミットIDは`commit_1`を指定する  
      - commit_3 2019/03/01
      - commit_2 2019/02/01
      - commit_1 2019/01/01

    リベースの指示には、commit_3 は squash, commit_2 は pick を指定する  
      - pick commit_2
      - squash commit_3

## remoteブランチの削除
  - 空ブランチのpushで削除する場合  
    1. `git branch -d [削除するブランチ]`
    1. `git push origin :[削除するブランチ]`  
      (空のブランチをpushしているので削除される)

   - `--delete`で削除する場合
     1. `git push --delete origin [削除するブランチ名]`

## 他人の削除したリモートブランチがローカルに残っている場合
  - `git fetch --prune`

## pushしてしまったあとに、コミットを失敗していることに気がついた場合
  - まだ誰もpullしていない場合、強制上書きする  
    `git reset HEAD^ --hard`  
    `git push origin -f`  
  - もう誰かpullしている場合、打ち消しをpushする
    `git revert HEAD^`  
    `git push`

## git diff したら、old mode と new mode で差分が表示される
  - ファイルを保存していたディスクのファイルシステムを変更するなどして、ファイルを変更していないにもかかわらず、以下の差分が発生することがある  
    
      `old mode 100755`  
      `new mode 100644`  
    
    この場合、ファイルのパーミッションの変更をgitがチェックしているので、
  以下の設定を行えば、パーミッションの変更をチェックしなくなる
    `git config core.filemode false`  
  実際にこのパーミッション変更をチェックしないようにしたほうがよいのか、そのファイルのパーミッションを直したほうがいいのかは場合による

## ステージングされているファイルの削除
  - `git rm --cached [ファイル名]`
  - `git rm -r --cached [ディレクトリ名]`

## リモートのブランチにローカルを強制的に合わせる場合
  - origin/developがリモートのブランチ
  - `git fetch origin`
  - `git reset --hard origin/develop`

## キーワードが含まれる変更をhunkで表示
  - `git log -p -S'KEYWORD'`  
  - `git log -p -G'REGEX KEYWORD'`  # 正規表現  

## 空コミット
  - ファイルの変更なしにコミットメッセージを残したい場合  
  - `git commit --allow-empty -m [メッセージ]`

## 修正履歴をファイル単位で表示
  - `git blame [ファイル名]`  

## 修正履歴を行範囲を指定してファイル単位で表示
  - `git blame -L [開始行番号],[終了行番号] [ファイル名]`  

## コミットIDを指定して修正履歴をファイル単位で表示
  - `git blame [コミットID] -- [ファイル名]`

## 対象文字列を含むファイルを検索
  - 単純文字列で検索する場合  
    `git grep [文字列]`
  - 正規表現で検索する場合
    - 標準正規表現  
      `git grep -G [正規表現]`
    - 拡張正規表現  
      `git grep -E [正規表現]`
  - and 条件を付ける場合  
    `git grep -e [文字列1] --and -e [文字列2]`
  - or 条件を付ける場合  
    `git grep -e [文字列1] --or -e [文字列2]`
  - not 条件を付ける場合  
    `git grep -e [文字列1] --not -e [文字列2]`




