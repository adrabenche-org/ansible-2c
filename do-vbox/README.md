# What 
Deploy on standalone Digital Ocean Droplet, or a Virtual Box machine. Before start **access as root to the box using ssh is required**.

A new user called **operator** will be created.

## Deploy

You must deploy the ansible playbooks on the following order. To know how to do it you must check on each role `README.md` file. 
Add the IP address to the inventory on the inventory file `.inventory/hosts_inventory` and then access role by role:

1. [setup_server](roles/setup_server/README.md)
```bash
$ ansible-playbook -i inventory/ -l cardano-nodes setup-node.yml
```
2. [cardano_node](roles/cardano_node/README.md)
```bash
$ ansible-playbook -i inventory/ -l cardano-nodes install-cardano-node.yml
```
3. [cardano_cli](roles/cardano_cli/README.md)
```bash
$ ansible-playbook -i inventory/ -l cardano-nodes install-cardano-cli.yml
```
4. [oura](roles/oura/README.md)
```bash
$ ansible-playbook -i inventory/ -l cardano-nodes install-oura.yml
```
## Install full stack

Or, if you want to deploy all the ansible playbooks with all the apps, just configure each role (as said on each README.md file previously mentioned) and execute
```bash
$ ansible-playbook -i inventory/ -l cardano-nodes install-full-stack.yml
```

:exclamation: : **For Digital Ocean**, probably you **only** need to change the on the file `.roles/cardano_node/defaults/main.yml`, under `cardano_node_db_fs: "/dev/sdb"` to `cardano_node_db_fs: "/dev/sda"`