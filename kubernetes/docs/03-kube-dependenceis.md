# Installing Kubernetes Dependencies

We will install Kubernetes dependencies using Ansible.

## Ansible Inventory
An inventory file is provided in this repository - `kubernetes/hosts`.
Edit this file and set the appropriate `ansible_hosts` values.

## Install Dependencies
Assuming you are in `kubernetes` directory from the root of the cloned 
repo, review the playbook - `playbooks/kube-dependencies.yaml` - and 
related files once before running it.

```
ansible-playbook -i hosts playbooks/kube-dependencies.yaml
```

Dependencies will be installed on all the Controller and Worker nodes
along with appropriate configurations required for bootstrapping a 
highly available Kubernetes cluster.

Next: [kube-apiserver Load Balancer](04-kubeapi-lb.md)
