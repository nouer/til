---
title: 2019年12月版 AWS Amplify + AppSync + Cloud9 + Vue.js でとりあえず動くまでの手順
tags: amplify AppSync Vue.js cloud9 CodeCommit
author: nouernet
slide: false
---
# 目的
  1. Cloud9上での aws amplify, aws appsync を利用する開発環境の構築
  1. vue上での subscription による リアルタイムデータ配信アプリの構築
  1. amplify の機能による S3+CloudFlont でのアプリのデプロイ

# 前提  
  1. 利用するリージョンは ap-northeast-1  
  1. amplifyで利用するiamユーザは amplify-test-user
  1. アプリ名はmyapp
  1. api名はmyappapi

# 構築手順
<ol>
<li>CodeCommitへのGitリポジトリ作成  
    * 'amplify_test'を使用

</li><li>Cloud9の開発環境作成  
    * aws consoleで作成

</li><li>Cloud9の一時認証の利用を解除  
    <ol><li>ツールバーのAWS Cloud9でメニューを開く
    </li><li>Preferencesを開く
    </li><li>AWS SETTINGSを開く
    </li><li>Credentialsを開く
    </li><li>AWS managed temporary credentials をオフにする

</ol></li><li>開発環境とGitリポジトリの連携  
  
```console
$ git clone ssh://git-codecommit.ap-northeast-1.amazonaws.com/v1/repos/amplify_test
```  
  
</li><li>nodeのインストール
  最新、または、好みのバージョンを確認

```console
$ nvm ls-remote
```
  指定したバージョンでインストールを実行

```console
$ nvm install 指定のバージョン
```

</li><li>aws amplify cli のインストール

```console
$ npm install -g @aws-amplify/cli
```

</li><li>amplify の初期設定
    <ol><li>configureを実行

```console
$ amplify configure
```

</li><li>管理者アカウントでaws consoleをブラウザで開く

```console
Follow these steps to set up access to your AWS account:

Sign in to your AWS administrator account:
https://console.aws.amazon.com/
Press Enter to continue
``` 

</li><li>利用するリージョンを選択、ユーザ名を入力  
出力されたurlをaws cosoleを開けたブラウザで開いてユーザを作成  
デフォルトの値は入っているので作成を完了するだけ

```console
Specify the AWS Region
? region:  ap-northeast-1
Specify the username of the new IAM user:
? user name:  amplify-test-user
Complete the user creation using the AWS console
https://console.aws.amazon.com/iam/home?region=undefined#/users$new?step=final&accessKey&userNames=amplify-test-user&permissionType=policies&policies=arn:aws:iam::aws:policy%2FAdministratorAccess
Press Enter to continue
```

</li><li>ユーザ作成で得ることのできた accessKeyId と secretAccessKey を入力

```console
Enter the access key of the newly created user:
? accessKeyId:  ********************
? secretAccessKey:  ****************************************
This would update/create the AWS Profile in your local machine
? Profile Name:  default

Successfully set up the new user.
```

</li></ol><li>vue cli / vue cli init のインストール  

```console
$ npm install -g @vue/cli
$ npm install -g @vue/cli-init
```   

</li><li>vue project の作成

```console
$ mkdir myapp
$ cd myapp
$ vue init webpack .

? Generate project in current directory? Yes
? Project name myapp
? Project description A Vue.js project
? Author 
? Vue build standalone
? Install vue-router? Yes
? Use ESLint to lint your code? No
? Set up unit tests No
? Setup e2e tests with Nightwatch? No
? Should we run `npm install` for you after the project has been created? (recommended) npm

$ cd myapp
```

</li><li>Cloud9でブラウザ表示できるように設定を修正

```build/webpack.dev.conf.js
- host: HOST || config.dev.host,
- port: PORT || config.dev.port,
+ host: '0.0.0.0',
+ port: '8080',
+ disableHostCheck: true,
```

</li><li>アプリケーションを実行

