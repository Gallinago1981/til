# Road to Serverless
- Twitter:@david_syer

## Agenda
- Cloud abstraction, and serverless
  - plugin in/out
- Spring Cloud Funtion
- Raising the value line

## Cloud abstraction
- vm(IaaS) -> containers(CaaS) -> Apps(PaaS) -> Function(FaaS)
- インフラ周りの抽象化　-> 仮想化
- FaaS ≒ Serverless (= Function)

## Serverless and Function
- Event driven
  - パケット中のデータに業務的な意味を持たせる
- Dynamic resource utilization
- Billing per message
  - Function callによる課金（メッセージ単位）
- Prototypes become production code really qruickly
  - アイディアのプロトタイプとして早く出したい
  - プロトタイプコーディングしたがそのままリリース
- Focus on business logic
  - IN/OUT だけ考えればいい
  - データをどこにどのように出すかは考えない

* Springが掲げる目標に近し考え方

- CNCF WG Whitepaper
  - serverlessの定義が記載されている

## service block
 - twitter ? : @kennybastani
 
## Business Login and the value line
- NETFLIXがマイクロサービスを適用する
  - インフラを取り除きたい
  - 外のデータソースからの脱却（integration spaghetti）
  - アプリケーションとして独立させたい
  - Data in/out から離れたい？

## Amazon Lamda
- Javaをサポートしているのでいいかも

## Google Cloud Function
- まだ正式サポートではない。いづれやるはず
- 自動化が足りない
- パイプラインがない
- IDEに対応していない

## Serverless Provider
- Azure Function / native java support
- IMB OpenWhisk / native java support
- Oracle Fn / native java support
- OpenFaaS
- Fission
- Kubeless
- Riff https://github.com/projectriff

* native java support以外は何らかの施策が必要

## Spring Cloud Function
- serverless functionが始められる
- auto configurationも可
- unit testなどテストを実施したのちにcloudへのupできる
- 必要なのはSpringを知ることではなくJava Functionを知っていること

## Project Reactor
- Flux/Mono -> reactor type
- Publisherを拡張したもの↑
- 未来に"何か"をやってくれることを確約してくれる。
- event思考方に対応

- fluxの意味を調べる

## Spring cloud function adapter
- Adapter : Cloud(aws)のライブラリとかにattach?
- Servlerless Providerがcloudサービスの差異を吸収している？

## Sprig Cloud Function
- Adapter for AWS lamdba, and other "serverless" service providers
  - 近々、公開される予定

## Business Logic and the value line
- Value Lineが抽象的なラインを上げられる。(低レイアーは関係ない)
  - CPU Intel/AMDかは関係ない
  - OS Ubunt16, 17 / Redhutとか
  - Reactor: http://projectreactor.io