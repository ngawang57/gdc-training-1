# `kube-apiserver` Load Balancer

Here we will install and configure load balancer for `kube-apiserver` 
using Nginx.

## Load Balancer Configuration
Assuming your CWD is `gdc-training/kubernetes`, 
edit `playbooks/configs/nginx-loadbalancer.conf` and make appropriate
changes. The rest is taken care of in the Ansible playbook.

## Install and Configure Nginx
Review the playbook - `playbooks/nginx-loadbalancer.yaml` - before running.

```
ansible-playbooks -i hosts playbooks/nginx-loadbalancer.yaml
```

Once installation is complete check to make sure it is configured properly.

```
nc -v lb 6443
```
You can use IP address instead of `lb`.


Next: [Bootstrapping the Cluster](05-bootstrap-cluster.md)
