# encoding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANT_OS = 'ubuntu/trusty64'
VM_NAME = 'zoo'

Vagrant.configure(2) do |config|

  config.vm.box = VAGRANT_OS
  config.vm.hostname = VM_NAME
  config.vm.network "private_network", ip: '192.168.99.2'

  config.vm.provider "virtualbox" do |v|
    v.name = VM_NAME
    v.memory = 2048
    v.cpus = 2
  end

  config.vm.define :zoo do |zoo|  # Just to override "default" VM's name
  end

  # Ansible provisioner
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
    ansible.inventory_path = "ansible/inventory"
    ansible.sudo = true
    ansible.verbose = "vvv"
  end

  config.vm.provision "shell", inline: "netstat -lntp", run: "always"

end
