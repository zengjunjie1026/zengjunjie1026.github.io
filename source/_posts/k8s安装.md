---
title: k8s安装
date: 2021-08-16 18:01:24
tags:
---

k8s-安装
Kubernetes是什么？
Kubernetes是容器集群管理系统，是一个开源的平台，可以实现容器集群的自动化部署、自动扩缩容、维护等功能。 通过Kubernetes你可以：

快速部署应用
快速扩展应用
无缝对接新的应用功能
节省资源，优化硬件资源的使用
Kubernetes 特点
可移植: 支持公有云，私有云，混合云，多重云（multi-cloud）
可扩展: 模块化, 插件化, 可挂载, 可组合
自动化: 自动部署，自动重启，自动复制，自动伸缩/扩展
使用Kubernetes能做什么？
多个进程（作为容器运行）协同工作。（Pod）
存储系统挂载
Distributing secrets
应用健康检测
应用实例的复制
Pod自动伸缩/扩展
Naming and discovering
负载均衡
滚动更新
资源监控
日志访问
调试应用程序
提供认证和授权
Kubernetes 组件
K8s是由许多个的组件组成的 分为Master组件和节点（Node）组件

Master组件
Master组件提供集群的管理控制中心。 Master组件可以在集群中任何节点上运行。但是为了简单起见，通常在一台VM/机器上启动所有Master组件，并且不会在此VM/机器上运行用户容器。

kube-apiserver
kube-apiserver用于暴露Kubernetes API。任何的资源请求/调用操作都是通过kube-apiserver提供的接口进行。请参阅构建高可用群集。

ETCD
etcd是Kubernetes提供默认的存储系统，保存所有集群数据，使用时需要为etcd数据提供备份计划。

kube-controller-manager
kube-controller-manager运行管理控制器，它们是集群中处理常规任务的后台线程。逻辑上，每个控制器是一个单独的进程，但为了降低复杂性，它们都被编译成单个二进制文件，并在单个进程中运行。

kube-scheduler
kube-scheduler 监视新创建没有分配到Node的Pod，为Pod选择一个Node。

节点（Node）组件
节点组件运行在Node，提供Kubernetes运行时环境，以及维护Pod。

kubelet
kubelet是主要的节点代理，它会监视已分配给节点的pod，具体功能：

安装Pod所需的volume。
下载Pod的Secrets。
Pod中运行的 docker（或experimentally，rkt）容器。
定期执行容器健康检查。
Reports the status of the pod back to the rest of the system, by creating a mirror pod if necessary.
Reports the status of the node back to the rest of the system.
kube-proxy
kube-proxy通过在主机上维护网络规则并执行连接转发来实现Kubernetes服务抽象。

Kubernetes 安装前的准备
概述
本次安装采用 Ubuntu Server X64 16.04 LTS 版本安装 kubernetes 集群环境，集群节点为 1 主 2 从模式，此次对虚拟机会有些基本要求，如下：

OS：Ubuntu Server X64 18.04 LTS（16.04 版本步骤相同，再之前则不同）
CPU：最低要求，1 CPU 2 核
内存：最低要求，2GB
磁盘：最低要求，20GB
创建三台虚拟机，分别命名如下：
```bash
Ubuntu Server 18.04 X64 Kubernetes Master
Ubuntu Server 18.04 X64 Kubernetes Slave1
Ubuntu Server 18.04 X64 Kubernetes Slave2
```
对虚拟机系统的配置：
```bash
关闭交换空间：sudo swapoff -a
避免开机启动交换空间：注释 /etc/fstab 中的 swap
关闭防火墙：ufw disable
使用 APT 安装 Docker
安装
```
```bash
# 更新软件源  
sudo apt-get update  
# 安装所需依赖
sudo apt-get -y install apt-transport-https ca-certificates curl software-properties-common
# 安装 GPG 证书
curl -fsSL http://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
# 新增软件源信息
sudo add-apt-repository "deb [arch=amd64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
# 再次更新软件源
sudo apt-get -y update
# 安装 Docker CE 版
sudo apt-get -y install docker-ce  
```
验证
```bash
docker version
Client:
 Version:           18.09.6
 API version:       1.39
 Go version:        go1.10.8
 Git commit:        481bc77
 Built:             Sat May  4 02:35:57 2019
 OS/Arch:           linux/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          18.09.6
  API version:      1.39 (minimum version 1.12)
  Go version:       go1.10.8
  Git commit:       481bc77
  Built:            Sat May  4 01:59:36 2019
  OS/Arch:          linux/amd64
  Experimental:     false

```
配置加速器
对于使用 systemd 的系统，请在 /etc/docker/daemon.json 中写入如下内容（如果文件不存在请新建该文件）
```json
{
  "registry-mirrors": [
    "https://registry.docker-cn.com"
  ]
}
```
验证加速器是否配置成功：

