# Acessing the Cluster Remotely

For now the the cluster can be accessed only from the Kubernetes control plane nodes.

To access the cluster from your local machine,
1. Copy the kube-config file from the control plane node to your local machine.
2. Copy the `kubectl` binary from control plane node to your local machine.

*Note: the local machine should be able to reach the cluster nodes for this to work*

## Copy kube-config to local machine
On local machine:
```
mkdir $HOME/.kube
scp controller-0:.kube/config $HOME/.kube/
```

## Copy `kubectl` binary to local machine
On the local machine:
```
scp controller-0:/usr/local/bin/kubectl .
sudo cp kubectl /usr/local/bin/
```

## Test
On the local machine:
```
kubectl get nodes
```

Next: [Smoke Test](09-smoke-test.md)
