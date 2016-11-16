# What is ubertask optimization?
Ubertask is to submit small jobs that you want to run locally and not to distribute it to the cluster.

# Where in CM is the Kerberos Security Realm value displayed?
Administration -> Settings -> Kerberos (Category)-> Kerberos Security Realm

# Which CDH service(s) host a property for enabling Kerberos authentication?
Cloudera Manager, Cloudera Navigator adn HUE.

# How do you upgrade the CM agents?
CM Agents are upgraded when cloudera manager is upgraded.

# Give the tsquery statement used to chart Hue's CPU utilization?
```
SELECT total_cpu_system_rate_across_hue_servers + total_cpu_user_rate_across_hue_servers 
```

# Name all the roles that make up the Hive service
HiveServer2, HiveMetastore,WebCat Server, Gateway

# What steps must be completed before integrating Cloudera Manager with Kerberos?

Before integrating with Kerberos, Set up a working KDC.

These are the steps to follow:
- The KDC should be configured to have non-zero ticket lifetime and renewal lifetime. 
- OpenLdap client libraries should be installed on the Cloudera Manager Server host if you want to use Active Directory.
- Kerberos client libraries should be installed on ALL hosts. 
- Create a principal account for Cloudera Manager that has permissions to create other accounts in the KDC.
