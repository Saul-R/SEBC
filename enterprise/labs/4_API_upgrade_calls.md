

# Report the latest available version of the API
```
[root@ip-172-31-25-141 ec2-user]# curl --insecure -X GET -u "rgaleanog:cloudera" "https://172.31.25.141:7183/api/version"
v14
```

# Report the CM version
```
curl --insecure -X GET -u rgaleanog:cloudera "https://172.31.25.141:7183/api/v14/cm/version"

[rgaleanog@ip-172-31-25-139 ~]$ curl --insecure -X GET -u rgaleanog:cloudera "https://172.31.25.141:7183/api/v14/cm/version"
{
  "version" : "5.9.0",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20161006-1801",
  "gitHash" : "898a5e032c080e18833dfc58180761f6ef2ea351",
  "snapshot" : false
}

```

# List all CM users
```
curl --insecure -X GET -u rgaleanog:cloudera "https://172.31.25.141:7183/api/v14/users"

[rgaleanog@ip-172-31-25-139 ~]$ curl --insecure -X GET -u rgaleanog:cloudera "https://172.31.25.141:7183/api/v14/users"
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
}

```

# Report the database server in use by CM
```
curl --insecure -X  GET -u rgaleanog:cloudera "https://172.31.25.141:7183/api/v14/cm/scmDbInfo"

[rgaleanog@ip-172-31-25-139 ~]$ curl --insecure -X  GET -u rgaleanog:cloudera "https://172.31.25.141:7183/api/v14/cm/scmDbInfo"
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
```
