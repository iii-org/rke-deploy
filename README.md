# rke-deploy
rke 安裝 cluster

## ssh key for all node
```
#enter root user
sudo -i
cd .ssh/
ssh-keygen
ssh-copy-id localadmin@10.20.0.68
ssh-copy-id localadmin@10.20.0.73
ssh-copy-id localadmin@10.20.0.74
```

## Install kubectl 、 rke 、 nfs-common\
```sh
sudo snap install kubectl --classic  
sudo apt install nfs-common
wget https://github.com/rancher/rke/releases/download/v1.1.15/rke_linux-amd64
mv rke_linux-amd64 rke
chmod +x rke
rke --version
```

## Create HA and cluster config file
```
root@RKE2-68:~# ./rke config --name cluster.yml
[+] Cluster Level SSH Private Key Path [~/.ssh/id_rsa]:
[+] Number of Hosts [1]: 3
[+] SSH Address of host (1) [none]: 10.20.0.68
[+] SSH Port of host (1) [22]: 22
[+] SSH Private Key Path of host (10.20.0.68) [none]:
[-] You have entered empty SSH key path, trying fetch from SSH key parameter
[+] SSH Private Key of host (10.20.0.68) [none]:
[-] You have entered empty SSH key, defaulting to cluster level SSH key: ~/.ssh/                                                                                                                                                             id_rsa
[+] SSH User of host (10.20.0.68) [ubuntu]: localadmin
[+] Is host (10.20.0.68) a Control Plane host (y/n)? [y]: y
[+] Is host (10.20.0.68) a Worker host (y/n)? [n]: y
[+] Is host (10.20.0.68) an etcd host (y/n)? [n]: y
[+] Override Hostname of host (10.20.0.68) [none]: rke-68
[+] Internal IP of host (10.20.0.68) [none]: 10.20.0.68
[+] Docker socket path on host (10.20.0.68) [/var/run/docker.sock]:
[+] SSH Address of host (2) [none]: 10.20.0.73
[+] SSH Port of host (2) [22]: 22
[+] SSH Private Key Path of host (10.20.0.73) [none]:
[-] You have entered empty SSH key path, trying fetch from SSH key parameter
[+] SSH Private Key of host (10.20.0.73) [none]:
[-] You have entered empty SSH key, defaulting to cluster level SSH key: ~/.ssh/id_rsa
[+] SSH User of host (10.20.0.73) [ubuntu]: localadmin
[+] Is host (10.20.0.73) a Control Plane host (y/n)? [y]: y
[+] Is host (10.20.0.73) a Worker host (y/n)? [n]: y
[+] Is host (10.20.0.73) an etcd host (y/n)? [n]: y
[+] Override Hostname of host (10.20.0.73) [none]: rke-73
[+] Internal IP of host (10.20.0.73) [none]: 10.20.0.73
[+] Docker socket path on host (10.20.0.73) [/var/run/docker.sock]:
[+] SSH Address of host (3) [none]: 10.20.0.74
[+] SSH Port of host (3) [22]: 22
[+] SSH Private Key Path of host (10.20.0.74) [none]:
[-] You have entered empty SSH key path, trying fetch from SSH key parameter
[+] SSH Private Key of host (10.20.0.74) [none]:
[-] You have entered empty SSH key, defaulting to cluster level SSH key: ~/.ssh/id_rsa
[+] SSH User of host (10.20.0.74) [ubuntu]: localadmin
[+] Is host (10.20.0.74) a Control Plane host (y/n)? [y]: y
[+] Is host (10.20.0.74) a Worker host (y/n)? [n]: y
[+] Is host (10.20.0.74) an etcd host (y/n)? [n]: y
[+] Override Hostname of host (10.20.0.74) [none]: rke-74
[+] Internal IP of host (10.20.0.74) [none]: 10.20.0.74
[+] Docker socket path on host (10.20.0.74) [/var/run/docker.sock]:
[+] Network Plugin Type (flannel, calico, weave, canal) [canal]: calico
[+] Authentication Strategy [x509]:
[+] Authorization Mode (rbac, none) [rbac]: rbac
[+] Kubernetes Docker image [rancher/hyperkube:v1.18.16-rancher1]:
[+] Cluster domain [cluster.local]:
[+] Service Cluster IP Range [10.43.0.0/16]:
[+] Enable PodSecurityPolicy [n]:
[+] Cluster Network CIDR [10.42.0.0/16]:
[+] Cluster DNS Service IP [10.43.0.10]:
[+] Add addon manifest URLs or YAML files [no]:
```

## reference
* https://github.com/rancher/rke/releases
* https://medium.com/@sarpkoksal/rke-kubernetes-installation-ha-or-noha-5f3b0e27b32f
* https://rancher.com/docs/rke/latest/en/installation/
