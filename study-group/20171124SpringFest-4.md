# Openshit

## 見てね
developers.redhat.com

## microservie from 2014

## microservice load to 2015
- vm管理が大変
- host down 
  - scaling / multiple hosts / 望ましい状態と現在の状態の管理
  - 自動的にサービスが立ち上がり再現できること
- ポートが8080以外でも再起動できるように。自動的に！

## Open Container Initiative (OCI)
- Runtime Spec
- Image Spec
 * あとでリンクを見る
- standerdを知るべき

## Kubernetes
- 舵取り
- アプリケーションを管理する
- Sring BootはアプリケーションでありVMではない

## Pods
- 大量のSpring Bootの集合

## OpenShift のエンタープライズ版が kubernete ?

# なぜカバネティスなのか?
- スケールアップ/ダウンは容易にできる
- サービスのロードバランシングは容易にできる
- Podがどこにいるかは意識する必要はないkervernateisが管理する

## DEMO
- git:(master) ./mvnw clean febric8:deploy
- oc login --server ${URL}
  - OpenShift の tokenが必要

## 

Eureka -> services
Concifg Server -> ConfigMapms
NETFLIX -> Services
APIKING -> 
Zuul
HYSTRIX

## Spring Cloud Luvernetes

## Demo (Discovery)


Eureka -> services
Concifg Server -> ConfigMapms
NETFLIX -> Services
APIKING -> 
Zuul -> lstio
HYSTRIX -> Lstio


## カナリアリリース
- 最初は少ない人数に対しリリースし、問題なければ多人数へ展開する手法
- Canaly Release

## Demo (Canaly Release∂ß)
