```
[rgaleanog@ip-172-31-25-139 ~]$ hadoop distcp hftp://ip-172-31-25-141.eu-central-1.compute.internal:50070/user/rgaleanog/teragenDiscp hdfs://ec2-52-3-88-79.compute-1.amazonaws.com/tmp
16/11/16 12:20:30 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hftp://ip-172-31-25-141.eu-central-1.compute.internal:50070/user/rgaleanog/teragenDiscp], targetPath=hdfs://ec2-52-3-88-79.compute-1.amazonaws.com/tmp, targetPathExists=true, filtersFile='null'}
16/11/16 12:20:31 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-25-137.eu-central-1.compute.internal/172.31.25.137:8032
16/11/16 12:20:32 INFO tools.SimpleCopyListing: Paths (files+dirs) cnt = 3; dirCnt = 1
16/11/16 12:20:32 INFO tools.SimpleCopyListing: Build file listing completed.
16/11/16 12:20:32 INFO Configuration.deprecation: io.sort.mb is deprecated. Instead, use mapreduce.task.io.sort.mb
16/11/16 12:20:32 INFO Configuration.deprecation: io.sort.factor is deprecated. Instead, use mapreduce.task.io.sort.factor
16/11/16 12:20:32 INFO tools.DistCp: Number of paths in the copy list: 3
16/11/16 12:20:32 INFO tools.DistCp: Number of paths in the copy list: 3
16/11/16 12:20:32 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-25-137.eu-central-1.compute.internal/172.31.25.137:8032
16/11/16 12:20:32 INFO mapreduce.JobSubmitter: number of splits:2
16/11/16 12:20:32 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1479315912258_0001
16/11/16 12:20:33 INFO impl.YarnClientImpl: Submitted application application_1479315912258_0001
16/11/16 12:20:33 INFO mapreduce.Job: The url to track the job: http://ip-172-31-25-137.eu-central-1.compute.internal:8088/proxy/application_1479315912258_0001/
16/11/16 12:20:33 INFO tools.DistCp: DistCp job-id: job_1479315912258_0001
16/11/16 12:20:33 INFO mapreduce.Job: Running job: job_1479315912258_0001
16/11/16 12:20:40 INFO mapreduce.Job: Job job_1479315912258_0001 running in uber mode : false
16/11/16 12:20:40 INFO mapreduce.Job:  map 0% reduce 0%
16/11/16 12:20:47 INFO mapreduce.Job:  map 50% reduce 0%
16/11/16 12:20:52 INFO mapreduce.Job:  map 100% reduce 0%
16/11/16 12:27:26 INFO mapreduce.Job: Job job_1479315912258_0001 completed successfully
16/11/16 12:27:26 INFO mapreduce.Job: Counters: 40
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=254390
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=1298
		HDFS: Number of bytes written=500000103
		HDFS: Number of read operations=27
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=7
		HFTP: Number of bytes read=0
		HFTP: Number of bytes written=0
		HFTP: Number of read operations=0
		HFTP: Number of large read operations=0
		HFTP: Number of write operations=0
	Job Counters 
		Launched map tasks=2
		Other local map tasks=2
		Total time spent by all maps in occupied slots (ms)=408010
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=408010
		Total vcore-seconds taken by all map tasks=408010
		Total megabyte-seconds taken by all map tasks=417802240
	Map-Reduce Framework
		Map input records=3
		Map output records=1
		Input split bytes=240
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=110
		CPU time spent (ms)=12280
		Physical memory (bytes) snapshot=432828416
		Virtual memory (bytes) snapshot=3141132288
		Total committed heap usage (bytes)=493355008
	File Input Format Counters 
		Bytes Read=1058
	File Output Format Counters 
		Bytes Written=103
	org.apache.hadoop.tools.mapred.CopyMapper$Counter
		BYTESCOPIED=500000000
		BYTESEXPECTED=500000000
		BYTESSKIPPED=0
		COPY=2
		SKIP=1
```


```
[rgaleanog@ip-172-31-25-139 ~]$ hdfs fsck /user/rgaleanog/teragenDiscp -files -blocks -files -blocks
Connecting to namenode via http://ip-172-31-25-141.eu-central-1.compute.internal:50070
FSCK started by rgaleanog (auth:SIMPLE) from /172.31.25.139 for path /user/rgaleanog/teragenDiscp at Wed Nov 16 12:46:37 EST 2016
/user/rgaleanog/teragenDiscp <dir>
/user/rgaleanog/teragenDiscp/_SUCCESS 0 bytes, 0 block(s):  OK

/user/rgaleanog/teragenDiscp/part-m-00000 500000000 bytes, 4 block(s):  OK
0. BP-668357531-172.31.25.141-1479233391092:blk_1073745656_4832 len=134217728 Live_repl=3
1. BP-668357531-172.31.25.141-1479233391092:blk_1073745657_4833 len=134217728 Live_repl=3
2. BP-668357531-172.31.25.141-1479233391092:blk_1073745658_4834 len=134217728 Live_repl=3
3. BP-668357531-172.31.25.141-1479233391092:blk_1073745659_4835 len=97346816 Live_repl=3

Status: HEALTHY
 Total size:	500000000 B
 Total dirs:	1
 Total files:	2
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 125000000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Wed Nov 16 12:46:37 EST 2016 in 1 milliseconds


The filesystem under path '/user/rgaleanog/teragenDiscp' is HEALTHY

```


