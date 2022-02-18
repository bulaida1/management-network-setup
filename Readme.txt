1. set a temporary ip address on all servers and make sure there is SSH connectivity afterwards
ip addr add x.x.x.x/x dev ens160
ip link set ens160 up
ip r add default via x.x.x.x

3. paste all management node servers ip and hostnames in hosts_prep.xlsx. copy the values in column "inventory" to the hosts file

4. edit the network details in guardicore_interfaces_ens160.yaml. replace 'gateway4: <x.x.x.x>' with the default gateway. replace 'addresses: [<x.x.x.x>, <x.x.x.x>]' with the DNS servers. Is asumed that these are the same for all management nodes.

5. run:
ansible-playbook set_network.yaml -i hosts -u "$USER" -k