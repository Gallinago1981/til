# Jenkins

## 基調講演

- 利用者数は2年間で9倍

- Jenkins pipeline
  - githubにjenkinsの手順を記述したpipelineに移りつつある
  - iterative
  - Transformational
  - pipelineの実行部分を書き換えてパフォーマンス向上や可用性の向上の取り組みが行われている
- Blue Ocean
  - モダンなフロントエンドアプリとサーバサイドの切り分けている

- Ever Green
  - Jenkinsを劇的に簡単にしなければならない
  - 最初からCI/DIが使えるシステムを作りたい
  - 必要なものはパッケージされているようにしたい
  - 利用者は必要なものを取り出すだけ
  - GitHub, Dockerが最初から使えるとかにしたい
  - Goal
    - Chromeの自動updateのようなものが必要
    - コミュニティのサーバと接続し障害情報などが連携されるようにする
    - 自動Update怖い？
      - update失敗時のrollback
      - 障害のコミュニティへの連携
        - 個人情報が入っていないようにしなければならない
    - 本番機能のモニターし改善した物をDeployしている(Amazonは30秒に1回とか)

- Configuration as code
  - Jenkinsの変更をpush -> pull request -> releaseの流れを作りたい
  - 設定変更が記録されていないから、変更するのが怖い
    - snow break
    - 属人化するのをやめさせたい
  - 設定ファイルをyamlに書いてgitで管理したらいいんじゃない？

- cloud native jenkins
  - 大規模に使っている人向け
  - 目標
    - Jenkinsの管理者は属人化している
    - 気軽にインストールして、1人 -> チーム -> 複数チームと拡大していった際にスケーリングしていくものを作りたい
  - buildした成果物をAmazon S3に保存するとか
  - ビルドログをAmazon watchに送るとか
  - 分散かされたJenkins
    - k8sで実現する
  - コミュニティの中で分科会を作って意見交換をしている

- Jenkins X
  - k8sが流行っているね
  - k8sは荒削りのシステムで更新が多い
  - 利用方法を学ぶ必要があるが正解を見出すのが難しい
  - k8sのbest practiceを見出さなかきゃいけない
  - jenkins x でk8sをプロダクトで利用することで幸せになれる？
  - k8sに関する様々なベストプラクティスの集大成
  - Jenkins -> 地図
  - Jenkins X -> 新幹線
    - ほとんどの人が使いたいというものを用意する（BestPracticeの集大成)

- まとめ
  - Jenkinsも色々と新しい機能が付与されているので積極的に使って欲しい

## Accelerate with Jenkins X

- 開発者がクラウドでの自動化を促進するためのツール
- ソフトウェア開発を支援

- オープンソースのツールを使って開発されている
- k8sに特化している
- k8sを拡張したもの
- 拡張する際に使用する言語はなんでもいい？
- k8sは難しいけど、Jenkins Xを使うことで用意になる
- CLI, IDE Toolがついてきている

### Accelerate
- いい本だよ
- DevOpsについてリサーチしたものが書かれた本
- 数年分のDevOpsの現状
- 4つの指標
  - デプロイの頻度
  - Chenge Reed Time
  - MTTR ( Mean Time To Recovery)
  - デプロイんの失敗頻度 

- 優れたチームでは46倍のデプロイ回数、ReadTimeは2600倍, 失敗頻度は1/7

- GitOps
  - あらゆる変更はGitで管理されるべき
  - Jenkins Xは
  - デプロイプロセスを改善する
    - CI/DIパイプラインを自動化
  - プレビュー環境もあるで
    - 作業中のブランチをmaster mergeする前に確認することができる環境
  - JankinS X は Trunkベースの開発を推奨
  - BranchのLifeTimeは短く
  - k8sの機能を活かしていく
  - マイクロサービスの開発サポートを行う

- アーキテクチャ
  - ステージングと本番が両方用意されている
  - Jenkinsのパイプラインを使える

- なぜk8sを使うとメリットがあるのか
  - 特定のベンダーに依存しない
  - アプリケーションを構築ごプラットフォームを自由に選べる
  - k8sはある意味、標準化の役割を担っている




## Accelerate with Jenkins X

