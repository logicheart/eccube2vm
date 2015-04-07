# eccube2vm
EC-CUBE 2.13.3 and VirtualBox/Vagrant configuration

EC-CUBE2.13系をローカル仮想環境にインストールするためのプロダクト一式です。


## 環境構築方法

Linux, Apache, PostgreSQL, PHPの環境をVagrantで構築できます。

*※現時点ではMacでの環境構築方法を記述しています。Windows版は追って記載します。*


### VirtualBoxのインストール

1. http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html より対象OSのパッケージをダウンロード
2. パッケージよりインストールする。（画面の指示通りで問題ありません）

### Vagrant のインストール

1. http://www.vagrantup.com/downloads より対象OSのパッケージをダウンロード
2. パッケージよりインストールする。
3. ターミナルでvagrantのインストールを確認

```
$ vagrant -v
Vagrant 1.7.2
```

### その他の準備

1. プラグインのインストール

```
$ vagrant plugin install vagrant-omnibus
```

### プロダクトのダウンロード

```
$ cd <適当なpath>
$ git clone https://github.com/logicheart/eccube2vm.git
```

### サーバ構築・起動

```
$ cd <path>/eccube2vm/
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
