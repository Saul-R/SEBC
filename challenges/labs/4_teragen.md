
```
[bavaria@ip-172-31-0-115 ~]$ time yarn jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Ddfs.block.size=16777216  51200000 tgen512m
16/11/18 05:58:22 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-0-115.eu-central-1.compute.internal/172.31.0.115:8032
16/11/18 05:58:23 INFO terasort.TeraSort: Generating 51200000 using 2
16/11/18 05:58:23 INFO mapreduce.JobSubmitter: number of splits:2
16/11/18 05:58:23 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
16/11/18 05:58:23 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1479465617115_0003
16/11/18 05:58:23 INFO impl.YarnClientImpl: Submitted application application_1479465617115_0003
16/11/18 05:58:23 INFO mapreduce.Job: The url to track the job: http://ip-172-31-0-115.eu-central-1.compute.internal:8088/proxy/application_1479465617115_0003/
16/11/18 05:58:23 INFO mapreduce.Job: Running job: job_1479465617115_0003
16/11/18 05:58:28 INFO mapreduce.Job: Job job_1479465617115_0003 running in uber mode : false
16/11/18 05:58:28 INFO mapreduce.Job:  map 0% reduce 0%
16/11/18 05:58:39 INFO mapreduce.Job:  map 9% reduce 0%
16/11/18 05:58:40 INFO mapreduce.Job:  map 17% reduce 0%
16/11/18 05:58:42 INFO mapreduce.Job:  map 21% reduce 0%
16/11/18 05:58:43 INFO mapreduce.Job:  map 26% reduce 0%
16/11/18 05:58:45 INFO mapreduce.Job:  map 31% reduce 0%
16/11/18 05:58:46 INFO mapreduce.Job:  map 36% reduce 0%
16/11/18 05:58:48 INFO mapreduce.Job:  map 41% reduce 0%
16/11/18 05:58:49 INFO mapreduce.Job:  map 46% reduce 0%
16/11/18 05:58:51 INFO mapreduce.Job:  map 51% reduce 0%
16/11/18 05:58:52 INFO mapreduce.Job:  map 56% reduce 0%
16/11/18 05:58:54 INFO mapreduce.Job:  map 61% reduce 0%
16/11/18 05:58:55 INFO mapreduce.Job:  map 66% reduce 0%
16/11/18 05:58:57 INFO mapreduce.Job:  map 71% reduce 0%
16/11/18 05:58:58 INFO mapreduce.Job:  map 76% reduce 0%
16/11/18 05:59:01 INFO mapreduce.Job:  map 86% reduce 0%
16/11/18 05:59:04 INFO mapreduce.Job:  map 97% reduce 0%
16/11/18 05:59:05 INFO mapreduce.Job:  map 98% reduce 0%
16/11/18 05:59:06 INFO mapreduce.Job:  map 100% reduce 0%
16/11/18 05:59:06 INFO mapreduce.Job: Job job_1479465617115_0003 completed successfully
16/11/18 05:59:07 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=239528
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=170
		HDFS: Number of bytes written=5120000000
		HDFS: Number of read operations=8
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=4
	Job Counters
		Launched map tasks=2
		Other local map tasks=2
		Total time spent by all maps in occupied slots (ms)=69926
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=69926
		Total vcore-seconds taken by all map tasks=69926
		Total megabyte-seconds taken by all map tasks=71604224
	Map-Reduce Framework
		Map input records=51200000
		Map output records=51200000
		Input split bytes=170
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=470
		CPU time spent (ms)=77340
		Physical memory (bytes) snapshot=393318400
		Virtual memory (bytes) snapshot=3129626624
		Total committed heap usage (bytes)=487587840
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=109963291816450258
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=5120000000

real	0m47.105s
user	0m5.952s
sys	0m0.319s
```

