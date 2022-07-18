# ncs-system-integrate

# Installation

## 1. ssh to kube-client node as root user.
```
root@k8s-master1:/# 
```

## 2. Setup ~/kube/.config
copy your kubeconfig from rancher.
```
root@k8s-master1:/# mkdir ~/.kube/
root@k8s-master1:/# vi ~/.kube/config
```

## 3. Installation


### download script
```
wget https://raw.githubusercontent.com/boombe40/ncs-system-integrate/main/install-ncp-system.sh -O install-ncp-system.sh

```

### input your credential and configure option.
```
root@k8s-master1:/# bash ./install-ncp-system.sh 
===== prepare virtualenv =====
kubectl command not found, then starting install kubectl first.
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 43.5M  100 43.5M    0     0  44.9M      0 --:--:-- --:--:-- --:--:-- 44.8M
helm command not found, then starting install helm3 first.
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 11156  100 11156    0     0   122k      0 --:--:-- --:--:-- --:--:--  122k
Downloading https://get.helm.sh/helm-v3.9.1-linux-amd64.tar.gz
Verifying checksum... Done.
Preparing to install helm into /usr/local/bin
helm installed into /usr/local/bin/helm
===== Gethering information =====
login space.nipa.cloud
Username: pratin@nipa.cloud
Password: ProjectID you install this cluster.
See your ProjectID from link: https://space.nipa.cloud/project
ProjectID: f0e09177b31a4f3e95a6af1bd9934aa4
Create new application credential name: kubernetes-f0e09177b31a4f3e95a6af1bd9934aa4-test-script-cluster
=== avialable Loadbalancer flavor ===
+--------------------------------------+--------------+
| id                                   | name         |
+--------------------------------------+--------------+
| 1b3c2cbc-4d26-4e7c-a63a-795b15c7e422 | lhd.large.v1 |
| 611c59d5-4202-4901-a030-3d56116037c0 | lhs.large.v1 |
| 71f09912-305c-4e10-8b4e-eda2e47794a0 | lss.large.v1 |
+--------------------------------------+--------------+
Select flavor you want to used.
loadbalancer id: 71f09912-305c-4e10-8b4e-eda2e47794a0
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /root/.kube/config
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /root/.kube/config
"cpo" has been added to your repositories
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /root/.kube/config
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /root/.kube/config
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "cpo" chart repository
Update Complete. ⎈Happy Helming!⎈
NAME: cinder-csi
LAST DEPLOYED: Mon Jul 18 10:09:20 2022
NAMESPACE: ncs-system
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
Use the following storageClass csi-cinder-sc-retain and csi-cinder-sc-delete only for RWO volumes.
secret/cloud-config created
serviceaccount/cloud-controller-manager created
daemonset.apps/openstack-cloud-controller-manager created
root@k8s-master1:/# 
```

## 4. Verifying the installation is successful.
```
kube get pod -n ncs-system
```