# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "centos7.2"
  config.ssh.insert_key = false
  config.vm.network :private_network, ip: "192.168.33.10"

  # シンボリックリンク貼りたい & メモリを自由に割り当てたい
  config.vm.provider :virtualbox do |vb|
    vb.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/home/vagrant/","1"]
    vb.customize ["modifyvm", :id, "--memory", "3072"]
  end

  # 共有フォルダ設定
  %w(
    project
    .go
  ).each do |dir|
    config.vm.synced_folder "./#{dir}", "/home/vagrant/#{dir}" if  File.exist?("./#{dir}")
  end
  
  # playbookの設定
  config.vm.provision 'ansible_local' do |ansible|
    ansible.install = true
    ansible.limit = 'all'
    ansible.inventory_path = 'remote_playbook/inventory/local'
    ansible.playbook = 'remote_playbook/playbook.yml'
  end
end