```bash
sudo systemctl restart docker
docker info
```
# 出现如下语句即表示配置成功
```bash
Registry Mirrors:
 https://registry.docker-cn.com/
```
修改主机名

在同一局域网中主机名不应该相同，所以我们需要做修改，直接修改 /etc/hostname 里的名称即可

```bash
vim  /etc/hostname  
#kubernetes-master
```
安装 kubeadm
kubeadm 是 kubernetes 的集群安装工具，能够快速安装 kubernetes 集群。

配置软件源

安装系统工具
```bash
apt-get update && apt-get install -y apt-transport-https
# 安装 GPG 证书
curl https://mirrors.aliyun.com/kubernetes/apt/doc/apt-key.gpg | apt-key add -
# 写入软件源；注意：我们用系统代号为 bionic，但目前阿里云不支持，所以沿用 16.04 的 xenial
cat << EOF >/etc/apt/sources.list.d/kubernetes.list
> deb https://mirrors.aliyun.com/kubernetes/apt/ kubernetes-xenial main
> EOF
```
安装 kubeadm，kubelet，kubectl
安装
```bash
apt-get update  
apt-get install -y kubelet kubeadm kubectl
```
安装过程如下，注意 kubeadm 的版本号
```bash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  conntrack cri-tools kubernetes-cni socat
The following NEW packages will be installed:
  conntrack cri-tools kubeadm kubectl kubelet kubernetes-cni socat
0 upgraded, 7 newly installed, 0 to remove and 96 not upgraded.
Need to get 50.6 MB of archives.
After this operation, 290 MB of additional disk space will be used.
Get:1 http://mirrors.aliyun.com/ubuntu bionic/main amd64 conntrack amd64 1:1.4.4+snapshot20161117-6ubuntu2 [30.6 kB]
Get:2 http://mirrors.aliyun.com/ubuntu bionic/main amd64 socat amd64 1.7.3.2-2ubuntu2 [342 kB]
Get:3 https://mirrors.aliyun.com/kubernetes/apt kubernetes-xenial/main amd64 cri-tools amd64 1.12.0-00 [5,343 kB]
Get:4 https://mirrors.aliyun.com/kubernetes/apt kubernetes-xenial/main amd64 kubernetes-cni amd64 0.7.5-00 [6,473 kB]
Get:5 https://mirrors.aliyun.com/kubernetes/apt kubernetes-xenial/main amd64 kubelet amd64 1.14.1-00 [21.5 MB]
Get:6 https://mirrors.aliyun.com/kubernetes/apt kubernetes-xenial/main amd64 kubectl amd64 1.14.1-00 [8,806 kB]
Get:7 https://mirrors.aliyun.com/kubernetes/apt kubernetes-xenial/main amd64 kubeadm amd64 1.14.1-00 [8,150 kB]
Fetched 50.6 MB in 5s (9,912 kB/s) 
Selecting previously unselected package conntrack.
(Reading database ... 67205 files and directories currently installed.)
Preparing to unpack .../0-conntrack_1%3a1.4.4+snapshot20161117-6ubuntu2_amd64.deb ...
Unpacking conntrack (1:1.4.4+snapshot20161117-6ubuntu2) ...
Selecting previously unselected package cri-tools.
Preparing to unpack .../1-cri-tools_1.12.0-00_amd64.deb ...
Unpacking cri-tools (1.12.0-00) ...
Selecting previously unselected package kubernetes-cni.
Preparing to unpack .../2-kubernetes-cni_0.7.5-00_amd64.deb ...
Unpacking kubernetes-cni (0.7.5-00) ...
Selecting previously unselected package socat.
Preparing to unpack .../3-socat_1.7.3.2-2ubuntu2_amd64.deb ...
Unpacking socat (1.7.3.2-2ubuntu2) ...
Selecting previously unselected package kubelet.
Preparing to unpack .../4-kubelet_1.14.1-00_amd64.deb ...
Unpacking kubelet (1.14.1-00) ...
Selecting previously unselected package kubectl.
Preparing to unpack .../5-kubectl_1.14.1-00_amd64.deb ...
Unpacking kubectl (1.14.1-00) ...
Selecting previously unselected package kubeadm.
Preparing to unpack .../6-kubeadm_1.14.1-00_amd64.deb ...
Unpacking kubeadm (1.14.1-00) ...
Setting up conntrack (1:1.4.4+snapshot20161117-6ubuntu2) ...
Setting up kubernetes-cni (0.7.5-00) ...
Setting up cri-tools (1.12.0-00) ...
Setting up socat (1.7.3.2-2ubuntu2) ...
Setting up kubelet (1.14.1-00) ...
Created symlink /etc/systemd/system/multi-user.target.wants/kubelet.service → /lib/systemd/system/kubelet.service.
Setting up kubectl (1.14.1-00) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
# 注意这里的版本号，我们使用的是 kubernetes v1.14.1
Setting up kubeadm (1.14.1-00) ...
```
```bash
# 设置 kubelet 自启动，并启动 kubelet
systemctl enable kubelet && systemctl start kubelet
kubeadm：用于初始化 Kubernetes 集群
kubectl：Kubernetes 的命令行工具，主要作用是部署和管理应用，查看各种资源，创建，删除和更新组件
kubelet：主要负责启动 Pod 和容器
配置 kubeadm
安装 kubernetes 主要是安装它的各个镜像，而 kubeadm 已经为我们集成好了运行 kubernetes 所需的基本镜像。但由于国内的网络原因，在搭建环境时，无法拉取到这些镜像。此时我们只需要修改为阿里云提供的镜像服务即可解决该问题
```
创建并修改配置

