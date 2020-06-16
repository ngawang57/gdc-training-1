# Ansible Lab

This directory contains two files of interest:
1. `Vagrantfile` - defines a VirtualBox VM to be used a an Ansible-managed host
2. `add-user.yaml` - Ansible playbook to provision a user account along with the VM


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
Clone this repository into your home directory on the lab server `172.31.33.124`:
```
cd 
git clone https://github.com/lungtendo/gdc-training
cd gdc-training/ansible
```
You should now be inside the `ansible` directory of the cloned git repository.

## 3. Assign a static IP address to the VM
Edit the `Vagrantfile` and replace the placeholder `CHANGE_ME` text with an IP addresses from a /24 CIDR alloted to you.

On line 16:

Change `node.vm.network "private_network", ip: "CHANGE_ME"`<br/>
to `node.vm.network "private_network", ip: "192.168.xy.114"`

## 4. User account for the VM
Edit the `add-user.yaml` file and replace occurances of placeholder text `<USERNAME>` with your user name.

## 4. Provision the VMs
In the current directory (`~/gdc-training/ansible`), run
```
vagrant up
```
This will provision the VM which is based on a vanilla Ubuntu 18.04 cloud image. 

Run `vagrant status` to check the status of the newly provisioned VM.

If you face problem while provisioning the VM, you can delete it (`vagrant destroy`) and try to provision again (`vagrant up`).

## 5. Access the new VM
Make sure you can reach your newly provisioned VM.
```
ping -c 2 192.168.xy.114
```

And make sure you can login without password:
```
ssh 192.168.xy.114
```
If you can login your lab is ready.
 
## 6. Ansible smoke test
Define an Ansible inventory file:
```
echo 'server1 ansible_host=192.168.xy.114' > ~/hosts
```
This creates `hosts` file at the root of your home directory with a sigle entry.
 
See if Ansible can talk to your new VM:
```
ansible -i ~/hosts -m ping all
```
 
To run an Ansible playbook:
```
ansible-playbook -i ~/hosts playbook.yaml
```
Of course, you need to define `playbook.yaml`.

## 7. Official Ansible documentation
1. [Getting started](https://docs.ansible.com/ansible/latest/user_guide/intro_getting_started.html)
2. [Full documentation](https://docs.ansible.com/ansible/latest/index.html)
3. [Modules index](https://docs.ansible.com/ansible/latest/modules/modules_by_category.html)
