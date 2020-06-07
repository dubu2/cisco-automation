Role Name
=========

Multiple common automation tasks for managing Cisco Network Devices

Requirements
------------

CSR-1000v stood up as a test VM for Cisco / Ansible Automation Commands - Change the hostname to csr-1 and create a user named "test_user" per the "cisco-automation/hosts" file vars. Complete the ssh key share between hosts and contorller. copy .ssh/known-hosts to root.

Role Variables
--------------

Create "hosts" file inside the "cisco-automation" directory with following contents:
```
[cisco_unit_testing]
csr-1

[cisco_unit_testing:vars]
ansible_connection=network_cli
ansible_network_os=ios
ansible_become=yes
ansible_become_method=enable
ansible_password=sup3r$ecretPa$$w0rd
ansible_user=test_user
ansible_python_interpreter=/usr/bin/python
```

These variables are necessary for Ansible to use the proper syntax and methods of elevation for Cisco devices, as opposed to plain Linux devices.  They can also be put into the "group_vars/all.yml" file.

Dependencies
------------


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
- name: cisco automation
  hosts: cisco_unit_testing
  become: yes
  gather_facts: True
  roles:
    - cisco-automation
```
License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
