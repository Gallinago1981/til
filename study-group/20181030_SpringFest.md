# Spring Fest 2018

## Keynote (The State of Spring, java and Kotlin)


- JavaとKotlinのお話
- java
  - Java8の採用が多い
  - Spring のベースバージョンがjava8
  - java9は少ないけどLTSではないから当然
  - Azul Systemでは2024以降もサポートしている？
    - これは間違い
    - Oracleのライセンスならってこと
  - 次のLTSは17 (2021年?)
  - Java8ベースライン
    - 2023年までサポート
  - Java 11 LTS
    - 2023以降までサポート
  - Java 17 LTS
    - 2021年
    - java 12 -16 が半年ごとにリリースされたSTS
  - Spring freamework relewase Matrix
    - SPR 4.3 java8のみで2020/07まで
    - SPR 5.0 EOL 2019/05
    - SPR 5.1 EOL 2019/12
    - SPR 5.2 2019/7 リリース予定
  - High-perfomance polyglot VM
    - Substrave VM
      - GO をコンパイルしDockerやLinuxのサーバへデプロイできる
      - メモリ消費が少ない
      - 新しいJVMのやり方に合わせて
- Kotlin
  - GithubではKotlinの利用率が増えている
  - Android Developerが移行してるのが原因の１つ
  - サーバサイドでも利用されている
  - Javaに続くJVM言語の１つになるであろう
  - kotlin1.3
    - 安定したCoroutines
    - Kotlin/Native
      - C++のライブライなどが利用できる。マルチプラットフォームのプログラミング言語
  - https://try.kotolinlang.org
    - Javaの知識をKotlinにConvertするためのサイト？
  - Spring Freameworkのkotlinチュートリアルがあるよ

- Spring Framework 5.1
  - 5.0 は JDK9
  - 5.1 は JDK11 LTS
  - メモリ消費量が減り早くなる

- Spring Boot 2.1は先日リリースされた
  - java 11をサポート
  - Spring framework 5.1がベースになっている
  - パフォーマンス、およびメモリ使用量が改善されている
  - Spring Data JDBCが始まっている。Hibernamte 5.3に対応
  - heep size、パフォーマンスが1/3ほど改善

- Roadmap
  - Spring Framework 5.2 
    - Kotlin 1.3をベースラインとした対応を行う
    - Spring FrameworkとKotlinのAPIで利用できる？
    - Coroutines サポート
    - Beanの生成が容易になる
    - Kotlinのコードサポートを含めて行う
  - GraalVM
    - 5.1からサポートしている？
    - 5.2から正式？
    - grall.jsonにクラスとメソッドを書く？
    - 1.0.0.-rc7-graal
    - Spring Bootの起動が7ms
  - R2DBC
    - Reactive プログラミングサポート
    - SQLサポーとは提供されるのか？
      - ムリって言ってた
    - SQL SPIを提供するよ
    - Reactive Stream base
    - 現在はPostgreSQLドライバだけだけど他も作っていくよ
    - Minimal Driver SPI
      - beginTransaction
      - close
      - createSavepoint
      - createStatement
    - 来年提供予定

  - RSocket
    - ネットワークのreactiveに当たる部分
    - 4つのモデルをサポートしている
      - Request Response
      - Fire an forget
      - Request - stream
    - Java, JavaScript, C++, Kotlinでサポートしている
    - Spring 依存ではない
    - Spring freamework 5.2で導入されてくる

  - Spring Fu
    - incubator
    - annotationがへる？
    - 2.1 Functionalを利用するとメモリ使用料、性能も大きく改善する
    - Kofu configuration
      - Kotlin DSL

## エンタープライズ・マイクロサービスの格言

- 去年の資料はSideshareにあるよ
- Spring Fest 2018のサイトに今年のは貼られる
- オブジェクト指向がわからないのに、マイクロサービスに呼びついてもできるわけない
- そもそもマイクロにならない
- 方法論もないし、手探りて作れるのか
  - 技術論はよく聞くが方法論がない
  - DDDは方法論ではなく技術論
    - どのフェーズでそもそも使うのか
