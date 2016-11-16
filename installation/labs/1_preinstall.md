
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
[ec2-user@server02 ~]$ sudo mount
/dev/xvda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw,rootcontext="system_u:object_r:tmpfs_t:s0")
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/xvdb1 on /data1 type ext4 (rw)
/dev/xvdc1 on /data2 type ext4 (rw)
[ec2-user@server02 ~]$
```

# Display disks usage
```
#[ec2-user@server02 ~]$ df -h
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
[root@server02 ec2-user]# ifconfig
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
[root@server02 ec2-user]# nslookup 35.156.79.146
Server:		172.31.0.2
Address:	172.31.0.2#53

Non-authoritative answer:
146.79.156.35.in-addr.arpa	name = ec2-35-156-79-146.eu-central-1.compute.amazonaws.com.

Authoritative answers can be found from:

[root@server02 ec2-user]# nslookup ec2-35-156-76-146.eu-central-1.compute.amazonaws.com
Server:		172.31.0.2
Address:	172.31.0.2#53

Non-authoritative answer:
Name:	ec2-35-156-76-146.eu-central-1.compute.amazonaws.com
Address: 172.31.25.139

[root@server02 ec2-user]# getent hosts 35.156.79.146
35.156.79.146   ec2-35-156-79-146.eu-central-1.compute.amazonaws.com
[root@server02 ec2-user]# getent hosts ec2-35-156-79-146.eu-central-1.compute.amazonaws.com
35.156.79.146   ec2-35-156-79-146.eu-central-1.compute.amazonaws.com
```

# Verify the nscd service is running
```
sudo yum install nscd -y
sudo chkconfig nscd on
sudo service nscd start
sudo service nscd status

[root@server02 ec2-user]#
[root@server02 ec2-user]# chkconfig nscd on
[root@server02 ec2-user]# service nscd start
Starting nscd:                                             [  OK  ]
[root@server02 ec2-user]# sudo service nscd statu
[root@server02 ec2-user]# sudo service nscd status
nscd (pid 23325) is running...
```

# Verify the ntpd service is running

```
chkconfig ntpd on
sudo service ntpd status
sudo service ntpd start

[root@server02 ec2-user]# chkconfig ntpd on
[root@server02 ec2-user]# sudo service ntpd status
ntpd is stopped
[root@server02 ec2-user]# sudo service ntpd start
Starting ntpd:                                             [  OK  ]
[root@server02 ec2-user]#
```



# Checkreqs Script

```
[ec2-user@server01 ~]$ cat checkreqs
### OS INFO
//--- uname -a
server01
Linux server01 2.6.32-573.el6.x86_64 #1 SMP Wed Jul 1 18:23:37 EDT 2015 x86_64 x86_64 x86_64 GNU/Linux
server02
Linux server02 2.6.32-573.el6.x86_64 #1 SMP Wed Jul 1 18:23:37 EDT 2015 x86_64 x86_64 x86_64 GNU/Linux
server03
Linux server03 2.6.32-573.el6.x86_64 #1 SMP Wed Jul 1 18:23:37 EDT 2015 x86_64 x86_64 x86_64 GNU/Linux
server04
Linux server04 2.6.32-573.el6.x86_64 #1 SMP Wed Jul 1 18:23:37 EDT 2015 x86_64 x86_64 x86_64 GNU/Linux
server05
Linux server05 2.6.32-573.el6.x86_64 #1 SMP Wed Jul 1 18:23:37 EDT 2015 x86_64 x86_64 x86_64 GNU/Linux

//--- cat /etc/redhat-release
server01
Red Hat Enterprise Linux Server release 6.7 (Santiago)
server02
Red Hat Enterprise Linux Server release 6.7 (Santiago)
server03
Red Hat Enterprise Linux Server release 6.7 (Santiago)
server04
Red Hat Enterprise Linux Server release 6.7 (Santiago)
server05
Red Hat Enterprise Linux Server release 6.7 (Santiago)

### NETWORK
//--- dmesg | egrep NIC
server01
Netfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated NICs.
server02
Netfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated NICs.
server03
Netfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated NICs.
server04
Netfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated NICs.
server05
Netfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated NICs.

