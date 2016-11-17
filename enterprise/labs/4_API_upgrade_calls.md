

# Report the latest available version of the API
```
http://172.31.25.141:7180/api/v12
```

# Report the CM version
```
curl -X GET -u rgaleanog:cloudera "http://172.31.25.141:7180/api/v12/cm/version"


[rgaleanog@ip-172-31-25-139 ~]$ curl -X GET -u rgaleanog:cloudera "http://172.31.25.141:7180/api/v12/cm/version"
{
  "version" : "5.8.3",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20161019-1014",
  "gitHash" : "518f0d6d44abc87bc392646e4369a20c8192b7cf",
  "snapshot" : false
```

# List all CM users
```
curl -X GET -u rgaleanog:cloudera "http://172.31.25.141:7180/api/v12/users"


[rgaleanog@ip-172-31-25-139 ~]$ curl -X GET -u rgaleanog:cloudera "http://172.31.25.141:7180/api/v12/users"
{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  }, {
    "name" : "rgaleanog",
    "roles" : [ "ROLE_ADMIN" ]
  } ]
```

# Report the database server in use by CM
```
curl -X GET -u rgaleanog:cloudera "http://172.31.25.141:7180/api/v12/cm/service"
```
