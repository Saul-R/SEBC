
- Region:
```
- region: Frankfurt: eu-central-1b
- AIM: ami-97698cf8
- OS: Red Hat Enterprise Linux Server release 6.7 (Santiago)
```



- Disk space:
```
[ec2-user@ip-172-31-9-239 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      5,8G  1,7G  3,9G  31% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdc        37G  177M   35G   1% /mnt
/dev/xvdb1       14G   36M   13G   1% /var/lib
/dev/xvdb2       16G   45M   15G   1% /var/log
/dev/xvdc        37G  177M   35G   1% /data1
/dev/xvdd        37G  177M   35G   1% /data2

[ec2-user@ip-172-31-9-240 /]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      5,8G  1,7G  3,9G  31% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdb1       14G   36M   13G   1% /var/lib
/dev/xvdb2       16G   45M   15G   1% /var/log
/dev/xvdc        37G  177M   35G   1% /data1
/dev/xvdd        37G  177M   35G   1% /data2

[ec2-user@ip-172-31-9-241 var]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      5,8G  1,7G  3,9G  31% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdc        37G  177M   35G   1% /mnt
/dev/xvdb1       14G   36M   13G   1% /var/lib
/dev/xvdb2       16G   45M   15G   1% /var/log
/dev/xvdc        37G  177M   35G   1% /data1
/dev/xvdd        37G  177M   35G   1% /data2

[ec2-user@ip-172-31-9-243 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      5,8G  1,7G  3,9G  31% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdc        37G  177M   35G   1% /mnt
/dev/xvdb1       14G   36M   13G   1% /var/lib
/dev/xvdb2       16G   45M   15G   1% /var/log
/dev/xvdc        37G  177M   35G   1% /data1
/dev/xvdd        37G  177M   35G   1% /data2

[ec2-user@ip-172-31-9-242 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      5,8G  1,7G  3,9G  31% /
tmpfs           7,3G     0  7,3G   0% /dev/shm
/dev/xvdc        37G  177M   35G   1% /mnt
/dev/xvdb1       14G   36M   13G   1% /var/lib
/dev/xvdb2       16G   45M   15G   1% /var/log
/dev/xvdc        37G  177M   35G   1% /data1
/dev/xvdd        37G  177M   35G   1% /data2
```



- List repositories:
```
[ec2-user@ip-172-31-9-241 var]$ yum repolist enabled
Complementos cargados:amazon-id, rhui-lb, security
Repo rhui-REGION-client-config-server-6 forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-client-config-server-6 forced skip_if_unavailable=True due to: /etc/pki/rhui/product/rhui-client-config-server-6.crt
Repo rhui-REGION-client-config-server-6 forced skip_if_unavailable=True due to: /etc/pki/rhui/rhui-client-config-server-6.key
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content-rhel6.crt
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/content-rhel6.key
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content-rhel6.crt
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/content-rhel6.key
Could not contact CDS load balancer rhui2-cds01.eu-central-1.aws.ce.redhat.com, trying others.


Could not contact any CDS load balancers: rhui2-cds01.eu-central-1.aws.ce.redhat.com, rhui2-cds02.eu-central-1.aws.ce.redhat.com.
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