```
[bavaria@ip-172-31-0-115 ~]$ time yarn jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort tgen512m tgen512m-output
16/11/18 05:50:04 INFO terasort.TeraSort: starting
16/11/18 05:50:05 INFO input.FileInputFormat: Total input paths to process : 4
Spent 286ms computing base-splits.
Spent 6ms computing TeraScheduler splits.
Computing input splits took 293ms
Sampling 10 splits of 308
Making 8 from 100000 sampled records
Computing parititions took 1159ms
Spent 1454ms computing partitions.
16/11/18 05:50:07 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-0-115.eu-central-1.compute.internal/172.31.0.115:8032
16/11/18 05:50:07 INFO mapreduce.JobSubmitter: number of splits:308
16/11/18 05:50:07 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1479465617115_0002
16/11/18 05:50:08 INFO impl.YarnClientImpl: Submitted application application_1479465617115_0002
16/11/18 05:50:08 INFO mapreduce.Job: The url to track the job: http://ip-172-31-0-115.eu-central-1.compute.internal:8088/proxy/application_1479465617115_0002/
16/11/18 05:50:08 INFO mapreduce.Job: Running job: job_1479465617115_0002
16/11/18 05:50:14 INFO mapreduce.Job: Job job_1479465617115_0002 running in uber mode : false
16/11/18 05:50:14 INFO mapreduce.Job:  map 0% reduce 0%
16/11/18 05:50:22 INFO mapreduce.Job:  map 1% reduce 0%
16/11/18 05:50:24 INFO mapreduce.Job:  map 3% reduce 0%
16/11/18 05:50:25 INFO mapreduce.Job:  map 4% reduce 0%
16/11/18 05:50:32 INFO mapreduce.Job:  map 5% reduce 0%
16/11/18 05:50:33 INFO mapreduce.Job:  map 6% reduce 0%
16/11/18 05:50:34 INFO mapreduce.Job:  map 7% reduce 0%
16/11/18 05:50:36 INFO mapreduce.Job:  map 8% reduce 0%
16/11/18 05:50:42 INFO mapreduce.Job:  map 9% reduce 0%
16/11/18 05:50:44 INFO mapreduce.Job:  map 11% reduce 0%
16/11/18 05:50:50 INFO mapreduce.Job:  map 12% reduce 0%
16/11/18 05:50:51 INFO mapreduce.Job:  map 13% reduce 0%
16/11/18 05:50:52 INFO mapreduce.Job:  map 14% reduce 0%
16/11/18 05:50:53 INFO mapreduce.Job:  map 15% reduce 0%
16/11/18 05:50:58 INFO mapreduce.Job:  map 16% reduce 0%
16/11/18 05:51:00 INFO mapreduce.Job:  map 17% reduce 0%
16/11/18 05:51:02 INFO mapreduce.Job:  map 18% reduce 0%
16/11/18 05:51:03 INFO mapreduce.Job:  map 19% reduce 0%
16/11/18 05:51:08 INFO mapreduce.Job:  map 20% reduce 0%
16/11/18 05:51:09 INFO mapreduce.Job:  map 21% reduce 0%
16/11/18 05:51:11 INFO mapreduce.Job:  map 22% reduce 0%
16/11/18 05:51:12 INFO mapreduce.Job:  map 23% reduce 0%
16/11/18 05:51:17 INFO mapreduce.Job:  map 24% reduce 0%
16/11/18 05:51:19 INFO mapreduce.Job:  map 25% reduce 0%
16/11/18 05:51:20 INFO mapreduce.Job:  map 26% reduce 0%
16/11/18 05:51:23 INFO mapreduce.Job:  map 27% reduce 0%
16/11/18 05:51:26 INFO mapreduce.Job:  map 28% reduce 0%
16/11/18 05:51:27 INFO mapreduce.Job:  map 29% reduce 0%
16/11/18 05:51:30 INFO mapreduce.Job:  map 30% reduce 0%
16/11/18 05:51:33 INFO mapreduce.Job:  map 31% reduce 0%
16/11/18 05:51:35 INFO mapreduce.Job:  map 32% reduce 0%
16/11/18 05:51:37 INFO mapreduce.Job:  map 33% reduce 0%
16/11/18 05:51:40 INFO mapreduce.Job:  map 34% reduce 0%
16/11/18 05:51:43 INFO mapreduce.Job:  map 35% reduce 0%
16/11/18 05:51:44 INFO mapreduce.Job:  map 36% reduce 0%
16/11/18 05:51:47 INFO mapreduce.Job:  map 37% reduce 0%
16/11/18 05:51:48 INFO mapreduce.Job:  map 38% reduce 0%
16/11/18 05:51:52 INFO mapreduce.Job:  map 39% reduce 0%
16/11/18 05:51:54 INFO mapreduce.Job:  map 40% reduce 0%
16/11/18 05:51:55 INFO mapreduce.Job:  map 41% reduce 0%
16/11/18 05:51:56 INFO mapreduce.Job:  map 42% reduce 0%
16/11/18 05:52:01 INFO mapreduce.Job:  map 43% reduce 0%
16/11/18 05:52:02 INFO mapreduce.Job:  map 44% reduce 0%
16/11/18 05:52:04 INFO mapreduce.Job:  map 45% reduce 0%
16/11/18 05:52:08 INFO mapreduce.Job:  map 46% reduce 0%
16/11/18 05:52:10 INFO mapreduce.Job:  map 47% reduce 0%
16/11/18 05:52:13 INFO mapreduce.Job:  map 48% reduce 0%
16/11/18 05:52:15 INFO mapreduce.Job:  map 49% reduce 0%
16/11/18 05:52:17 INFO mapreduce.Job:  map 50% reduce 0%
16/11/18 05:52:20 INFO mapreduce.Job:  map 51% reduce 0%
16/11/18 05:52:23 INFO mapreduce.Job:  map 52% reduce 0%
16/11/18 05:52:24 INFO mapreduce.Job:  map 53% reduce 0%
16/11/18 05:52:25 INFO mapreduce.Job:  map 54% reduce 0%
16/11/18 05:52:30 INFO mapreduce.Job:  map 55% reduce 0%
16/11/18 05:52:32 INFO mapreduce.Job:  map 56% reduce 0%
16/11/18 05:52:33 INFO mapreduce.Job:  map 57% reduce 0%
16/11/18 05:52:37 INFO mapreduce.Job:  map 58% reduce 0%
16/11/18 05:52:40 INFO mapreduce.Job:  map 59% reduce 0%
16/11/18 05:52:41 INFO mapreduce.Job:  map 60% reduce 0%
16/11/18 05:52:43 INFO mapreduce.Job:  map 61% reduce 0%
16/11/18 05:52:46 INFO mapreduce.Job:  map 62% reduce 0%
16/11/18 05:52:49 INFO mapreduce.Job:  map 63% reduce 0%
16/11/18 05:52:51 INFO mapreduce.Job:  map 64% reduce 0%
16/11/18 05:52:52 INFO mapreduce.Job:  map 65% reduce 0%
16/11/18 05:52:54 INFO mapreduce.Job:  map 66% reduce 0%
16/11/18 05:52:58 INFO mapreduce.Job:  map 67% reduce 0%
16/11/18 05:53:01 INFO mapreduce.Job:  map 68% reduce 0%
16/11/18 05:53:02 INFO mapreduce.Job:  map 69% reduce 0%
16/11/18 05:53:07 INFO mapreduce.Job:  map 70% reduce 0%
16/11/18 05:53:08 INFO mapreduce.Job:  map 71% reduce 0%
16/11/18 05:53:10 INFO mapreduce.Job:  map 73% reduce 0%
16/11/18 05:53:15 INFO mapreduce.Job:  map 74% reduce 0%
16/11/18 05:53:16 INFO mapreduce.Job:  map 75% reduce 0%
16/11/18 05:53:18 INFO mapreduce.Job:  map 76% reduce 0%
16/11/18 05:53:22 INFO mapreduce.Job:  map 77% reduce 0%
16/11/18 05:53:23 INFO mapreduce.Job:  map 78% reduce 0%
16/11/18 05:53:25 INFO mapreduce.Job:  map 79% reduce 0%
16/11/18 05:53:27 INFO mapreduce.Job:  map 80% reduce 0%
16/11/18 05:53:30 INFO mapreduce.Job:  map 81% reduce 0%
16/11/18 05:53:33 INFO mapreduce.Job:  map 82% reduce 0%
16/11/18 05:53:35 INFO mapreduce.Job:  map 83% reduce 0%
16/11/18 05:53:37 INFO mapreduce.Job:  map 84% reduce 0%
16/11/18 05:53:39 INFO mapreduce.Job:  map 85% reduce 0%
16/11/18 05:53:45 INFO mapreduce.Job:  map 85% reduce 3%
16/11/18 05:53:46 INFO mapreduce.Job:  map 85% reduce 10%
16/11/18 05:53:47 INFO mapreduce.Job:  map 85% reduce 17%
16/11/18 05:53:48 INFO mapreduce.Job:  map 86% reduce 17%
16/11/18 05:53:49 INFO mapreduce.Job:  map 86% reduce 24%
16/11/18 05:53:51 INFO mapreduce.Job:  map 86% reduce 25%
16/11/18 05:53:52 INFO mapreduce.Job:  map 87% reduce 25%
16/11/18 05:53:57 INFO mapreduce.Job:  map 88% reduce 25%
16/11/18 05:53:58 INFO mapreduce.Job:  map 88% reduce 26%
16/11/18 05:54:00 INFO mapreduce.Job:  map 89% reduce 26%
16/11/18 05:54:05 INFO mapreduce.Job:  map 90% reduce 26%
16/11/18 05:54:08 INFO mapreduce.Job:  map 91% reduce 26%
16/11/18 05:54:12 INFO mapreduce.Job:  map 92% reduce 27%
16/11/18 05:54:17 INFO mapreduce.Job:  map 93% reduce 27%
16/11/18 05:54:22 INFO mapreduce.Job:  map 94% reduce 27%
16/11/18 05:54:27 INFO mapreduce.Job:  map 95% reduce 28%
16/11/18 05:54:31 INFO mapreduce.Job:  map 96% reduce 28%
16/11/18 05:54:34 INFO mapreduce.Job:  map 97% reduce 28%
16/11/18 05:54:40 INFO mapreduce.Job:  map 98% reduce 28%
16/11/18 05:54:41 INFO mapreduce.Job:  map 98% reduce 29%
16/11/18 05:54:42 INFO mapreduce.Job:  map 99% reduce 29%
16/11/18 05:54:46 INFO mapreduce.Job:  map 100% reduce 29%
16/11/18 05:54:49 INFO mapreduce.Job:  map 100% reduce 31%
16/11/18 05:54:50 INFO mapreduce.Job:  map 100% reduce 42%
16/11/18 05:54:51 INFO mapreduce.Job:  map 100% reduce 45%
16/11/18 05:54:52 INFO mapreduce.Job:  map 100% reduce 50%
16/11/18 05:54:53 INFO mapreduce.Job:  map 100% reduce 57%
16/11/18 05:54:54 INFO mapreduce.Job:  map 100% reduce 58%
16/11/18 05:54:55 INFO mapreduce.Job:  map 100% reduce 62%
16/11/18 05:54:56 INFO mapreduce.Job:  map 100% reduce 69%
16/11/18 05:54:57 INFO mapreduce.Job:  map 100% reduce 71%
16/11/18 05:54:58 INFO mapreduce.Job:  map 100% reduce 74%
16/11/18 05:54:59 INFO mapreduce.Job:  map 100% reduce 78%
16/11/18 05:55:00 INFO mapreduce.Job:  map 100% reduce 81%
16/11/18 05:55:01 INFO mapreduce.Job:  map 100% reduce 84%
16/11/18 05:55:02 INFO mapreduce.Job:  map 100% reduce 89%
16/11/18 05:55:03 INFO mapreduce.Job:  map 100% reduce 90%
16/11/18 05:55:04 INFO mapreduce.Job:  map 100% reduce 92%
16/11/18 05:55:05 INFO mapreduce.Job:  map 100% reduce 94%
16/11/18 05:55:07 INFO mapreduce.Job:  map 100% reduce 96%
16/11/18 05:55:08 INFO mapreduce.Job:  map 100% reduce 97%
16/11/18 05:55:11 INFO mapreduce.Job:  map 100% reduce 99%
16/11/18 05:55:13 INFO mapreduce.Job:  map 100% reduce 100%
16/11/18 05:55:13 INFO mapreduce.Job: Job job_1479465617115_0002 completed successfully
16/11/18 05:55:14 INFO mapreduce.Job: Counters: 50
	File System Counters
		FILE: Number of bytes read=2284428450
		FILE: Number of bytes written=4560588819
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=5120048356
		HDFS: Number of bytes written=5120000000
		HDFS: Number of read operations=948
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=16
	Job Counters
		Launched map tasks=308
		Launched reduce tasks=8
		Data-local map tasks=307
		Rack-local map tasks=1
		Total time spent by all maps in occupied slots (ms)=2007919
		Total time spent by all reduces in occupied slots (ms)=631897
		Total time spent by all map tasks (ms)=2007919
		Total time spent by all reduce tasks (ms)=631897
		Total vcore-seconds taken by all map tasks=2007919
		Total vcore-seconds taken by all reduce tasks=631897
		Total megabyte-seconds taken by all map tasks=2056109056
		Total megabyte-seconds taken by all reduce tasks=647062528
	Map-Reduce Framework
		Map input records=51200000
		Map output records=51200000
		Map output bytes=5222400000
		Map output materialized bytes=2237835551
		Input split bytes=48356
		Combine input records=0
		Combine output records=0
		Reduce input groups=51200000
		Reduce shuffle bytes=2237835551
		Reduce input records=51200000
		Reduce output records=51200000
		Spilled Records=102400000
		Shuffled Maps =2464
		Failed Shuffles=0
		Merged Map outputs=2464
		GC time elapsed (ms)=25649
		CPU time spent (ms)=1069530
		Physical memory (bytes) snapshot=152590606336
		Virtual memory (bytes) snapshot=495601422336
		Total committed heap usage (bytes)=179575455744
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters
		Bytes Read=5120000000
	File Output Format Counters
		Bytes Written=5120000000
16/11/18 05:55:14 INFO terasort.TeraSort: done

real	5m10.840s
user	0m9.749s
sys	0m0.502s
```


