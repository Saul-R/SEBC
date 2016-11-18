
# On every node: ()
```
[ec2-user@ip-172-31-25-141 ~]$ cat /etc/yum.repos.d/mysql-community.repo
[mysql-connectors-community]
name=MySQL Connectors Community
baseurl=http://repo.mysql.com/yum/mysql-connectors-community/el/6/$basearch/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql

[mysql-tools-community]
name=MySQL Tools Community
baseurl=http://repo.mysql.com/yum/mysql-tools-community/el/6/$basearch/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql


# Enable to use MySQL 5.6
[mysql56-community]
name=MySQL 5.6 Community Server
baseurl=http://repo.mysql.com/yum/mysql-5.6-community/el/6/$basearch/
enabled=0
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
```


# Mysql Version:
```
[ec2-user@ip-172-31-0-115 ~]$ mysql --version
mysql  Ver 14.14 Distrib 5.6.34, for Linux (x86_64) using  EditLine wrapper
```

# Databases
```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hue                |
| metastore          |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| sentry             |
+--------------------+
8 rows in set (0,00 sec)
```



SHOW GRANTS FOR 'hue'@'localhost'




