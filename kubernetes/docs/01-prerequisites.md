# Prerequsites
Before continuing with this guide make sure you have the following tools installed:
- [VirtualBox](https://www.virtualbox.org/)
- [Vagrant](https://www.vagrantup.com/)
- [Ansible](https://github.com/ansible/ansible)

In VirtualBox, create a host-only network if you don't already have one.

List host-only networks:
```
vboxmanage list hostonlyifs
```

Create a host-only network:
```
vboxmanage hostonlyif create
```