```
[bavaria@ip-172-31-0-115 ~]$ hdfs dfs -ls /user/bavaria/tgen512m
Found 5 items
-rw-r--r--   3 bavaria supergroup          0 2016-11-18 05:48 /user/bavaria/tgen512m/_SUCCESS
-rw-r--r--   3 bavaria supergroup 1280000000 2016-11-18 05:48 /user/bavaria/tgen512m/part-m-00000
-rw-r--r--   3 bavaria supergroup 1280000000 2016-11-18 05:48 /user/bavaria/tgen512m/part-m-00001
-rw-r--r--   3 bavaria supergroup 1280000000 2016-11-18 05:48 /user/bavaria/tgen512m/part-m-00002
-rw-r--r--   3 bavaria supergroup 1280000000 2016-11-18 05:48 /user/bavaria/tgen512m/part-m-00003

```


```

Status: HEALTHY
 Total size:	5120000000 B
 Total dirs:	1
 Total files:	3
 Total symlinks:		0
 Total blocks (validated):	306 (avg. block size 16732026 B)
 Minimally replicated blocks:	306 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		4
 Number of racks:		1
FSCK ended at Fri Nov 18 06:03:57 EST 2016 in 4 milliseconds


The filesystem under path '/user/bavaria/tgen512m' is HEALTHY
```

