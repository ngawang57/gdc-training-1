# Installing Kubernetes Dependencies

We will install Kubernetes dependencies using Ansible.

## Ansible Inventory
An inventory file is provided in this repository - `kubernetes/hosts`.
Edit this file and set the appropriate `ansible_hosts` values.

## Install Dependencies
Review the playbook - `kubernetes/playbooks/kube-dependencies.yaml` - and 
related files once before running it.

Assuming you are in `kubernetes` directory from the root of the cloned 
repo, and run
```
ansible-playbook -i hosts playbooks/kube-dependencies.yaml
```

Dependencies will be installed on all the Controller and Worker nodes
along with appropriate configurations required for bootstrapping a 
highly available Kubernetes cluster.