```bash
kubeadm config print init-defaults --kubeconfig ClusterConfiguration > kubeadm.yml
```
修改配置内容# 修改配置为如下内容
```bash
apiVersion: kubeadm.k8s.io/v1beta1
bootstrapTokens:
- groups:
  - system:bootstrappers:kubeadm:default-node-token
  token: abcdef.0123456789abcdef
  ttl: 24h0m0s
  usages:
  - signing
  - authentication
kind: InitConfiguration
localAPIEndpoint:
  # 修改为主节点 IP
  advertiseAddress: 192.168.141.130
  bindPort: 6443
nodeRegistration:
  criSocket: /var/run/dockershim.sock
  name: kubernetes-master
  taints:
  - effect: NoSchedule
    key: node-role.kubernetes.io/master
---
apiServer:
  timeoutForControlPlane: 4m0s
apiVersion: kubeadm.k8s.io/v1beta1
certificatesDir: /etc/kubernetes/pki
clusterName: kubernetes
controlPlaneEndpoint: ""
controllerManager: {}
dns:
  type: CoreDNS
etcd:
  local:
    dataDir: /var/lib/etcd
# 国内不能访问 Google，修改为阿里云
imageRepository: registry.aliyuncs.com/google_containers
kind: ClusterConfiguration
# 修改版本号
kubernetesVersion: v1.17.0
networking:
  dnsDomain: cluster.local
  # 配置成 Calico 的默认网段
  podSubnet: "192.168.0.0/16"
  serviceSubnet: 10.96.0.0/12
scheduler: {}
---
# 开启 IPVS 模式
apiVersion: kubeproxy.config.k8s.io/v1alpha1
kind: KubeProxyConfiguration
featureGates:
  SupportIPVSProxyMode: true
mode: ipvs
```
查看和拉取镜像
# 查看所需镜像列表
```bash
kubeadm config images list --config kubeadm.yml
# 拉取镜像
kubeadm config images pull --config kubeadm.yml
```
安装 kubernetes 主节点
执行以下命令初始化主节点，该命令指定了初始化时需要使用的配置文件，其中添加 --upload-certs 参数可以在后续执行加入节点时自动分发证书文件。追加的 tee kubeadm-init.log 用以输出日志。
```bash
kubeadm init --config=kubeadm.yml --experimental-upload-certs | tee kubeadm-init.log
```

