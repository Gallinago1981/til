# Container SIG Meet-up 2018 Fall

## KubernetesとServerless　(Serverless for 何もしたくない人)

- knative / サーバレス
- 仮想環境ではやることがたくさんある
  - k8sにしたらかとはいえ楽にはならない
    - Why running your own k8s deployment coud be terrible idea
    - クラウドサービス使えはk8sの保守はしないでよくなる
  - コンテナ時代のエンジニアはコンテナの面倒だけ見ればいい
  - OpenShift(REDHat)/ Amazon (EKS) / Google (GKE)
- 担当範囲をさらに小さくしたい
  - マイクロサービスにすることで１つのマイクロサービスを見るだけになる
  - けど、実際はサービス間連携（リトライ、タイムアウトなど）
  - lstio
    - k8sのpodの仕組みを使って通信制御を行う
    - envoyっていうコンテナを入れることでリトライとかがへる
    - エンジニアはapp logicだけやればいいようになる
    - 設定ファイルを変更することでdelay 通信とかを作れる

- さらに担当範囲を小さくする
  - サーバーレス
  - app logic以外は全て邪魔
  - knative
    - k8sにFaaS機能を付け加えるアドオン
    - コンテナ管理からユーザを解放する
    - 自分が意図したアプリ、コードのみを管理すればいい時代になる

- さらに担当範囲を小さくする
  - 設定ファイルが邪魔だからなくせる世界が来て欲しい

## Cloud Native Computing Foundation(CNCF)アップグレード情報～2018年を振り返る

- Cloud Nativeとは
  - 物理 -> 仮想 -> クラウド -> クラウド ネイティブ
  - 早く安全に自分たちのサービスを利用させたい
  - 物理時代は筐体の投資が必要になったけど、そのリスクを減らすための仮想化、クラウドが出てきた
  - クラウドとクラウドネイティブは、スケールをするかしないかの違い
    - クラウドでオートスケールはあるけど、色々と大変。うまくいかないことも多い
  - CNCFが2015年に立ち上がりベンダーロックインなくクラウドを移動できるよう標準化と調整をする中立な業界団体
    - 母体はLinux Fundation
  - docker -> k8s
    - 1 アプリケーションのコンテナ化
    - 2 CI/CD
    - 3 オーケストレーションが可能かをチェックする
- 2018 CNCF Blog (http://bit.ly/cncf18blog)
  - CNCFメンバーが今年になって急増
  - CNCFプロジェクトの成熟度はGRADUATIONになったら利用してもいいんじゃね？
  - 別に満たしてなくても使ってもいい
  - sandboxがめっちゃ増えている
  - https://l.cncf.io
    - 競合する製品も表示される

- CNCF 概要
  - https//github.com/cncf/presentations/tree/master/japanese
  - ぜんぶつさんに間違ってたら言ってね
  - containersig30
    - クーポン30%引き
  - CNCFは競合は歓迎している

## パネルディスカッション「インフラとアプリの境界で」～仮装で仮想を語る～

- 現在抱えている問題/辛いと思っている部分は？
  - GKEで運用しているが、サーバエンジニアがk8sの理解度の違いや認識を合わせるのに苦労している
  - ハードウェア保守、ライフサイクルとして何かしている。アプリ側との協力しようにも時間がかかるとかしている
    k8sのリソースのyaml設定をどうしたらいいかが悩ましい
    アプリ側の設定を委ねた場合、上がっていくバージョンを追従していくことができるかが課題
    インフラでガイドラインではなくテンプレートを提供している
    設定ファイルをリリース依頼するウェブアプリを作って指定できる項目を絞り込んでいる
  - 各OSSのEOL対応が大変
    オンプレ -> 仮想化 -> コンテナ化
    スケールしていくので管理コストがあまり変わっていない
    インフラとアプリの境界による弊害はあまり感じていない
  - 保守/運用コストについてはアプリ側に連携できているのか？
    サーバを準備するのにかかるコスト感は伝えられている

- これからどのように仕事をしていきたいか
  - 管理するレイヤーがどんどん増えていっている
    CI/CDとかの管理もやっているが、インフラエンジニアの母数が増えていかない
    取捨選択して低レイヤーは管理していく物を利用していき、アプリ側の方に貢献していきたい
    マネジドサービスをどんどん使っていきたいけど、オンプレをどうするかが悩ましい
    オンプレに依存しているレガシーなものは残っているが、新規サービスなどはパブリックに寄せる
    -> ハイブリットになっていくのかどうか
  - マネージャー？インフラ？サーバアプリ？
    興味としては、コンテナに強い関心がある
    ベテランになってきたのでマネジメント
    広告、ソシャゲーのインフラ基盤を立ち上げるのが難しくなくなってきた
    興味、関心は機械学習とかに向けてサービスの強くする
  - インフラが必要ですか？
    SREに相当する人は必要。GKEとか使っているとどうしても必要ではない
  - インフラ　から プラットフォームに改名した
    サービス、生産性の向上に力を入れている
    社内システムのレガシーなシステムをモダンにしていきたい
    エンジニア以外の生産性向上をさせていきたい

- これからコンテナを使って開発していこうと思っている人たちに一言
  - Dockerはサンプルでちょっとやると動いちゃう
    一旦、深掘り
    マルチステージビルドがわかっているとか
    コンテナのサイズ
    コンテナのプロセス
    ちょっと動く以上のことをやるといい
    コンテナの情報収集はスライドをよく見る
    勉強会にちょくちょく参加
  - 組織とか背景によってアプローチは変わる
    アプリの人からコンテナでプロダクションをやりたいというリクエストから始まった
    リリースサイクルの向上
    IaaSは準備に時間がかかるので改善したいという要望が強かった
    k8s中心とした技術が多くて混沌して混乱する
    何を実現したいのかを目標としてちゃんと立てることが必要
    コンテナサービスの役割をちゃんと考えることが必要
    ベストプラクティスはまだない！
  - ベイグランドのアンインストールがまずは必要
    コンテナは再現性が高い
    開発環境による違いが少ないので生産性が上がる

- Q&A
  - 情報の均一化をはかるのは何か行なっているのか
    - GCPのチュートリアルクーポン クイックラボでチーム内で共有した
    - 作業の手順をkiberaに留めている
    - 半期の目標にした
    - 開発者内のハンズオンが行われている
      - 1回やったあと時間があくのでキャッチアップ会もやっている
  - コンテナ化に失敗したなと感じたことは？
    - マイクロサービスはコピペが多い
    - よくわからないまま進めていくことが問題
    - アーキテクチャの見直しとかやらないの？
      - 大きな変更は余裕がない
