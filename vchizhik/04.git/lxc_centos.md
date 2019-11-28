# Victor Chizhik

## File config
```

lxc.arch = amd64
lxc.cgroup.memory.limit_in_bytes = 512M

#network
lxc.net.0.type = veth
lxc.net.0.link = lxcbr0
lxc.net.0.flags = up
lxc.net.0.hwaddr = 00:16:3e:xx:xx:xx
```

## Start
```
lxc-create -t download -f config.conf -n centos7 -- --dist centos --release 7 --arch amd64
lxc-start -n centos7
cat bootstrap.sh | chroot /var/lib/lxc/centos7/rootfs /bin/bash
```

## Adduser
```
yum update
yum install -y vim git wget curl
useradd -G sudo insider 
sed -i '$ a \\nsudo  ALL=NOPASSWD:ALL' /etc/sudoers 
```