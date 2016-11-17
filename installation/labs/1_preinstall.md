
# Check vm.swappiness on all your nodes

```
sudo sysctl vm.swappiness=1 # Disable
sudo bash -c "echo 'vm.swappiness = 1' >> /etc/sysctl.conf" # Make permanent changes
```

# Display the mount attributes of all volumes
```
echo -e "o\nn\np\n1\n\n\n\nw" | sudo fdisk /dev/xvdb 
echo -e "o\nn\np\n1\n\n\n\nw" | sudo fdisk /dev/xvdc 
echo -e "o\nn\np\n1\n\n+15GB\n\nw" |sudo fdisk /dev/xvdf
echo -e "o\nn\np\n2\n\n\n\nw" |sudo fdisk /dev/xvdf
sudo fdisk /dev/xvdb #u/n/p/1/w
sudo fdisk /dev/xvdc #u/n/p/1/w
sudo fdisk /dev/xvdf #u/n/p/1/w
sudo mkfs.ext4 /dev/xvdb1
sudo mkfs.ext4 /dev/xvdc1
sudo mkfs.ext4 /dev/xvdf1
sudo partprobe
sudo mkdir /data1 /data2
```

# Display mount points
```
[ec2-user@ip-172-31-25-137 ~]$ sudo mount
/dev/xvda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw,rootcontext="system_u:object_r:tmpfs_t:s0")
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/xvdb1 on /data1 type ext4 (rw)
/dev/xvdc1 on /data2 type ext4 (rw)
[ec2-user@ip-172-31-25-137 ~]$
```

# Display disks usage
```
#[ec2-user@ip-172-31-25-137 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  2,0G  7,3G  21% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb1       40G   48M   38G   1% /data1
/dev/xvdc1       40G   48M   38G   1% /data2
```

# Disable transparent hugepages
```
sudo echo never > /sys/kernel/mm/redhat_transparent_hugepage/defrag
```

# Report the network interface attributes
```
[root@ip-172-31-25-137 ec2-user]# ifconfig
eth0      Link encap:Ethernet  HWaddr 02:71:BC:42:30:17
          inet addr:172.31.25.137  Bcast:172.31.31.255  Mask:255.255.240.0
          inet6 addr: fe80::71:bcff:fe42:3017/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9001  Metric:1
          RX packets:47408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:62468514 (59.5 MiB)  TX bytes:783481 (765.1 KiB)
          Interrupt:143

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

# Show forward and reverse host lookups using getent and nslookup
```
[root@ip-172-31-25-137 ec2-user]# nslookup 35.156.79.146
Server:		172.31.0.2
Address:	172.31.0.2#53

Non-authoritative answer:
146.79.156.35.in-addr.arpa	name = ec2-35-156-79-146.eu-central-1.compute.amazonaws.com.

Authoritative answers can be found from:

[root@ip-172-31-25-137 ec2-user]# nslookup ec2-35-156-76-146.eu-central-1.compute.amazonaws.com
Server:		172.31.0.2
Address:	172.31.0.2#53

Non-authoritative answer:
Name:	ec2-35-156-76-146.eu-central-1.compute.amazonaws.com
Address: 172.31.25.139

[root@ip-172-31-25-137 ec2-user]# getent hosts 35.156.79.146
35.156.79.146   ec2-35-156-79-146.eu-central-1.compute.amazonaws.com
[root@ip-172-31-25-137 ec2-user]# getent hosts ec2-35-156-79-146.eu-central-1.compute.amazonaws.com
35.156.79.146   ec2-35-156-79-146.eu-central-1.compute.amazonaws.com
```

# Verify the nscd service is running
```
sudo yum install nscd -y
sudo chkconfig nscd on
sudo service nscd start
sudo service nscd status

[root@ip-172-31-25-137 ec2-user]#
[root@ip-172-31-25-137 ec2-user]# chkconfig nscd on
[root@ip-172-31-25-137 ec2-user]# service nscd start
Starting nscd:                                             [  OK  ]
[root@ip-172-31-25-137 ec2-user]# sudo service nscd statu
[root@ip-172-31-25-137 ec2-user]# sudo service nscd status
nscd (pid 23325) is running...
```

# Verify the ntpd service is running

```
chkconfig ntpd on
sudo service ntpd status
sudo service ntpd start

