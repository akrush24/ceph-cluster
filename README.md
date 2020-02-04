# ceph-cluster
it's my config file for CEPH Cluster
# Installation
* install pkgs on OS 
```ceph-deploy install --release=nautilus n0{1,2,3,4}.sds.srv.local```
* put config file ./ceph.conf in /etc/ceph.conf
```ceph-deploy --overwrite-conf admin n0{1,2,3,4}.sds.srv.local```

# Destroy ALL
```
# ceph-deploy purge n0{1,2,3,4}
# ceph-deploy purgedata n0{1,2,3,4}
```
creal data and metadata information from HDD
```
## first delete OLD lvm
# for i in `vgs|grep ceph-|awk '{print $1}'`;do vgremove -y $i;done
## second run
# ceph-deploy disk zap n01 /dev/sdb /dev/sdc /dev/sdd
```

* delete mon
```
# ceph-deploy mon destroy n01
```

