### A simple Ansible playbook to exectue a task on Node using variables


### variables.yml

```sh
--- # Ansible playbook to execute task on target node using variables
- hosts: demo
  user: ansible
  become: yes
  connection: ssh
  vars:
          pkgname: httpd
  tasks:
          - name: install HTTPD server
            action: yum name='{{pkgname}}' state=installed

```
