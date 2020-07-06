# Cisco_Re-IP_Switch
Re-IP a Cisco switch from one vlan to another

First draft is working, needs additonal testing.

The handler for saving the config is commented out by default. If you want the config to save at the end of the playbook uncomment the ```notify: save ios``` line in the last task in cisco_re-ip_switch/tasks/main.yml.

An ansible.cfg file is included to disable host key checking for this playbook. This is required due to the host key changing when the IP changes. You can choose to use your own ansible.cfg file if you wish instead.

To use this playbook/role, update the vars in ```cisco_re-ip_switch/vars/main.yml```.

* ```target_interface: Vlan4000``` // target for new layer 3 SVI management interface (capital V is important)
* ```source_interface: Vlan100``` // current layer 3 SVI management interface (capital V is important)
* ```current_subnet: "192.168.101."``` // make sure to keep the . at the end so the regex works properly
* ```new_subnet: "192.168.103."``` // make sure to keep the . at the end so the regex works properly
* ```old_cidr: "/24"``` // concatenates to the end of the IP address for the ios_l3_interfaces config
* ```new_cidr: "/24"``` // concatenates to the end of the IP address for the ios_l3_interfaces config
* ```default_gateway: "192.168.103.1"``` // new default gateway to set if re-ip is successful