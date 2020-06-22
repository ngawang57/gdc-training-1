# Kubernetes Cluster - WIP

**This a work in progress**

This guide walks you through setting up a highly available
[Kubernetes](https://github.com/kubernetes/kubernetes) cluster using `kubeadm`. 

## The Lab Environment
The resulting Kubernetes cluster will be running on VirtualBox provisioned with Vagrant and Ansible.
This setup uses [Docker CE](https://github.com/docker/docker-ce) as the container
[runtime](https://kubernetes.io/docs/setup/production-environment/container-runtimes) 
and [Calico](https://docs.projectcalico.org/getting-started/kubernetes/) 
[CNI](https://kubernetes.io/docs/concepts/extend-kubernetes/compute-storage-net/network-plugins/) 
plugin for networking.

## Contents
In order to set up the cluster, the contents of this guide should be followed 
in the order listed below.

- [Prerequisites](docs/01-prerequisites.md)
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
