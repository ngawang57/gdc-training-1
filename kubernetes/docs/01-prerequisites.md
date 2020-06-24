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

## SSH Key Pair
Generate SSH key pair for the local user if you don't already have one.
```
ssh-keygen -t rsa -C 'your-email@domain'
```

## Destroy Existing VMs
Destroy existing VMs from previous lab to free up resources.

List VMs / running VMs:
```
vboxmanage list vms
vboxmanage list vms runningvms
```

Go to the Vagrant project directory and delete the VMs:
```
cd ~/gdc-training/ansible
vagrant destroy -f
```

> Verify that there are no orphaned VMs.

Next: [Provisioning Compute Resources](02-compute-resources.md)