- SoRには向かない、もし取り組むならハイブリッドがいい

- エンタープライズ・マイクロサービスとは
  - 主にエンプラ系のシステムをマイクロサービスをマイグレーションしたシステム
  - なんか、普通に定義されているマイクロサービスとは違う
  - サービスベースアーキテクチャ

- エンプラ系が得意なSI企業はマイクロサービスアーキテクチャでのシステム開発は向かないようだ
  - なぜ向かないのか？
    - 試行錯誤するとか、スピード感が合わない（ドキュメントの要否とか）

- マイクロサービスとは相対的なんだ
  - エンプラ系の粒度とMSのサイズ感を同じにしちゃいけない
  - クジラのマイクロと、てんとう虫のマイクロはそもそも大きさが違うからサービス粒度も当然異なる

- マイクロサービスの粒度は勘で決める
  - そもそもピザ２枚のコンテキスト境界を決めることができるのか？
    - 特にマイグレーションする際の切り出し方が不明じゃないか
    - 勘でいいんじゃないか？
  - 最初の粒度は、業務や機能でサービスを分ける
    - 必要に応じて徐々に粒度を細かくすればいい(その際にDDDができればいい) 

- 開発プロセスはアジャイル的である
  - 要求とMSA、実装という山を相互に行き交うことで谷間を埋めなければ開発はうまく進まない
  - 探索的な開発である
  - スリーピークモデル
  - 世の中にWFで開発しているところはないんじゃない？
    - プロタイプを作っている時点で１つの繰り返しになる

- 適応度関数には品質特性シナリオを使う
  - MSでは非機能要件が大事であるにも関わらず、その部分が抜けて要件定義が終了するケースがある
  - 品質特性シナリオを元に非機能要件をMSAに反映させ、性能テストetcで計測可能とする

- クリューバ方式でチームを編成する
  - ネットで検索しても出てこない
  - 100匹の狼を従えた羊より、100匹の羊を従えた狼の方が強い
  - 優秀なチームリーダを配置することで最低限の品質をチークリーダで保証する

- 開発編
  - 共通処理はやめる
  - 処理を共通化することで、MS個別の進化が損なわれコストがかかる
  - 必要があればMSとして切り出す
  - 各MS内に共通機能があると共通機能の変更があると全てのMSがリリース対象となるのでMSのメリットが失われる

- テストはちゃんと作らなければならない
  - MSの進化を短時間で行うためにはテストが重要
    - CI環境を整える
    - カバレッジ率などの品質管理を実施する

- Unitテストは高速化する
  - @SpringBootTestを付与してUnitテストを行うと、テストの実行時間がかかりすぎる
  - Unitテストは@RunWith(SpringRunner.class)で行う

- 難しいことは避ける
  - 複雑なトランザクションを扱うので、コレオグラフィ、Sagaパターンなど適用することは困難
  - MS間は極力、同期通信でACID確保
    - 性能などの問題はインフラで頑張った方がいい

- 定説を疑え
  - 「順番を知る必要はない」は論外で「複雑になる」のでコスト増大
  - レガシはデータがまとまってるなんで誰が行ったw

- バッチには注意する
  - バッチがいつの間にか様々なサービスを使い始める事故が起こることがある
  - バッチも１つのサービスとして認識する必要がある


## エンタープライズアジャイルとSpring/Wagby

- SoEへ踏み出したい
  - DX(デジタルトランスフォーメーション)は全ての企業がSoEへ踏み出さなければAmazonに蹂躙されますという煽り
  - 自社の情報システム部にSoE分野に踏み出したい
  - エンタープライズアジャイルとは、エンタープライズ開発をしてきた企業がアジャイル開発を行いたい

- アジャイルでいい
- アジャイル的アプローチを取り入れたいという視点
- ユーザ企業がアジャイルに向き合えるかが問われる
  - アジャイル開発には丸投げ不可