```bash
#your configuration file uses a deprecated API spec: "kubeadm.k8s.io/v1beta1". Please use 'kubeadm config migrate --old-config old.yaml --new-config new.yaml', which will write the new, similar spec using a newer API version.
W0106 17:26:39.941946   25748 common.go:77] your configuration file uses a deprecated API spec: "kubeadm.k8s.io/v1beta1". Please use 'kubeadm config migrate --old-config old.yaml --new-config new.yaml', which will write the new, similar spec using a newer API version.
W0106 17:26:39.944487   25748 validation.go:28] Cannot validate kube-proxy config - no validator is available
W0106 17:26:39.944533   25748 validation.go:28] Cannot validate kubelet config - no validator is available
[init] Using Kubernetes version: v1.17.0
[preflight] Running pre-flight checks
	[WARNING IsDockerSystemdCheck]: detected "cgroupfs" as the Docker cgroup driver. The recommended driver is "systemd". Please follow the guide at https://kubernetes.io/docs/setup/cri/
[preflight] Pulling images required for setting up a Kubernetes cluster
[preflight] This might take a minute or two, depending on the speed of your internet connection
[preflight] You can also perform this action in beforehand using 'kubeadm config images pull'
[kubelet-start] Writing kubelet environment file with flags to file "/var/lib/kubelet/kubeadm-flags.env"
[kubelet-start] Writing kubelet configuration to file "/var/lib/kubelet/config.yaml"
[kubelet-start] Starting the kubelet
[certs] Using certificateDir folder "/etc/kubernetes/pki"
[certs] Generating "ca" certificate and key
[certs] Generating "apiserver" certificate and key
[certs] apiserver serving cert is signed for DNS names [kubernetes-master kubernetes kubernetes.default kubernetes.default.svc kubernetes.default.svc.cluster.local] and IPs [10.96.0.1 192.168.62.159]
[certs] Generating "apiserver-kubelet-client" certificate and key
[certs] Generating "front-proxy-ca" certificate and key
[certs] Generating "front-proxy-client" certificate and key
[certs] Generating "etcd/ca" certificate and key
[certs] Generating "etcd/server" certificate and key
[certs] etcd/server serving cert is signed for DNS names [kubernetes-master localhost] and IPs [192.168.62.159 127.0.0.1 ::1]
[certs] Generating "etcd/peer" certificate and key
[certs] etcd/peer serving cert is signed for DNS names [kubernetes-master localhost] and IPs [192.168.62.159 127.0.0.1 ::1]
[certs] Generating "etcd/healthcheck-client" certificate and key
[certs] Generating "apiserver-etcd-client" certificate and key
[certs] Generating "sa" key and public key
[kubeconfig] Using kubeconfig folder "/etc/kubernetes"
[kubeconfig] Writing "admin.conf" kubeconfig file
[kubeconfig] Writing "kubelet.conf" kubeconfig file
[kubeconfig] Writing "controller-manager.conf" kubeconfig file
[kubeconfig] Writing "scheduler.conf" kubeconfig file
[control-plane] Using manifest folder "/etc/kubernetes/manifests"
[control-plane] Creating static Pod manifest for "kube-apiserver"
W0106 17:26:44.531537   25748 manifests.go:214] the default kube-apiserver authorization-mode is "Node,RBAC"; using "Node,RBAC"
[control-plane] Creating static Pod manifest for "kube-controller-manager"
W0106 17:26:44.532749   25748 manifests.go:214] the default kube-apiserver authorization-mode is "Node,RBAC"; using "Node,RBAC"
[control-plane] Creating static Pod manifest for "kube-scheduler"
[etcd] Creating static Pod manifest for local etcd in "/etc/kubernetes/manifests"
[wait-control-plane] Waiting for the kubelet to boot up the control plane as static Pods from directory "/etc/kubernetes/manifests". This can take up to 4m0s
[apiclient] All control plane components are healthy after 24.504808 seconds
[upload-config] Storing the configuration used in ConfigMap "kubeadm-config" in the "kube-system" Namespace
[kubelet] Creating a ConfigMap "kubelet-config-1.17" in namespace kube-system with the configuration for the kubelets in the cluster
[upload-certs] Storing the certificates in Secret "kubeadm-certs" in the "kube-system" Namespace
[upload-certs] Using certificate key:
781e69718ac47389e4e65f025cb9cb842ae621f495323b08f8c3cc5fe69c5a82
[mark-control-plane] Marking the node kubernetes-master as control-plane by adding the label "node-role.kubernetes.io/master=''"
[mark-control-plane] Marking the node kubernetes-master as control-plane by adding the taints [node-role.kubernetes.io/master:NoSchedule]
[bootstrap-token] Using token: abcdef.0123456789abcdef
[bootstrap-token] Configuring bootstrap tokens, cluster-info ConfigMap, RBAC Roles
[bootstrap-token] configured RBAC rules to allow Node Bootstrap tokens to post CSRs in order for nodes to get long term certificate credentials
[bootstrap-token] configured RBAC rules to allow the csrapprover controller automatically approve CSRs from a Node Bootstrap Token
[bootstrap-token] configured RBAC rules to allow certificate rotation for all node client certificates in the cluster
[bootstrap-token] Creating the "cluster-info" ConfigMap in the "kube-public" namespace
[kubelet-finalize] Updating "/etc/kubernetes/kubelet.conf" to point to a rotatable kubelet client certificate and key
[addons] Applied essential addon: CoreDNS
[addons] Applied essential addon: kube-proxy

Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/
```
Then you can join any number of worker nodes by running the following on each as root:
```bash
kubeadm join 192.168.62.159:6443 --token abcdef.0123456789abcdef \
    --discovery-token-ca-cert-hash sha256:7237dd082021214d77c1d99f0cdc2a1a110c33ba94c5e2df699ea3cebbab1ea4 
```
注意：如果安装 kubernetes 版本和下载的镜像版本不统一则会出现 timed out waiting for the condition 错误。中途失败或是想修改配置可以使用 kubeadm reset 命令重置配置，再做初始化操作即可。

配置 kubectl
```bash
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config(非root才做)
```