//--- egrep HOSTNAME /etc/sysconfig/network
server01
HOSTNAME=ip-172-31-25-141.eu-central-1.compute.internal
server02
HOSTNAME=ip-172-31-25-137.eu-central-1.compute.internal
server03
HOSTNAME=ip-172-31-25-138.eu-central-1.compute.internal
server04
HOSTNAME=ip-172-31-25-139.eu-central-1.compute.internal
server05
HOSTNAME=ip-172-31-25-140.eu-central-1.compute.internal

//--- cat /etc/sysconfig/network-scripts/ifcfg-eth* | egrep "^DEVICE|BOOTPROTO|ONBOOT|NETMASK|NETWORK|IPADDR|PEERDNS"
server01
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
PEERDNS="yes"
server02
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
PEERDNS="yes"
server03
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
PEERDNS="yes"
server04
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
PEERDNS="yes"
server05
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
PEERDNS="yes"

### DISK INFO
//--- lsblk
server01
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  10G  0 disk
└─xvda1 202:1    0  10G  0 part /
xvdb    202:16   0  40G  0 disk
└─xvdb1 202:17   0  40G  0 part /data2
xvdc    202:32   0  40G  0 disk
└─xvdc1 202:33   0  40G  0 part /data1
server02
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  10G  0 disk
└─xvda1 202:1    0  10G  0 part /
xvdb    202:16   0  40G  0 disk
└─xvdb1 202:17   0  40G  0 part /data1
xvdc    202:32   0  40G  0 disk
└─xvdc1 202:33   0  40G  0 part /data2
server03
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  10G  0 disk
└─xvda1 202:1    0  10G  0 part /
xvdb    202:16   0  40G  0 disk
└─xvdb1 202:17   0  40G  0 part /data1
xvdc    202:32   0  40G  0 disk
└─xvdc1 202:33   0  40G  0 part /data2
server04
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  10G  0 disk
└─xvda1 202:1    0  10G  0 part /
xvdb    202:16   0  40G  0 disk
└─xvdb1 202:17   0  40G  0 part /data1
xvdc    202:32   0  40G  0 disk
└─xvdc1 202:33   0  40G  0 part /data2
server05
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  10G  0 disk
└─xvda1 202:1    0  10G  0 part /
xvdb    202:16   0  40G  0 disk
└─xvdb1 202:17   0  40G  0 part /data1
xvdc    202:32   0  40G  0 disk
└─xvdc1 202:33   0  40G  0 part /data2

//--- egrep "^/dev/*" /proc/mounts
server01
/dev/xvda1 / ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdb1 /data2 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdc1 /data1 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
server02
/dev/xvda1 / ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdb1 /data1 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdc1 /data2 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
server03
/dev/xvda1 / ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdb1 /data1 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdc1 /data2 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
server04
/dev/xvda1 / ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdb1 /data1 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdc1 /data2 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
server05
/dev/xvda1 / ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdb1 /data1 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0
/dev/xvdc1 /data2 ext4 rw,seclabel,relatime,barrier=1,data=ordered 0 0

//--- df -h
server01
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  2,1G  7,2G  23% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb1       40G   48M   38G   1% /data2
/dev/xvdc1       40G   48M   38G   1% /data1
server02
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  2,1G  7,2G  23% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb1       40G   48M   38G   1% /data1
/dev/xvdc1       40G   48M   38G   1% /data2
server03
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  2,1G  7,2G  23% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb1       40G   48M   38G   1% /data1
/dev/xvdc1       40G   48M   38G   1% /data2
server04
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  2,1G  7,2G  23% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb1       40G   48M   38G   1% /data1
/dev/xvdc1       40G   48M   38G   1% /data2
server05
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  2,1G  7,2G  23% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb1       40G   48M   38G   1% /data1
/dev/xvdc1       40G   48M   38G   1% /data2

### CPU INFO
//--- nproc
server01
4
server02
4
server03
4
server04
4
server05
4

//--- egrep "^model name\s+:" /proc/cpuinfo
server01
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
server02
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
server03
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
server04
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
server05
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
model name	: Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz

### MEM INFO
//--- egrep "^MemTotal|SwapTotal|HugePages_Total" /proc/meminfo
server01
MemTotal:       15297616 kB
SwapTotal:             0 kB
HugePages_Total:       0
server02
MemTotal:       15297616 kB
SwapTotal:             0 kB
HugePages_Total:       0
server03
MemTotal:       15297616 kB
SwapTotal:             0 kB
HugePages_Total:       0
server04
MemTotal:       15297616 kB
SwapTotal:             0 kB
HugePages_Total:       0
server05
MemTotal:       15297616 kB
SwapTotal:             0 kB
HugePages_Total:       0

### SELINUX CHECK
//--- egrep "^SELINUX" /etc/sysconfig/selinux
server01
SELINUX=enforcing
SELINUXTYPE=targeted
server02
SELINUX=enforcing
SELINUXTYPE=targeted
server03
SELINUX=enforcing
SELINUXTYPE=targeted
server04
SELINUX=enforcing
SELINUXTYPE=targeted
server05
SELINUX=enforcing
SELINUXTYPE=targeted

### SSHD SERVICE
//--- chkconfig --list sshd
server01
sshd           	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server02
sshd           	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server03
sshd           	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server04
sshd           	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server05
sshd           	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado

### USER LIMITS
//--- egrep "^[^# ].+" /etc/security/limits.conf
server01
server02
server03
server04
server05

### NTP SERVICE
//--- service ntpd status
server01
ntpd (pid  2440) is running...
server02
ntpd (pid  23435) is running...
server03
ntpd (pid  2445) is running...
server04
ntpd (pid  2400) is running...
server05
ntpd (pid  2418) is running...

//--- chkconfig --list ntpd
server01
ntpd           	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server02
ntpd           	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server03
ntpd           	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server04
ntpd           	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server05
ntpd           	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado

//--- date
server01
lun nov 14 11:48:42 EST 2016
server02
lun nov 14 11:48:43 EST 2016
server03
lun nov 14 11:48:43 EST 2016
server04
lun nov 14 11:48:43 EST 2016
server05
lun nov 14 11:48:44 EST 2016

//--- ntpq -p
server01
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+spacys.de       131.188.3.222    2 u   46   64  377    5.498  -16.717  18.000
+jitter.tickadj. 127.67.113.92    2 u   29   64  377  176.275   -6.943  13.369
-ntp1.m-online.n 212.18.1.106     2 u   46   64  377    7.934    8.555  14.646
*h1939797.strato 130.149.17.21    2 u   24   64  377   15.577   -9.387   7.542
server02
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+2.202.196.104.a 128.138.141.172  2 u   51   64  377   99.311  -30.923  21.195
+a03.alphasrv.ne 192.53.103.104   2 u   43   64  377    5.572  -22.381  14.052
-ntp.wdc1.us.lea 199.102.46.72    2 u   33   64  377  103.802   11.462  12.025
*muenchen.klaus- 131.211.8.244    2 u   37   64  377    7.581   -5.809  12.528
server03
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+ns3.customer-re 192.53.103.104   2 u   31  128  377   26.512   -3.779   6.720
+www.mistersixt. 78.47.234.59     3 u   34  128  377    5.689  -11.491  10.143
*trillian.jollyb 131.188.3.222    2 u   87  128  377    4.356    3.572  13.257
+213.95.200.109  129.69.1.153     2 u   40  128  377    4.454  -12.298   9.035
server04
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*x.ns.gin.ntt.ne 249.224.99.213   2 u   41   64  377    0.831   -3.787   4.959
+chl.la          127.67.113.92    2 u   44   64  377  167.934   -6.792   6.680
-uhrwerk.wertarb 131.188.3.222    2 u   30   64  377    5.798    2.767  13.471
+panel1.web2.clu 37.120.191.245   3 u   41   64  377   11.796   -5.305  10.735
server05
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
-re.uni-paderbor .DCF.            1 u   35   64  377   14.693   -6.842   5.600
+repos.lax-noc.c 127.67.113.92    2 u   47   64  377  148.148   -0.192   4.141
*stratum2-4.NTP. 129.70.130.70    2 u   43  128  377   15.607   -0.228   2.694
+213.95.200.109  129.69.1.153     2 u   41   64  377    4.400   -5.025   3.528

## FIREWALL SERVICE
//--- service iptables status
server01
iptables: Firewall is not running.
server02
iptables: Firewall is not running.
server03
iptables: Firewall is not running.
server04
iptables: Firewall is not running.
server05
iptables: Firewall is not running.

