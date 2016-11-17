# Configure repository in all nodes

# Enable to use MySQL 5.5
```
[mysql55-community]
©ec2-user@ip-172-31-25-139 ~]$ cat  /etc/yum.repos.d/mysql-community.repo
name=MySQL 5.5 Community Server
baseurl=http://repo.mysql.com/yum/mysql-5.5-community/el/6/$basearch/
enabled=0
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
```

# Install mysql-server in two servers (Master & Slave)
## On master:
```
sudo yum install mysql mysql-server -y
```
## On slave:
```
sudo yum install mysql mysql-server -y
```


## Other nodes:
```
sudo yum install mysql
```

# Configure mysql-server on Master and Slave
## On Master: 
```
[ec2-user@ip-172-31-25-141 ~]$ cat /etc/my.cnf
# For advice on how to change settings please see
# http://dev.mysql.com/doc/refman/5.5/en/server-configuration-defaults.html

[mysqld]
#
# Remove leading # and set to the amount of RAM for the most important data
# cache in MySQL. Start at 70% of total RAM for dedicated server, else 10%.
# innodb_buffer_pool_size = 128M
#
# Remove leading # to turn on a very important data integrity option: logging
# changes to the binary log between backups.
log_bin=mysql-bin
server-id=1
key_buffer = 16M
key_buffer_size = 32M
max_allowed_packet = 32M
thread_stack = 256K
thread_cache_size = 64
query_cache_limit = 8M
query_cache_size = 64M
query_cache_type = 1
max_connections = 550
read_buffer_size = 2M
read_rnd_buffer_size = 16M
sort_buffer_size = 8M
join_buffer_size = 8M
# InnoDB settings
innodb_file_per_table = 1
innodb_flush_log_at_trx_commit  = 2
innodb_log_buffer_size = 64M
innodb_buffer_pool_size = 4G
innodb_thread_concurrency = 8
innodb_flush_method = O_DIRECT
innodb_log_file_size = 512M
#
# Remove leading # to set options mainly useful for reporting servers.
# The server defaults are faster for transactions and fast SELECTs.
# Adjust sizes as needed, experiment to find the optimal values.
# join_buffer_size = 128M
# sort_buffer_size = 2M
# read_rnd_buffer_size = 2M
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock

# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0

# Recommended in standard MySQL setup
#sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid
sql_mode=STRICT_ALL_TABLES
```

## On Slave: 
```
[ec2-user@ip-172-31-25-137 ~]$ cat /etc/my.cnf
# For advice on how to change settings please see
# http://dev.mysql.com/doc/refman/5.5/en/server-configuration-defaults.html

[mysqld]
#
# Remove leading # and set to the amount of RAM for the most important data
# cache in MySQL. Start at 70% of total RAM for dedicated server, else 10%.
# innodb_buffer_pool_size = 128M
#
# Remove leading # to turn on a very important data integrity option: logging
# changes to the binary log between backups.
log_bin=mysql-bin
server-id=2
key_buffer = 16M
key_buffer_size = 32M
max_allowed_packet = 32M
thread_stack = 256K
thread_cache_size = 64
query_cache_limit = 8M
query_cache_size = 64M
query_cache_type = 1
max_connections = 550
read_buffer_size = 2M
read_rnd_buffer_size = 16M
sort_buffer_size = 8M
join_buffer_size = 8M
# InnoDB settings
innodb_file_per_table = 1
innodb_flush_log_at_trx_commit  = 2
innodb_log_buffer_size = 64M
innodb_buffer_pool_size = 4G
innodb_thread_concurrency = 8
innodb_flush_method = O_DIRECT
innodb_log_file_size = 512M
#
# Remove leading # to set options mainly useful for reporting servers.
# The server defaults are faster for transactions and fast SELECTs.
# Adjust sizes as needed, experiment to find the optimal values.
# join_buffer_size = 128M
# sort_buffer_size = 2M
# read_rnd_buffer_size = 2M
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock

# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0

# Recommended in standard MySQL setup
#sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid
sql_mode=STRICT_ALL_TABLES
```
# Configure mysql on both servers:
Start the mysqld service.
Use /usr/bin/mysql_secure_installation to:
a. Set password protection for the server

b. Revoke permissions for anonymous users
c. Permit remote privileged login
d. Remove test databases
e. Refresh privileges in memory
f. Refreshes the mysqld service

# Configure Master/Slave behaviour:
```
On the master MySQL node, grant replication privileges for your replica node:
a. Log in with mysql -u ... -p 
b. Note the FQDN of your replica host.

c. mysql> GRANT REPLICATION SLAVE ON *.* TO 'repl'@'ip-172-31-25-137.eu-central-1.compute.internal' IDENTIFIED BY 'password';
NOTE: MySQL must be restart to work an this point.
d. mysql> SET GLOBAL binlog_format = 'ROW'; 
e. mysql> FLUSH TABLES WITH READ LOCK;
In a second terminal session, log into the MySQL master and show its status:
a. mysql> SHOW MASTER STATUS;
b. Make note of the file name and byte offset. The replica needs this info to sync to the master. mysqld-bin.000002 107
c. Logout of the second session; remove the lock on the first with mysql> UNLOCK TABLES;
Login to the replica server and configure a connection to the master:
mysql> CHANGE MASTER TO MASTER_HOST='ip-172-31-25-141.eu-central-1.compute.internal', MASTER_USER='repl', MASTER_PASSWORD='password', MASTER_LOG_FILE='mysqld-bin.000003', MASTER_LOG_POS=107;
Initiate slave operations on the replica
a. mysql> START SLAVE;
b. mysql> SHOW SLAVE STATUS \G
c. If successful, the Slave_IO_State field will read Waiting for master to send event
d. Once successful, capture this output and store it in installation/2_replica_working.md
e. Review your log (/var/log/mysqld.log) for errors. If stuck, consult with a colleague or instructor.
mysql> SHOW SLAVE STATUS \G;
```


# Check correct status
```
mysql> show slave status \G
*************************** 1. row ***************************
               Slave_IO_State: Waiting for master to send event
                  Master_Host: server01
                  Master_User: repl
                  Master_Port: 3306
                Connect_Retry: 60
              Master_Log_File: mysql-bin.000009
          Read_Master_Log_Pos: 41808576
               Relay_Log_File: mysqld-relay-bin.000014
                Relay_Log_Pos: 41808722
        Relay_Master_Log_File: mysql-bin.000009
             Slave_IO_Running: Yes
            Slave_SQL_Running: Yes
              Replicate_Do_DB:
          Replicate_Ignore_DB:
           Replicate_Do_Table:
       Replicate_Ignore_Table:
      Replicate_Wild_Do_Table:
  Replicate_Wild_Ignore_Table:
                   Last_Errno: 0
                   Last_Error:
                 Skip_Counter: 0
          Exec_Master_Log_Pos: 41808576
              Relay_Log_Space: 41808922
              Until_Condition: None
               Until_Log_File:
                Until_Log_Pos: 0
           Master_SSL_Allowed: No
           Master_SSL_CA_File:
           Master_SSL_CA_Path:
              Master_SSL_Cert:
            Master_SSL_Cipher:
               Master_SSL_Key:
        Seconds_Behind_Master: 0
Master_SSL_Verify_Server_Cert: No
                Last_IO_Errno: 0
                Last_IO_Error:
               Last_SQL_Errno: 0
               Last_SQL_Error:
  Replicate_Ignore_Server_Ids:
             Master_Server_Id: 1
1 row in set (0.00 sec)
```














