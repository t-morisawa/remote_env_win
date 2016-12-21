
# remote_env_win

## 環境構築手順

Vagrantをインストール

https://www.vagrantup.com/downloads.html

ただし、Vagrant 1.8.7だけCentOS7.2が動かないので注意

以下のコマンドで環境構築

```sh
$ vagrant box add centos7.2 https://github.com/CommanderK5/packer-centos-template/releases/download/0.7.2/vagrant-centos-7.2.box
$ vagrant up # at /path/to/remote_env_win
```

 * boxの名前は必ずcentos7.2とする。
 * boxのURLが無効だったら http://www.vagrantbox.es/ からcentos7.2のboxのURLを探す。
 * vagrant up後、ansibleの冪等性を保つためfatalが出力されるが問題ない。最終的に以下のように `unreachable=0 failed=0` となっていればOK。

```
PLAY RECAP *********************************************************************
localhost                  : ok=14   changed=9    unreachable=0    failed=0
```
