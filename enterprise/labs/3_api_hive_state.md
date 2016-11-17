

# Check status
```
[ec2-user@ip-172-31-25-141 ~]$ curl -X GET -u rgaleanog:cloudera "http://172.31.25.141:7180/api/v12/clusters/rgaleanog/services/hive/"
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-25-141.eu-central-1.compute.internal:7180/cmf/serviceRedirect/hive",
  "roleInstancesUrl" : "http://ip-172-31-25-141.eu-central-1.compute.internal:7180/cmf/serviceRedirect/hive/instances",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  } ],
  "configStalenessStatus" : "FRESH",
  "clientConfigStalenessStatus" : "FRESH",
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive",
  "entityStatus" : "GOOD_HEALTH"
```

# Stop Hive Server
```
[ec2-user@ip-172-31-25-141 ~]$ curl -X POST -u rgaleanog:cloudera "http://172.31.25.141:7180/api/v12/clusters/rgaleanog/services/hive/commands/stop"
{
  "id" : 590,
  "name" : "Stop",
  "startTime" : "2016-11-16T14:15:46.149Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
```

# Start Hive Server
```
[ec2-user@ip-172-31-25-141 ~]$ curl -X POST -u rgaleanog:cloudera "http://172.31.25.141:7180/api/v12/clusters/rgaleanog/services/hive/commands/start"
{
  "id" : 595,
  "name" : "Start",
  "startTime" : "2016-11-16T14:16:29.842Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
```