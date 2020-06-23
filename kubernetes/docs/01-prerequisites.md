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

Next: [Provisioning Compute Resources](02-compute-resources.md)
