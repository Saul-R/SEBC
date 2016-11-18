
- Region:
```
- region: Frankfurt: eu-central-1b
- AIM: ami-8e96ac93
- OS: Red Hat Enterprise Linux Server release 6.7 (Santiago)
```


- Disk space:
```
[ec2-user@ip-172-31-0-113 /]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  2,0G  7,4G  21% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb        37G  177M   35G   1% /opt
/dev/xvdd1       14G   36M   13G   1% /var/log
/dev/xvdd2       16G   46M   15G   1% /var/lib

[ec2-user@ip-172-31-0-114 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  2,0G  7,4G  21% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdd1       14G   36M   13G   1% /var/log
/dev/xvdb        37G  177M   35G   1% /opt
/dev/xvdd2       16G   46M   15G   1% /var/lib

[ec2-user@ip-172-31-0-115 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  2,0G  7,4G  21% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdd1       14G   36M   13G   1% /var/log
/dev/xvdb        37G  177M   35G   1% /opt
/dev/xvdd2       16G   45M   15G   1% /var/lib

[ec2-user@ip-172-31-0-116 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  1,7G  7,6G  19% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdd1       14G   36M   13G   1% /var/log
/dev/xvdb        37G  177M   35G   1% /opt
/dev/xvdd2       16G   45M   15G   1% /var/lib

[ec2-user@ip-172-31-0-117 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      9,8G  2,0G  7,4G  21% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdd1       14G   36M   13G   1% /var/log
/dev/xvdb        37G  177M   35G   1% /opt
/dev/xvdd2       16G   46M   15G   1% /var/lib
```



- List repositories:
```
[ec2-user@ip-172-31-0-113 var]$ sudo yum repolist
Complementos cargados:amazon-id, rhui-lb, security
rhui-REGION-client-config-server-6                                                                                                                        | 2.9 kB     00:00
rhui-REGION-client-config-server-6/primary_db                                                                                                             | 4.0 kB     00:00
rhui-REGION-rhel-server-releases                                                                                                                          | 3.5 kB     00:00
rhui-REGION-rhel-server-releases/primary_db                                                                                                               |  51 MB     00:00
rhui-REGION-rhel-server-rh-common                                                                                                                         | 3.8 kB     00:00
rhui-REGION-rhel-server-rh-common/primary_db                                                                                                              |  65 kB     00:00
id del repositorio                                                     nombre del repositorio                                                                              estado
rhui-REGION-client-config-server-6                                     Red Hat Update Infrastructure 2.0 Client Configuration Server 6                                          3
rhui-REGION-rhel-server-releases                                       Red Hat Enterprise Linux Server 6 (RPMs)                                                            18.369
rhui-REGION-rhel-server-rh-common                                      Red Hat Enterprise Linux Server 6 RH Common (RPMs)                                                     129
repolist: 18.501
```

- Create users:
```
[ec2-user@ip-172-31-9-239 ~]$ tail -n 2 /etc/passwd
bavaria:x:2700:2700::/home/bavaria:/bin/bash
saxony:x:2800:2800::/home/saxony:/bin/bash

[ec2-user@ip-172-31-9-239 ~]$ tail -n 2 /etc/group
democratic:x:2801:saxony
social:x:2802:bavaria

```