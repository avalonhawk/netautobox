# -*- mode: ruby -*-
# vi: set ft=ruby :

require "vagrant-host-shell"
require "vagrant-junos"

Vagrant.configure(2) do |config|
  config.vm.box = "phusion/ubuntu-14.04-amd64"
  config.vm.box_check_update = false

  config.vm.define "nms" do |nms|
    nms.vm.host_name = "nms"
    nms.vm.network "private_network", ip: "172.16.1.12"
    nms.vm.synced_folder "data/", "/vagrant_data"
#  config.vm.provision "shell",inline: <<-SHELL
#    apt-get update
#    apt-get -qq install git
#    git clone https://github.com/ipspace/NetOpsWorkshop
#    sh -c "/home/vagrant/NetOpsWorkshop/install/install.sh
#  SHELL
  end

  config.vm.define "srx" do |srx|
    srx.vm.box = "juniper/ffp-12.1X47-D15.4-packetmode"
    srx.vm.host_name = "srx"
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
