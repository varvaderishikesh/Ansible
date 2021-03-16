### Ansible playbook to exectue a task on different nodes using conditions

- Whenever we have different scenario, we put conditions according to scenario.
- When statement: Sometimes you want to skip a particular command on a particular node.

### conditions.yml
```sh
--- # My Condition Playbook
- hosts: demo
  user: ansible
  become: yes
  connection: ssh
  tasks:
          - name: Install apache server for Ubuntu
            command: apt-get -y install apache2
            when: ansible_os_family == "Debian"
          - name: Install apache server for Linux
            command: yum install httpd -y
            when: ansible_os_family == "RedHat"

```

