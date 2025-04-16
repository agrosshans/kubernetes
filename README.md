

https://www.nocentino.com/posts/

---

# Kubernetes
Setup and install Kubernetes


### Kubernetes version used at the time I wrote the documentation

curl https://cdn.dl.k8s.io/release/stable.txt
v1.32.3



### Hosts Configuration
On the worker node:
```bash
[root@kubernetes-worker-node ~]# cat /etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6

# kubernetes cluster
192.168.124.51 kubernetes-control-plane.local.lanathome.org kubernetes-control-plane.local kubernetes-control-plane c1-cp1
192.168.124.52 kubernetes-worker-node1.local.lanathome.org kubernetes-worker-node1.local kubernetes-worker-node1 c1-node1
192.168.124.53 kubernetes-worker-node2.local.lanathome.org kubernetes-worker-node2.local kubernetes-worker-node2 c1-node2

```

### OS Information
On the control plane node:
```bash
[root@kubernetes-control-plane ~]# cat /etc/redhat-release 
CentOS Stream release 9
```

On the worker node1:
```bash
[root@kubernetes-worker-node1 ~]# cat /etc/redhat-release 
CentOS Stream release 9
```

On the worker node2:
```bash
[root@kubernetes-worker-node2 ~]# cat /etc/redhat-release 
CentOS Stream release 9
```

### Install bash-completion
```bash
# sudo dnf install bash-completion


add this line in ~/.bashrc

source /usr/share/bash-completion/bash_completion

```bash
# vim ~/.bashrc
```


### kubernetes version
get the latest version of kubernetes from: https://cdn.dl.k8s.io/release/stable.txt


### Setup Kubernetes Repository
Create the Kubernetes repository file:
```bash
cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://pkgs.k8s.io/core:/stable:/v1.32/rpm/
enabled=1
gpgcheck=1
gpgkey=https://pkgs.k8s.io/core:/stable:/v1.32/rpm/repodata/repomd.xml.key
EOF
```

### Setup Docker-CE Repository
Create the Kubernetes repository file:
```bash
cat <<EOF | sudo tee /etc/yum.repos.d/docker-ce.repo
[docker-ce-stable]
name=Docker CE Stable - $basearch
baseurl=https://download.docker.com/linux/centos/$releasever/$basearch/stable
enabled=1
gpgcheck=1
gpgkey=https://download.docker.com/linux/centos/gpg

[docker-ce-stable-debuginfo]
name=Docker CE Stable - Debuginfo $basearch
baseurl=https://download.docker.com/linux/centos/$releasever/debug-$basearch/stable
enabled=0
gpgcheck=1
gpgkey=https://download.docker.com/linux/centos/gpg

[docker-ce-stable-source]
name=Docker CE Stable - Sources
baseurl=https://download.docker.com/linux/centos/$releasever/source/stable
enabled=0
gpgcheck=1
gpgkey=https://download.docker.com/linux/centos/gpg

[docker-ce-test]
name=Docker CE Test - $basearch
baseurl=https://download.docker.com/linux/centos/$releasever/$basearch/test
enabled=0
gpgcheck=1
gpgkey=https://download.docker.com/linux/centos/gpg

[docker-ce-test-debuginfo]
name=Docker CE Test - Debuginfo $basearch
baseurl=https://download.docker.com/linux/centos/$releasever/debug-$basearch/test
enabled=0
gpgcheck=1
gpgkey=https://download.docker.com/linux/centos/gpg

[docker-ce-test-source]
name=Docker CE Test - Sources
baseurl=https://download.docker.com/linux/centos/$releasever/source/test
enabled=0
gpgcheck=1
gpgkey=https://download.docker.com/linux/centos/gpg

[docker-ce-nightly]
name=Docker CE Nightly - $basearch
baseurl=https://download.docker.com/linux/centos/$releasever/$basearch/nightly
enabled=0
gpgcheck=1
gpgkey=https://download.docker.com/linux/centos/gpg

[docker-ce-nightly-debuginfo]
name=Docker CE Nightly - Debuginfo $basearch
baseurl=https://download.docker.com/linux/centos/$releasever/debug-$basearch/nightly
enabled=0
gpgcheck=1
gpgkey=https://download.docker.com/linux/centos/gpg

[docker-ce-nightly-source]
name=Docker CE Nightly - Sources
baseurl=https://download.docker.com/linux/centos/$releasever/source/nightly
enabled=0
gpgcheck=1
gpgkey=https://download.docker.com/linux/centos/gpg
EOF
```

--- 
