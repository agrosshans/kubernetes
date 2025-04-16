# kubernetes
setup and install kubernetes

[root@kubernetes-worker-node ~]# cat /etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
#
# kubernetes cluster
192.168.124.51 kubernetes-control-plane.local.lanathome.org kubernetes-control-plane.local kubernetes-control-plane
192.168.124.52 kubernetes-worker-node.local.lanathome.org kubernetes-worker-node.local kubernetes-worker-node




[root@kubernetes-control-plane ~]# cat /etc/redhat-release 
CentOS Stream release 9

[root@kubernetes-worker-node ~]# cat /etc/redhat-release 
CentOS Stream release 9


# setup repo
cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://pkgs.k8s.io/core:/stable:/v1.32/rpm/
enabled=1
gpgcheck=1
gpgkey=https://pkgs.k8s.io/core:/stable:/v1.32/rpm/repodata/repomd.xml.key
EOF

