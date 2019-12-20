# aws amplify, aws appsync の環境構築
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
1. CodeCommitへのGitリポジトリ作成  
    'amplify_test'を使用
1. Cloud9の開発環境作成  
    aws consoleで作成
1. Cloud9の一時認証の利用を解除  
    1. ツールバーのAWS Cloud9でメニューを開く
    1. Preferencesを開く
    1. AWS SETTINGSを開く
    1. Credentialsを開く
    1. AWS managed temporary credentials をオフにする
1. 開発環境とGitリポジトリの連携  
    今後のコマンドはCloud9のコンソールで実行
    ```console
    $ git clone ssh://git-codecommit.ap-northeast-1.amazonaws.com/v1/repos/amplify_test
1. nodeのインストール
    ```console
    $ nvm ls-remote
    $ nvm install 指定のバージョン
    ```
1. aws amplify cli のインストール
    ```console
    $ npm install -g @aws-amplify/cli
    ```
1. amplify を設定
    1. configureを実行
        ```console
        $ amplify configure
        ```
    1. 管理者アカウントでaws consoleをブラウザで開く
        ```console
        Follow these steps to set up access to your AWS account:
        
        Sign in to your AWS administrator account:
        https://console.aws.amazon.com/
        Press Enter to continue
        ``` 
    1. 利用するリージョンを選択、ユーザ名を入力  
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
    1. ユーザ作成で得ることのできた accessKeyId と secretAccessKey を入力
        ```console
        Enter the access key of the newly created user:
        ? accessKeyId:  ********************
        ? secretAccessKey:  ****************************************
        This would update/create the AWS Profile in your local machine
        ? Profile Name:  default
        
        Successfully set up the new user.
        ```
1. vue cli / vue cli init のインストール  
    ```console
    $ npm install -g @vue/cli
    $ npm install -g @vue/cli-init
    ```   
1. vue project の作成
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
1. Cloud9でブラウザ表示できるように設定を修正
    ```build/webpack.dev.conf.js
    - host: HOST || config.dev.host,
    - port: PORT || config.dev.port,
    + host: '0.0.0.0',
    + port: '8080',
    + disableHostCheck: true,
    ```
1. アプリケーションを実行
    ```console
    $ npm run dev
    ```
1. メニューの Preview -> Preview Running Application を実行  
  Cloud9内のブラウザでVueのセットアップが完了していることを確認
1. aws-amplify をインストール
    ```console
    $ npm install @aws-amplify/api
    $ npm install @aws-amplify/pubsub
    ```
1. amplify の初期設定
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
1. amplify の初期設定確認
    ```console
    $ amplify status

    Current Environment: dev

    | Category | Resource name | Operation | Provider plugin |
    | -------- | ------------- | --------- | --------------- |
    ```
1. api の追加準備
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
1. api の追加内容確認
    ```console
    $ amplify status

    Current Environment: dev

    | Category | Resource name | Operation | Provider plugin   |
    | -------- | ------------- | --------- | ----------------- |
    | Api      | myappapi      | Create    | awscloudformation |
    ```    
1. バックエンドに api の追加内容を反映
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
1. myapp を修正  
    main.js を修正
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
    App.vue を修正
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
    router/index.js を修正
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
    components/Test01.vue を追加
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
1. subscription を利用してみる  
  Test01.vue を修正
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
1. Hosting の準備
    ```console
    $ amplify add hosting

    ? Select the environment setup: DEV (S3 only with HTTP)
    ? hosting bucket name myapp-20191220055634-hostingbucket
    ? index doc for the website index.html
    ? error doc for the website index.html
    ```
1. Hosting の追加内容の確認
    ```console
    $ amplify status
    
    Current Environment: dev
    
    | Category | Resource name   | Operation | Provider plugin   |
    | -------- | --------------- | --------- | ----------------- |
    | Hosting  | S3AndCloudFront | Create    | awscloudformation |
    | Api      | myappapi        | No Change | awscloudformation |
    
    ```  
1. バックエンドに Hosting の追加内容を反映
    ```console
    $ amplify push

    Current Environment: dev

    | Category | Resource name   | Operation | Provider plugin   |
    | -------- | --------------- | --------- | ----------------- |
    | Hosting  | S3AndCloudFront | Create    | awscloudformation |
    | Api      | myappapi        | No Change | awscloudformation |
    ? Are you sure you want to continue? Yes
    ```
1. バックエンドの Hosting を公開
    ```console
    $ amplify publish
    ```
1. 作成した amplify のリソースを削除
    ```console
    $ amplify delete
    ```
