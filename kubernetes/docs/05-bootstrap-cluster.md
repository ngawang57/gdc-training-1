# Bootstrapping the Cluster

We will use `kubeadm` to bootstrap the cluster. We will not use Ansible here.

## First Control Plane Node
Login to one of the control plane nodes using SSH:
```
ssh controller-0
```
or use IP address instead.

### Host Name
Make sure the host name is set correctly:
```
hostname -f
```

If not, set the host name:
```
sudo hostnamectl set-hostname controller-0.local
```
Replace `local` with proper domain name for production set up.

### Initialize
```
sudo kubeadm init \
  --control-plane-endpoint=192.168.XY.30 \
  --apiserver-cert-extra-sans=lb.local \
  --apiserver-advertise-address=192.168.XY.10 \
  --pod-network-cidr=10.244.0.0/16 \
  --service-cidr=10.32.0.0/16 \
  --upload-certs | tee cluster_initialized.txt
```
Replace `XY` with proper values.

Once initialzed, follow the on-screen instructions to:
- create a kube config for accessing cluster
- install a Pod network

#### Kube config
In order to access the cluster as a regular user:
```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

#### Install a Pod network
CNI plugin for Pod network. As a regular user:
```
kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml
```

## Other Control Plane Nodes
While bootstrapping the first control plane node,
instructions for joining additional control plane and worker
nodes are provided. A copy of the instructions should be
available in `cluster_initialized.txt` file.

Join command for additional control plane node looks like:
```
sudo kubeadm join 192.168.XY.30:6443 \
  --token 9vr73a.a8uxyaju799qwdjv \
  --discovery-token-ca-cert-hash sha256:7c2e69131a36ae2a042a339b33381c6d0d43887e2de83720eff5359e26aec866 \
  --control-plane \
  --certificate-key f8902e114ef118304e561c3ecd4d0b543adc226b7a07f675f56564185ffe0c07 \
  --apiserver-advertise-address=192.168.XY.11
```
The `--apiserver-advertise-address` is required when you have multiple network interfaces on the node.

## Worker Nodes
Similarly, join the worker nodes using the provided command.
```
sudo kubeadm join 192.168.XY.30:6443 \
  --token 9vr73a.a8uxyaju799qwdjv \
  --discovery-token-ca-cert-hash sha256:7c2e69131a36ae2a042a339b33381c6d0d43887e2de83720eff5359e26aec866
```

## Check the Cluster
On one of the control plane nodes, run
```
kubectl get nodes
```

Next: [Ingress Controller and Load Balancer](07-ingress-lb.md)
