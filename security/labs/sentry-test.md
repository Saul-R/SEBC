


# Verify user privileges
```
[rgaleanog@ip-172-31-25-141 ~]$ beeline
Beeline version 1.1.0-cdh5.8.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG
scan complete in 2ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG
Enter username for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG: rgaleanog
Enter password for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20161117085050_1f46578c-92a2-439a-8da1-5fc2d4f06f25): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20161117085050_1f46578c-92a2-439a-8da1-5fc2d4f06f25); Time taken: 0.65 seconds
INFO  : Executing command(queryId=hive_20161117085050_1f46578c-92a2-439a-8da1-5fc2d4f06f25): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117085050_1f46578c-92a2-439a-8da1-5fc2d4f06f25); Time taken: 0.251 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (2.277 seconds)
0: jdbc:hive2://localhost:10000/default>
```


# Create a Sentry role with full authorization
```
CREATE ROLE sentry_admin;
GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
GRANT ROLE sentry_admin TO GROUP rgaleanog;
0: jdbc:hive2://localhost:10000/default> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20161117093131_586e1bf2-cb62-4d0c-945f-c82fd9ae25fb): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20161117093131_586e1bf2-cb62-4d0c-945f-c82fd9ae25fb); Time taken: 0.296 seconds
INFO  : Executing command(queryId=hive_20161117093131_586e1bf2-cb62-4d0c-945f-c82fd9ae25fb): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117093131_586e1bf2-cb62-4d0c-945f-c82fd9ae25fb); Time taken: 0.258 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.69 seconds)
```
# Create additional test users


```
kadmin.local:  [ec2-user@ip-172-31-25-141 ~]$ sudo kadmin.local
Authenticating as principal rgaleanog/admin@RGALEANOG.FNG with password.
kadmin.local:  add_principal george
WARNING: no policy specified for george@RGALEANOG.FNG; defaulting to no policy
Enter password for principal "george@RGALEANOG.FNG":
Re-enter password for principal "george@RGALEANOG.FNG":
Principal "george@RGALEANOG.FNG" created.
kadmin.local:  add_principal ferdinand
WARNING: no policy specified for ferdinand@RGALEANOG.FNG; defaulting to no policy
Enter password for principal "ferdinand@RGALEANOG.FNG":
Re-enter password for principal "ferdinand@RGALEANOG.FNG":
Principal "ferdinand@RGALEANOG.FNG" created.
kadmin.local:  exit
```


# Create test roles


```
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG
scan complete in 3ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG
Enter username for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG: rgaleanog
Enter password for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20161117093838_396e0dc0-458e-4d89-8137-44b7890aa44a): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20161117093838_396e0dc0-458e-4d89-8137-44b7890aa44a); Time taken: 0.095 seconds
INFO  : Executing command(queryId=hive_20161117093838_396e0dc0-458e-4d89-8137-44b7890aa44a): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117093838_396e0dc0-458e-4d89-8137-44b7890aa44a); Time taken: 0.056 seconds
INFO  : OK
No rows affected (0,211 seconds)
0: jdbc:hive2://localhost:10000/default> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20161117093838_0b2adbd3-d590-4741-b0a7-a9ea70d02a1b): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20161117093838_0b2adbd3-d590-4741-b0a7-a9ea70d02a1b); Time taken: 0.099 seconds
INFO  : Executing command(queryId=hive_20161117093838_0b2adbd3-d590-4741-b0a7-a9ea70d02a1b): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117093838_0b2adbd3-d590-4741-b0a7-a9ea70d02a1b); Time taken: 0.031 seconds
INFO  : OK
No rows affected (0,14 seconds)
0: jdbc:hive2://localhost:10000/default>
```

# Grant read privilege for all tables to reads

