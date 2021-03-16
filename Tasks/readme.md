### A simple Ansible playbook to exectue a task on Node


### task.yml
```sh
--- # Playbook with task to be executed on a target node
- hosts: demo
  user: ansible
  become: yes
  connection: ssh
  tasks:
          - name: Install HTTPD on CentOS 7
            action: yum name=httpd state=installed
```
