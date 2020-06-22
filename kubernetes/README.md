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

### The Lab VMs
This lab consists of five VMs - two control plane nodes (`controller-0,1`), 
two worker nodes (`worker-0,1`), and one `kubeapi` load balancer.
![KubernetesCluster](images/kubernetes-cluster.png | width=800)


## Contents
In order to set up the cluster, the contents of this guide should be followed 
in the order listed below.
- [Prerequisites](docs/01-prerequisites.md)
- [Provisioning Compute Resources](docs/02-compute-resources.md)
- [Installing Kubernetes Dependencies](docs/03-kube-dependenceis.md)
- [`kubeapi` Load Balancer](docs/04-kubeapi-lb.md)
- [Bootstrapping the Cotroller Plane](docs/05-bootstrap-controllers.md)
- [Bootstrapping the Worker Nodes](docs/06-bootstrap-workers.md)
- [Ingress Controller and Load Balancer](docs/07-ingress-lb.md)
- [Configure `kubectl` for Remote Access](docs/08-remote-access.md)
- [Smoke Tests](docs/09-smoke-test.md)
- [Clean Up](docs/10-clean-up.md)

## Credits
[Kubernetes the Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way)
