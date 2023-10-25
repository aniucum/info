master
```
firewall-cmd --permanent --add-port=6443/tcp
firewall-cmd --permanent --add-port=2379-2380/tcp
firewall-cmd --permanent --add-port=10250/tcp
firewall-cmd --permanent --add-port=10251/tcp
firewall-cmd --permanent --add-port=10252/tcp
firewall-cmd --permanent --add-port=10255/tcp
firewall-cmd --permanent --add-port=8472/udp # flannel 
firewall-cmd --add-masquerade --permanent
```
worker
```
firewall-cmd --permanent --add-port=10250/tcp
firewall-cmd --permanent --add-port=10255/tcp
firewall-cmd --permanent --add-port=8472/udp # flannel 
firewall-cmd --permanent --add-port=30000-32767/tcp
firewall-cmd --add-masquerade --permanent
```
https://github.com/coreos/coreos-kubernetes/blob/master/Documentation/kubernetes-networking.md


### calico 
- https://stackoverflow.com/questions/67701010/kubernetes-cluster-with-firewall-enabled-on-centoscalico-not-working