```console
$ npm run dev
```

</li><li>メニューの Preview -> Preview Running Application を実行  
  Cloud9内のブラウザでVueのセットアップが完了していることを確認

</li><li>aws-amplify をインストール

```console
$ npm install @aws-amplify/api
$ npm install @aws-amplify/pubsub
```

</li><li>amplify の初期設定

```console
$ amplify init

Note: It is recommended to run this command from the root of your app directory
? Enter a name for the project myapp
? Enter a name for the environment dev
? Choose your default editor: Vim (via Terminal, Mac OS only)
? Choose the type of app that you're building javascript
Please tell us about your project
? What javascript framework are you using vue
? Source Directory Path:  src
? Distribution Directory Path: dist
? Build Command:  npm run-script build
? Start Command: npm run-script serve
```

</li><li>amplify の初期設定確認

```console
$ amplify status

Current Environment: dev

| Category | Resource name | Operation | Provider plugin |
| -------- | ------------- | --------- | --------------- |
```

</li><li>api の追加準備

```console
$ amplify add api

? Please select from one of the below mentioned services: GraphQL
? Provide API name: myappapi
? Choose the default authorization type for the API API key
? Enter a description for the API key: 
? After how many days from now the API key should expire (1-365): 365
? Do you want to configure advanced settings for the GraphQL API No, I am done.
? Do you have an annotated GraphQL schema? No
? Do you want a guided schema creation? Yes
? What best describes your project: Single object with fields (e.g., “Todo” with ID, name, description)


? Do you want to edit the schema now? No
```

</li><li>api の追加内容確認

```console
$ amplify status

Current Environment: dev

| Category | Resource name | Operation | Provider plugin   |
| -------- | ------------- | --------- | ----------------- |
| Api      | myappapi      | Create    | awscloudformation |
```    

</li><li>バックエンドに api の追加内容を反映

```console
$ amplify push

Current Environment: dev

| Category | Resource name | Operation | Provider plugin   |
| -------- | ------------- | --------- | ----------------- |
| Api      | myappapi      | Create    | awscloudformation |

? Are you sure you want to continue? Yes
? Do you want to generate code for your newly created GraphQL API Yes
? Choose the code generation language target javascript
? Enter the file name pattern of graphql queries, mutations and subscriptions src/graphql/**/*.js
? Do you want to generate/update all possible GraphQL operations - queries, mutations and subscriptions
 Yes
? Enter maximum statement depth [increase from default if your schema is deeply nested] 2
```

</li><li>myapp を修正  
<ol><li>main.js を修正

```main.js
import Vue from 'vue'
import App from './App'
import API from '@aws-amplify/api'
import PubSub from '@aws-amplify/pubsub'
import awsconfig from './aws-exports'
import router from './router'

API.configure(awsconfig)
PubSub.configure(awsconfig)

Vue.config.productionTip = false

/* eslint-disable no-new */
new Vue({
  el: '#app',
  router,
  components: { App },
  template: '<App/>'
})
```

</li><li>App.vue を修正

```App.vue
<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
</style>
```

</li><li>router/index.js を修正

```router/index.js
import Vue from 'vue'
import Router from 'vue-router'
import Test01 from '@/components/Test01'

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'Test01',
      component: Test01
    }
  ]
})
```

</li><li>components/Test01.vue を追加

```components/Test01.vue
<template>
  <div>
    <button @click="addTodo">Add Todo</button>
    <ul>
      <li v-for="todo in todos" :key="todo.id"> {{todo.name}} - {{todo.description}} </li>
    </ul>
  </div>
</template>

<script>
import API, { graphqlOperation } from '@aws-amplify/api'
import { createTodo } from '../graphql/mutations'
import { listTodos } from '../graphql/queries'
window.LOG_LEVEL = 'VERBOSE'

export default {
  name: 'Test01',
  data () {
    return {
      todos: []
    }
  },
  methods :{
    async addTodo(){
      const todo = {
        name: "New Todo Title",
        description: "do something at " + Date()
      }
      await API.graphql(graphqlOperation(createTodo, { input: todo }))
      this.getData()
    },
    async getData() {
      const todoData = await API.graphql(graphqlOperation(listTodos))
      this.todos = []
      this.todos.push(...this.todos, ...todoData.data.listTodos.items);
    }
  },
  created(){
    this.getData()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
```

