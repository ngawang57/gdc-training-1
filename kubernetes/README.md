# Kubernetes Cluster - WIP

**This a work in progress**

This guide walks you through setting up a highly available
[Kubernetes](https://github.com/kubernetes/kubernetes) cluster using `kubeadm`. 

## The Lab Environment
The resulting Kubernetes cluster will be running on [VirtualBox](https://www.virtualbox.org/) 
provisioned with [Vagrant](https://www.vagrantup.com/) and 
[Ansible](https://github.com/ansible/ansible).
This setup uses [Docker CE](https://github.com/docker/docker-ce) as the container
[runtime](https://kubernetes.io/docs/setup/production-environment/container-runtimes) 
and [Calico](https://docs.projectcalico.org/getting-started/kubernetes/) 
[CNI](https://kubernetes.io/docs/concepts/extend-kubernetes/compute-storage-net/network-plugins/) 
plugin for networking.

All the VMs provisioned using Vagrant are based on official Ubuntu 18.04 images.

## Prerequsites
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

## Contents
In order to set up the cluster, the contents of this guide should be followed 
in the order listed below.

- [Provisioning Compute Resources](02-compute-resources.md)
- [Installing Kubernetes Dependencies](03-kube-dependenceis.md)
- [`kubeapi` Load Balancer](04-kubeapi-lb.md)
- [Bootstrapping the Cotroller Plane](05-bootstrap-controllers.md)
- [Bootstrapping the Worker Nodes](06-bootstrap-workers.md)
- [Ingress Controller and Load Balancer](07-ingress-lb.md)
- [Configure `kubectl` for Remote Access](08-remote-access.md)
- [Smoke Tests](09-smoke-test.md)
- [Clean Up](10-clean-up.md)

## Credits
[Kubernetes the Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way)
