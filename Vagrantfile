# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2004"
  config.vm.synced_folder '.', '/vagrant'
  config.vm.provider "virtualbox" do |vb|
    vb.name = 'nushell'
    vb.gui = false
    vb.memory = 8192
    vb.cpus = 8
    vb.linked_clone = true
  end
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
