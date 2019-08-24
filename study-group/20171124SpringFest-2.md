# Struts -> Spring ノウハウ

## Struts 1.x
- struts 2013/04/05 サポートが終了
- Class Loaderが操作可能な脆弱性が発見される
- パッチを当てる
  - 業者がいる
  - 派生フレームワークがあった場合はそちらから使える

## 載せ替え先
- Strtus2
  - Action Base MVC
  - Struts 1.x との互換性がない
  - 深刻な脆弱性が見つかることが多い

## Java##
- MVC -> 搭載されず
- JSF -> コンポーネントベース
- Strutsの移植先には向かない

## Spring
- Action Base MVC
- 脆弱性対応速度がいい
- 開発スピードが早い
- 情報量が多い
- Privotal

## サービスの説明
- 不具合の修正、改修は行わない。
  - 対応する場合は別フェーズ

## 入力チェック順
 - @GroupSequenceで対応できる
 - 入力値とエラーメッセージの保持
   - Flash Scopeで対応