```
0: jdbc:hive2://localhost:10000/default> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20161117093939_ff4c9d8c-3a38-4f46-b0f4-70e5c189494d): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20161117093939_ff4c9d8c-3a38-4f46-b0f4-70e5c189494d); Time taken: 0.064 seconds
INFO  : Executing command(queryId=hive_20161117093939_ff4c9d8c-3a38-4f46-b0f4-70e5c189494d): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117093939_ff4c9d8c-3a38-4f46-b0f4-70e5c189494d); Time taken: 0.043 seconds
INFO  : OK
No rows affected (0,114 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20161117093939_b2f3bf64-fa54-4813-a08f-59839f1f4934): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20161117093939_b2f3bf64-fa54-4813-a08f-59839f1f4934); Time taken: 0.055 seconds
INFO  : Executing command(queryId=hive_20161117093939_b2f3bf64-fa54-4813-a08f-59839f1f4934): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117093939_b2f3bf64-fa54-4813-a08f-59839f1f4934); Time taken: 0.071 seconds
INFO  : OK
No rows affected (0,134 seconds)
```

# Grant read privilege for default.sample07 only to 'writes':
```
0: jdbc:hive2://localhost:10000/default> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20161117093939_d9b19a30-3e62-42b5-9e5b-7ead7577e9c3): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20161117093939_d9b19a30-3e62-42b5-9e5b-7ead7577e9c3); Time taken: 0.058 seconds
INFO  : Executing command(queryId=hive_20161117093939_d9b19a30-3e62-42b5-9e5b-7ead7577e9c3): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117093939_d9b19a30-3e62-42b5-9e5b-7ead7577e9c3); Time taken: 0.088 seconds
INFO  : OK
No rows affected (0,155 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20161117093939_c585ed5a-2691-4005-a528-c81e15c67a8f): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20161117093939_c585ed5a-2691-4005-a528-c81e15c67a8f); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20161117093939_c585ed5a-2691-4005-a528-c81e15c67a8f): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117093939_c585ed5a-2691-4005-a528-c81e15c67a8f); Time taken: 0.039 seconds
INFO  : OK
No rows affected (0,102 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20161117093939_1a67e1f1-5a1a-4c44-8a48-4c7adc334e5c): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20161117093939_1a67e1f1-5a1a-4c44-8a48-4c7adc334e5c); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20161117093939_1a67e1f1-5a1a-4c44-8a48-4c7adc334e5c): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117093939_1a67e1f1-5a1a-4c44-8a48-4c7adc334e5c); Time taken: 0.024 seconds
INFO  : OK
No rows affected (0,084 seconds)
```

# kinit as george, then login to beeline
```
[ec2-user@ip-172-31-25-141 ~]$ kinit george
Password for george@RGALEANOG.FNG:
[ec2-user@ip-172-31-25-141 ~]$ beeline
Beeline version 1.1.0-cdh5.8.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG
scan complete in 2ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG
Enter username for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG: george
Enter password for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG: ******
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20161117094141_ed5374d8-60e4-4f42-ac9c-b49b079c26a8): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20161117094141_ed5374d8-60e4-4f42-ac9c-b49b079c26a8); Time taken: 0.065 seconds
INFO  : Executing command(queryId=hive_20161117094141_ed5374d8-60e4-4f42-ac9c-b49b079c26a8): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117094141_ed5374d8-60e4-4f42-ac9c-b49b079c26a8); Time taken: 0.137 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0,332 seconds)
```

# kinit as ferdinand, then login to beeline
```
[ec2-user@ip-172-31-25-141 ~]$ kinit ferdinand
Password for ferdinand@RGALEANOG.FNG:
[ec2-user@ip-172-31-25-141 ~]$ beeline
Beeline version 1.1.0-cdh5.8.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG
scan complete in 2ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG
Enter username for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG: ferdinand
Enter password for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-25-141@RGALEANOG.FNG: *********
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20161117094242_c67e4908-0c12-4c02-bd83-c12c420f531c): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20161117094242_c67e4908-0c12-4c02-bd83-c12c420f531c); Time taken: 0.065 seconds
INFO  : Executing command(queryId=hive_20161117094242_c67e4908-0c12-4c02-bd83-c12c420f531c): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20161117094242_c67e4908-0c12-4c02-bd83-c12c420f531c); Time taken: 0.115 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0,3 seconds)

```