```bash
kubectl get node
```
至此主节点配置完成
```bash
kubeadm init 的执行过程
init：指定版本进行初始化操作
preflight：初始化前的检查和下载所需要的 Docker 镜像文件
kubelet-start：生成 kubelet 的配置文件 var/lib/kubelet/config.yaml，没有这个文件 kubelet 无法启动，所以初始化之前的 - kubelet 实际上启动不会成功
certificates：生成 Kubernetes 使用的证书，存放在 /etc/kubernetes/pki 目录中
kubeconfig：生成 KubeConfig 文件，存放在 /etc/kubernetes 目录中，组件之间通信需要使用对应文件
control-plane：使用 /etc/kubernetes/manifest 目录下的 YAML 文件，安装 Master 组件
etcd：使用 /etc/kubernetes/manifest/etcd.yaml 安装 Etcd 服务
wait-control-plane：等待 control-plan 部署的 Master 组件启动
apiclient：检查 Master 组件服务状态。
uploadconfig：更新配置
kubelet：使用 configMap 配置 kubelet
patchnode：更新 CNI 信息到 Node 上，通过注释的方式记录
mark-control-plane：为当前节点打标签，打了角色 Master，和不可调度标签，这样默认就不会使用 Master 节点来运行 Pod
bootstrap-token：生成 token 记录下来，后边使用 kubeadm join 往集群中添加节点时会用到
addons：安装附加组件 CoreDNS 和 kube-proxy
```
使用 kubeadm 配置 slave 节点
将 slave 节点加入到集群中很简单，只需要在 slave 服务器上安装 kubeadm，kubectl，kubelet 三个工具，然后使用 kubeadm join 命令加入即可。准备工作如下：

修改主机名
配置软件源
安装三个工具

```bash
kubeadm join 192.168.62.159:6443 --token abcdef.0123456789abcdef   --discovery-token-ca-cert-hash sha256:7237dd082021214d77c1d99f0cdc2a1a110c33ba94c5e2df699ea3cebbab1ea4 
```
说明：

token
可以通过安装 master 时的日志查看 token 信息
可以通过 kubeadm token list 命令打印出 token 信息
如果 token 过期，可以使用 kubeadm token create 命令创建新的 token
discovery-token-ca-cert-hash
可以通过安装 master 时的日志查看 sha256 信息
可以通过

```bash
openssl x509 -pubkey -in /etc/kubernetes/pki/ca.crt | openssl rsa -pubin -outform der 2>/dev/null | openssl dgst -sha256 -hex | sed 's/^.* //' 
```
命令查看 sha256 信息

```bash
kubectl get nodes
kubectl get pod -n kube-system -o wide
```
配置网络
容器网络是容器选择连接到其他容器、主机和外部网络的机制。容器的 runtime 提供了各种网络模式，每种模式都会产生不同的体验。例如，Docker 默认情况下可以为容器配置以下网络：

none： 将容器添加到一个容器专门的网络堆栈中，没有对外连接。
host： 将容器添加到主机的网络堆栈中，没有隔离。
default bridge： 默认网络模式。每个容器可以通过 IP 地址相互连接。
自定义网桥： 用户定义的网桥，具有更多的灵活性、隔离性和其他便利功能。

什么是 CNI
CNI(Container Network Interface) 是一个标准的，通用的接口。在容器平台，Docker，Kubernetes，Mesos 容器网络解决方案 flannel，calico，weave。只要提供一个标准的接口，就能为同样满足该协议的所有容器平台提供网络功能，而 CNI 正是这样的一个标准接口协议。

Kubernetes 中的 CNI 插件
CNI 的初衷是创建一个框架，用于在配置或销毁容器时动态配置适当的网络配置和资源。插件负责为接口配置和管理 IP 地址，并且通常提供与 IP 管理、每个容器的 IP 分配、以及多主机连接相关的功能。容器运行时会调用网络插件，从而在容器启动时分配 IP 地址并配置网络，并在删除容器时再次调用它以清理这些资源。

运行时或协调器决定了容器应该加入哪个网络以及它需要调用哪个插件。然后，插件会将接口添加到容器网络命名空间中，作为一个 veth 对的一侧。接着，它会在主机上进行更改，包括将 veth 的其他部分连接到网桥。再之后，它会通过调用单独的 IPAM（IP地址管理）插件来分配 IP 地址并设置路由。

在 Kubernetes 中，kubelet 可以在适当的时间调用它找到的插件，为通过 kubelet 启动的 pod进行自动的网络配置。

Kubernetes 中可选的 CNI 插件如下：
```bash
Flannel
Calico
Canal
Weave-
```
什么是 Calico
Calico 为容器和虚拟机提供了安全的网络连接解决方案，并经过了大规模生产验证（在公有云和跨数千个集群节点中），可与 Kubernetes，OpenShift，Docker，Mesos，DC / OS 和 OpenStack 集成。

Calico 还提供网络安全规则的动态实施。使用 Calico 的简单策略语言，您可以实现对容器，虚拟机工作负载和裸机主机端点之间通信的细粒度控制。

