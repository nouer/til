---
title: 2019年12月版 Cloud9 + Vue でとりあえず動くまでの手順
tags: vue.js cloud9
author: nouernet
slide: false
---

# 目的

  1. Cloud9上での vue app の開発環境の構築

# 前提  

  1. 利用するリージョンは ap-northeast-1  
  1. アプリ名は myapp

# 構築手順
<ol>
<li>Cloud9の開発環境作成  

  aws consoleで作成

</li><li>nodeのインストール

  最新、または、好みのバージョンを確認

```console
$ nvm ls-remote
```
  指定したバージョンでインストールを実行

```console
$ nvm install 指定のバージョン
```

今回は v13.5.0 をインストール

```console
$ nvm install v13.5.0
```

</li><li>vue cli のインストール

```console
$ npm install @vue/cli
```

</li><li>vue project の作成

```console
$ vue create myapp 
$ cd myapp
```

</li><li>vue app を起動して確認（失敗）

```console
$ npm run serve 
```

  メニューの Preview -> Preview Running Application を実行  
  <font color="red">Invalid Host header と表示されアクセスできない</font>

</li><li>vue config の作成

vue.config.js を以下の内容で myapp のルートに作成する

```vue.config.js
module.exports = {
  devServer: {
    disableHostCheck: true
  }
}
```

</li><li>vue app を起動して確認

```console
$ npm run serve 
```

  メニューの Preview -> Preview Running Application を実行  
  Vueアプリが表示される

</li>
