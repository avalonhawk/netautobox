# Network Automation Lab

Lab environment based on Ansible VM and vSRX + VIRL for basic multivendor lab. 

The `Vagrant` file creates:
* one **nms** virtual machine running Ubuntu 14.04 and loads necessary modules
* one **srx** virtual machine running vSRX box for VMware Vagrant providers
* Both VMs are connected to the *vmnet2* network - shared with VIRL. See below

The `.virl` topology file creates a toplogy with the following attributes:
* two IOSv routers
* each router has a connection to the `flat` network
* one direct link between routers


