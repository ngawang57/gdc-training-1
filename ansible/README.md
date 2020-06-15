# Ansible Lab

This directory contains two files of interest:
1. `Vagrantfile` - defines a VirtualBox VMs to be used a an Ansible-managed host
2. `add-user.yaml` - Ansible playbook to provision a user account along with the VMs


## 1. Generate SSH Keys on the lab server
Login to the lab server:
```
ssh username@172.31.33.124
```
Replace `username` with your own login name.

Create SSH key pair to be used for authentication against the Ansible-managed VM defined by the `Vagranfile`.
```
ssh-keygen -t rsa -C "your-email@ddress"
```

## 2. Clone this repository
Clone this repository into your home directory:
```
cd 
git clone https://github.com/lungtendo/gdc-training
cd gdc-training/ansible
```

## 3. Assign a static IP address to the VM
Edit the `Vagrantfile` and replace the placeholder `CHANGE_ME` text with an IP addresses from a /24 CIDR alloted to you.

On line 16:

Change `node.vm.network "private_network", ip: "CHANGE_ME"`<br/>
to `node.vm.network "private_network", ip: "192.168.xy.114"`

## 4. User account for the VM
Edit the `add-user.yaml` file and replace `<USERNAME>` with your user name of choice. The placeholder test occurs in three places.

## 4. Provision the VMs

In the current directory (`~/gdc-training/ansib;e`), run
```
vagrant up
```
This will provision the VM which is based on a vanilla Ubuntu 18.04 cloud image. 

Run `vagrant status` to check the status of the newly provisioned VM.

If you face problem while provisioning the VM, you can delete it (`vagrant destroy`) and try to provision again (`vagrant up`).

## 5. Login to the new VM
Make sure you can access your newly provisioned VM:
```
ping -c 2 192.168.xy.114
```

If you can `ping` it, try to login:
```
ssh 192.168.xy.114
```
If you can login, your lab is ready.
 
## 6. Ansible smoke test
Define an Ansible inventory file:
```
echo 'server1 ansible_host=192.168.xy.144' > ~/hosts
```
 
See is Ansible can talk to your new VM:
```
ansible -i ~/hosts -m ping all
```
 
If this works, you are ready to continue with Ansible exercises.
 
To run an Ansible playbook:
```
ansible-playbook -i ~/hosts playbook.yaml
```