- Jenkins ジャーニー
  - Dya1 始まり
    - ビルドの並列化ができない
    - 結果がJenkins上にしかない
  - Day100 
  - Day150
    - 成果物をAWSS3などに逃すとかが必要
    - masterに成果物を持たないは選択肢の１つ
  - Day300
    - ジョブ間での必要な依存が異なる
    - コンテナの中でジョブを実行することで各ジョブが隔離される
  - Day310
    - GitOps
  - Day365
    - ノードを追加せずk8sなどで管理を行う
    - コンテナ管理も不要になる
  - Day412
    - 互換性のないプラグインが必要とする場合
    - HELM
      - なにこれ？
      - パッケージマネージャー
      - Jenkinsの管理もできるの？
      - 様々なOSSの設定をコードで定義し、何回でもデプロイすることができる
      - Build
        - install command
        - helm install stable/jenkins -f values.yaml
        - values,.yamlに必要なプラグインの情報を設定することができる
        - k8sクラスタを作りhelmで構築することで同じ環境を別コンテナで作れる
    - k8s
      - ノードプールのオートスケール
        - ワーカーのスケールアウトを意識せずできる
      - 一時的なワークスペース
    - Jenkinsfile
      - k8sのmanifestを直接かけるし、外だしすることもできる
    - Colud Build
      - 1日120分の無料ビルド枠
  
  - 安全で信頼できるデプロイメントのためになにが必要？
    - kubectl apply -f manifests/
    - どこのクラスタにデプロイするのかを選択

  - KUBECONFIGを認証ファイルとしてJenkinsに引き渡す
    - k8s CLI Plubginsを利用する？
    - KubeConfigファイルが必要？
  - Blue/Green Deployment
    - デプロイメントにラベルを付与する
      - ラベルがついているpodに引き当てる

  - JenkinsをCIにSpinnakerをGKEの冗長性のあるCDに
    - Spinnaker
      - オープンソースのマルチクラウド向け継続的デリバリー

## AWSとJenkinsを活用して1年間で約500回商用デプロイした話とKubernetes活用

- とあるWEBサービス開発プロジェクトの概要
  - B2C向け新規Web ECサービス
  - 複数の会社が参加している
  - 頻繁あ変更に耐えうるアーキテクチャ設計
    - GIt/Jenkins
    - Swagger
      - インクリメンタルなAPI設計
    - AWS / Ansible
  - Swagger
    - REST APIを記述するための企画
    - Swagger Editor
    - Swagger UI

- 開発フローとビルドパイプライン
  - ブランチ戦略はGitLaフローを採用
  - Test NGはpullrequest NG
  - Jenkins FileとMultibranch Pipelineでジョブ定義
  - Swaggerのテンプレートを魔改造した話
  - 他者ヘンダーへ越境して1日約10回リリースを達成した話

- Jenkins運用中に発生した事件後
  - スローテスト問題によるJenkinsのビルド待ち行列
    - 開発は進むと1回のCI実行に20分近くかかるようになった
    - PR発行からMasterマージまでの時間がかかった
    - Field InjectionからConstractor InjectionにApplicationContextno再ロード時間を短縮
    - パイプラインのうち同時実行可能な部分を並列化
    - parallelディレクティブを利用し並列実行した
  - Disk fUll
    - ビルド結果を定期的に削除する設定を追加した
    - HDDの容量を増やして対応した
  - Jenkinおじさん問題
    - Jenkinsのジョブがブラックボックス化し有識者しかメンテナンスができない

- まとめ
  - プロジェクト当初からCI/CDパイプラインを本格開始前に準備できていたこと
    - 開発後からの自動化は高コスト
  - AWSを使うことでAnsibleとImmutable Infrastractureが構築できた
    - 差分は環境変数くらい
  - Jenkinsの運用がブラックボックスにならないように透明化しておく
  - 検証環境で自動デプロイの実績をつみそのまま商用環境に持っていく

- Jenkinsとk8sで動かす話す
  - 開発環境をk8sで運用している
  - docker-composeで運用していた開発環境をk8s化
  - k8s Dashboardでpodのリソース・ログ確認など運用が容易になった
  - GKEのdashboardと同じ
  - EC2インスタンスにSSHでアクセスするのはめんどいよね
  - kops ケーオぷす でk8sを構築　

- Jenkinsをk8sで動かす方法
  - master /agent 共にk8s場でpodを動かす
  - AWS code buildに外だし
  - jenkinsからはプラグイン経由でビルド実行できる
  - 最大20並列で実行する
  - ビルド時間単位での従量課金制
   

- 

