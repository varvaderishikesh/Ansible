# Ansible

- Ansible is an open-source configuration management tool, deployment and orchestration tool.
- Ansible uses YAML syntax for expressing Ansible playbooks. YAML is very easy for humans to understand, read and write when compared to other data formats like XML and JSON.
- Ansible is agentless, unlike Chef which requires an agent called chef-client.
- Ansible communicates using ssh whereas Chef needs a knife CLI to communicate.

# Ansible server setup with nodes

### Ansible Installation

### Prerequisites

1. An AWS EC2 instance 

### Installation steps:

Add a EPEL (Extra Packages for Enterprise Linux)third party repository to get packages for Ansible 
```sh 
rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```

Install Ansible
```sh 
yum install ansible -y 
```

Check Ansible version 

```sh 
ansible --version
```

Create a new user for ansible administration & grant admin access to user (Master and Slave)
```sh 
useradd ansadmin
passwd ansadmin
# below command addes ansadmin to sudoers file. But strongly recommended to use "visudo" command if you are aware vi or nano editor. 
echo "ansadmin ALL=(ALL) ALL" >> /etc/sudoers
```
Now, uncomment the following using vi editor
```sh 
vi /etc/ssh/sshd_config
Uncomment the following:
PermitRootLogin yes
PasswordAuthentication yes

Comment the following 
#PermitEmptyPasswords no
#PasswordAuthentication no

And restart the sshd using : 
- service sshd restart
```

Login as a ansadmin user on master and generate ssh key (Master)
```sh 
ssh-keygen
```
Copy keys onto all ansible client nodes (Master)
```sh 
ssh-copy-id <target-server>
```

Update target servers information on /etc/ansible/hosts file (Master)
```sh 
echo "<target server IP>" > /etc/ansible/hosts
```
Run ansible command as ansadmin user it should be successful (Master)
```sh 
ansible all -m ping
```

### Now I have written some useful Ansible playbooks inside this repository. You can check them as per your requirement.
