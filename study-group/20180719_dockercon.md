# Docker Tokyo 201807

## docker buildが30倍以上早くなる話
- Buildkit
  - DAG構造を備える中間言語であるLLB を用いる
  - LLBは主にDocker FIleから作られる
  - # syntax = 非標準の命令を利用できる
  - RUN --mout= キャシュするディレクトリを指定できる
    - キャッシュ以外の用途も計画中
  - root権限なしで利用可能
    - user namespaceを使うので/etc/subuidが必要
    - 

  - export DOCKER_BUILDKIT ?

- Docker Application Packages
Docker hubへのpush/pullできる
docker-compse.yamlをdocker hubで共有できる

- 現在のDockerの不満
  - Dockerfileのキャッシュが効きにくい
  - N行目を書き換えると以降が効かない
  - 並列実行ができない
  - sshの鍵をCOPYで置くの危ない。環境変数に書くのも当然危ない

## docker con 報告会

- エンタープライズ色が強い
  - mobyの発表がオープンソースで前回はあった
  - windowsサポートに力を入れている
  - .NET の資産をコンテナ化することに力を入れている
  - dockerも世代交代の時代
- 特定のベンダープラットホームへのロックインを防止する
  - 特定のベンダーに依存しないようにしたいと考えている。

- 運用管理者向けの発表
  - 異なるDokcerクラスた間でのワークロード
    - Docker EE Federation Application Management
      - Dokcer EE / AKS / EKS
  - windowsサーバーをKubernatesでサポート可能
    - .NET アプリケーションのオーケストレーションを行うようにするらしい
    - MSと手を組んでるで

- 開発者向けの発表
  - Dokcer Desktopでアプリ開発テンプレートを使って容易に
    - CLIでDockerを使っている人には必要ないかもしれない
    - Quick StartのためGUIを提供する
    - Application Design Manager
    - 主要なIDEツールとは連携しているらしい
  - コンポーズのエンハンス
    - 環境に関わるものとアプリを分離させる
    - コンポーズのヘルムチャートに変換する？
- EKS(AWS K8s)? AKS(Azure K8s)?

## Docker con pert3
- docker-ce
  - 18.06
    - サポート期間が7か月になる

- 海外イベントへの参加
  - 準備
    - パスポートを準備
    - ESTA(電子渡航認証システム)申請
      - 両親の情報も必要
      - アメリカ行くには必須
      - 有効期間は2年間
    - 航空券、宿泊予約
      - 入国審査では、どこに何しに行くかを聞かれる
  - 心構え
    - 「サンフランシスコ 治安」で検索しよう。治安が悪いところはまぁまぁある。
    - 日本国総領事館が安全の手引きに書いてる
    - 現金は持ち歩かない方がいい
      - ナイフで脅された時に持ち金全部渡した方がいいで
  - 事前に入れるべきアプリ
    - Google翻訳
      - レストランのメニュー表を読ませるのに便利
      - カメラモード最高
    - Uber / Lfty
      - タクシーは基本的に捕まらない
      - オンラインで呼び出した方がいい
    - DockerCon公式アプリ
      - 事前登録とかの登録がある
      - 参加出来ない場合もあるから事前登録が必要
  - 日本からの出国
    - 「自動化ゲート」推奨
      - 指紋登録すると楽
    - 機内 Wi-fi
    - 時差対策
  - 米国についたら
    - 荷物を一度は必ず受け取る
      - 乗り継ぎでも全部受け取る
  - 入国審査
    - 何をしにきたのか
      - 飛行機の紙を見せるといい
    - どこに何日間宿泊するのか？
  - 会場に着いたら
    - バッチをもらう
      - IDを見せるともらえる
    - Tシャツ
      - 参加者しかもらえないからもらっておけ
    - 展示ブースを巡回
  - 会場での過ごし方
    - セッションの入退室は自由
    - 朝食・昼食・おやつあり
  - セッションだけではない
    - ハンズオンラボ
    - トレーニング
  - 気づき
    - 当たって砕けろ
    - ヒアリングは重要
    - 宿泊代はケチるな

## LT-1 ChainerMNをDocker　コンテナでうごかす
- chainer
  - PFNが開発しているPython製の深層学習向けフレームワーク 
- chainer MN
  - 分散学習用に必要な機能を実装したCHainerの追加パッケージ
- docker-hubのパス + everpeace/docker-chainer

## LT-2 KubeFlow Machine Learning on k8s
- KubeFlow
  - k8s上で機械学習タスクを管理するOSSプロジェクト
- なぜ kubeflow
  - MLをCloud Nativeにする
- k8sさえあれば、オンプレでもクラウドでもOK
- 分散学習を簡単に利用できるようにする

## LT-3 Dockerとk8s, helmをTwelve Factor APP
- Twelve Factor APP (https://12factor.net/)
- 1コンテナ = 1プロセス
- googleが発表したDockerのベストプラクティスがある

  

## LT-4 OpenShift

- コンテナアプリケーション基盤
  - k8s + α
  - コミュニティー / エンタープライズ版がある

- カタログ運用
  - 開発環境の構築方法不明
  - CI/CDで作れるよ

## LT-5 Rancher
- コンテナマネジメント
- Enterprise Container Management
  - LineのSideShareに上がっている
- k8s
  - やっぱり難しいんかー
- k8sにはフル対応している
  - rancher.com/docs
  - rke?
  - サポートに金払えw
- Rio
  - 