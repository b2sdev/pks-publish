
## Rancher로 클러스터 설정하기

### 멀티 노드를 가진 단일 클러스터

* Master node
```shell
# Master node
$ cd ~
$ sudo apt updated

$ curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC=" \
server --cluster-init \
--disable traefik \
--disable metricks-server \
--node-name master1 --docker" \
INSTALL_K3S_VERSION="v1.20.0-rc4+k3s1" sh -s -

# node-token과 IP 확인
$ sudo cat /var/lib/rancher/k3s/server/node-token
$ kubectl get node master1 -ojsonpath="{.status.addresses[0].address}"

# Worker node
NODE_TOKEN=... 
MASTER_IP=...

$ curl -sfL https://get.k3s.io | K3S_URL=https://$MASTER_IP:6443 \
K3S_TOKEN=$NODE_TOKEN \
INSTALL_K3S_EXEC="--node-name m1-worker1 --docker" \
INSTALL_K3S_VERSION="v1.20.0-rc4+k3s1" sh -s -
```

* kubectl 명령을 사용하기 위한 환경 설정
```shell
$ mkdir ~/.kube
$ sudo cp /etc/rancher/k3s/k3s.yaml ~/.kube/confifg
$ sudo chown -R $(id -u):$(id -g) ~/.kube
$ echo "export KUBECONFIG=~/.kube/config" >> ~/.bashrc
$ source ~/.bashrc
```

* 클러스터 확인
```shell
$ kubectl cluster-info
$ kubectl get node -o wide
```

* 클러스터 환경 삭제
```shell
# Master
$ /usr/local/bin/k3s-uninstall.sh

# Workers
$ /usr/local/bin/k3s-agent-uninstall.sh
```

### Another master node
```shell
# Master node의 token과 IP
$ NODE_TOKEN=... 
$ MASTER_IP=...

$ curl -sfL https://get.k3s.io | K3S_TOKEN=$NODE_TOKEN \
INSTALL_K3S_EXEC=" \
server --server https://$MASTER_IP:6443 \
--disable traefik \
--disable metrics-server \
--node-name master2 --docker" \
INSTALL_K3S_VERSION="v1.20.0-rc4+k4s1" sh -s -
```