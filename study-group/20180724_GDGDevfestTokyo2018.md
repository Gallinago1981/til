# GDG Devfest Tokyo2018

## kubeflowの話

### Lv3 機械学習モデルが連日連夜１００個走る

- Facebookの機械学習基盤

- TransorFlow Extended
  - Google が提唱している論文
  - 月単位から週単位に変わった
  - TFXを使うことでGoogle Play 

- Kubeflow
  - Simple
  - Portable
  - Scalable - k8sの機能を使ってスケーラビリティを担保

- monitoringとloggingが必要
  - Kubeflowが色々とサポートしてくれる
  - Kubeflow Family
    - Argo コンテナワークフローエンジン
      - CI, CDが可能
      - イベントトリガーが開発中
        - 毎月のイベントや、アラート検知しロールバックするなどの機能が開発中
      - Wev UIも提供されている
        - 処理時間もみられる
    - Pachyderm
      - 複雑なデータパイプラインの管理
    - Jupyterhub
      - 協働可能なJupyter Notebook
      - データサイエンティストがモデル作成をNodebookで行う
      - KubeflowではTensorFlowに分散学習基盤を提供
    - CRD形式でTEnsorFlow以外の機械学習フレームワークのジョブの実行も可能
      - Pytorch
      - Caffe2
      - Chainer, etc
    - Katib
      - ハイパーパラメーターチューニング
      - Google Vizierと呼ばれるブラックボックス最適化の手法からインスパイアされたKuveflowFamily
      - 特定のDLフレームワークに依存しない形でチューニングが可能
      - Random, Grid Hyperband, Bayesian Optimization
    - TransorFlow Serving
      - 推論結果をサービング
      - TFモデルの推論結果をサービングRFの計算グラフで書かれたモデルをC++で書かれたシステムでデリバリおー
      - 全ての処理をTensorFlowの計算グラフに落とし込めないと使えない
      - 一長一短がある
    - 推論結果のサービんぐ(Seldon Core)
      - R
      - Scikit-learn
      - RF
      - Spark
      - ジュリアってのがあるらしい()
  - 181216
    - v1.0がリリースされDEMOが公開される予定
    - モデル評価
    - 良いモデルをプロダクションへロールアウト
      - -> 無理じゃね
  - Tensorflow Extendの世界がKubeflowに
  - 現状
    - k8sが辛い
    - 各ツールの学習コストが高い
    - まだ歯抜け状態
  - 期待していること
    - リソースの最適化ができる

## Google アシスタント最新動向

- 誕生してから約2年
  - 5億デバイスに入ってる

- WEAR OSが9月にupdateされる
  - 長押しからスワイプでの起動になる
- IoTとのI/F機能
- VoI
  - WEB Fookされてメッセージが来るだけ（嘘だけど）
- ルーティーンが使えるようになった
  - 日本語対応ができた
  - Googleアシスタントが多言語された
- 日本語で話しかけると英語で返答してくれるかも
- Smart4Action
  - 電球操作、加湿器操作などができるようになった
  - リモコンが使える機器は音声Actionで扱える時代
  - 自宅を特定するためにOAuthを利用している
  - 自宅にどのデバイスがあるか設定されていることが前提
  - HOMEグラフ？
- 認証認可の話
  - GoogleアカウントのSigninは簡単
    - 日本語は非対応
  - OAuthサーバを持っていればAccessTokenが帰ってくるのでそれを使う

- 決済、予約は
  - Transactions APIを使う

- Actions on Google

