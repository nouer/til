# Commiterの変更方法
 - 新しい環境からgitにコミットしたらCommiterを間違えていた場合等
 - リポジトリ直下の`.gitconfig`を修正する  
    git config --local user.name Johnny  
    git config --local user.email johnny@hoge.com
 - 現在のCommitに適応する場合、`git --amend`で情報を変更する

# Authorの変更方法
 - 新しい環境からgitにコミットしたらAuthorを間違えていた場合等
 - `git --amend --author`で修正する  
    git commit --amend --author="Johnny <johnny@hoge.com>"
    git log --pretty=full
    