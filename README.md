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

## reference
* https://github.com/rancher/rke/releases
* https://medium.com/@sarpkoksal/rke-kubernetes-installation-ha-or-noha-5f3b0e27b32f
