# vagrant-kube

Deploy a Kubernetes cluster in Vagrant

```
git clone git@github.com:treytabner/vagrant-kube.git
vagrant up
```

After it's deployed, you can SSH in to the master with `vagrant ssh node1`.

```
[vagrant@node1 ~]$ kubectl get deploy,service,pods --all-namespaces -o wide
NAMESPACE     NAME                          DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
default       deploy/web-hostname           2         2         2            2           7m
kube-system   deploy/kube-discovery         1         1         1            1           8m
kube-system   deploy/kube-dns               1         1         1            1           8m
kube-system   deploy/kubernetes-dashboard   1         1         1            1           7m

NAMESPACE     NAME                       CLUSTER-IP       EXTERNAL-IP   PORT(S)         AGE       SELECTOR
default       svc/kubernetes             10.96.0.1        <none>        443/TCP         8m        <none>
default       svc/web-hostname           10.102.218.52    <nodes>       80:31464/TCP    7m        run=web-hostname
kube-system   svc/kube-dns               10.96.0.10       <none>        53/UDP,53/TCP   8m        name=kube-dns
kube-system   svc/kubernetes-dashboard   10.108.196.179   <nodes>       80:31404/TCP    7m        app=kubernetes-dashboard

NAMESPACE     NAME                                       READY     STATUS    RESTARTS   AGE       IP               NODE
default       po/web-hostname-2546452764-cq5sc           1/1       Running   0          7m        10.244.2.2       node3
default       po/web-hostname-2546452764-cqr0b           1/1       Running   0          4m        10.244.1.3       node2
kube-system   po/dummy-2088944543-35pdx                  1/1       Running   0          8m        192.168.77.197   node1
kube-system   po/etcd-node1                              1/1       Running   0          7m        192.168.77.197   node1
kube-system   po/kube-apiserver-node1                    1/1       Running   0          8m        192.168.77.197   node1
kube-system   po/kube-controller-manager-node1           1/1       Running   0          8m        192.168.77.197   node1
kube-system   po/kube-discovery-1769846148-wrqm8         1/1       Running   0          8m        192.168.77.197   node1
kube-system   po/kube-dns-2924299975-55g42               4/4       Running   0          8m        10.244.0.3       node1
kube-system   po/kube-flannel-ds-4zv0s                   2/2       Running   0          7m        192.168.77.197   node1
kube-system   po/kube-flannel-ds-d09b4                   2/2       Running   2          7m        192.168.77.23    node2
kube-system   po/kube-flannel-ds-grcsj                   2/2       Running   2          7m        192.168.77.93    node3
kube-system   po/kube-proxy-05nn0                        1/1       Running   0          7m        192.168.77.93    node3
kube-system   po/kube-proxy-r03n1                        1/1       Running   0          8m        192.168.77.197   node1
kube-system   po/kube-proxy-xdrzx                        1/1       Running   0          7m        192.168.77.23    node2
kube-system   po/kube-scheduler-node1                    1/1       Running   0          7m        192.168.77.197   node1
kube-system   po/kubernetes-dashboard-3203831700-kq2jg   1/1       Running   0          7m        10.244.0.2       node1
```
