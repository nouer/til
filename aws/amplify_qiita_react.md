---
title: 2019年12月版 AWS Amplify + AppSync + Cloud9 + React でとりあえず動くまでの手順
tags: amplify AppSync React.js cloud9 CodeCommit
author: nouernet
slide: false
---
# 目的
  1. Cloud9上での aws amplify, aws appsync を利用する開発環境の構築
  1. React上での subscription による リアルタイムデータ配信アプリの構築
  1. amplify の機能による S3+CloudFlont でのアプリのデプロイ

##### [Vue.js バージョンはこちら](https://qiita.com/nouernet/items/02812ad93d23d86ed05b)

# 前提  
  1. 利用するリージョンは ap-northeast-1  
  1. CodeCommitのリポジトリ名は ampplify_test_react
  1. amplifyで利用するiamユーザは amplify-test-user
  1. アプリ名はmytodo
  1. api名はmytodoapi

# 注意
  この投稿は @aws_amplify/api, @aws_amplify/pubsub パッケージを利用しています。 <br/><font color="red">aws_amplify, aws_amplify_vue パッケージと同時に利用することはできません。</font>

# 構築手順
<ol>
<li>CodeCommitへのGitリポジトリ作成  
    * 'amplify_test_react'を使用

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
$ git clone ssh://git-codecommit.ap-northeast-1.amazonaws.com/v1/repos/amplify_test_react
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

</li></ol><li>react のインストールとプロジェクトの作成 

```console
$ npx create-react-app mytodo
$ cd mytodo
```   

</li><li>アプリケーションを実行して確認

```console
$ npm start
```

  メニューの Preview -> Preview Running Application を実行  
  Cloud9内のブラウザでReactのセットアップが完了していることを確認

</li><li>SecurityErrorが表示される場合

以下のエラーが表示される場合は、React Scriptの問題

```
SecurityError: Failed to construct 'WebSocket': An insecure WebSocket connection may not be initiated from a page loaded over HTTPS.
```

対応するには React Script 3.3.0 を利用しないようにする  
以下の通り React Script 3.2.0 を利用するにうにpackage.jsonを修正してインストールする

```package.json
- "react-scripts": "3.3.0"
+ "react-scripts": "3.2.0"
```