安装网络插件 Calico
参考官方文档安装：https://docs.projectcalico.org/v3.7/getting-started/kubernetes/

在 Master 节点操作即可
```bash
kubectl apply -f https://docs.projectcalico.org/v3.11/manifests/calico.yaml
```
安装时显示如下输出
```bash
configmap/calico-config created
customresourcedefinition.apiextensions.k8s.io/felixconfigurations.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/ipamblocks.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/blockaffinities.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/ipamhandles.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/ipamconfigs.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/bgppeers.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/bgpconfigurations.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/ippools.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/hostendpoints.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/clusterinformations.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/globalnetworkpolicies.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/globalnetworksets.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/networkpolicies.crd.projectcalico.org created
customresourcedefinition.apiextensions.k8s.io/networksets.crd.projectcalico.org created
clusterrole.rbac.authorization.k8s.io/calico-kube-controllers created
clusterrolebinding.rbac.authorization.k8s.io/calico-kube-controllers created
clusterrole.rbac.authorization.k8s.io/calico-node created
clusterrolebinding.rbac.authorization.k8s.io/calico-node created
daemonset.extensions/calico-node created
serviceaccount/calico-node created
deployment.extensions/calico-kube-controllers created
```serviceaccount/calico-kube-controllers created
```
### 确认安装是否成功

```bash
watch kubectl get pods --all-namespaces
```
需要等待所有状态为 Running，注意时间可能较久，3 - 5 分钟的样子
```bash
2.0s: kubectl get pods –all-namespaces kubernetes-master: Fri May 10 18:16:51 2019
NAMESPACE NAME READY STATUS RESTARTS AGE
kube-system calico-kube-controllers-8646dd497f-g2lln 1/1 Running 0 50m
kube-system calico-node-8jrtp 1/1 Running 0 50m
kube-system coredns-8686dcc4fd-mhwfn 1/1 Running 0 51m
kube-system coredns-8686dcc4fd-xsxwk 1/1 Running 0 51m
kube-system etcd-kubernetes-master 1/1 Running 0 50m
kube-system kube-apiserver-kubernetes-master 1/1 Running 0 51m
kube-system kube-controller-manager-kubernetes-master 1/1 Running 0 51m
kube-system kube-proxy-p8mdw 1/1 Running 0 51m
kube-system kube-scheduler-kubernetes-master
```

解决 ImagePullBackOff
在使用 watch kubectl get pods –all-namespaces 命令观察 Pods 状态时如果出现 ImagePullBackOff 无法 Running 的情况，请尝试使用如下步骤处理：

Master 中删除 Nodes：kubectl delete nodes
Slave 中重置配置：kubeadm reset
Slave 重启计算机：reboot
Slave 重新加入集群：kubeadm join
完成搭建

检查组件

```bash
kubectl get cs
输出如下
NAME STATUS MESSAGE ERROR


调度服务，主要作用是将 POD 调度到 Node
scheduler Healthy ok

自动化修复服务，主要作用是 Node 宕机后自动修复 Node 回到正常的工作状态
controller-manager Healthy ok

服务注册与发现
etcd-0 Healthy {“health”:”true”}
检查 Master 状态
```
```bash
kubectl cluster-info
#输出如下
Kubernetes master is running at https://192.168.62.159:6443
KubeDNS is running at https://192.168.62.159:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
To further debug and diagnose cluster problems, use ‘kubectl cluster-info dump’.
```
运行第一个容器实例

使用 kubectl 命令创建两个监听 80 端口的 Nginx Pod（Kubernetes 运行容器的最小单元）
```bash
kubectl run nginx --image=nginx --replicas=2 --port=80
```

```bash
kubectl run --generator=deployment/apps.v1 is DEPRECATED and will be removed in a future version. Use kubectl run --generator=run-pod/v1 or kubectl create instead.
deployment.apps/nginx created
```
查看全部 Pods 的状态

```bash
kubectl get pods
```

```bash
nginx-5578584966-f7vl5   0/1     ContainerCreating   0          55s
nginx-5578584966-p9s24   0/1     ContainerCreating   0          55s
nginx-5578584966-f7vl5   1/1     Running   0          18m
nginx-5578584966-p9s24   1/1     Running   0          18m
查看已部署的服务