- Wagby
  - ノンプログラミングでJavaソースを生成して画面レイアウトを作ったりすることができる
  - wagby自体のカスタマイズがjavaで行える
  - クラウドも可
  - salcefoce/kinnoteとは違い、DB構造が見えることが利点
  - 認証系にSpringSecurityを使っているので様々な認証方式に対応できる
  - スケーリングではなくサービスのモジュール化による運用改善の方が重視されている
    - 1000台のインスタンスが必要になるようなSoEでは使われない（用途が違う）
　- 

## Rakuten Travel and Spring

- Spring Initializr
  - ディレクトリ構造とかを作ってくれる。プロジェクトの構造やConfigurationとかも
    - web interface
      - service Type project
        - Executable Jar
        - web conteiner
      - Library type Project
    - Spring Tools
  - Project repository
  - spring cloud config repository
  - readme
  - editor config

- application configurations traditional way
  - アプリケーションパッケージごとに設定ファイルがあり。しかも、かく環境（dev, stage, prod)
  - spring cloud configurationを使うことで各サービスに配布できる
  - labelはブランチ(gitのmaster branchを使うならmasterを指定する)
  - uri spring-config clientが接続するアドレス？gitのじゃないの？
  - application.ymlに優先度の順位があるらしいけど、どういう理屈で上書きされるのかを知る必要がある

- actators
  - エンドポイント
  - ヘルスチェックやconfigファイルの設定状況などを見ることができる
  - Spring Boot Admin　サーバにclientの情報を登録する
  - Adminサーバのuriをclient起動時に登録されるのでclientのapplication.ymlにadminサーバのURIを設定する

- swagger
  - 情報の可視化に有効
  - swagger editorがSpring Boot Adminにあるの？
  - endpointの可視化ができる
  - io.spring.ui, io.spring.fox?



## Knative: Serving your serverless Java Service on Kubernetes the 12 - Factory Way

- bit.ly/knserving
- Serverless Computing
  - サーバ管理は不要
  - 24時間サーバが動いているけど管理、監視が必要がない
  - サーバレストはデータセンターがないという意味ではない
  - IBM Bluemix OpenWhiskがサーバレス初のOSS

- サーバレスは必要？
  - Agility
  - 最適化とコスト削減ができる

- Architectural evolution
  - service ベースで初めて行く
  - 次にマイクrさービスベースのアプリケーションになる
  - マイクロサービスとFunctionの違い
    - マイクロサービス
      - singole purpose
    - Function
      - マイクロサービスをより細かくしていく
  - サーバレスの悪いところ
    - Vendor Lock-in
    - デバックしにくい
    - モニタリングツールがない

- Serverless Vs FaaS
- FaaS
- backend as a service
  - することがないときは休眠状態になる

- knative
  - 7/24 から発表された
  - knativeを使うことでサーバレスを自分たちのサービスとして利用できる
  - k8s限定？
  - knativeを使うことでサーバレスアプリケーションをvendor lockin せず利用することができる
  - sacle up/out/down を自動的に行う
  - Red hat の open shiftに説明があるよ
  - bit.ly/mono2microdb
  - bit.ly/istio-book



## OAuth2.0とSpring Security5.1による実装

- OAuth2.0
  - 認可の流れを規定したプロトコル
    - RFC6749
  - 1.0もあるけどStruts1.xとStruts2.xくらい違う
- アクセストークン
  - サーバのデータにアクセスするための許可証
- スコープ
  - アクセストークンがやることができる範囲
- ID/PASSじゃダメなの？
  - 盗んだ人はなんでもやりたい放題
  - トークンを消せばいいいからある程度
- リソースオーナー
  - 情報の持ち主
- リソースサーバー
  - 情報を保持するサーバー
- クライアンち
- 認可サーバー
  - アクセストークンを発行する人
- TODO管理アプリ
  - クライアントから認可サーバに言って、リダイレクトされたクライアントがまた表示される

