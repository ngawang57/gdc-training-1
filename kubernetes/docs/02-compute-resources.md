# Provisioning Compute Resources

The compute resources will be provisioned using Vagrant. The [Vagrantfile](../Vagrantfile)
is located at `kubernetes/Vagrantfile`.

In order to provision the resources:
1. Clone this repository - `git clone https://github.com/lungtendo/gdc-training`.
2. `cd gdc-training/kubernetes`.
3. Edit the `Vagrantfile` and replace `XY` in `NETWORK_PREFIX = "192.168.XY."` with proper address.
4. Edit the ansible plabook `playbooks/add-user.yaml` and replace `USERNAME` with your user name.
5. Make other changes to suit your environment.
6. Run `vagrant up`.

In a few miutes you should have five VMs running. 

## `/etc/hosts` Entry
Add entries in your local `/etc/hosts` file for each of the VMs.
```
192.168.XY.11  controller-0.local controller-0
192.168.XY.12  controller-1.local controller-1
192.168.XY.21  worker-0.local worker-0
192.168.XY.22  worker-1.local worker-1
192.168.XY.30 lb.local lb
```
Replace `XY` or the addresses with appropriate values for your environment.

## Access the VMs

### Using Vagrant
Run `vagrant status` to check.
Run `vagrant ssh <vm_name>` to login.

### Directly
Make sure you can login directly using plain SSH on all the VMs.
