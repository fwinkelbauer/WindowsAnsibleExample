# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-add-repository -y ppa:ansible/ansible
    sudo apt-get -y update
    sudo apt-get -y install software-properties-common
    sudo apt-get -y install libffi-dev libssl-dev
    sudo apt-get -y install ansible
    sudo apt-get -y install python-pip
    sudo -H pip install --upgrade setuptools
    sudo -H pip install --upgrade pip
    sudo -H pip install pywinrm
    sudo -H pip install pywinrm[credssp]
  SHELL
end
