# Visual Studio Code til
## 除外設定
<pre>
  // ファイルブラウザに表示しない
  "files.exclude": {
    "**/.git": true,
    "**/.svn": true,
    "**/.DS_Store": true
  },

  // ファイルブラウザには表示するが、検索から除外する
  "search.exclude": {
    "**/node_modules": true,
    "**/bower_components": true,
    // 例えばキャッシュディレクトリを追加すると、検索で余計なファイルが出てこなくて便利
    "**/tmp/cache": true
  },
</pre>

## WSLのgitを利用する
  1. 以下のexeをダウンロードしておく  
    [andy-5/wslgit/releases](https://github.com/andy-5/wslgit/releases)
  1. settings.jsonを記述
<pre>
   {
       "terminal.integrated.shell.windows": "C:\\Users\\username\\AppData\\Local\\Microsoft\\WindowsApps\\ubuntu.exe",
       "git.path": "C:\\tools\\wslgit.exe"
   }
</pre>

  