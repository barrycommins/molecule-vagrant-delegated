# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-16.04"
  config.vm.synced_folder "./", "/molecule/molecule_vagrant_test"

  # install python, molecule and ansible
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y python python-pip
    pip install molecule ansible
  SHELL

  # run molecule test
  config.vm.provision "molecule", type: "shell", inline: "cd /molecule/molecule_vagrant_test && molecule test"
end