</li><li>実行してブラウザでTodoが追加されることを確認

</ol></li><li>subscription を利用してみる  
<ol><li>Test01.vue を修正

```components/Test01.vue
<template>
  <div>
    <button @click="addTodo">Add Todo</button>
    <ul>
      <li v-for="todo in todos" :key="todo.id"> {{todo.name}} - {{todo.description}} </li>
    </ul>
  </div>
</template>

<script>
import API, { graphqlOperation } from '@aws-amplify/api'
import { createTodo } from '../graphql/mutations'
import { listTodos } from '../graphql/queries'
import { onCreateTodo } from '../graphql/subscriptions';

window.LOG_LEVEL = 'VERBOSE'

export default {
  name: 'Test01',
  data () {
    return {
      todos: []
    }
  },
  methods :{
    async addTodo(){
      const todo = {
        name: "New Todo Title",
        description: "do something at " + Date()
      }
      await API.graphql(graphqlOperation(createTodo, { input: todo }))
      //this.getData()
    },
    async getData() {
      const todoData = await API.graphql(graphqlOperation(listTodos))
      this.todos.push(...this.todos, ...todoData.data.listTodos.items);
    },
    subscribe(){
      API.graphql(graphqlOperation(onCreateTodo)).subscribe({
        next: (eventData) => {
          const todo = eventData.value.data.onCreateTodo
          this.todos.push(todo)
        }
      })
    }
  },
  created(){
    this.getData()
    this.subscribe()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
```

</li><li>実行して２つのブラウザで同期的にTodoが追加されることを確認

</ol></li><li>Hosting の準備

```console
$ amplify add hosting

? Select the environment setup: DEV (S3 only with HTTP)
? hosting bucket name myapp-20191220055634-hostingbucket
? index doc for the website index.html
? error doc for the website index.html
```
</li><li>Hosting の追加内容の確認

```console
$ amplify status

Current Environment: dev

| Category | Resource name   | Operation | Provider plugin   |
| -------- | --------------- | --------- | ----------------- |
| Hosting  | S3AndCloudFront | Create    | awscloudformation |
| Api      | myappapi        | No Change | awscloudformation |

```  

</li><li>バックエンドに Hosting の追加内容を反映

```console
$ amplify push

Current Environment: dev

| Category | Resource name   | Operation | Provider plugin   |
| -------- | --------------- | --------- | ----------------- |
| Hosting  | S3AndCloudFront | Create    | awscloudformation |
| Api      | myappapi        | No Change | awscloudformation |
? Are you sure you want to continue? Yes
```

</li><li>バックエンドの Hosting を公開

```console
$ amplify publish
```

</li><li>PublishされたURLを２つのブラウザで開いて同期的にTodoが追加されることを確認

</li><li>作成した amplify のリソースを削除

```console
$ amplify delete
```

</li>

# 参考
1. [AWS Amplify + Vue.js + AppSync + Cognito +その他諸々でリアルタイム更新なサーバレスWebアプリをデプロイ](https://qiita.com/nakayama_cw/items/6d3514b51c5fbf9ba450)

1. [【お手軽ハンズオンで AWS を学ぶ】AWS Amplify で Todo アプリを作ろう！ AWS AppSync ＆ Amazon DynamoDB によるリアルタイムメッセージング](https://masakanou.hatenadiary.org/entry/20080126/p3)

1. [AWS Amplify Getting Start](https://aws-amplify.github.io/docs/js/start)
