# gitflowとは
- gitのツール
- 自分でgitのブランチモデルを自由に操作するのではなく、フレームワークの中で操作するためのツール
- 各ブランチの役割
-- master: プロダクトのリリースブランチ、リリース時にreleaseブランチからマージされる
-- release: リリースブランチ、リリース時にdevelopブランチからマージされる
-- develop: 開発のメインブランチ、機能追加時にfeatureブランチからマージされる
-- feature branches: 機能の追加を行うブランチ、developブランチから分岐して修正し、developブランチにマージする
-- hotfixes: 緊急のバグフィックスなど、現在のプロダクトへの変更を行うブランチ、masterブランチから分岐する、修正後、relaseブランチにマージされる

# インストール
- macの場合homebrewでインストールが簡単  
`git install git`
`git install git-flow`

# 使い方
- 初期化する  
`git flow init`
- 機能追加を始める、内部的にはfeatureブランチが作成される  
`git flow feature start [name]`
- 機能追加を終わる、内部的にはdevelopブランチにマージして、featureブランチが削除される  
`git flow feature finish`
- 機能追加をリモートに入れる  
`git flow feature publish [name]`
- 機能追加をリモートから取り込む  
`git flow feature pull [name]`
- リリース作成を始める、developブランチからreleaseブランチが作成される  
`git flow release start [name]`
- リリース作成に修正を取り込む、developブランチからreleaseブランチに修正をマージする  
`git flow relase publish [name]`
- リリース作成を終わる、relaseブランチからmasterブランチにマージされる、developブランチにもマージされる  
`git flow release finish [name]`
- ホットフィックスを始める  
`git flow hotfix start [name]`
- ホットフィックスを終わる  
`git flow hotfix finish [name]`
 
# コマンドリスト
    git flow init
    git flow feature start | finish | publish | pull [name]
    git flow release start | finish | publish | pull [name]
    git flow hotfix  start | finish | publish | pull [name]

# 参考資料
https://danielkummer.github.io/git-flow-cheatsheet/index.ja_JP.html
