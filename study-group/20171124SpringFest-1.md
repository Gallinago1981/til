# エンタープライズで利用するSpring Boot

## 目的
- Spring Bootの使い方中心

## はじめに
- SpringBootは動くものをシンプルに作成
- ロール制御、監査情報、ロギング
- ライブラリ選定

- システム監視

## アプリ構成概要

写真
サンプルはGithub

## バリデーション
- 相関チェックのアノテーションがない
- Spring Validatorを利用

## オブジェクトマッピング
- Spring MVCは個別に設定する必要があった
  modelmapperで代用

## ORM
- DOMAsprin
- XML不要
- 2WAY-SQL SQLテンプレートをそのまま実行

## 排他制御
- @Versionアノテーションで楽観的排他制御

## セキュリティ

- Spring Expression Language (SpEL)
  - 権限テーブルの設計
  - Spring Securityではメンテナンスコストがあがる

- HandlerInterceptorAdapter

## 二重送信防止

- サーバーサイドでの実装
- post-redirect-get
  - redirectさせることでreloadによる再送信を防止
- Tokenによる制御
  - EntityListerner

## 監査情報
 - Dpring Data JPA -> domaじゃ無理


## 静的コンテンツ
timeleafでjqueryなどのバージョンを一元管理

## キャッシュ制御
- Spring Bootの設定で管理可能

## 開発環境
- Flayway DBマイグレーション
- gradle doker plugin
  - gradleとdockerが連携する

## テスト管理(spock)

## 運用
- Spring Bootのprofilesで対応
- 起動パラメータでの上書きが可能

## ロギング
- default logback/console出力

## アプリケーションの状態
- Spring Boot Actuator
- HTTPで様々な情報を見れる
- スレッドダンプやメトリクスが取れる
- ymlのmanagementで制御する

## JMX監視
- yml jmxをenabledにする
- モニタリングはできないのでzabbixなどと連携してみる

## 設定ファイルの暗号化
- jasypt-spring-boot-starter
- @EnableEncyptablePropertyに暗号化対象のファイルを列挙する
- jaspt.jar で暗号化できる
- ymlでencを指定して複合化