```bash
kubectl get deployment
输出如下
NAME READY UP-TO-DATE AVAILABLE AGE
nginx 2/2 2 2 91m
```
映射服务，让用户可以访问
```bash
kubectl expose deployment nginx –port=80 –type=LoadBalancer
```
输出如下
```bash
service/nginx exposed
```
查看已发布的服务
```bash
kubectl get services
NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
kubernetes ClusterIP 10.96.0.1 443/TCP 21h
nginx LoadBalancer 10.96.133.79 80:31091/TCP 13m
```
查看服务详情
```bash
kubectl describe service nginx

Name: nginx
Namespace: default
Labels: run=nginx
Annotations:
Selector: run=nginx
Type: LoadBalancer
IP: 10.96.133.79
Port: 80/TCP
TargetPort: 80/TCP
NodePort: 31091/TCP
Endpoints: 192.168.17.1:80,192.168.8.130:80
Session Affinity: None
External Traffic Policy: Cluster
Events:
```
验证是否成功 通过浏览器访问 Master 服务器
```bash
http://192.168.62.159:30830/
```
停止服务
```bash
kubectl delete deployment nginx
```
输出如下
```bash
deployment.extensions “nginx” deleted
kubectl delete service nginx
```
输出如下
```bash
service “nginx” deleted
```
结尾
目前是已经把K8s集群搭建完成了 并且我们用它部署了nginx,先到这里把


节点： Kubernetes 集群中的服务器
集群： Kubernetes 管理的一组服务器集合
边界路由器： 为局域网和 Internet 路由数据包的路由器，执行防火墙保护局域网络
集群网络： 遵循 Kubernetes 网络模型实现集群内的通信的具体实现，比如 Flannel 和 Calico
服务： Kubernetes 的服务 (Service) 是使用标签选择器标识的一组 Pod Service (Deployment)。
除非另有说明，否则服务的虚拟 IP 仅可在集群内部访问
内部访问方式 ClusterIP
ClusterIP 服务是 Kubernetes 的默认服务。它给你一个集群内的服务，集群内的其它应用都可以访问该服务。集群外部无法访问它。在某些场景下我们可以使用 Kubernetes 的 Proxy 模式来访问服务，比如调试服务时


这种访问方式，只能是在Service的内部访问。

三种外部访问方式
NodePort
NodePort 服务是引导外部流量到你的服务的最原始方式。NodePort，正如这个名字所示，在所有节点（虚拟机）上开放一个特定端口，任何发送到该端口的流量都被转发到对应服务。

NodePort 服务特征如下：

每个端口只能是一种服务 
端口范围只能是 30000-32767（可调）  
不在 YAML 配置文件中指定则会分配一个默认端口 

建议： 不要在生产环境中使用这种方式暴露服务，大多数时候我们应该让 Kubernetes 来选择端口
它这种模式就是我们第一次部署的那种模式，每个Node节点都可以通过这个ip+端口来访问这个服务

### LoadBalancer
LoadBalancer 服务是暴露服务到 Internet 的标准方式。所有通往你指定的端口的流量都会被转发到对应的服务。它没有过滤条件，没有路由等。这意味着你几乎可以发送任何种类的流量到该服务，像 HTTP，TCP，UDP，WebSocket，gRPC 或其它任意种类。



Ingress
Ingress 事实上不是一种服务类型。相反，它处于多个服务的前端，扮演着 “智能路由” 或者集群入口的角色。你可以用 Ingress 来做许多不同的事情，各种不同类型的 Ingress 控制器也有不同的能力。它允许你基于路径或者子域名来路由流量到后端服务。

Ingress 可能是暴露服务的最强大方式，但同时也是最复杂的。Ingress 控制器有各种类型，包括 Google Cloud Load Balancer， Nginx，Contour，Istio，等等。它还有各种插件，比如 cert-manager (它可以为你的服务自动提供 SSL 证书)/

如果你想要使用同一个 IP 暴露多个服务，这些服务都是使用相同的七层协议（典型如 HTTP），你还可以获取各种开箱即用的特性（比如 SSL、认证、路由等等）



### 什么是 Ingress
通常情况下，Service 和 Pod 的 IP 仅可在集群内部访问。集群外部的请求需要通过负载均衡转发到 Service 在 Node 上暴露的 NodePort 上，然后再由 kube-proxy 通过边缘路由器 (edge router) 将其转发给相关的 Pod 或者丢弃。而 Ingress 就是为进入集群的请求提供路由规则的集合

Ingress 可以给 Service 提供集群外部访问的 URL、负载均衡、SSL 终止、HTTP 路由等。为了配置这些 Ingress 规则，集群管理员需要部署一个 Ingress Controller，它监听 Ingress 和 Service 的变化，并根据规则配置负载均衡并提供访问入口

使用 Nginx Ingress Controller
本次实践的主要目的就是将入口统一，不再通过 LoadBalancer 等方式将端口暴露出来，而是使用 Ingress 提供的反向代理负载均衡功能作为我们的唯一入口。通过以下步骤操作仔细体会。