参考： [create-react-appで作ったアプリがhttpsだと動かない](https://qiita.com/uemuram/items/a8f727b780bfd115bbaf)

</li><li>aws-amplify をインストール

```console
$ npm install @aws-amplify/api
$ npm install @aws-amplify/pubsub
$ npm install aws-amplify-react
```

</li><li>amplify の初期設定

```console
$ amplify init

Note: It is recommended to run this command from the root of your app directory
? Enter a name for the project mytodo
? Enter a name for the environment dev
? Choose your default editor: Vim (via Terminal, Mac OS only)
? Choose the type of app that you're building javascript
Please tell us about your project
? What javascript framework are you using react
? Source Directory Path:  src
? Distribution Directory Path: build
? Build Command:  npm run-script build
? Start Command: npm run-script start
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
? Provide API name: mytodoapi
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
| Api      | mytodoapi     | Create    | awscloudformation |
```    

</li><li>バックエンドに api の追加内容を反映

```console
$ amplify push

Current Environment: dev

| Category | Resource name | Operation | Provider plugin   |
| -------- | ------------- | --------- | ----------------- |
| Api      | mytodoapi     | Create    | awscloudformation |

? Are you sure you want to continue? Yes
? Do you want to generate code for your newly created GraphQL API Yes
? Choose the code generation language target javascript
? Enter the file name pattern of graphql queries, mutations and subscriptions src/graphql/**/*.js
? Do you want to generate/update all possible GraphQL operations - queries, mutations and subscriptions
 Yes
? Enter maximum statement depth [increase from default if your schema is deeply nested] 2
```

</li><li>mytodo を修正  
<ol><li>App.js を修正

```App.js
import React, { useEffect, useReducer } from 'react';

import API, { graphqlOperation } from '@aws-amplify/api';
import PubSub from '@aws-amplify/pubsub';

import { createTodo } from './graphql/mutations';
import { listTodos } from './graphql/queries';

import awsconfig from './aws-exports';
import './App.css';

// Configure Amplify
API.configure(awsconfig);
PubSub.configure(awsconfig);

// Action Types
const QUERY = 'QUERY';

const initialState = {
  todos: [],
};

const reducer = (state, action) => {
  switch (action.type) {
    case QUERY:
      return {...state, todos: action.todos};
    default:
      return state;
  }
};

async function createNewTodo() {
  const todo = {
    name: "New Todo Title",
    description: "do something at " + Date()
  }
  await API.graphql(graphqlOperation(createTodo, { input: todo }));
}

function App() {
  const [state, dispatch] = useReducer(reducer, initialState);

  useEffect(() => {
    async function getData() {
      const todoData = await API.graphql(graphqlOperation(listTodos));
      dispatch({ type: QUERY, todos: todoData.data.listTodos.items });
    }
    getData();
  }, []);

  return (
    <div>
    <div className="App">
      <button onClick={createNewTodo}>Add Todo</button>
    </div>
    <div>
      {state.todos.length > 0 ? 
        state.todos.map((todo) => <p key={todo.id}>{todo.name} : {todo.description}</p>) :
        <p>Add Todo</p> 
      }
    </div>
  </div>
  );
}

export default App;
```

</li><li>実行してブラウザでTodoが追加されることを確認

```console
$ npm start
```

  Add Todoボタンをクリックしたあと、リロードすることでTodoが追加されていることが確認できる

</ol></li><li>subscription を利用してみる  
<ol><li>App.js を修正

```App.js
import React, { useEffect, useReducer } from 'react';

import API, { graphqlOperation } from '@aws-amplify/api';
import PubSub from '@aws-amplify/pubsub';

import { createTodo } from './graphql/mutations';
import { listTodos } from './graphql/queries';
import { onCreateTodo } from './graphql/subscriptions';

import awsconfig from './aws-exports';
import './App.css';

// Configure Amplify
API.configure(awsconfig);
PubSub.configure(awsconfig);

// Action Types
const QUERY = 'QUERY';
const SUBSCRIPTION = 'SUBSCRIPTION';

const initialState = {
  todos: [],
};

const reducer = (state, action) => {
  switch (action.type) {
    case QUERY:
      return {...state, todos: action.todos};
    case SUBSCRIPTION:
      return {...state, todos:[...state.todos, action.todo]};
    default:
      return state;
  }
};

async function createNewTodo() {
  const todo = {
    name: "New Todo Title",
    description: "do something at " + Date()
  }
  await API.graphql(graphqlOperation(createTodo, { input: todo }));
}

function App() {
  const [state, dispatch] = useReducer(reducer, initialState);

  useEffect(() => {
    async function getData() {
      const todoData = await API.graphql(graphqlOperation(listTodos));
      dispatch({ type: QUERY, todos: todoData.data.listTodos.items });
    }
    getData();
    const subscription = API.graphql(graphqlOperation(onCreateTodo)).subscribe({
        next: (eventData) => {
          const todo = eventData.value.data.onCreateTodo;
          dispatch({ type: SUBSCRIPTION, todo });
        }
      });
  
    return () => subscription.unsubscribe();
  }, []);

  return (
    <div>
    <div className="App">
      <button onClick={createNewTodo}>Add Todo</button>
    </div>
    <div>
      {state.todos.length > 0 ? 
        state.todos.map((todo) => <p key={todo.id}>{todo.name} : {todo.description}</p>) :
        <p>Add Todo</p> 
      }
    </div>
  </div>
  );
}

export default App;
```

</li><li>実行して２つのブラウザで同期的にTodoが追加されることを確認

</ol></li><li>Hosting の準備

```console
$ amplify add hosting

? Select the environment setup: DEV (S3 only with HTTP)
? hosting bucket name mytodo-20191223025707-hostingbucket
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
| Api      | mytodoapi       | No Change | awscloudformation |
```  

</li><li>バックエンドに Hosting の追加内容を反映

```console
$ amplify push

Current Environment: dev

| Category | Resource name   | Operation | Provider plugin   |
| -------- | --------------- | --------- | ----------------- |
| Hosting  | S3AndCloudFront | Create    | awscloudformation |
| Api      | mytodoapi       | No Change | awscloudformation |
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

amplify delete した後、再度 amplify init で作成し直す場合は、aws-exports.js ファイルを削除しておく。init や add で更新されない。

amplify init したアプリを deleteせずに再度initする場合、CloudFormation上から削除できなくなるので、注意。

<!--
</li><li>auth の追加を準備

Cognitoによる認証機能の追加

```console
$ amplify add auth

Using service: Cognito, provided by: awscloudformation
 
 The current configured provider is Amazon Cognito. 
 
 Do you want to use the default authentication and security configuration? Default configuration
 Warning: you will not be able to edit these selections. 
 How do you want users to be able to sign in? Username
 Do you want to configure advanced settings? No, I am done.
```
</li><li>auth の追加内容確認

```console
$ amplify status

Current Environment: dev

| Category | Resource name   | Operation | Provider plugin   |
| -------- | --------------- | --------- | ----------------- |
| Auth     | mytodo7e022658  | Create    | awscloudformation |
| Api      | mytodoapi       | No Change | awscloudformation |
| Hosting  | S3AndCloudFront | No Change | awscloudformation |
```    

</li><li>バックエンドに auth の追加内容を反映

```console
$ amplify push

Current Environment: dev

| Category | Resource name   | Operation | Provider plugin   |
| -------- | --------------- | --------- | ----------------- |
| Auth     | mytodo7e022658  | Create    | awscloudformation |
| Api      | mytodoapi       | No Change | awscloudformation |
| Hosting  | S3AndCloudFront | No Change | awscloudformation |
```
</li>

-->

# 参考
1. [【お手軽ハンズオンで AWS を学ぶ】AWS Amplify で Todo アプリを作ろう！ AWS AppSync ＆ Amazon DynamoDB によるリアルタイムメッセージング](https://masakanou.hatenadiary.org/entry/20080126/p3)

1. [AWS Amplify Getting Start](https://aws-amplify.github.io/docs/js/start)

1. [create-react-appで作ったアプリがhttpsだと動かない](https://qiita.com/uemuram/items/a8f727b780bfd115bbaf)