- Android P
  - Googleの検索結果のコンテンツが表示されたけど、そのコンテンツに対するサジェストが表示されるようになる
  - コンテンツに対するAction(音楽再生など）
  - App Actions
    - SEO観点
- AMP
  - モバイル向けの最適化されているよね
  - Google アシスタントでも使われる

- Google HOMEは作れる
  - Google アシスタント SDKで作れる
  - Node.js向けのが出ている
  - GitHUBにあるのでプルリクとIssueをあげる

- Assistant Developer Community Japan

## Firebase Overview

- Firebaseのサービスは結構ある(18サービス)
  - 開発、グロス、本番？に別れている

- とりあえず入れたいFirebase
  - Firebase Crashytics
    - 解析ツール。アプリのクラッシュログを収集
    - Cloud Functionと連携可能
  - Firebase Perfomance
    - アプリのパフォーマンスを測定する
    - 起動時間、ネットワーク時間、フォワグランド時間、バックグラウンド時間、スクリーンの描画時間
      - network traceには低レベルプログラミングされると計測されない

  - Google Analytics for Firebase
    - モバイル向けGoogle Analyitics
    - WEbのGoogle Analytics
    - BigQuery -> Data Store

  - App Index
    - 検索結果にアプリを表示する
    - ダウンロードボタンつき

- Prediction周りの話
  - 7日間のデータを元にユーザの次の行動を予測する
  - 離脱しそう、離脱しなさそう、課金しそう、課金しなさそうの４属性をデフォルトで推測
  - Remote Config
    - 離脱しそうなユーザに対してキャンペーンをうつ
    - A/B Testing
      - 対象jのユーザー属性を指定して、A/Bテストできる
    - Messaging
      - Push通知ができる
  - In-app Message
    - コンソールからメッセージ、バナーの表示が可能
    - タイトル入れたり背景色を変えたりすることができる

- firesote周りの話
  - Firebase realtime database
  - firebase firestore
    - データ型はDocument
    - 擬似リレーションができる
    - firebase database はQueryが貧弱
      - それらをカバーしている？
  - firebase database
    - NoSQL
    - realtime data sync with JSON Tree
    - Available data on offline
      - 一度取得したデータはクライアント側でキャッシュされる
    - JOINをクライアント側でやらなきゃいけない
      - JOINっていうかコンテンツ単位のSPA的な作りにすべきでしょ？
  - Firebase Cloud Functions

## Google アシスタント

- アクションを開発する３つの方法
  - Actions SDKを利用する
    - 自然言語処理とかも自分で作る人
  - Dialogflowを利用する
    - 自然言語処理はGoogleの技術に任せたい人向け
    - 機能を開発する人用
  - テンプレート
    - 便利

- Dialogflow
  - 自然言語処理をGoogleが処理してくれる
  - コードは書かない
  - 対応言語が豊富
  - あらゆるチャットボットサービスに対応
  - SDKが豊富
  - アナリティクス機能

- できないこと
  - ユーザの発言から特定の文字を取得する
    - 身長、体重を取得したい
- GCPアカウント
  - クレジットカードは登録されていることが望ましい
  - G Suiteアカウントではないものが望ましい

- 新規Agentを作成する

- intent
  - 会話の設計を行う
  - １つの目的につき、1つのintentを作成
  - 謎のintent
    - Default Fullback Intent
      - 一致しなかった場合の使い方みたいなの
    - Default Welcome intent
      - ようこそ？

- entity
  - 聞き出した後のレスポンスを記載する
  - Key, Valuesを設定する
  - Keyは聞き出した結果

- actions-on-google-nodejsライブラリ
  - 使いやすいらしい
  - dialogflowとのやり取りはJSON

- cloud functionでTypeScriptが使いたい人はgithubを参照



- 最新動向

- Transaction APIや細かいSDKの話

## Firebase Database high traffic production application

- メルカリチャンネルという機能で使っている
- Live e-commerce
  - Messages
  - Limes
  - Notifications
  - Item list

- デットラインが近い
  - 1ヶ月後にリリースしたい
  - クラウドを
- リアルタイムでの同期

- SDKが強力
- 1JSON 1Database
- 1(firebase): n (multiple database)

- Architecture design
  - Read
    - SDKを使うだけで基本は大丈夫
    - リアルタイム配信は入室したタイミングからのスタートをさせる
    - データにtimestampを持って過去分は捨てる
  - Write
    - REST APIを利用している
    - favはQUEUINGして更新している
    - REST API or SDK WebSocket
    - Authentication
      - Database token -> 非推奨
      - Google OAuth2
        - cachesしている
        - tokenのexpireがきた時だけ再認証している
      - keep-alive
        - EU, USしかない
        - choconというミドルウェアで行なっている
      - 投稿頻度の制御
        - 毎回送信する必要がない
        - 1秒間で行われたのを毎回更新するのではなく、100msごとなどに集約してから送る
    - motivation
      - 1秒間で1000writeが限界
    - schema設計
      - Rule
        - JSONの設定みたいなもの
    - クライアントからは更新していない
    - サーバサイドのみで更新している
- 権限を動的に変更する
  - permmisionを制御するための定義をすることができる

- 運用の話
  - スケーラビリティ
    - メルカリ59,000/sec
    - オートスケーリングは不可
    - 1000 query/sec , 1M connection
      - 10万人以上くるとアクセスできない
    - IDごとの割ってインスタンスを別に立てる
    - 15以上のインスタンスで運用している
    - クラウドFiresotreはオートスケーリングできる
  - Monitor
    - Kibana
    - Mackarel
    - Stackdriver
      - 複数インスタンスのメトリクスを１画面で見ることができる
      - 同時接続数
      - 負荷
      - エラー率
  - トラブルシューティング
    - １つのサービスは絶対に落ちる
      - 落ちることを前提に次にどうするかを定める必要がある
      - システムアラートが上がったりする
      - slackのアラートチャンネルをもうけ、通知している。
  - メンテナンスモード
    - 管理画面からボタン押下でメンテナンスモードになる
    - 自動化はせず人判断で行なっている
    - 状況に応じて判断した方がいい

## GCPで作るデータ処理パイプライン

- バッチとストリーム処理の概要と問題
  - バッチ処理
    - データの範囲が有限
    - 全データが揃っている
    - データをまとめて処理することができる
  - ストリーム処理
    - 時間軸上のデータ
    - 範囲が無限。
    - 区切らないと集計できない
    - FX自動売買bot
      - 通貨ペアごとの価格や取引数の移動平均
  - 似たような処理をしているのに別々の対応が必要
    - 言語
    - 実行環境
  - インフラ管理
    - バッチ処理
      - 複雑な処理のフェーズにより適切な並列数が変わる
    - ストリーム処理
      - 時間帯により入力データ凌駕変動する
  - GCPで上記の課題の解決を図る
    - Apache Beanm
      - バッチ処理とストリーム処理をシームレスに記述
      - 対応言語 Java, Python, go
    - 分散実行インフラ
      - フルマネージド
        - サーバ管理不要
      - オートスケール
    - Apache Beam
      - データ処理の流れを宣言的に記述する
      - IO対応
        - バッチ、ストリームを同時起動可能
          - バッチで集計値を算出してストリームデータに結果を埋め込むこともできる
    - Google Cloud Dataflow
      - サーバレスだよ
      - 負荷に応じてオートスケールしてくれる
      - 負担が大きいタスクを動的にリバランスしてくれる
      - Apache Beam実行基盤としてのGCPのサービス

## 機械学習どこから手をつける

- 機械学習を使った「手元で動く何か」を作るまでの考え方
- 機械学習アプリのプロトタイプ

- 機械学習でいま何ができるんだっけ？
  - Solving problems with AI for everyone
    - 自動運転とか
    - 目を空かんして心疾患を予測
    - Google Glassのスマートファクトリー
      - 工場で煩雑さを紙とペン使ってて手が塞がれているのに手を使う
      - 音声入力の結果をグラスに表示している
- 実際どこから手をつければいいんだろう
  - さっさとプロトタイプつくっちゃおう
  - 数学的な勉強もいいけど、プロトタイプつくっちゃった方が幸せな気がする
  - やってみなきゃわからないことがつきまとう
  - 機械学習モデルの学習・実装
  - プロトタイピングについて
    - 技術的負債になりやすい
    - 人に依存しちゃう
    - デプロイ先について
      - サーバーじゃなくてもスマホでもラズパイでもOK
      - 遅延が少ないとか、セキュリティ的な話
      - tensolflow liteで話がされているよ
    - プロトタイプ作りながら数学も勉強するが正解かなー

- 楽するために
  - TensorFlow Lite
    - モバイルアプリケーションが作れて機械学習もできるレアな人材むけw
  - ML Kit For Firebase
  - TensorFlow.js
    - 学習もできて、モデルもできて推論もできる
  - AIY
  - ラズパイ上でも動くよ

- Tensorflow
- Observable
  - Jupyter notebookのJavaScript版

- ちゃんとプロダクトに仕上げるために
  - 機械学習は水物
  - 継続的なでデプロイが必要
  - 機械学習の公平性
  