
```
curl -X GET -u rgaleanog:cloudera "http://172.31.25.141:7180/api/v12/cm/version"
```

[ec2-user@ip-172-31-25-141 ~]$ curl -X GET -u rgaleanog:cloudera "http://172.31.25.141:7180/api/v12/cm/version"
{
  "version" : "5.8.2",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20160916-1426",
  "gitHash" : "d23c620f3a3bbd85d8511d6ebba49beaaab14b75",
  "snapshot" : false