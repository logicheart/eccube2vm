# eccube2vm
EC-CUBE 2.13.3 and VirtualBox/Vagrant configuration

EC-CUBE2.13系をローカル仮想環境にインストールするためのプロダクト一式です。


## 環境構築方法

Linux, Apache, PostgreSQL, PHPの環境をVagrantで構築できます。

### 【Windows】msysGit(Git for Windows)のインストール

1. https://msysgit.github.io/ よりGit for Windowsをダウンロード
2. exeファイルを実行し指示に従いインストールする。
3. インストール中「Use Git from Git Bash Only」「Use Git from the Windows Command Prompt」を選択する画面では、「Use Git from Git Bash Only」を選択する。（説明の都合上）
4. インストール中「Checkout Windows-style, commit Unix-style line endings」「Checkout as-is, commit Unix-style line endings」「Checkout as-is, commit as-is」を選択する画面では、 **「Checkout as-is, commit as-is」を選択する。** （絶対！）

※Macの場合はBashターミナル、Gitがデフォルトでインストールされているので新たにインストールする必要はありません。

### 【Mac&Windows共通】VirtualBoxのインストール

1. http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html より対象OSのパッケージをダウンロード
2. パッケージよりインストールする。（画面の指示通りで問題ありません）

### 【Mac&Windows共通】Vagrant のインストール

1. http://www.vagrantup.com/downloads より対象OSのパッケージをダウンロード
2. パッケージよりインストールする。

### ターミナルの起動方法

####【Mac】

アプリケーション－「ユーティリティ」－「ターミナル」を起動

####【Windows】

スタートメニュー－「Git」－「Git Bash」を起動

#### ターミナルでvagrantのインストールを確認

```
$ vagrant -v
Vagrant 1.7.2
```

### 【Mac&Windows共通】その他の準備

1. プラグインのインストール

```
$ vagrant plugin install vagrant-omnibus
```

### プロダクトのダウンロード

```
$ pwd
（現在のディレクトリ）
$ cd <適当なディレクトリ>
$ git clone https://github.com/logicheart/eccube2vm.git
$ ls
 :
eccube2vm
 :
```

### サーバ構築・起動

```
$ cd eccube2vm
$ vagrant up
```

*Congratulations!!! Install Success. Please access http://localhost:10080* と表示されたら正常終了です。

※初回は仮想マシンのイメージをダウンロードするため時間がかかります。

### サーバにアクセス

1. ブラウザよりhttp://localhost:10080 にアクセス

2. EC-CUBEのインストーラが表示されるので、指示に従い初期構築を行う。

### サーバ停止

```
$ vagrant halt
```