//--- chkconfig --list iptables
server01
iptables       	0:desactivado	1:desactivado	2:desactivado	3:desactivado	4:desactivado	5:desactivado	6:desactivado
server02
iptables       	0:desactivado	1:desactivado	2:desactivado	3:desactivado	4:desactivado	5:desactivado	6:desactivado
server03
iptables       	0:desactivado	1:desactivado	2:desactivado	3:desactivado	4:desactivado	5:desactivado	6:desactivado
server04
iptables       	0:desactivado	1:desactivado	2:desactivado	3:desactivado	4:desactivado	5:desactivado	6:desactivado
server05
iptables       	0:desactivado	1:desactivado	2:desactivado	3:desactivado	4:desactivado	5:desactivado	6:desactivado

//--- service ip6tables status
server01
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

server02
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

server03
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

server04
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

server05
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
server01
ip6tables      	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server02
ip6tables      	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server03
ip6tables      	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server04
ip6tables      	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado
server05
ip6tables      	0:desactivado	1:desactivado	2:activo	3:activo	4:activo	5:activo	6:desactivado

### NSSWITCH & HOST.CONF
//--- egrep "^hosts:" /etc/nsswitch.conf
server01
hosts:      files dns
server02
hosts:      files dns
server03
hosts:      files dns
server04
hosts:      files dns
server05
hosts:      files dns

//--- cat /etc/host.conf
server01
multi on
server02
multi on
server03
multi on
server04
multi on
server05
multi on

//--- getent hosts
server01
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.25.141   server01
172.31.25.137   server02
172.31.25.138   server03
172.31.25.139   server04
172.31.25.140   server05
server02
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.25.141   server01
172.31.25.137   server02
172.31.25.138   server03
172.31.25.139   server04
172.31.25.140   server05
server03
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.25.141   server01
172.31.25.137   server02
172.31.25.138   server03
172.31.25.139   server04
172.31.25.140   server05
server04
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.25.141   server01
172.31.25.137   server02
172.31.25.138   server03
172.31.25.139   server04
172.31.25.140   server05
server05
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.25.141   server01
172.31.25.137   server02
172.31.25.138   server03
172.31.25.139   server04
172.31.25.140   server05

### DNS CACHE
//--- service nscd status
server01
nscd (pid 2373) is running...
server02
nscd (pid 23325) is running...
server03
nscd (pid 2376) is running...
server04
nscd (pid 2332) is running...
server05
nscd (pid 2349) is running...

//--- chkconfig --list ncsd
server01
error al leer la información del servicio ncsd: No existe el fichero o el directorio
server02
error al leer la información del servicio ncsd: No existe el fichero o el directorio
server03
error al leer la información del servicio ncsd: No existe el fichero o el directorio
server04
error al leer la información del servicio ncsd: No existe el fichero o el directorio
server05
error al leer la información del servicio ncsd: No existe el fichero o el directorio

### SWAPPINESS
//--- cat /proc/sys/vm/swappiness
server01
1
server02
1
server03
1
server04
1
server05
1

### IPV4 TCP
//--- sysctl -a | egrep "net.ipv4.tcp_"
server01
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
net.ipv4.tcp_mem = 1431168	1908224	2862336
net.ipv4.tcp_wmem = 4096	16384	4194304
net.ipv4.tcp_rmem = 4096	87380	4194304
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
server02
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
net.ipv4.tcp_mem = 1431168	1908224	2862336
net.ipv4.tcp_wmem = 4096	16384	4194304
net.ipv4.tcp_rmem = 4096	87380	4194304
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
server03
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
net.ipv4.tcp_mem = 1431168	1908224	2862336
net.ipv4.tcp_wmem = 4096	16384	4194304
net.ipv4.tcp_rmem = 4096	87380	4194304
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
server04
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
net.ipv4.tcp_mem = 1431168	1908224	2862336
net.ipv4.tcp_wmem = 4096	16384	4194304
net.ipv4.tcp_rmem = 4096	87380	4194304
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
server05
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
net.ipv4.tcp_mem = 1431168	1908224	2862336
net.ipv4.tcp_wmem = 4096	16384	4194304
net.ipv4.tcp_rmem = 4096	87380	4194304
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