### 部署 Tomcat
部署 Tomcat 但仅允许在内网访问，我们要通过 Ingress 提供的反向代理功能路由到 Tomcat 之上
```bash
apiVersion:  apps/v1
kind: Deployment
metadata:
  name: tomcat-app
spec:
  selector:
    matchLabels:
      app: tomcat
  replicas: 2
  template:
    metadata:
      labels:
        app: tomcat
    spec:
      containers:
      - name: tomcat
        image: tomcat
        ports:
        - containerPort: 8080
---
apiVersion: v1
kind: Service
metadata:
  name: tomcat-http
spec:
  ports:
    - port: 8080
      targetPort: 8080
  # ClusterIP, NodePort, LoadBalancer
  type: ClusterIP
  selector:
    app: tomcat
```
安装 Nginx Ingress Controller
Ingress Controller 有许多种，我们选择最熟悉的 Nginx 来处理请求，其它可以参考官方文档

下载 Nginx Ingress Controller 配置文件
```bash
wget https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/mandatory.yaml
```
修改配置文件，找到配置如下位置 (搜索 serviceAccountName) 在下面增加一句 hostNetwork: true
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-ingress-controller
  namespace: ingress-nginx
  labels:
    app.kubernetes.io/name: ingress-nginx
    app.kubernetes.io/part-of: ingress-nginx
spec:
  # 可以部署多个实例
  replicas: 1
  selector:
    matchLabels:
      app.kubernetes.io/name: ingress-nginx
      app.kubernetes.io/part-of: ingress-nginx
  template:
    metadata:
      labels:
        app.kubernetes.io/name: ingress-nginx
        app.kubernetes.io/part-of: ingress-nginx
      annotations:
        prometheus.io/port: "10254"
        prometheus.io/scrape: "true"
    spec:
      serviceAccountName: nginx-ingress-serviceaccount
      # 增加 hostNetwork: true，意思是开启主机网络模式，暴露 Nginx 服务端口 80
      hostNetwork: true
      containers:
        - name: nginx-ingress-controller
          image: quay.io/kubernetes-ingress-controller/nginx-ingress-controller:0.24.1
          args:
            - /nginx-ingress-controller
            - --configmap=$(POD_NAMESPACE)/nginx-configuration
            - --tcp-services-configmap=$(POD_NAMESPACE)/tcp-services
            - --udp-services-configmap=$(POD_NAMESPACE)/udp-services
            - --publish-service=$(POD_NAMESPACE)/ingress-nginx
// 以下代码省略...
```
### 部署 Ingress
Ingress 翻译过来是入口的意思，说白了就是个 API 网关（想想 Zuul 和 Spring Cloud Gateway）
```yaml
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
  name: nginx-web
  annotations:
    # 指定 Ingress Controller 的类型
    kubernetes.io/ingress.class: "nginx"
    # 指定我们的 rules 的 path 可以使用正则表达式
    nginx.ingress.kubernetes.io/use-regex: "true"
    # 连接超时时间，默认为 5s
    nginx.ingress.kubernetes.io/proxy-connect-timeout: "600"
    # 后端服务器回转数据超时时间，默认为 60s
    nginx.ingress.kubernetes.io/proxy-send-timeout: "600"
    # 后端服务器响应超时时间，默认为 60s
    nginx.ingress.kubernetes.io/proxy-read-timeout: "600"
    # 客户端上传文件，最大大小，默认为 20m
    nginx.ingress.kubernetes.io/proxy-body-size: "10m"
    # URL 重写
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  # 路由规则
  rules:
  # 主机名，只能是域名，修改为你自己的
  - host: k8s.test.com
    http:
      paths:
      - path:
        backend:
          # 后台部署的 Service Name，与上面部署的 Tomcat 对应
          serviceName: tomcat-http
          # 后台部署的 Service Port，与上面部署的 Tomcat 对应
          servicePort: 8080

```
验证是否成功

```bash
kubectl get deployment
```
# 输出如下
```bash
NAME         READY   UP-TO-DATE   AVAILABLE   AGE
tomcat-app   2/2     2            2           88m
```

```bash
kubectl get service
```
# 输出如下
```bash
NAME          TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
kubernetes    ClusterIP   10.96.0.1       <none>        443/TCP    2d5h
tomcat-http   ClusterIP   10.97.222.179   <none>        8080/TCP   89m

```
### 查看 Nginx Ingress Controller
```bash
kubectl get pods -n ingress-nginx -o wide
```

```bash
# 输出如下，注意下面的 IP 地址，就是我们实际访问地址
NAME                                        READY   STATUS    RESTARTS   AGE   IP                NODE                 NOMINATED NODE   READINESS GATES
nginx-ingress-controller-76f9fddcf8-vzkm5   1/1     Running   0          61m   192.168.141.160   kubernetes-node-01   <none>           <none>

kubectl get ingress

# 输出如下
NAME        HOSTS          ADDRESS   PORTS   AGE
nginx-web   k8s.test.com             80      61m
```
测试访问
成功代理到 Tomcat 即表示成功