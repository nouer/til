# 徹底攻略 AWS認定 ソリューションアーキテクト – アソシエイト教科書 徹底攻略シリーズ
## AWSサービス全体の概要
 - Well-Architectedフレームワーク  
  「運用上の優秀性」、「セキュリティ」「信頼性」「パフォーマンス効率」「コスト最適化」を5つの柱として設計原則のこと  
  ベストプラクティスに沿っているかを確認するためのチェックリストがある
  - AWSインフラストラクチャの概要  
   リージョンとリージョンを構成するアベイラビリティーゾーンから成る
   エッジロケーションと呼ばれるCloudFrontやRoute53を提供する、ユーザに物理的に近いデータセンターも存在する
  - AWSサービスの範囲  
    - グローバルサービス  
     IAMやCloudFron、Route53
    - リージョンサービス  
     VPCやDynamoDB、Lambda
    - アベイラビリティゾーンサービス  
     VPCサブネット、EC2、RDS

    グローバルサービス内にリージョンサービスが、リージョンサービス内にアベイラビリティゾーンサービスが存在している  
    $3はグローバルサービスだが、データは特定のリージョンに保管される
  - アクセス制御サービス
    - IAMサービス  
     AWSアカウントの管理  
     IAMユーザおよびIAMグループの管理  
     IAMポリシーによる権限管理  
    - IAMサービスを通じたAWSの操作
      - WEBブラウザでログインして操作  
       ログインとパスワード(2重認証も可能）での認証  
      - AWS CLIで操作
       アクセスキーIDとシークレットアクセスキー(2重認証も可能)での認証
       IAMロールでの認証が推奨
      - AWS SDKでAPIから操作  
       アクセスキーIDとシークレットアクセスキー(2重認証も可能)での認証
       IAMロールでの認証が推奨
  - ネットワークサービス
    - VPCの構成要素
      - サブネット
      - インターネットゲートウェイ
      - ルートテーブル
      - NATゲートウェイ
      - NATインスタンス
      - バーチャルプライベートゲートウェイ
      - VPCフローログ
      - Elastic IP(EIP)
      - VPCピアリング接続
      - VPCエンドポイント  
        ネットワークレイヤーとアプリケーションレイヤーの2種類のVPCエンドポイントがある  
        ゲートウェイ型はルートテーブルに指定されているターゲットを追加することでS3やDyanamoDBにアクセスする際にインターネットを経由せずにAWS内のプライベート接続を利用できる  
        インターフェイス型はAWS PrivateLinkと呼ばれ、AWSへのAPI接続する際にインターネットを経由せずにAWS内のプライベート接続を利用できる
      - セキュリティグループ  
        インスタンス単位で設定するファイアウォール（ENI毎）
        デフォルトはすべて拒否  
        すべてのルールが適用される  
        ステートフル
      - ネットワークACL  
        サブネット単位で設定するファイアウォール  
        デフォルトはすべて許可    
        主に異なるサブネット間の通信を制御する  
        サブネットに１つのネットワークACLを設定できる  
        ルールの番号順で適用される
        ステートレス
    - VPC内で利用できるネットワークサービス
      - Elastic Load Balancing(ELB)
        - 3つのタイプが存在する  
          Classic Load Balancer(CLB)  
          Application Load Balancer(ALB)  
          Network Load Balancer(NLB)
        - ELBの特徴
          - 高可用性
          - 自動スケーリング
          - セキュリティ機能  
            SSL複合機能
          - ヘルスチェックとモニタリング
          - 外部ELBと内部ELB
          - クロスゾーン負荷分散
      - Auto Scaling
    - その他のネットワークサービス
      - Route 53
      - Direct Connect
      - Virtual Private Gateway
      - CloudFront  
        CDNサービス、オリジンとしてELBやEC2, S3などを指定できる  
        SSL化できる  
        署名付きURLを発行でき、一定時間だけアクセスを許可するURLを発行できる  
        カスタムエラーページを設定できる  
        アクセスユーザーの地域情報から、地域限定のアクセス許可／拒否を行うことができる  
        ストリーミング配信ができる
  - コンピューティングサービス
    - EC2  
      インスタンスメタデータが取得できる、http://169.254.169.254/latest/meta-data/
    - AMI
    - Lambda
    - API Gateway
    - EMR(Amazon Elastic MapReduce)
    - ECS(Amazon ElasticContainer Service)
    - VM Import/Export
  - ストレージサービス
    - S3(Amazon S3)
    - EBS(Amazon EBS)
    - インスタンスストア（エフェメラルディスク）
    - EFS(Amazon Elastic File System)
    - SGW(AWS Storage Gateway)  
      - キャッシュ型ボリュームゲートウェイ  
        S3に保存される。アクセス頻度の高いデータはローカルにキャッシュされて高速でアクセスできる。インターフェイスはiSCSI。
      - 保管型ボリュームゲートウェイ  
        データをスナップショットとしてS3に格納する。インターフィエイスはiSCSI。
      - テープゲートウェイ  
        物理テープ装置の代替としてデータをS3(Glacier）にかくのうする。インターフェイスはiSCSI。
      - ファイルゲートウェイ  
        データをS3に直接オブジェクトとして格納する。インターフェイスはNFS。
    - AWS Import/Export
    - AWS Import/Export Snowball
  - データベースサービス
    - RDS  
      サポートされるデータベースエンジン  
        - Amazon Aurora(Aurora)
        - PstgreSQL
        - MySQL
        - MariaDB
        - Oracle Database
        - SQL Server 

      リードレプリカが利用できるのは、MySQL, MariaDB, PostgreSQL, Aurora  
      リードレプリカはマルチAZや異なるリージョンでも利用可能
      SSL接続でRDSを利用できるのは、MySQL, MariaDB, SQL Server, Oracle, PostgreSQL  
    - DynamoDB  
      デフォルトは結果整合性モデル（読み取りに一貫性はない）だが、読み取り一貫性オプションを付けることで、
      一貫性を保つことができる
    - Redshift  
      マネージド型データウェアハウスサービス  
      大量のデータの集計・分析に向いている。
    - ElastiCache
  - データ通知・連携処理サービス
    - 通知処理
      - Amazon Simple Email Service(SES)
        APIで、メールを利用して通知を行うことができる
      - Amazon Simple Notification Service (SNS)
        HTTPSなどのさまざまなプロトコルでアプリケーションから送信することができる
        CloudWatchやSQS、LambdaをはじめとしたAWSのさまざまなサービスへの通知・連携も可能
      - SNSの構成
        - トピック
        - サブスクライバ（購読者）
        - パブリッシュ（メッセージの配信）
    - メッセージキューイング処理
      - Amazon Simple Queue Service(SQS)
    - パイプライン処理
      - Amazon Data Pipeline(Data Pipeline)
        - データのETL処理をスケジュール機能で自動化できる
        - データの順次処理をワークフロー形式で定義
        - 処理の成功・失敗などのイベント通知が可能
        - オンプレとの連携が可能
    - ストリーミング処理
      - Aamazon Kinesis
        - Kinesisの構成
          - Kinesis Data Streams
          - Kinesis Data Firehose
          - Kinesis Data Analytics
  - 構成管理サービス  
    - 構成管理
      - プロビジョニング
      - デプロイ
    - Amazon CloudFormation
      - テンプレート
      - スタック
    - Amazon Elastic Beanstalk
    - AWS OpsWorks
    - AWS CodeDeploy
  - 運用管理サービス
    - CloudWatchの概要
      - EC2のメトリクス
      - 標準メトリクス
        - CPUUtilization
        - DiskReadOps
        - DisReadBytes
        - NetworkIn
      - カスタムメトリクス
    - CloudWatchの監視間隔と保存期間
      - 基本モニタリング  
        無料、5分間隔、最大15ヶ月保存
      - 詳細モニタリング  
        有料、1分間隔、最大15ヶ月保存
      - 監視間隔はAWSサービスによって異なる
    - CloudWatchアラームによるアラームとアクション設定
      - CloudWatchの3つの状態
        - OK
        - ALARM
        - INSUFFICIENT-DATA
    - CloudWatch Eventsによるイベント駆動型監視とアクション設定
    - その他の運用管理サービス
      - CloudWatch Logs
      - CloudTrail
      - VPCフローログ
      - AWS Config
      - AWS Systems Manager
      - AWS Trusted Advisor
      
## AWSにおける高可用アーキテクチャ

## AWSにおけるパフォーマンス
## AWSにおけるセキュリティ設計
## AWSにおけるコスト最適化
## AWSにおける運用管理
## 