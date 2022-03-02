# management-network-setup

This is Ansible code to setup network prerequisites for management nodes deployment  
Tested on: Centra version: 39.2.4

# Instructions
1. set a temporary ip address on all servers and make sure there is SSH connectivity between control node and the rest of servers:
ip addr add x.x.x.x/x dev ens160
ip link set ens160 up
ip r add default via x.x.x.x

2. paste all management node servers ip, subnet (in short format, without the "/") and hostnames in hosts_prep.xlsx. copy the values in column "inventory" to the hosts file

3. edit the network details in guardicore_interfaces_ens160.yaml. replace 'gateway4: <x.x.x.x>' with the default gateway. replace 'addresses: [<x.x.x.x>, <x.x.x.x>]' with the DNS servers. Is asumed that these are the same for all management nodes.

4. run from control node:
ansible-playbook set_network.yaml -i hosts -u "$USER" -k

5. restart all servers
