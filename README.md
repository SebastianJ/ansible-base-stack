## Installation/setup

Clone the repo:
```
git clone https://github.com/SebastianJ/ansible-base-stack.git && cd ansible-base-stack
```

Install roles using ansible galaxy:
```
ansible-galaxy install --role-file requirements.yml --roles-path roles
```

## Usage

### Inventory file

#### Alternative 1
Create inventories/YOUR_INVENTORY/inventory
Copy inventories/example/group_vars/all.yml to inventories/YOUR_INVENTORY/group_vars/all.yml

Run ansible:
```
ANSIBLE_STRATEGY=free ansible-playbook playbook.yml --inventory inventories/YOUR_INVENTORY/inventory
```


#### Alternative 2
Create inventories/YOUR_INVENTORY/inventory

Run ansible:
```
ANSIBLE_STRATEGY=free ansible-playbook playbook.yml --inventory inventories/YOUR_INVENTORY/inventory --extra-vars "ssh_port=8601 user_account_name=deploy user_account_path=/home/deploy"
```

### Without inventory file

Replace IP_ADDRESS with the ip address of the host you want to configure.

#### Using authorized keys
```
ANSIBLE_STRATEGY=free ansible-playbook --inventory IP_ADDRESS, playbook.yml --extra-vars "ansible_ssh_user=root"
```

#### Using a password
```
ANSIBLE_STRATEGY=free ansible-playbook --inventory IP_ADDRESS, playbook.yml --extra-vars "ansible_ssh_user=root ansible_ssh_pass=pass"
```
