# tig
## cygwinでtigのインストール

  - setup.exeで以下をインストールしておく  
    - ncurses
    - libncurses
    - libiconv
  - 以下を実行
<pre>
$ cd 作業ディレクトリ
$ git clone git://github.com/jonas/tig.git
$ cd git
$ make configure
$ CFLAGS="-I/usr/include/ncursesw" LDLIBS="-lcursesw"
# ↓インストール先のディレクトリを記述します 
$ ./configure --prefix="$HOME/tig"
$ make
$ make install
</pre>
