
# Create directory
```
sudo su hdfs
hdfs dfs -mkdir /precious
```

# Put data into directory
```
wget https://github.com/rgaleanog/SEBC/archive/master.zip
hdfs dfs -put master.zip /precious
hdfs dfs -ls /precious
```

# Enable snapshots
```
hdfs dfsadmin -allowSnapshot /precious
```


# Create snapshots
```
hdfs dfs -createSnapshot /precious sebc-hdfs-test
```
# Delete the directory
```
hdfs dfs -rm -r /precious/
```

# Delete the ZIP file
```
hdfs dfs -rm /precious/master.zip
```

# Restore the deleted file
```
hdfs dfs -cp  hdfs:///precious/.snapshot/sebc-hdfs-test/master.zip hdfs:///precious/.
```

# Results:
```
[hdfs@ip-172-31-25-139 ~]$ wget https://github.com/rgaleanog/SEBC/archive/master.zip
--2016-11-16 03:11:35--  https://github.com/rgaleanog/SEBC/archive/master.zip
Resolving github.com... 192.30.253.112, 192.30.253.113
Connecting to github.com|192.30.253.112|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://codeload.github.com/rgaleanog/SEBC/zip/master [following]
--2016-11-16 03:11:35--  https://codeload.github.com/rgaleanog/SEBC/zip/master
Resolving codeload.github.com... 192.30.253.121, 192.30.253.120
Connecting to codeload.github.com|192.30.253.121|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 615610 (601K) [application/zip]
Saving to: “master.zip”

100%[===========================================================================================================>] 615,610      818K/s   in 0.7s    

2016-11-16 03:11:36 (818 KB/s) - “master.zip” saved [615610/615610]

[hdfs@ip-172-31-25-139 ~]$ hdfs dfs -put master.zip /precious
[hdfs@ip-172-31-25-139 ~]$ hdfs dfs -ls /precious
Found 1 items
-rw-r--r--   3 hdfs supergroup     615610 2016-11-16 03:11 /precious/master.zip
[hdfs@ip-172-31-25-139 ~]$ hdfs dfsadmin -allowSnapshot /precious
Allowing snaphot on /precious succeeded
[hdfs@ip-172-31-25-139 ~]$ hdfs dfs -createSnapshot /precious sebc-hdfs-test
Created snapshot /precious/.snapshot/sebc-hdfs-test

[hdfs@ip-172-31-25-139 ~]$ hdfs dfs -rm -r /precious/
rm: Failed to move to trash: hdfs://ip-172-31-25-141.eu-central-1.compute.internal:8020/precious: The directory /precious cannot be deleted since /precious is snapshottable and already has snapshots
[hdfs@ip-172-31-25-139 ~]$ hdfs dfs -rm /precious/master.zip
16/11/16 03:46:09 INFO fs.TrashPolicyDefault: Moved: 'hdfs://ip-172-31-25-141.eu-central-1.compute.internal:8020/precious/master.zip' to trash at: hdfs://ip-172-31-25-141.eu-central-1.compute.internal:8020/user/hdfs/.Trash/Current/precious/master.zip1479285969131
[hdfs@ip-172-31-25-139 ~]$ hdfs dfs -ls /precious
[hdfs@ip-172-31-25-139 ~]$ hdfs dfs -ls /precious/.snapshot/sebc-hdfs-test
Found 1 items
-rw-r--r--   3 hdfs supergroup     615610 2016-11-16 03:11 /precious/.snapshot/sebc-hdfs-test/master.zip
[hdfs@ip-172-31-25-139 ~]$ hdfs dfs -cp  hdfs:///precious/.snapshot/sebc-hdfs-test/master.zip hdfs:///precious/.
[hdfs@ip-172-31-25-139 ~]$ hdfs dfs -ls /precious
Found 1 items
-rw-r--r--   3 hdfs supergroup     615610 2016-11-16 03:49 /precious/master.zip

```