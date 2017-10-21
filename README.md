# Network Automation Lab

Lab environment based on [Ivan Pepelnjak's](https://github.com/ipspace/) Ansible VM and vSRX + VIRL [topology](https://github.com/ipspace/NetOpsWorkshop/tree/master/topologies/vSRX%2BVIRL) for basic multivendor lab. This lab is being used for the [Building Network Automation Solutions Workshop](http://www.ipspace.net/Building_Network_Automation_Solutions) course.

The `Vagrantfile` creates:
* one **nms** virtual machine running Ubuntu 14.04 and loads necessary modules
* one **srx** virtual machine running vSRX box for VMware Vagrant providers
* Both VMs are connected to the *vmnet2* network - shared with VIRL. See below

The `ansible_lab.virl` topology file creates a toplogy with the following attributes:
* two IOSv routers
* each router has a connection to the `flat` network
* one direct link between routers


