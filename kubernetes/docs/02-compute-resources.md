# Provisioning Compute Resources

The compute resources will be provisioned using Vagrant. The [Vagrantfile](../Vagrantfile)
is located at `kubernetes/Vagrantfile`.

In order to provision the resources:
1. Clone this repository - `git clone https://github.com/lungtendo/gdc-training`.
2. `cd gdc-training/kubernetes`.
3. Edit the `Vagrantfile` and adjust settings appropriate for your environment.
4. Run `vagrant up`.

## Access the VMs
In a couple of miutes you should have five VMs running. 

Run `vagrant status` to check. 

Run `vagrant ssh <vm_name>` to login.

## `/etc/hosts` Entry
Add entries in `/etc/hosts` for each of the VMs.
```
192.168.XY.11  controller-1.local controller-1
192.168.XY.12  controller-2.local controller-2
192.168.XY.21  worker-1.local worker-1
192.168.XY.22  worker-2.local worker-2
192.168.XY.30 lb.local lb
```

Replace `XY` or the addresses with appropriate values for your environment.

