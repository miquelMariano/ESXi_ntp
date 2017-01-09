Role Name
=========

This role configure ntp servers in our ESXi servers

Requirements
------------

No requirements

Role Variables
--------------

Is necessary that variables ntp1 & ntp2 has been defined in our inventory file

Example:

		[all]
		servers_group1
		servers_group2

		[servers_group1]
		server1
		server2
		server3

		[servers_group2]
		server11
		server12
		server13

		[all:vars]
		ntp1='0.pool.ntp.org'
		ntp2='1.pool.ntp.org'

Dependencies
------------

No dependencies

Example Playbook
----------------

		- hosts: "{{ servers }}:!localhost"
  		  user: root
  		  serial: 15
 		  roles:
 		  - "miquelMariano.ESXi_{{ role }}"

Usage
------

ansible-playbook playbooks/ESXi_config.yml -i inventory/ESXi --extra-vars "servers=servers_group1 role=ntp_config" --tags "set|get”


License
-------

BSD

Author Information
------------------

[@miquelMariano](https://twitter.com/miquelMariano)

