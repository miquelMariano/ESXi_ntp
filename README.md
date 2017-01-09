Role Name
=========

This role configure ntp servers in our ESXi servers

Requirements
------------

No requirements

Role Variables
--------------

Is necessary that variables ntp1 & ntp2 has been defined in our inventory file

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

ansible-playbook playbooks/ESXi_config.yml -i inventory/ESXi --extra-vars "servers=test role=ntp_config" --tags "set|get”


License
-------

BSD

Author Information
------------------

[@miquelMariano](https://twitter.com/miquelMariano)