[root@ip-172-31-25-137 ec2-user]# chkconfig ntpd on
[root@ip-172-31-25-137 ec2-user]# sudo service ntpd status
ntpd is stopped
[root@ip-172-31-25-137 ec2-user]# sudo service ntpd start
Starting ntpd:                                             [  OK  ]
[root@ip-172-31-25-137 ec2-user]#
```



# Checkreqs Script

```
[### OS INFO
//--- uname -a
ip-172-31-25-141.eu-central-1.compute.internal
Linux ip-172-31-25-141.eu-central-1.compute.internal 2.6.32-573.el6.x86_64 #1 SMP Wed Jul 1 18:23:37 EDT 2015 x86_64 x86_64 x86_64 GNU/Linux
ip-172-31-25-137.eu-central-1.compute.internal
Linux ip-172-31-25-137.eu-central-1.compute.internal 2.6.32-573.el6.x86_64 #1 SMP Wed Jul 1 18:23:37 EDT 2015 x86_64 x86_64 x86_64 GNU/Linux
ip-172-31-25-138.eu-central-1.compute.internal
Linux ip-172-31-25-138.eu-central-1.compute.internal 2.6.32-573.el6.x86_64 #1 SMP Wed Jul 1 18:23:37 EDT 2015 x86_64 x86_64 x86_64 GNU/Linux
ip-172-31-25-139.eu-central-1.compute.internal
Linux ip-172-31-25-139.eu-central-1.compute.internal 2.6.32-573.el6.x86_64 #1 SMP Wed Jul 1 18:23:37 EDT 2015 x86_64 x86_64 x86_64 GNU/Linux
ip-172-31-25-140.eu-central-1.compute.internal
Linux ip-172-31-25-140.eu-central-1.compute.internal 2.6.32-573.el6.x86_64 #1 SMP Wed Jul 1 18:23:37 EDT 2015 x86_64 x86_64 x86_64 GNU/Linux

//--- cat /etc/redhat-release
ip-172-31-25-141.eu-central-1.compute.internal
Red Hat Enterprise Linux Server release 6.7 (Santiago)
ip-172-31-25-137.eu-central-1.compute.internal
Red Hat Enterprise Linux Server release 6.7 (Santiago)
ip-172-31-25-138.eu-central-1.compute.internal
Red Hat Enterprise Linux Server release 6.7 (Santiago)
ip-172-31-25-139.eu-central-1.compute.internal
Red Hat Enterprise Linux Server release 6.7 (Santiago)
ip-172-31-25-140.eu-central-1.compute.internal
Red Hat Enterprise Linux Server release 6.7 (Santiago)

### NETWORK
//--- dmesg | egrep NIC
ip-172-31-25-141.eu-central-1.compute.internal
Netfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated NICs.
ip-172-31-25-137.eu-central-1.compute.internal
Netfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated NICs.
ip-172-31-25-138.eu-central-1.compute.internal
Netfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated NICs.
ip-172-31-25-139.eu-central-1.compute.internal
Netfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated NICs.
ip-172-31-25-140.eu-central-1.compute.internal
Netfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated NICs.

//--- egrep HOSTNAME /etc/sysconfig/network
ip-172-31-25-141.eu-central-1.compute.internal
HOSTNAME=ip-172-31-25-141.eu-central-1.compute.internal
ip-172-31-25-137.eu-central-1.compute.internal
HOSTNAME=ip-172-31-25-137.eu-central-1.compute.internal
ip-172-31-25-138.eu-central-1.compute.internal
HOSTNAME=ip-172-31-25-138.eu-central-1.compute.internal
ip-172-31-25-139.eu-central-1.compute.internal
HOSTNAME=ip-172-31-25-139.eu-central-1.compute.internal
ip-172-31-25-140.eu-central-1.compute.internal
HOSTNAME=ip-172-31-25-140.eu-central-1.compute.internal

//--- cat /etc/sysconfig/network-scripts/ifcfg-eth* | egrep "^DEVICE|BOOTPROTO|ONBOOT|NETMASK|NETWORK|IPADDR|PEERDNS"
ip-172-31-25-141.eu-central-1.compute.internal
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
PEERDNS="yes"
ip-172-31-25-137.eu-central-1.compute.internal
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
PEERDNS="yes"
ip-172-31-25-138.eu-central-1.compute.internal
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
PEERDNS="yes"
ip-172-31-25-139.eu-central-1.compute.internal
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
PEERDNS="yes"
ip-172-31-25-140.eu-central-1.compute.internal
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
PEERDNS="yes"

### DISK INFO
//--- lsblk
ip-172-31-25-141.eu-central-1.compute.internal
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  10G  0 disk
└─xvda1 202:1    0  10G  0 part /
xvdb    202:16   0  40G  0 disk
└─xvdb1 202:17   0  40G  0 part /opt
xvdc    202:32   0  40G  0 disk
└─xvdc1 202:33   0  40G  0 part /data1
xvdf    202:80   0  30G  0 disk
├─xvdf1 202:81   0  14G  0 part /var/log
└─xvdf2 202:82   0  16G  0 part /var/lib
ip-172-31-25-137.eu-central-1.compute.internal
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  10G  0 disk
└─xvda1 202:1    0  10G  0 part /
xvdb    202:16   0  40G  0 disk
└─xvdb1 202:17   0  40G  0 part /data1
xvdc    202:32   0  40G  0 disk
└─xvdc1 202:33   0  40G  0 part /opt
xvdf    202:80   0  30G  0 disk
├─xvdf1 202:81   0  14G  0 part /var/log
└─xvdf2 202:82   0  16G  0 part /var/lib
ip-172-31-25-138.eu-central-1.compute.internal
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  10G  0 disk
└─xvda1 202:1    0  10G  0 part /
xvdb    202:16   0  40G  0 disk
└─xvdb1 202:17   0  40G  0 part /data1
xvdc    202:32   0  40G  0 disk
└─xvdc1 202:33   0  40G  0 part /opt
xvdf    202:80   0  30G  0 disk
├─xvdf1 202:81   0  14G  0 part /var/log
└─xvdf2 202:82   0  16G  0 part /var/lib
ip-172-31-25-139.eu-central-1.compute.internal
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  10G  0 disk
└─xvda1 202:1    0  10G  0 part /
xvdb    202:16   0  40G  0 disk
└─xvdb1 202:17   0  40G  0 part /data1
xvdc    202:32   0  40G  0 disk
└─xvdc1 202:33   0  40G  0 part /opt
xvdf    202:80   0  30G  0 disk
├─xvdf1 202:81   0  14G  0 part /var/log
└─xvdf2 202:82   0  16G  0 part /var/lib
ip-172-31-25-140.eu-central-1.compute.internal
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  10G  0 disk
└─xvda1 202:1    0  10G  0 part /
xvdb    202:16   0  40G  0 disk
└─xvdb1 202:17   0  40G  0 part /data1
xvdc    202:32   0  40G  0 disk
└─xvdc1 202:33   0  40G  0 part /opt
xvdf    202:80   0  30G  0 disk
├─xvdf1 202:81   0  14G  0 part /var/log
└─xvdf2 202:82   0  16G  0 part /var/lib

//--- egrep "^/dev/*" /proc/mounts
ip-172-31-25-141.eu-central-1.compute.internal
/dev/xvda1 / ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdc1 /data1 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdb1 /opt ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdf1 /var/log ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdf2 /var/lib ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
ip-172-31-25-137.eu-central-1.compute.internal
/dev/xvda1 / ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdb1 /data1 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdc1 /opt ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdf1 /var/log ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdf2 /var/lib ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
ip-172-31-25-138.eu-central-1.compute.internal
/dev/xvda1 / ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdb1 /data1 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdc1 /opt ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdf2 /var/lib ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdf1 /var/log ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
ip-172-31-25-139.eu-central-1.compute.internal
/dev/xvda1 / ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdb1 /data1 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdc1 /opt ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdf1 /var/log ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdf2 /var/lib ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
ip-172-31-25-140.eu-central-1.compute.internal
/dev/xvda1 / ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdb1 /data1 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdc1 /opt ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdf1 /var/log ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdf2 /var/lib ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0

//--- df -h
ip-172-31-25-141.eu-central-1.compute.internal
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  6,0G  3,3G  65% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdc1       40G  855M   37G   3% /data1
/dev/xvdb1       40G  4,8G   33G  13% /opt
cm_processes    7,3G   46M  7,3G   1% /var/run/cloudera-scm-agent/process
/dev/xvdf1       14G  160M   13G   2% /var/log
/dev/xvdf2       16G  4,0G   11G  27% /var/lib
ip-172-31-25-137.eu-central-1.compute.internal
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  5,5G  3,8G  59% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb1       40G   71M   38G   1% /data1
/dev/xvdc1       40G  3,5G   34G  10% /opt
cm_processes    7,3G   22M  7,3G   1% /var/run/cloudera-scm-agent/process
/dev/xvdf1       14G   69M   13G   1% /var/log
/dev/xvdf2       16G  1,5G   14G  10% /var/lib
ip-172-31-25-138.eu-central-1.compute.internal
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  3,9G  5,5G  42% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb1       40G   14G   24G  38% /data1
/dev/xvdc1       40G  3,5G   34G  10% /opt
cm_processes    7,3G  3,7M  7,3G   1% /var/run/cloudera-scm-agent/process
/dev/xvdf2       16G  111M   15G   1% /var/lib
/dev/xvdf1       14G   58M   13G   1% /var/log
ip-172-31-25-139.eu-central-1.compute.internal
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  3,9G  5,4G  42% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb1       40G   16G   22G  42% /data1
/dev/xvdc1       40G  3,5G   34G  10% /opt
cm_processes    7,3G  3,6M  7,3G   1% /var/run/cloudera-scm-agent/process
/dev/xvdf1       14G   62M   13G   1% /var/log
/dev/xvdf2       16G  109M   15G   1% /var/lib
ip-172-31-25-140.eu-central-1.compute.internal
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  3,9G  5,5G  42% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb1       40G   17G   21G  46% /data1
/dev/xvdc1       40G  3,5G   34G  10% /opt
cm_processes    7,3G  3,7M  7,3G   1% /var/run/cloudera-scm-agent/process
/dev/xvdf1       14G   61M   13G   1% /var/log
/dev/xvdf2       16G  107M   15G   1% /var/lib

### CPU INFO
//--- nproc
ip-172-31-25-141.eu-central-1.compute.internal
4
ip-172-31-25-137.eu-central-1.compute.internal
4
ip-172-31-25-138.eu-central-1.compute.internal
4
ip-172-31-25-139.eu-central-1.compute.internal
4
ip-172-31-25-140.eu-central-1.compute.internal
4

//--- egrep "^model name\s+:" /proc/cpuinfo
ip-172-31-25-141.eu-central-1.compute.internal
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
ip-172-31-25-137.eu-central-1.compute.internal
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
ip-172-31-25-138.eu-central-1.compute.internal
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
ip-172-31-25-139.eu-central-1.compute.internal
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
ip-172-31-25-140.eu-central-1.compute.internal
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name     : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz

### MEM INFO
//--- egrep "^MemTotal|SwapTotal|HugePages_Total" /proc/meminfo
ip-172-31-25-141.eu-central-1.compute.internal
MemTotal:       15297616 kB
SwapTotal:             0 kB
HugePages_Total:       0
ip-172-31-25-137.eu-central-1.compute.internal
MemTotal:       15297616 kB
SwapTotal:             0 kB
HugePages_Total:       0
ip-172-31-25-138.eu-central-1.compute.internal
MemTotal:       15297616 kB
SwapTotal:             0 kB
HugePages_Total:       0
ip-172-31-25-139.eu-central-1.compute.internal
MemTotal:       15297616 kB
SwapTotal:             0 kB
HugePages_Total:       0
ip-172-31-25-140.eu-central-1.compute.internal
MemTotal:       15297616 kB
SwapTotal:             0 kB
HugePages_Total:       0

### SELINUX CHECK
//--- egrep "^SELINUX" /etc/sysconfig/selinux
ip-172-31-25-141.eu-central-1.compute.internal
SELINUX=disabled
SELINUXTYPE=targeted
ip-172-31-25-137.eu-central-1.compute.internal
SELINUX=disabled
SELINUXTYPE=targeted
ip-172-31-25-138.eu-central-1.compute.internal
SELINUX=disabled
SELINUXTYPE=targeted
ip-172-31-25-139.eu-central-1.compute.internal
SELINUX=disabled
SELINUXTYPE=targeted
ip-172-31-25-140.eu-central-1.compute.internal
SELINUX=disabled
SELINUXTYPE=targeted

### SSHD SERVICE
//--- chkconfig --list sshd
ip-172-31-25-141.eu-central-1.compute.internal
sshd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-137.eu-central-1.compute.internal
sshd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-138.eu-central-1.compute.internal
sshd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-139.eu-central-1.compute.internal
sshd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-140.eu-central-1.compute.internal
sshd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado

### USER LIMITS
//--- egrep "^[^# ].+" /etc/security/limits.conf
ip-172-31-25-141.eu-central-1.compute.internal
ip-172-31-25-137.eu-central-1.compute.internal
ip-172-31-25-138.eu-central-1.compute.internal
ip-172-31-25-139.eu-central-1.compute.internal
ip-172-31-25-140.eu-central-1.compute.internal

### NTP SERVICE
//--- service ntpd status
ip-172-31-25-141.eu-central-1.compute.internal
ntpd (pid  2440) is running...
ip-172-31-25-137.eu-central-1.compute.internal
ntpd (pid  23435) is running...
ip-172-31-25-138.eu-central-1.compute.internal
ntpd (pid  2445) is running...
ip-172-31-25-139.eu-central-1.compute.internal
ntpd (pid  2400) is running...
ip-172-31-25-140.eu-central-1.compute.internal
ntpd (pid  2418) is running...

//--- chkconfig --list ntpd
ip-172-31-25-141.eu-central-1.compute.internal
ntpd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-137.eu-central-1.compute.internal
ntpd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-138.eu-central-1.compute.internal
ntpd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-139.eu-central-1.compute.internal
ntpd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-140.eu-central-1.compute.internal
ntpd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado

//--- date
ip-172-31-25-141.eu-central-1.compute.internal
jue nov 17 00:30:18 EST 2016
ip-172-31-25-137.eu-central-1.compute.internal
jue nov 17 00:30:18 EST 2016
ip-172-31-25-138.eu-central-1.compute.internal
jue nov 17 00:30:19 EST 2016
ip-172-31-25-139.eu-central-1.compute.internal
jue nov 17 00:30:19 EST 2016
ip-172-31-25-140.eu-central-1.compute.internal
jue nov 17 00:30:19 EST 2016

//--- ntpq -p
ip-172-31-25-141.eu-central-1.compute.internal
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*spacys.de       131.188.3.222    2 u  148 1024  377    5.465   -0.239   0.350
-jitter.tickadj. 127.67.113.92    2 u  130 1024  377  169.712    2.321   0.284
+ntp1.m-online.n 212.18.1.106     2 u  311 1024  377    8.286    0.325   0.352
+h1939797.strato 131.188.3.223    2 u  571 1024  377   13.710   -0.198   2.886
ip-172-31-25-137.eu-central-1.compute.internal
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+2.202.196.104.b 128.138.141.172  2 u  700 1024  377   99.224   -1.410   0.723
+a03.alphasrv.ne 192.53.103.108   2 u  458 1024  377    5.584    0.621   0.340
-ntp.wdc1.us.lea 209.51.161.238   2 u  786 1024  377  103.795    9.398   5.587
*muenchen.klaus- 131.211.8.244    2 u 1029 1024  377    7.557   -0.056   0.377
ip-172-31-25-138.eu-central-1.compute.internal
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+ns3.customer-re 192.53.103.108   2 u  435 1024  377   26.537    1.382   0.465
-www.mistersixt. 122.208.208.165  3 u  898 1024  377    6.174    2.234   1.588
*trillian.jollyb 131.188.3.222    2 u  403 1024  377    4.343   -0.053   0.746
+213.95.200.109  131.188.3.221    2 u  344 1024  377    4.617    0.431   0.244
ip-172-31-25-139.eu-central-1.compute.internal
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+x.ns.gin.ntt.ne 249.224.99.213   2 u  949 1024  377    0.799   -0.589   1.376
+chl.la          128.138.141.172  2 u  481 1024  377  168.060   -3.540   5.022
*uhrwerk.wertarb 131.188.3.222    2 u  705 1024  377    5.815   -0.100   0.218
-panel1.web2.clu 37.120.191.245   3 u  780 1024  377   11.750   -4.227   0.295
ip-172-31-25-140.eu-central-1.compute.internal
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*re.uni-paderbor .DCF.            1 u  477 1024  377   14.663   -1.115   1.772
+repos.lax-noc.c 128.138.140.44   2 u  714 1024  377  144.601   -0.743   0.516
-stratum2-4.NTP. 129.70.130.71    2 u  256 1024  377   15.843    4.473   0.251
+213.95.200.109  131.188.3.221    2 u  600 1024  377    4.290    0.815   0.602

## FIREWALL SERVICE
//--- service iptables status
ip-172-31-25-141.eu-central-1.compute.internal
iptables: Firewall is not running.
ip-172-31-25-137.eu-central-1.compute.internal
iptables: Firewall is not running.
ip-172-31-25-138.eu-central-1.compute.internal
iptables: Firewall is not running.
ip-172-31-25-139.eu-central-1.compute.internal
iptables: Firewall is not running.
ip-172-31-25-140.eu-central-1.compute.internal
iptables: Firewall is not running.

//--- chkconfig --list iptables
ip-172-31-25-141.eu-central-1.compute.internal
iptables            0:desactivado  1:desactivado  2:desactivado  3:desactivado  4:desactivado  5:desactivado  6:desactivado
ip-172-31-25-137.eu-central-1.compute.internal
iptables            0:desactivado  1:desactivado  2:desactivado  3:desactivado  4:desactivado  5:desactivado  6:desactivado
ip-172-31-25-138.eu-central-1.compute.internal
iptables            0:desactivado  1:desactivado  2:desactivado  3:desactivado  4:desactivado  5:desactivado  6:desactivado
ip-172-31-25-139.eu-central-1.compute.internal
iptables            0:desactivado  1:desactivado  2:desactivado  3:desactivado  4:desactivado  5:desactivado  6:desactivado
ip-172-31-25-140.eu-central-1.compute.internal
iptables            0:desactivado  1:desactivado  2:desactivado  3:desactivado  4:desactivado  5:desactivado  6:desactivado

//--- service ip6tables status
ip-172-31-25-141.eu-central-1.compute.internal
Table: filter
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination
1    ACCEPT     all      ::/0                 ::/0                state RELATED,ESTABLISHED
2    ACCEPT     icmpv6    ::/0                 ::/0
3    ACCEPT     all      ::/0                 ::/0
4    ACCEPT     udp      ::/0                 fe80::/64           state NEW udp dpt:546
5    ACCEPT     tcp      ::/0                 ::/0                state NEW tcp dpt:22
6    REJECT     all      ::/0                 ::/0                reject-with icmp6-adm-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination
1    REJECT     all      ::/0                 ::/0                reject-with icmp6-adm-prohibited

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination

ip-172-31-25-137.eu-central-1.compute.internal
Table: filter
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination
1    ACCEPT     all      ::/0                 ::/0                state RELATED,ESTABLISHED
2    ACCEPT     icmpv6    ::/0                 ::/0
3    ACCEPT     all      ::/0                 ::/0
4    ACCEPT     udp      ::/0                 fe80::/64           state NEW udp dpt:546
5    ACCEPT     tcp      ::/0                 ::/0                state NEW tcp dpt:22
6    REJECT     all      ::/0                 ::/0                reject-with icmp6-adm-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination
1    REJECT     all      ::/0                 ::/0                reject-with icmp6-adm-prohibited

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination

ip-172-31-25-138.eu-central-1.compute.internal
Table: filter
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination
1    ACCEPT     all      ::/0                 ::/0                state RELATED,ESTABLISHED
2    ACCEPT     icmpv6    ::/0                 ::/0
3    ACCEPT     all      ::/0                 ::/0
4    ACCEPT     udp      ::/0                 fe80::/64           state NEW udp dpt:546
5    ACCEPT     tcp      ::/0                 ::/0                state NEW tcp dpt:22
6    REJECT     all      ::/0                 ::/0                reject-with icmp6-adm-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination
1    REJECT     all      ::/0                 ::/0                reject-with icmp6-adm-prohibited

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination

ip-172-31-25-139.eu-central-1.compute.internal
Table: filter
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination
1    ACCEPT     all      ::/0                 ::/0                state RELATED,ESTABLISHED
2    ACCEPT     icmpv6    ::/0                 ::/0
3    ACCEPT     all      ::/0                 ::/0
4    ACCEPT     udp      ::/0                 fe80::/64           state NEW udp dpt:546
5    ACCEPT     tcp      ::/0                 ::/0                state NEW tcp dpt:22
6    REJECT     all      ::/0                 ::/0                reject-with icmp6-adm-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination
1    REJECT     all      ::/0                 ::/0                reject-with icmp6-adm-prohibited

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination

ip-172-31-25-140.eu-central-1.compute.internal
Table: filter
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination
1    ACCEPT     all      ::/0                 ::/0                state RELATED,ESTABLISHED
2    ACCEPT     icmpv6    ::/0                 ::/0
3    ACCEPT     all      ::/0                 ::/0
4    ACCEPT     udp      ::/0                 fe80::/64           state NEW udp dpt:546
5    ACCEPT     tcp      ::/0                 ::/0                state NEW tcp dpt:22
6    REJECT     all      ::/0                 ::/0                reject-with icmp6-adm-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination
1    REJECT     all      ::/0                 ::/0                reject-with icmp6-adm-prohibited

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination


//--- chkconfig --list ip6tables
ip-172-31-25-141.eu-central-1.compute.internal
ip6tables           0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-137.eu-central-1.compute.internal
ip6tables           0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-138.eu-central-1.compute.internal
ip6tables           0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-139.eu-central-1.compute.internal
ip6tables           0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-140.eu-central-1.compute.internal
ip6tables           0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado

### NSSWITCH & HOST.CONF
//--- egrep "^hosts:" /etc/nsswitch.conf
ip-172-31-25-141.eu-central-1.compute.internal
hosts:      files dns
ip-172-31-25-137.eu-central-1.compute.internal
hosts:      files dns
ip-172-31-25-138.eu-central-1.compute.internal
hosts:      files dns
ip-172-31-25-139.eu-central-1.compute.internal
hosts:      files dns
ip-172-31-25-140.eu-central-1.compute.internal
hosts:      files dns

//--- cat /etc/host.conf
ip-172-31-25-141.eu-central-1.compute.internal
multi on
ip-172-31-25-137.eu-central-1.compute.internal
multi on
ip-172-31-25-138.eu-central-1.compute.internal
multi on
ip-172-31-25-139.eu-central-1.compute.internal
multi on
ip-172-31-25-140.eu-central-1.compute.internal
multi on

//--- getent hosts
ip-172-31-25-141.eu-central-1.compute.internal
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.25.141   ip-172-31-25-141.eu-central-1.compute.internal server01 master01
172.31.25.137   ip-172-31-25-137.eu-central-1.compute.internal server02 master02
172.31.25.138   ip-172-31-25-138.eu-central-1.compute.internal server03 worker01
172.31.25.139   ip-172-31-25-139.eu-central-1.compute.internal server04 worker02
172.31.25.140   ip-172-31-25-140.eu-central-1.compute.internal server05 worker03
ip-172-31-25-137.eu-central-1.compute.internal
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.25.141   ip-172-31-25-141.eu-central-1.compute.internal server01 master01
172.31.25.137   ip-172-31-25-137.eu-central-1.compute.internal server02 master02
172.31.25.138   ip-172-31-25-138.eu-central-1.compute.internal server03 worker01
172.31.25.139   ip-172-31-25-139.eu-central-1.compute.internal server04 worker02
172.31.25.140   ip-172-31-25-140.eu-central-1.compute.internal server05 worker03
ip-172-31-25-138.eu-central-1.compute.internal
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.25.141   ip-172-31-25-141.eu-central-1.compute.internal server01 master01
172.31.25.137   ip-172-31-25-137.eu-central-1.compute.internal server02 master02
172.31.25.138   ip-172-31-25-138.eu-central-1.compute.internal server03 worker01
172.31.25.139   ip-172-31-25-139.eu-central-1.compute.internal server04 worker02
172.31.25.140   ip-172-31-25-140.eu-central-1.compute.internal server05 worker03
ip-172-31-25-139.eu-central-1.compute.internal
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.25.141   ip-172-31-25-141.eu-central-1.compute.internal server01 master01
172.31.25.137   ip-172-31-25-137.eu-central-1.compute.internal server02 master02
172.31.25.138   ip-172-31-25-138.eu-central-1.compute.internal server03 worker01
172.31.25.139   ip-172-31-25-139.eu-central-1.compute.internal server04 worker02
172.31.25.140   ip-172-31-25-140.eu-central-1.compute.internal server05 worker03
ip-172-31-25-140.eu-central-1.compute.internal
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.25.141   ip-172-31-25-141.eu-central-1.compute.internal server01 master01
172.31.25.137   ip-172-31-25-137.eu-central-1.compute.internal server02 master02
172.31.25.138   ip-172-31-25-138.eu-central-1.compute.internal server03 worker01
172.31.25.139   ip-172-31-25-139.eu-central-1.compute.internal server04 worker02
172.31.25.140   ip-172-31-25-140.eu-central-1.compute.internal server05 worker03

### DNS CACHE
//--- service nscd status
ip-172-31-25-141.eu-central-1.compute.internal
nscd (pid 2373) is running...
ip-172-31-25-137.eu-central-1.compute.internal
nscd (pid 23325) is running...
ip-172-31-25-138.eu-central-1.compute.internal
nscd (pid 2376) is running...
ip-172-31-25-139.eu-central-1.compute.internal
nscd (pid 2332) is running...
ip-172-31-25-140.eu-central-1.compute.internal
nscd (pid 2349) is running...

//--- chkconfig --list nscd
ip-172-31-25-141.eu-central-1.compute.internal
nscd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-137.eu-central-1.compute.internal
nscd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-138.eu-central-1.compute.internal
nscd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-139.eu-central-1.compute.internal
nscd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado
ip-172-31-25-140.eu-central-1.compute.internal
nscd                0:desactivado  1:desactivado  2:activo  3:activo  4:activo  5:activo  6:desactivado

### SWAPPINESS
//--- cat /proc/sys/vm/swappiness
ip-172-31-25-141.eu-central-1.compute.internal
1
ip-172-31-25-137.eu-central-1.compute.internal
1
ip-172-31-25-138.eu-central-1.compute.internal
1
ip-172-31-25-139.eu-central-1.compute.internal
1
ip-172-31-25-140.eu-central-1.compute.internal
1

### IPV4 TCP
//--- sysctl -a | egrep "net.ipv4.tcp_"
ip-172-31-25-141.eu-central-1.compute.internal
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_sack = 1
net.ipv4.tcp_retrans_collapse = 1
net.ipv4.tcp_syn_retries = 5
net.ipv4.tcp_synack_retries = 5
net.ipv4.tcp_max_orphans = 262144
net.ipv4.tcp_max_tw_buckets = 262144
net.ipv4.tcp_keepalive_time = 7200
net.ipv4.tcp_keepalive_probes = 9
net.ipv4.tcp_keepalive_intvl = 75
net.ipv4.tcp_retries1 = 3
net.ipv4.tcp_retries2 = 15
net.ipv4.tcp_fin_timeout = 60
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_abort_on_overflow = 0
net.ipv4.tcp_stdurg = 0
net.ipv4.tcp_rfc1337 = 0
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_orphan_retries = 0
net.ipv4.tcp_fack = 1
net.ipv4.tcp_reordering = 3
net.ipv4.tcp_ecn = 2
net.ipv4.tcp_dsack = 1
net.ipv4.tcp_mem = 1431168    1908224   2862336
net.ipv4.tcp_wmem = 4096 16384     4194304
net.ipv4.tcp_rmem = 4096 87380     4194304
net.ipv4.tcp_app_win = 31
net.ipv4.tcp_adv_win_scale = 2
net.ipv4.tcp_tw_reuse = 0
net.ipv4.tcp_frto = 2
net.ipv4.tcp_frto_response = 0
net.ipv4.tcp_low_latency = 0
net.ipv4.tcp_no_metrics_save = 0
net.ipv4.tcp_moderate_rcvbuf = 1
net.ipv4.tcp_tso_win_divisor = 3
net.ipv4.tcp_congestion_control = cubic
net.ipv4.tcp_abc = 0
net.ipv4.tcp_mtu_probing = 0
net.ipv4.tcp_base_mss = 512
net.ipv4.tcp_workaround_signed_windows = 0
net.ipv4.tcp_challenge_ack_limit = 100
net.ipv4.tcp_limit_output_bytes = 262144
net.ipv4.tcp_dma_copybreak = 4096
net.ipv4.tcp_slow_start_after_idle = 1
net.ipv4.tcp_available_congestion_control = cubic reno
net.ipv4.tcp_allowed_congestion_control = cubic reno
net.ipv4.tcp_max_ssthresh = 0
net.ipv4.tcp_thin_linear_timeouts = 0
net.ipv4.tcp_thin_dupack = 0
net.ipv4.tcp_min_tso_segs = 2
ip-172-31-25-137.eu-central-1.compute.internal
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_sack = 1
net.ipv4.tcp_retrans_collapse = 1
net.ipv4.tcp_syn_retries = 5
net.ipv4.tcp_synack_retries = 5
net.ipv4.tcp_max_orphans = 262144
net.ipv4.tcp_max_tw_buckets = 262144
net.ipv4.tcp_keepalive_time = 7200
net.ipv4.tcp_keepalive_probes = 9
net.ipv4.tcp_keepalive_intvl = 75
net.ipv4.tcp_retries1 = 3
net.ipv4.tcp_retries2 = 15
net.ipv4.tcp_fin_timeout = 60
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_abort_on_overflow = 0
net.ipv4.tcp_stdurg = 0
net.ipv4.tcp_rfc1337 = 0
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_orphan_retries = 0
net.ipv4.tcp_fack = 1
net.ipv4.tcp_reordering = 3
net.ipv4.tcp_ecn = 2
net.ipv4.tcp_dsack = 1
net.ipv4.tcp_mem = 1431168    1908224   2862336
net.ipv4.tcp_wmem = 4096 16384     4194304
net.ipv4.tcp_rmem = 4096 87380     4194304
net.ipv4.tcp_app_win = 31
net.ipv4.tcp_adv_win_scale = 2
net.ipv4.tcp_tw_reuse = 0
net.ipv4.tcp_frto = 2
net.ipv4.tcp_frto_response = 0
net.ipv4.tcp_low_latency = 0
net.ipv4.tcp_no_metrics_save = 0
net.ipv4.tcp_moderate_rcvbuf = 1
net.ipv4.tcp_tso_win_divisor = 3
net.ipv4.tcp_congestion_control = cubic
net.ipv4.tcp_abc = 0
net.ipv4.tcp_mtu_probing = 0
net.ipv4.tcp_base_mss = 512
net.ipv4.tcp_workaround_signed_windows = 0
net.ipv4.tcp_challenge_ack_limit = 100
net.ipv4.tcp_limit_output_bytes = 262144
net.ipv4.tcp_dma_copybreak = 4096
net.ipv4.tcp_slow_start_after_idle = 1
net.ipv4.tcp_available_congestion_control = cubic reno
net.ipv4.tcp_allowed_congestion_control = cubic reno
net.ipv4.tcp_max_ssthresh = 0
net.ipv4.tcp_thin_linear_timeouts = 0
net.ipv4.tcp_thin_dupack = 0
net.ipv4.tcp_min_tso_segs = 2
ip-172-31-25-138.eu-central-1.compute.internal
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_sack = 1
net.ipv4.tcp_retrans_collapse = 1
net.ipv4.tcp_syn_retries = 5
net.ipv4.tcp_synack_retries = 5
net.ipv4.tcp_max_orphans = 262144
net.ipv4.tcp_max_tw_buckets = 262144
net.ipv4.tcp_keepalive_time = 7200
net.ipv4.tcp_keepalive_probes = 9
net.ipv4.tcp_keepalive_intvl = 75
net.ipv4.tcp_retries1 = 3
net.ipv4.tcp_retries2 = 15
net.ipv4.tcp_fin_timeout = 60
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_abort_on_overflow = 0
net.ipv4.tcp_stdurg = 0
net.ipv4.tcp_rfc1337 = 0
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_orphan_retries = 0
net.ipv4.tcp_fack = 1
net.ipv4.tcp_reordering = 3
net.ipv4.tcp_ecn = 2
net.ipv4.tcp_dsack = 1
net.ipv4.tcp_mem = 1431168    1908224   2862336
net.ipv4.tcp_wmem = 4096 16384     4194304
net.ipv4.tcp_rmem = 4096 87380     4194304
net.ipv4.tcp_app_win = 31
net.ipv4.tcp_adv_win_scale = 2
net.ipv4.tcp_tw_reuse = 0
net.ipv4.tcp_frto = 2
net.ipv4.tcp_frto_response = 0
net.ipv4.tcp_low_latency = 0
net.ipv4.tcp_no_metrics_save = 0
net.ipv4.tcp_moderate_rcvbuf = 1
net.ipv4.tcp_tso_win_divisor = 3
net.ipv4.tcp_congestion_control = cubic
net.ipv4.tcp_abc = 0
net.ipv4.tcp_mtu_probing = 0
net.ipv4.tcp_base_mss = 512
net.ipv4.tcp_workaround_signed_windows = 0
net.ipv4.tcp_challenge_ack_limit = 100
net.ipv4.tcp_limit_output_bytes = 262144
net.ipv4.tcp_dma_copybreak = 4096
net.ipv4.tcp_slow_start_after_idle = 1
net.ipv4.tcp_available_congestion_control = cubic reno
net.ipv4.tcp_allowed_congestion_control = cubic reno
net.ipv4.tcp_max_ssthresh = 0
net.ipv4.tcp_thin_linear_timeouts = 0
net.ipv4.tcp_thin_dupack = 0
net.ipv4.tcp_min_tso_segs = 2
ip-172-31-25-139.eu-central-1.compute.internal
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_sack = 1
net.ipv4.tcp_retrans_collapse = 1
net.ipv4.tcp_syn_retries = 5
net.ipv4.tcp_synack_retries = 5
net.ipv4.tcp_max_orphans = 262144
net.ipv4.tcp_max_tw_buckets = 262144
net.ipv4.tcp_keepalive_time = 7200
net.ipv4.tcp_keepalive_probes = 9
net.ipv4.tcp_keepalive_intvl = 75
net.ipv4.tcp_retries1 = 3
net.ipv4.tcp_retries2 = 15
net.ipv4.tcp_fin_timeout = 60
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_abort_on_overflow = 0
net.ipv4.tcp_stdurg = 0
net.ipv4.tcp_rfc1337 = 0
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_orphan_retries = 0
net.ipv4.tcp_fack = 1
net.ipv4.tcp_reordering = 3
net.ipv4.tcp_ecn = 2
net.ipv4.tcp_dsack = 1
net.ipv4.tcp_mem = 1431168    1908224   2862336
net.ipv4.tcp_wmem = 4096 16384     4194304
net.ipv4.tcp_rmem = 4096 87380     4194304
net.ipv4.tcp_app_win = 31
net.ipv4.tcp_adv_win_scale = 2
net.ipv4.tcp_tw_reuse = 0
net.ipv4.tcp_frto = 2
net.ipv4.tcp_frto_response = 0
net.ipv4.tcp_low_latency = 0
net.ipv4.tcp_no_metrics_save = 0
net.ipv4.tcp_moderate_rcvbuf = 1
net.ipv4.tcp_tso_win_divisor = 3
net.ipv4.tcp_congestion_control = cubic
net.ipv4.tcp_abc = 0
net.ipv4.tcp_mtu_probing = 0
net.ipv4.tcp_base_mss = 512
net.ipv4.tcp_workaround_signed_windows = 0
net.ipv4.tcp_challenge_ack_limit = 100
net.ipv4.tcp_limit_output_bytes = 262144
net.ipv4.tcp_dma_copybreak = 4096
net.ipv4.tcp_slow_start_after_idle = 1
net.ipv4.tcp_available_congestion_control = cubic reno
net.ipv4.tcp_allowed_congestion_control = cubic reno
net.ipv4.tcp_max_ssthresh = 0
net.ipv4.tcp_thin_linear_timeouts = 0
net.ipv4.tcp_thin_dupack = 0
net.ipv4.tcp_min_tso_segs = 2
ip-172-31-25-140.eu-central-1.compute.internal
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_sack = 1
net.ipv4.tcp_retrans_collapse = 1
net.ipv4.tcp_syn_retries = 5
net.ipv4.tcp_synack_retries = 5
net.ipv4.tcp_max_orphans = 262144
net.ipv4.tcp_max_tw_buckets = 262144
net.ipv4.tcp_keepalive_time = 7200
net.ipv4.tcp_keepalive_probes = 9
net.ipv4.tcp_keepalive_intvl = 75
net.ipv4.tcp_retries1 = 3
net.ipv4.tcp_retries2 = 15
net.ipv4.tcp_fin_timeout = 60
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_abort_on_overflow = 0
net.ipv4.tcp_stdurg = 0
net.ipv4.tcp_rfc1337 = 0
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_orphan_retries = 0
net.ipv4.tcp_fack = 1
net.ipv4.tcp_reordering = 3
net.ipv4.tcp_ecn = 2
net.ipv4.tcp_dsack = 1
net.ipv4.tcp_mem = 1431168    1908224   2862336
net.ipv4.tcp_wmem = 4096 16384     4194304
net.ipv4.tcp_rmem = 4096 87380     4194304
net.ipv4.tcp_app_win = 31
net.ipv4.tcp_adv_win_scale = 2
net.ipv4.tcp_tw_reuse = 0
net.ipv4.tcp_frto = 2
net.ipv4.tcp_frto_response = 0
net.ipv4.tcp_low_latency = 0
net.ipv4.tcp_no_metrics_save = 0
net.ipv4.tcp_moderate_rcvbuf = 1
net.ipv4.tcp_tso_win_divisor = 3
net.ipv4.tcp_congestion_control = cubic
net.ipv4.tcp_abc = 0
net.ipv4.tcp_mtu_probing = 0
net.ipv4.tcp_base_mss = 512
net.ipv4.tcp_workaround_signed_windows = 0
net.ipv4.tcp_challenge_ack_limit = 100
net.ipv4.tcp_limit_output_bytes = 262144
net.ipv4.tcp_dma_copybreak = 4096
net.ipv4.tcp_slow_start_after_idle = 1
net.ipv4.tcp_available_congestion_control = cubic reno
net.ipv4.tcp_allowed_congestion_control = cubic reno
net.ipv4.tcp_max_ssthresh = 0
net.ipv4.tcp_thin_linear_timeouts = 0
net.ipv4.tcp_thin_dupack = 0
net.ipv4.tcp_min_tso_segs = 2
```