- アクセストークンの取得
  - 認可コード
    - サーバサイドアプリケーションで作られる
    - 認可コードが必要になるのはアクセストークンをクライアントサイドに渡さないようにしたくないから
    - アクセストークンをクライアント側に渡さないようにする
  - インプリシット
    - Javascript
  - OAuth2.0は認可なのに認証が必要になる
    - ID/PASSなどで認証する必要がある
    - cleint_id, client_passwordでoBasic認証するのが一般的
  - Bearer をHTTPヘッダーに入れることが多いけど決まり事ではない
  - アクセストークンにユーザ情報を含めておく
  - JWT ( JSON web Token: ジョット)
    - アクセストークンの中にユーザ情報、スコープなどを含める
    - ペイロード部をbase64でデコードすると中身が見える
    - 署名
      - 認可サーバの公開鍵が必要
      - JWK (JSON Web Key)
      - 公開かぎを計算するための情報を得ることができる？
  - アクセストークンの剥奪が不可能なので、アクセストークンの有効期限を短くする
  - リフレッシュトークンを使ってアクセストークンを新しく取得する

- 認可サーバの実装
  - Spring Security 5本体に新規開発することになった
  - Spring Security OAuth2はメンテナンスモードになり新規開発することはない
  - 認可サーバーは5.2から部分的に入りそう
    - keucloakとか使う
    - Twitter, Githubで代用するとか

- クライアントの実装
  - aplication.yml
    - registrationl.todo -> providerで定義された名前

- Spring Webflux
  - Webzvlientだと色々とやってくれるっぽい

- リソースサーバー
  - JWTを使うと認可サーバを使う必要はない



## Spring Data REST と Spring Cloud Contract

- 背景
  - SPA時代
  - Angular, REACTを標準としてきている時代
  - モダンなUIはフロントエンド側の実装になってきた
    - UI側にビジネスロジック
  - サーバサイドはAPIの実装
  - 工程やチーム構成の変化
    - 別々のチーム、リポジトリ、リリースサイクルがフロント、バックエンドで変えたい
  - リリースサイクルが異なることで想定外の事象が生じることがあるかもしれない
  - 標準化、自動生成
    - Spring Data Rest
  - 別々に進化できる仕組み
    - Spring Cloud Contract
- Spring Data Rest
  - 残念な実装
    - ServiceClassがDAOとかのブリッジになっていないか
  - Spring Data restの特徴
    - Entityに対する基本的なエンドポイントが自動生成される
  - Data部はSpring HATEOASのルールに則ったフォーマットで返される
    - Spring HATEOASだけで使うこともできる。エンドポイントは自動生成されない
    - 紐づく情報から異なるデータ部の情報を取得するためのLinkを知るためのの道しるべを得ることができる
  - 主キーのレコードに対するイベントをエンドポイントとして定義することができる
    - 例えばキャンセルできる注文とできない注文ではリンク部の有無で表現される
  - 自動生成されて簡単といはいえ、CRUDのみが対応している
    - ビジネスロジックは作らないとダメ
    - EventHandlerが用意されている。
      - メインとは別のトランザクションになる
    - @RepositoryRestController
      - 自動生成されたエンドポイントのオーバーライト
      - 自動生成のエンドポイントは優先度が一番低い状態で作られる
  - JSON SchemaからTypescriptのEntityが作ることができる
    - ドメイン定義がクライアントとサーバで異ならないようにすることができる
  - JPAではなくHibernate Searchを使うと全文検索ができる？
  - 検索が弱い
  - マルチテナント
    - Spring Securityからどのテナントかどうかを判別し取得できるようにした
    - テナントのキー情報を引き継いだ？
  - Spring Data Restを活用してボイラープレートコードを削減した。
  - チーム間のデータ共有をSpring Data REST, Spring HATEOASで繋いだ


