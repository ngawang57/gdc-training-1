# Prerequsites

## Tools
Before continuing with this guide make sure you have the following tools installed:
- [VirtualBox](https://www.virtualbox.org/)
- [Vagrant](https://www.vagrantup.com/)
- [Ansible](https://github.com/ansible/ansible)

## Network
In VirtualBox, create a host-only network if you don't already have one.

List host-only networks:
```
vboxmanage list hostonlyifs
```

Create a host-only network:
```
vboxmanage hostonlyif create
```

## User
When provisioning VMs using Vagrant, a user is provisioned and key-based 
SSH authentication enabled for it in each of the VMs using Ansible provisioner.
This user needs to be defined by editing the attached
[playbook](../playbooks/add-user.yaml). Refer [here](../../ansible/README.md).

The user provisioning the cluster should have a SSH key pair generated in
 `$HOME/.ssh` directory.
