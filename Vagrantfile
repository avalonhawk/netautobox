# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<-SHELL
  echo "#### Updating packages and installing git and ansible ####"
  apt-get update
  apt-get -qq install software-properties-common git
  apt-add-repository ppa:ansible/ansible
  apt-get update
  apt-get -qq install ansible
  echo "#### Cloning necessary git repos ####"
  git clone https://github.com/ipspace/NetOpsWorkshop /home/vagrant/NetOpsWorkshop
  git clone https://github.com/avalonhawk/netautobox /home/vagrant/netautobox
  echo "#### Running install scripts and changing ownership ####"
  sh -c "/home/vagrant/NetOpsWorkshop/install/install.sh"
  chown -Rh vagrant:vagrant /home/vagrant/NetOpsWorkshop
  chown -Rh vagrant:vagrant /home/vagrant/netautobox
SHELL

require "vagrant-host-shell"
require "vagrant-junos"

Vagrant.configure(2) do |config|
  config.vm.box = "phusion/ubuntu-14.04-amd64"
  config.vm.box_check_update = false

  config.vm.define "nms" do |nms|
    nms.vm.host_name = "nms.lab"
    nms.vm.network "private_network", ip: "172.16.1.12"
    nms.vm.synced_folder "data/", "/vagrant_data"
  config.vm.provision "shell",inline: $script
  end

  config.vm.define "srx" do |srx|
    srx.vm.box = "juniper/ffp-12.1X47-D15.4-packetmode"
    srx.vm.host_name = "srx.lab"
    srx.vm.network "private_network", ip: "172.16.1.13"

    srx.vm.provider "vmware_fusion" do |v|
      v.vmx["memsize"] = "2048"
      v.vmx["ethernet2.generatedAddress"] = nil
      v.vmx["ethernet2.connectionType"] = "custom"
      v.vmx["ethernet2.present"] = "TRUE"
      v.vmx["ethernet2.vnet"] = "vmnet2"
    end
  end
end
