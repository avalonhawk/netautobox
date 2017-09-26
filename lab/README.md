# Network Automation Lab

Lab environment based on Ansible VM and vSRX + VIRL for basic multivendor lab. Topology sourced from [here](https://github.com/ipspace/NetOpsWorkshop/tree/master/topologies/vSRX%2BVIRL)

The *Vagrant* file creates:
* **nms** virtual machine running Ubuntu 14.04 and loads necessary modules
* **srx** virtual machine running vSRX box for VMware Vagrant providers.

## Notes

* You **MUST** use VMware desktop virtualization product (Workstation or Fusion) - other hypervisors are not supported by VIRL.
* Use `--provider` argument when starting the Vagrant virtual machines for the first time; Vagrant might use the VirtualBox provider otherwise
* The Ansible and vSRX virtual machines are connected to *vmnet2* network (the VIRL management network) and use IP address 172.16.1.12 and 172.16.1.13.
* You might want to the included VIRL topology (with one Cisco IOS router and one Nexus-OS switch) as a starting point.

## More information

* [Ansible for Networking Engineers](http://www.ipspace.net/Ansible_for_Networking_Engineers) online course ([contents](https://my.ipspace.net/bin/list?id=AnsibleOC))
* [Building Network Automation Solutions](http://www.ipspace.net/Building_Network_Automation_Solutions) online course ([contents](https://my.ipspace.net/bin/list?id=NetAutSol))

