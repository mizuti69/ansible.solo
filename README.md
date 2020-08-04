# Ansible Playbooks

## How to Use
Develop using docker desktop for windows  
Add settings to mount project ansible on docker desktop  

### Step 0
The server running ansible must have python installed and have an ssh connection and network settings  

### Step 1
aunch docker desktop and build container

```
> cd docker
> docker-compose up -d
```

### Step 2
Define what to do  
Variables and execution can be branched if the definition is divided for each stage  

```
# vim hosts/develop
```

After defining, make sure that you can connect via ssh  

```
# ansible -i hosts/develop develop -m ping -u ssh_user --private-key=ssh_key
```

By defining it in ansible.cfg, it is possible to reduce the number of user names and keys specified.  

```
# vim ansible.cfg
```

## Step 3
Execution role setting  

```
# vim roles/basic-role/tasks/main.yml
```

and

```
# vim roles/basic-role/meta/main.yml
```

and

```
# vim roles/basic-role/hundlers/main.yml
```

## Step 4
Set variables according to the task to be executed  

* All grobal environments

```
# vim group_vars/all
```

* Host group environments

```
# vim group_vars/develop
```

* Host environments

```
# vim host_vars/devweb01
```

* Playbooks environment

```
# vim playbooks/*/vars/main.yml
```


See official documentation for variable precedence  

Variable precedence: Where should I put a variable?  
https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable  

### Step 5
Playbook execution  

```
# ansible-playbook -i hosts/develop provisioning.yml --syntax-check
# ansible-playbook -i hosts/develop provisioning.yml
```

## Documentetion
**Ansible Documentation**  
https://docs.ansible.com/  

**Ansible Documentation Module Index**  
https://docs.ansible.com/ansible/latest/modules/modules_by_category.html  

### Create a new project
create and initialize work directory

```
# ansible-garaxy init role_name
```

### ansible command option

**Options**  

* `--list-hosts`: outputs a list of matching hosts; does not execute anything else  
* `--syntax-check`: perform a syntax check on the playbook, but do not. execute it  

**Connection Options**  

* `-k`,`--ask-pass`: ask for connection password  
* `--private-key=PRIVATE_KEY_FILE`,`--key-file=PRIVATE_KEY_FILE`: use this file to authenticate the connection  
* `-u REMOTE_USER`,`--user=REMOTE_USER`: connect as this user (default=None)  

**Privilege Escalation Options**  

* `-b`, `--become`: run operations with sudo  
* `--become-user=BECOME_USER`: desired sudo user (default=root)  
* `-K`,`--ask-become-pass`: ask for privilege escalation password  

### ansible-playbook command option

**Options**  

* `-C, --check`: don't make any changes; instead, try to predict some of the changes that may occur  
* `-t TAGS`,`--tags=TAGS`: only run plays and tasks tagged with these values  
* `--skip-tags=SKIP_TAGS`: only run plays and tasks whose tags do not match these values  
