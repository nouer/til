# Amazon ECS
  Amazon Elastic Container Service  
  Dockerコンテナインスタンスのクラスター管理サービス  
  EC2上での起動と、Fargate上での起動のタイプがある


# ECSのネットワークモード
- bridge  
 デフォルト、Dockerのブリッジ機能が使われる  
 EC2の任意のポートをコンテナのポートにマッピングする  
 ENIを複数のタスクが共有する  
 ENI共有＝SecurityGroupも共有される  
 ENI共有＝通信帯域も共有  
 
- host  
 Dockerのホスト機能が使われる  
  1つのホストで同じポートを利用するタスクを複数起動することはできない
  
- awsvpc  
 ENIがタスクごとに直接アタッチされる  
 タスク間でのポートマッピングを考えなくて良い  
 ENI独立＝通信帯域が別  
 ENI独立＝SecurityGroupが別  
 ECSインスタンスとタスクでSecurityGroupを分けることもできる  
 ALB/NLBにIPターゲットとして登録ができる  
 
- なし  
 外部ネットワークへの接続なし