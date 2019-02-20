#githubからssh経由でcloneする方法
 1. sshで使用する鍵を作成する  
    ssh-keygen -t rsa
 1. ファイル名、パスフレーズを聞かれるが、お好きなように
 1. 出力された公開鍵をコピーする  
    clip < ~/.ssh/[公開鍵ファイル名] とか
    pbcopy < ~/.ssh/[公開鍵ファイル名] とか
 1. githubにログインして、`Settings`(Personal Setting)から、`SSH and GPG keys`を開ける
 1. `SSH keys`から、`New SSH key`を開ける
 1. `Title`は適当に、`Key`には、作成した鍵の`pub`ファイルの中身をペーストして`Add SSH key`を押す
 1. sshの接続設定を行う、以下は~/.ssh/configへの参考例、秘密鍵ファイルはgithub.pem   
<pre>
    Host mygithub
        HostName github.com
        User git
        IdentityFile ~/.ssh/github.pem
</pre>
 1. ssh経由でアクセスできることを確認する  
    ssh mygithub
 1. cloneする  
    git clone mygithub:[githubのユーザ名]/[リポジトリ名].git
 
# githubからhttps経由でcloneする方法
 1. .gitconfigファイルに、InsteadOfを記述する
 1. [2019/02/20 編集中]
