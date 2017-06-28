Role Name
=========

ESXi_ntp_config configure ntp servers in our ESXi servers

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

This play is executed when update_mode var is "true" and ensure that role is up to date. By default update var is "false"

miquelMariano.ESXi_{{ role }} folder must be exist. If not, the playbook not found role and fails. You shoud make dir manually "mkdir /etc/ansible/my_role"

```yaml
###
###ESXi_config.yml
###		
- hosts: ansible
  user: root
  tasks:
    - name: Ensure that role are up to date
      command: ansible-galaxy install --force {{ item }}
      with_items:
        - miquelMariano.ESXi_{{ role  }}
      when:
        - update_mode | default(False)
      tags: update
      ignore_errors: yes

- hosts: "{{ servers }}:!localhost"
  user: root
  serial: 1
  roles:
   - role: miquelMariano.ESXi_{{ role  }}
~
~
~

```

Usage
------

`ansible-playbook playbooks/ESXi_config.yml -i inventory/ESXi --extra-vars "servers=servers_group1 role=ntp_config update_mode=true" --tags "update|set|get"`


License
-------

BSD

Author Information
------------------

[miquelMariano.github.io](https://miquelMariano.github.io) | [Twitter](https://twitter.com/miquelMariano)

