
```

mysql> show grants for amon;
+-----------------------------------------------------------------------------------------------------+
| Grants for amon@%                                                                                   |
+-----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'amon'@'%' IDENTIFIED BY PASSWORD '*B909FCBD6258F83F10A0A6D04F800EE6FD739D0C' |
| GRANT ALL PRIVILEGES ON `amon`.* TO 'amon'@'%'                                                      |
+-----------------------------------------------------------------------------------------------------+
2 rows in set (0,00 sec)

mysql> show grants for hive;
+-----------------------------------------------------------------------------------------------------+
| Grants for hive@%                                                                                   |
+-----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'hive'@'%' IDENTIFIED BY PASSWORD '*7ECC0F9EBE99E50097F84B27A7CBAABD055EE312' |
| GRANT ALL PRIVILEGES ON `metastore`.* TO 'hive'@'%'                                                 |
+-----------------------------------------------------------------------------------------------------+
2 rows in set (0,00 sec)

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
[ec2-user@ip-172-31-0-116 ~]$ hdfs dfs -ls /user
Found 8 items
drwxr-xr-x   - admin   admin               0 2016-11-18 05:44 /user/admin
drwxr-xr-x   - bavaria supergroup          0 2016-11-18 05:50 /user/bavaria
drwxr-xr-x   - hdfs    supergroup          0 2016-11-18 05:43 /user/hdfs
drwxrwxrwx   - mapred  hadoop              0 2016-11-18 05:39 /user/history
drwxrwxr-t   - hive    hive                0 2016-11-18 05:41 /user/hive
drwxrwxr-x   - hue     hue                 0 2016-11-18 05:41 /user/hue
drwxrwxr-x   - oozie   oozie               0 2016-11-18 05:42 /user/oozie
drwxr-xr-x   - saxony  supergroup          0 2016-11-18 05:46 /user/saxony
```

```
[ec2-user@ip-172-31-0-115 ~]$ curl -X GET -u admin:admin http://ip-172-31-0-115.eu-central-1.compute.internal:7180/api/v12/hosts
{
  "items" : [ {
    "hostId" : "i-a333001f",
    "ipAddress" : "172.31.0.113",
    "hostname" : "ip-172-31-0-113.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-0-115.eu-central-1.compute.internal:7180/cmf/hostRedirect/i-a333001f",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15664758784
  }, {
    "hostId" : "i-a033001c",
    "ipAddress" : "172.31.0.114",
    "hostname" : "ip-172-31-0-114.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-0-115.eu-central-1.compute.internal:7180/cmf/hostRedirect/i-a033001c",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15664758784
  }, {
    "hostId" : "i-a133001d",
    "ipAddress" : "172.31.0.115",
    "hostname" : "ip-172-31-0-115.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-0-115.eu-central-1.compute.internal:7180/cmf/hostRedirect/i-a133001d",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15664758784
  }, {
    "hostId" : "i-a633001a",
    "ipAddress" : "172.31.0.116",
    "hostname" : "ip-172-31-0-116.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-0-115.eu-central-1.compute.internal:7180/cmf/hostRedirect/i-a633001a",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15664758784
  }, {
    "hostId" : "i-a733001b",
    "ipAddress" : "172.31.0.117",
    "hostname" : "ip-172-31-0-117.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-0-115.eu-central-1.compute.internal:7180/cmf/hostRedirect/i-a733001b",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15664758784
  } ]
```