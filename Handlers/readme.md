### A simple Ansible playbook to exectue a task on Node using handlers

Handlers are just like regular tasks in an Ansible playbook, but run only when a task contains a notify directive and also indicates that it changed something.

### handlers.yml
```sh
--- # Ansible Playbook with Handlers
- hosts: demo
  user: ansible
  become: yes
  connection: ssh
  tasks:
          - name: install HTTPD server
            action: yum name=httpd state=installed
            notify: restart httpd
  handlers:
          - name: restart httpd
            action: service name=httpd state=restarted


```

### Note:
- notify and name inside handlers section should be same in order for Handler to work
