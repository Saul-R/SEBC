


```
[root@ip-172-31-0-115 ec2-user]# tail -n 2 /var/log/cloudera-scm-server/cloudera-scm-server.log
2016-11-18 05:05:30,520 INFO WebServerImpl:org.mortbay.log: Started SelectChannelConnector@0.0.0.0:7180
2016-11-18 05:05:30,520 INFO WebServerImpl:com.cloudera.server.cmf.WebServerImpl: Started Jetty server.
```


```
mysql> grant all on scm.* TO 'scm'@'ip-172-31-0-115.eu-central-1.compute.internal' IDENTIFIED BY 'scm_pass';
Query OK, 0 rows affected (0,00 sec)

mysql> show grants for scm;
+----------------------------------------------------------------------------------------------------+
| Grants for scm@%                                                                                   |
+----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'scm'@'%' IDENTIFIED BY PASSWORD '*52FEE2327A0D95837BFA01DA3D8B434216D40E43' |
| GRANT ALL PRIVILEGES ON `scm`.* TO 'scm'@'%'                                                       |
+----------------------------------------------------------------------------------------------------+
2 rows in set (0,00 sec)
```

```
[root@ip-172-31-0-115 ec2-user]# sudo cat /etc/cloudera-scm-server/db.properties
# Copyright (c) 2012 Cloudera, Inc. All rights reserved.
#
# This file describes the database connection.
#

# The database type
# Currently 'mysql', 'postgresql' and 'oracle' are valid databases.
com.cloudera.cmf.db.type=mysql

# The database host
# If a non standard port is needed, use 'hostname:port'
com.cloudera.cmf.db.host=localhost

# The database name
com.cloudera.cmf.db.name=scm

# The database user
com.cloudera.cmf.db.user=scm

# The database user's password
com.cloudera.cmf.db.password=scm_pass
```

```
[root@ip-172-31-0-115 ec2-user]# /usr/share/cmf/schema/scm_prepare_database.sh -h ip-172-31-0-115.eu-central-1.compute.internal mysql scm scm scm_pass
JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.7.0_67-cloudera/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
2016-11-18 05:22:37,194 [main] INFO  com.cloudera.enterprise.dbutil.DbCommandExecutor  - Successfully connected to database.
All done, your SCM database is configured correctly!
[root@ip-172-31-0-115 ec2-user]# service cloudera-scm-server start
Starting cloudera-scm-server:                              [  OK  ]
```

