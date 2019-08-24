# Google Homeを遊びたおす会

## firebase
* 個人利用なら無料枠で行けそう
* 

## ボイスマッチ
* 機器ごとのマッチは自分で調べろよーって話ね
* IoT機器トリガーでGoogle Homeを起動させる
  * 温度センサー
  * イベントトリガーをラズバイでかければなんとかなる
* HDMI CEC規格でテレビのON/OFFを判別している
  * リモコンのON/OFFスイッチ信号が同じ場合があるよ
* アプリのSEO
  * 特に何もしてないよ
*  
## Action on Google
* account link

## Action on Google
goo.gl/4qn95R
* Arch

# IFTTT
* bozeにgoogleアシスタント搭載している
* AoG + Dialogflow
* Pros
  * コード書かなくても色々できる
  * 起動用の定型文を
* 
  * Philips Hue
  * 結果が得られない

# Action on Google
* AoG -> webhook
* AoG -> Dialogflow
  * cluoud上の
  * RPC形式でJSON
  * 非公開のまま稼働し続けられる
  * 16ロケール (海外にも対応)
  * 
  
* Explicit Invocation
アプリ名 + トリガー + コマンドフレーズ

* implicit invocation
 * アプリ名を指定しない聞き方（今日は天気は）
 * サードパーティを利用するかを聞いてくれる
 * 推薦されるかどうかかgoogle アシスタントの設定が重要
 * 
 * DialogFlow
   * トレーニングフレーズでいうであろう言葉を設定できる
 * Google Assistant SDK + Android Things
 * AIY Voice Kit
* サードパーティーがコマンドを持って行かれた場合
 * いつか治るであろうけど改善できなさそう
 * ChromecastでHDMI CECが使えるっぽいぞ

# Dialogflowとは
* できることできないこと
  * 身長と体重からBMIを計算するはできない
  * 静的なことはできる

* 同じようなIntentsは作らない
  * Entityの辞書で対応するが望ましい
  * Call member -> memberが辞書に登録される
* End Indentがあるといい
* Google アシスタントとDialogFlowを紐づけてからDialogflowを使った方がいい
* GCPプロジェクトの上限が20くらい
  * Actions on Google : GCPプロジェクト = 1:1
  * なるべくimportしよう
* 削除は30日間保留される
