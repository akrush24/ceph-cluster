# ceph-cluster
it's my config file for CEPH Cluster
# Installation
install pkgs on OS
* `ceph-deploy install --release=nautilus n0{1,2,3,4}.sds.srv.local`
put config file ./ceph.conf in /etc/ceph.conf
* `ceph-deploy --overwrite-conf admin n0{1,2,3,4}.sds.srv.local`
