# Angular windows開発環境構築

## 環境

Windows7 Professional (64bit)
PowerShell（管理者権限）
VisualStudio Code

## chocolateyのインストール

* PowerShellの実行ポリシーを確認

表示ステータスとかはここを参照
http://qiita.com/kikuchi/items/59f219eae2a172880ba6

~~~
> Get-ExecutionPolicy
Restricted
~~~

* スクリプトが実行可能なポリシーに変更

~~~
> Set-ExecutionPolicy Bypass
実行ポリシーの変更
実行ポリシーは、信頼されていないスクリプトからの保護に役立ちます。実行ポリシーを変更すると、about_Execution_Policies
のヘルプ トピック (http://go.microsoft.com/fwlink/?LinkID=135170)
で説明されているセキュリティ上の危険にさらされる可能性があります。実行ポリシーを変更しますか?
[Y] はい(Y)  [A] すべて続行(A)  [N] いいえ(N)  [L] すべて無視(L)  [S] 中断(S)  [?] ヘルプ (既定値は "N"): Y
~~~

* chocolateyのインストール

https://chocolatey.org/install

~~~
> iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
~~~


## node.jsのインストール

* node.jsのバージョン管理ツール(nodist)をインストールする

~~~
> cinst nodist -y
~~~

※ インストールが完了したらPowerShellを再起動する

~~~
> nodist -v
0.8.8
~~~

* nodist でインストールできるnode.jsのバージョンを確認する

~~~
> nodist dist
~~~

* 指定したnode.jsのバージョンに切り替える

~~~
> nodist 8.1.2
~~~

* 現在のnode.jsのバージョンを確認する

~~~
> nodist
  (x64)
	7.2.1
> 8.1.2  (global: 8.1.2)
~~~


## Angular-CLIをインストールする

* インストール

~~~
> npm install -g @angular/cli
> ng version
    _                      _                 ____ _     ___
   / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
  / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
 / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
/_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
					               |___/
@angular/cli: 1.1.2
node: 8.1.2
os: win32 x64
~~~


## AngularJS Project の新規作成

* 新規プロジェクトの作成
任意のディレクトリに移動する

~~~
> ng new ${project name}
~~~

* 雛形を実行する

以下のコマンドを実行し、ブラウザで「http://localhost:4200/」を入力する。

~~~
> cd ${project name}
> ng serve
~~~



