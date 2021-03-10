# rke-deploy
rke 安裝 cluster

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
