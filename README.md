
# remote_env_win

## 環境構築手順

VirtualBoxをインストール

https://www.virtualbox.org/wiki/Downloads

Vagrantをインストール（1.9.0推奨。特に、Vagrant 1.8.7はCentOS7.2が動かないので注意）

https://www.vagrantup.com/downloads.html

以下のコマンドで環境構築

```sh
$ vagrant box add centos7.2 https://github.com/CommanderK5/packer-centos-template/releases/download/0.7.2/vagrant-centos-7.2.box
$ vagrant up # at /path/to/remote_env_win
```

 * boxの名前は必ずcentos7.2とする。
 * boxのURLが無効だったら http://www.vagrantbox.es/ からcentos7.2のboxのURLを探す。
 * 初回起動時、タスクの一部は存在確認のためにfailedになるが、ignoringとなっているものに関しては正常な動作である。
 最終的に以下のようにunreachable / failedの項目が0になっていれば全ての正常に終了したことになる。

```
PLAY RECAP *********************************************************************
localhost                  : ok=14   changed=9    unreachable=0    failed=0
```
