# vagrant-kube

Deploy a Kubernetes cluster in Vagrant

```
git clone git@github.com:treytabner/vagrant-kube.git
vagrant up
```

After it's deployed, you can SSH in to the master with `vagrant ssh node1`.

```
[vagrant@node1 ~]$ kubectl get all --all-namespaces
NAMESPACE     NAME                                       READY     STATUS    RESTARTS   AGE
kube-system   po/dummy-2088944543-n79pp                  1/1       Running   0          4m
kube-system   po/etcd-node1                              1/1       Running   0          3m
kube-system   po/kube-apiserver-node1                    1/1       Running   2          4m
kube-system   po/kube-controller-manager-node1           1/1       Running   0          4m
kube-system   po/kube-discovery-1769846148-6021z         1/1       Running   0          4m
kube-system   po/kube-dns-2924299975-nxgs7               4/4       Running   0          4m
kube-system   po/kube-flannel-ds-25xhx                   2/2       Running   1          4m
kube-system   po/kube-flannel-ds-9081v                   2/2       Running   0          4m
kube-system   po/kube-flannel-ds-pp616                   2/2       Running   0          4m
kube-system   po/kube-proxy-50k9z                        1/1       Running   0          4m
kube-system   po/kube-proxy-794vt                        1/1       Running   0          4m
kube-system   po/kube-proxy-vk1w5                        1/1       Running   0          4m
kube-system   po/kube-scheduler-node1                    1/1       Running   0          4m
kube-system   po/kubernetes-dashboard-3203831700-w8q8q   1/1       Running   0          4m

NAMESPACE     NAME                       CLUSTER-IP      EXTERNAL-IP   PORT(S)         AGE
default       svc/kubernetes             10.96.0.1       <none>        443/TCP         5m
kube-system   svc/kube-dns               10.96.0.10      <none>        53/UDP,53/TCP   4m
kube-system   svc/kubernetes-dashboard   10.111.154.97   <nodes>       80:32136/TCP    4m

NAMESPACE     NAME                          DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
kube-system   deploy/kube-discovery         1         1         1            1           4m
kube-system   deploy/kube-dns               1         1         1            1           4m
kube-system   deploy/kubernetes-dashboard   1         1         1            1           4m

NAMESPACE     NAME                                 DESIRED   CURRENT   READY     AGE
kube-system   rs/dummy-2088944543                  1         1         1         4m
kube-system   rs/kube-discovery-1769846148         1         1         1         4m
kube-system   rs/kube-dns-2924299975               1         1         1         4m
kube-system   rs/kubernetes-dashboard-3203831700   1         1         1         4m
```