- Spring Cloud Contract
  - CDC (Consumer Driven Contract)
    - フロントエンドとサーバ間通信をモックに置き換えることでテスト環境の構築および実施を早める
      - モックデータの信頼度は誰も保証してくれない
      - モックのメンテナンスは？
      - UI/APIにチームが別れたことによって連携する対象が増えモックを用意するのも大変
    - APIでの連携する際に役立つもの？
    - マイクロサービスをターゲットとした顧客駆動の何か
    - Pact = contract testing tool.integration testをサポートするtool
    - Contract
      - インターフェース定義
      - サーバサイドが守る契約的な意味合い
  - Spring Cloud Contractor + pact
    - コンシューマ側でContractを自動生成する
    - Pact Broker から Spring Cloud Contractで自動生成できる
    - build に失敗するとクライアントサイドとのアンマッチであることがわかる
    - WireMockというのでMockサーバが作られる？
    - pactを使ってフロントエンドとサーバサイドを擬似的な接続テストが行える？
    - CIの回し方を考えないとあかんやつ

## 業務で使いたい WebFluxによるReactiveプログラミング

- リアクティブプログラミングの基本的なパターンを把握する
  - Stream APIの stream / map / collectに相当するもの
- ノンブロッキンぐなソースを「使う」ことを学ぶ

- リアクティブプログラミングとは
  - データの作成や変更の通知をきっかけにして処理をするようなプログラミング
  - publisher -> subclimeモデルのイベントハンドラというイメージに近い
    - 商品金額が変わった通知を受け、税額が自分を更新する

- 同期処理
  - 順番にお行儀よく待って処理すること

- スレッドを利用した非同期処理
  - 処理の塊を切り出してスレッドを立てる
  - 全てのスレッドが終わると全ての処理が終わる
  - webアプリケーションのプラクティスに違反する（スレッドは立てるべきじゃない）

- リアクティブプログラミング
  - 時間のかかる部分や得意ではない処理を外部に移譲する
    - データストアへのアクセス
    - 外部サービスへのアクセス

- リアクティブシステムとリアクティブプログラミング
  - リアクティブシステム
    - キューなどを介してメッセージドリブンで処理する
    - リアクティブプログラミングをつかわいでも実装できる

- Project Reactor
  - Java8 対応
  - Reactive Stremsに準拠

- Spring WEbFlux
  - Spring MVC5から導入された
  - ReactorをSpringのWEBで使えるようにしたもの

- Reactor
  - Java8のstream apiのようなものがたくさんある！
  - 非同期で動作する
  - 基本の基本は「Mono」と「Flux」
    - Mono
      - 単一要素を扱う
    - Flux
      - 複数の要素を使う

- 最初に覚えるメソッド
  - Mono / Flux
    - just
    - interval
    - doOnComplete()
    - log
      - 現在の状況をログに出力できる
      - 便利！

- 非同期に実行するのでmainメソッドが先に終わる
  - doOnCompleteなどでまつ
  - CountDownLanch　<- 一定回数がたったら終わる

- Spring Webflux
  - Spring MVCでMono / Fluxが使えるようになる
  - WebClientという新しいクライアントが使えるようになる
  - TomcatではなくNettyで起動する
  - @RestControllerって書くことで非同期のREST APIになる？
    - @GetMapping(produces = MediaType.TEXT_EVENT_STREAM)をつけるとmultipartみたいになる
  - Listとかでもいいで

- RestTemplate
  - Genericsが面倒なRestTemplate
  - List<Student> だと面倒くさい
  - Student だけなら簡単
  - RestTemplateがEVENT Streamに対応していない。
    - BufferedReaderを使うことができるけど、だいぶ行けてない

- WebClientならRestTemplateの問題が解決する
  - bodyToFluxでFluxで取得できる
  - 落とし穴
    - blockメソッドを用いてListやObjectを取り出すことができる
    - Netty場でBlockメソッドを呼び出すとエラーになる
    - mapメソッドを用いるなど、blockメソッドに頼らない実装が必要となる
      - Optional.getを使わない

- 課題設定
  - flatMap
    - streamのstreamではなくstreamにしたい場合に使うのがflatmap
