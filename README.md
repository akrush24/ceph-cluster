# ceph-cluster
it's my config file for CEPH Cluster
```
* n01.sds.srv.local - 10.110.27.10, 10.110.28.10
* n02.sds.srv.local - 10.110.27.11, 10.110.28.11
* n03.sds.srv.local - 10.110.27.12, 10.110.28.12
* n04.sds.srv.local - 10.110.27.13, 10.110.28.13
```
# Installation
## install pkgs on OS 
```ceph-deploy install --release=nautilus n0{1,2,3,4}.sds.srv.local```
## put config file ./ceph.conf in /etc/ceph.conf
```ceph-deploy --overwrite-conf admin n0{1,2,3,4}.sds.srv.local```

# Create MON
```
# ceph-deploy mon create-initial
```

# Create OSD
if necessary creal data and metadata information from HDD
```
## delete old lvm volumes
# for i in `vgs|grep ceph-|awk '{print $1}'`;do vgremove -y $i;done
```

```
# ceph-deploy disk zap n01:sd{b,c,d}
# ceph-deploy osd create --data n01:sd{b,c,d}
```

# Create MGR
```
# ceph-deploy mgr create n0{1,2,3,4}
```

# Unistall
## delete mon
```
# ceph-deploy mon destroy n01
```
## delete all
```
# ceph-deploy purge n0{1,2,3,4}
# ceph-deploy purgedata n0{1,2,3,4}
```

# USE
## create pool
```
# ceph osd pool create rbdpool 128
```
## set application to pool
```
# ceph osd pool application enable rbdpool rbd
```
## create rbd image
```
# rbd create rbdpool/my-test-image --size 102400
```
