# Create a home HDFS directory for this user as well
```
hdfs dfs mkdir /user/rgaleanog
```


# Teragen command
```
time yarn jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Ddfs.block.size=33554432 -Dmapred.map.tasks=4 100000000 teragen-output
```

# Terasort command
```
time yarn jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort teragen-output terasort-output
```

# Teragen command
```
[rgaleanog@ip-172-31-25-139 ~]$ time yarn jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Ddfs.block.size=33554432 -Dmapred.map.tasks=4 100000000 teragen-output
16/11/16 02:38:37 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-25-137.eu-central-1.compute.internal/172.31.25.137:8032
16/11/16 02:38:38 INFO terasort.TeraSort: Generating 100000000 using 4
16/11/16 02:38:38 INFO mapreduce.JobSubmitter: number of splits:4
16/11/16 02:38:38 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
16/11/16 02:38:38 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
16/11/16 02:38:38 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1479251868188_0005
16/11/16 02:38:38 INFO impl.YarnClientImpl: Submitted application application_1479251868188_0005
16/11/16 02:38:38 INFO mapreduce.Job: The url to track the job: http://ip-172-31-25-137.eu-central-1.compute.internal:8088/proxy/application_1479251868188_0005/
16/11/16 02:38:38 INFO mapreduce.Job: Running job: job_1479251868188_0005
16/11/16 02:38:44 INFO mapreduce.Job: Job job_1479251868188_0005 running in uber mode : false
16/11/16 02:38:44 INFO mapreduce.Job:  map 0% reduce 0%
16/11/16 02:38:55 INFO mapreduce.Job:  map 7% reduce 0%
16/11/16 02:38:56 INFO mapreduce.Job:  map 10% reduce 0%
16/11/16 02:38:58 INFO mapreduce.Job:  map 13% reduce 0%
16/11/16 02:38:59 INFO mapreduce.Job:  map 14% reduce 0%
16/11/16 02:39:01 INFO mapreduce.Job:  map 15% reduce 0%
16/11/16 02:39:02 INFO mapreduce.Job:  map 16% reduce 0%
16/11/16 02:39:04 INFO mapreduce.Job:  map 17% reduce 0%
16/11/16 02:39:05 INFO mapreduce.Job:  map 19% reduce 0%
16/11/16 02:39:07 INFO mapreduce.Job:  map 20% reduce 0%
16/11/16 02:39:08 INFO mapreduce.Job:  map 21% reduce 0%
16/11/16 02:39:10 INFO mapreduce.Job:  map 22% reduce 0%
16/11/16 02:39:11 INFO mapreduce.Job:  map 23% reduce 0%
16/11/16 02:39:12 INFO mapreduce.Job:  map 24% reduce 0%
16/11/16 02:39:14 INFO mapreduce.Job:  map 25% reduce 0%
16/11/16 02:39:16 INFO mapreduce.Job:  map 26% reduce 0%
16/11/16 02:39:18 INFO mapreduce.Job:  map 27% reduce 0%
16/11/16 02:39:19 INFO mapreduce.Job:  map 29% reduce 0%
16/11/16 02:39:21 INFO mapreduce.Job:  map 30% reduce 0%
16/11/16 02:39:22 INFO mapreduce.Job:  map 31% reduce 0%
16/11/16 02:39:24 INFO mapreduce.Job:  map 32% reduce 0%
16/11/16 02:39:25 INFO mapreduce.Job:  map 33% reduce 0%
16/11/16 02:39:27 INFO mapreduce.Job:  map 34% reduce 0%
16/11/16 02:39:28 INFO mapreduce.Job:  map 35% reduce 0%
16/11/16 02:39:30 INFO mapreduce.Job:  map 36% reduce 0%
16/11/16 02:39:31 INFO mapreduce.Job:  map 37% reduce 0%
16/11/16 02:39:33 INFO mapreduce.Job:  map 38% reduce 0%
16/11/16 02:39:34 INFO mapreduce.Job:  map 39% reduce 0%
16/11/16 02:39:36 INFO mapreduce.Job:  map 40% reduce 0%
16/11/16 02:39:37 INFO mapreduce.Job:  map 41% reduce 0%
16/11/16 02:39:39 INFO mapreduce.Job:  map 42% reduce 0%
16/11/16 02:39:40 INFO mapreduce.Job:  map 44% reduce 0%
16/11/16 02:39:43 INFO mapreduce.Job:  map 45% reduce 0%
16/11/16 02:39:45 INFO mapreduce.Job:  map 46% reduce 0%
16/11/16 02:39:46 INFO mapreduce.Job:  map 47% reduce 0%
16/11/16 02:39:48 INFO mapreduce.Job:  map 48% reduce 0%
16/11/16 02:39:49 INFO mapreduce.Job:  map 49% reduce 0%
16/11/16 02:39:51 INFO mapreduce.Job:  map 50% reduce 0%
16/11/16 02:39:52 INFO mapreduce.Job:  map 51% reduce 0%
16/11/16 02:39:54 INFO mapreduce.Job:  map 52% reduce 0%
16/11/16 02:39:55 INFO mapreduce.Job:  map 53% reduce 0%
16/11/16 02:39:57 INFO mapreduce.Job:  map 54% reduce 0%
16/11/16 02:39:58 INFO mapreduce.Job:  map 56% reduce 0%
16/11/16 02:40:01 INFO mapreduce.Job:  map 58% reduce 0%
16/11/16 02:40:03 INFO mapreduce.Job:  map 59% reduce 0%
16/11/16 02:40:04 INFO mapreduce.Job:  map 60% reduce 0%
16/11/16 02:40:06 INFO mapreduce.Job:  map 61% reduce 0%
16/11/16 02:40:07 INFO mapreduce.Job:  map 62% reduce 0%
16/11/16 02:40:09 INFO mapreduce.Job:  map 63% reduce 0%
16/11/16 02:40:10 INFO mapreduce.Job:  map 64% reduce 0%
16/11/16 02:40:12 INFO mapreduce.Job:  map 65% reduce 0%
16/11/16 02:40:13 INFO mapreduce.Job:  map 66% reduce 0%
16/11/16 02:40:15 INFO mapreduce.Job:  map 67% reduce 0%
16/11/16 02:40:16 INFO mapreduce.Job:  map 68% reduce 0%
16/11/16 02:40:18 INFO mapreduce.Job:  map 69% reduce 0%
16/11/16 02:40:19 INFO mapreduce.Job:  map 70% reduce 0%
16/11/16 02:40:21 INFO mapreduce.Job:  map 71% reduce 0%
16/11/16 02:40:22 INFO mapreduce.Job:  map 72% reduce 0%
16/11/16 02:40:24 INFO mapreduce.Job:  map 73% reduce 0%
16/11/16 02:40:25 INFO mapreduce.Job:  map 75% reduce 0%
16/11/16 02:40:27 INFO mapreduce.Job:  map 76% reduce 0%
16/11/16 02:40:29 INFO mapreduce.Job:  map 77% reduce 0%
16/11/16 02:40:31 INFO mapreduce.Job:  map 78% reduce 0%
16/11/16 02:40:32 INFO mapreduce.Job:  map 79% reduce 0%
16/11/16 02:40:34 INFO mapreduce.Job:  map 80% reduce 0%
16/11/16 02:40:35 INFO mapreduce.Job:  map 81% reduce 0%
16/11/16 02:40:37 INFO mapreduce.Job:  map 82% reduce 0%
16/11/16 02:40:38 INFO mapreduce.Job:  map 83% reduce 0%
16/11/16 02:40:40 INFO mapreduce.Job:  map 84% reduce 0%
16/11/16 02:40:41 INFO mapreduce.Job:  map 85% reduce 0%
16/11/16 02:40:43 INFO mapreduce.Job:  map 86% reduce 0%
16/11/16 02:40:44 INFO mapreduce.Job:  map 87% reduce 0%
16/11/16 02:40:46 INFO mapreduce.Job:  map 88% reduce 0%
16/11/16 02:40:47 INFO mapreduce.Job:  map 90% reduce 0%
16/11/16 02:40:49 INFO mapreduce.Job:  map 91% reduce 0%
16/11/16 02:40:50 INFO mapreduce.Job:  map 92% reduce 0%
16/11/16 02:40:52 INFO mapreduce.Job:  map 93% reduce 0%
16/11/16 02:40:53 INFO mapreduce.Job:  map 94% reduce 0%
16/11/16 02:40:55 INFO mapreduce.Job:  map 95% reduce 0%
16/11/16 02:40:56 INFO mapreduce.Job:  map 96% reduce 0%
16/11/16 02:40:58 INFO mapreduce.Job:  map 97% reduce 0%
16/11/16 02:41:01 INFO mapreduce.Job:  map 99% reduce 0%
16/11/16 02:41:03 INFO mapreduce.Job:  map 100% reduce 0%
16/11/16 02:41:03 INFO mapreduce.Job: Job job_1479251868188_0005 completed successfully
16/11/16 02:41:03 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=488804
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=344
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=532613
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=532613
		Total vcore-seconds taken by all map tasks=532613
		Total megabyte-seconds taken by all map tasks=545395712
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Input split bytes=344
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1297
		CPU time spent (ms)=149850
		Physical memory (bytes) snapshot=935907328
		Virtual memory (bytes) snapshot=6265597952
		Total committed heap usage (bytes)=829423616
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=214760662691937609
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=10000000000

real	2m28.657s
user	0m5.837s
sys	0m0.311s
```
# Terasort results

```
[rgaleanog@ip-172-31-25-139 ~]$ time yarn jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort teragen-output terasort-output
16/11/16 02:43:57 INFO terasort.TeraSort: starting
16/11/16 02:43:58 INFO input.FileInputFormat: Total input paths to process : 4
Spent 266ms computing base-splits.
Spent 6ms computing TeraScheduler splits.
Computing input splits took 273ms
Sampling 10 splits of 300
Making 6 from 100000 sampled records
Computing parititions took 927ms
Spent 1203ms computing partitions.
16/11/16 02:43:59 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-25-137.eu-central-1.compute.internal/172.31.25.137:8032
16/11/16 02:44:00 INFO mapreduce.JobSubmitter: number of splits:300
16/11/16 02:44:00 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1479251868188_0006
16/11/16 02:44:00 INFO impl.YarnClientImpl: Submitted application application_1479251868188_0006
16/11/16 02:44:00 INFO mapreduce.Job: The url to track the job: http://ip-172-31-25-137.eu-central-1.compute.internal:8088/proxy/application_1479251868188_0006/
16/11/16 02:44:00 INFO mapreduce.Job: Running job: job_1479251868188_0006
16/11/16 02:44:05 INFO mapreduce.Job: Job job_1479251868188_0006 running in uber mode : false
16/11/16 02:44:05 INFO mapreduce.Job:  map 0% reduce 0%
16/11/16 02:44:17 INFO mapreduce.Job:  map 1% reduce 0%
16/11/16 02:44:20 INFO mapreduce.Job:  map 4% reduce 0%
16/11/16 02:44:29 INFO mapreduce.Job:  map 5% reduce 0%
16/11/16 02:44:33 INFO mapreduce.Job:  map 7% reduce 0%
16/11/16 02:44:37 INFO mapreduce.Job:  map 8% reduce 0%
16/11/16 02:44:45 INFO mapreduce.Job:  map 9% reduce 0%
16/11/16 02:44:46 INFO mapreduce.Job:  map 11% reduce 0%
16/11/16 02:44:47 INFO mapreduce.Job:  map 12% reduce 0%
16/11/16 02:44:56 INFO mapreduce.Job:  map 13% reduce 0%
16/11/16 02:44:58 INFO mapreduce.Job:  map 14% reduce 0%
16/11/16 02:44:59 INFO mapreduce.Job:  map 16% reduce 0%
16/11/16 02:45:07 INFO mapreduce.Job:  map 17% reduce 0%
16/11/16 02:45:10 INFO mapreduce.Job:  map 18% reduce 0%
16/11/16 02:45:11 INFO mapreduce.Job:  map 19% reduce 0%
16/11/16 02:45:12 INFO mapreduce.Job:  map 20% reduce 0%
16/11/16 02:45:20 INFO mapreduce.Job:  map 21% reduce 0%
16/11/16 02:45:22 INFO mapreduce.Job:  map 22% reduce 0%
16/11/16 02:45:23 INFO mapreduce.Job:  map 23% reduce 0%
16/11/16 02:45:24 INFO mapreduce.Job:  map 24% reduce 0%
16/11/16 02:45:31 INFO mapreduce.Job:  map 25% reduce 0%
16/11/16 02:45:33 INFO mapreduce.Job:  map 26% reduce 0%
16/11/16 02:45:34 INFO mapreduce.Job:  map 27% reduce 0%
16/11/16 02:45:37 INFO mapreduce.Job:  map 28% reduce 0%
16/11/16 02:45:43 INFO mapreduce.Job:  map 29% reduce 0%
16/11/16 02:45:46 INFO mapreduce.Job:  map 31% reduce 0%
16/11/16 02:45:49 INFO mapreduce.Job:  map 32% reduce 0%
16/11/16 02:45:55 INFO mapreduce.Job:  map 33% reduce 0%
16/11/16 02:45:58 INFO mapreduce.Job:  map 34% reduce 0%
16/11/16 02:45:59 INFO mapreduce.Job:  map 35% reduce 0%
16/11/16 02:46:02 INFO mapreduce.Job:  map 36% reduce 0%
16/11/16 02:46:06 INFO mapreduce.Job:  map 37% reduce 0%
16/11/16 02:46:10 INFO mapreduce.Job:  map 38% reduce 0%
16/11/16 02:46:11 INFO mapreduce.Job:  map 39% reduce 0%
16/11/16 02:46:12 INFO mapreduce.Job:  map 40% reduce 0%
16/11/16 02:46:18 INFO mapreduce.Job:  map 41% reduce 0%
16/11/16 02:46:22 INFO mapreduce.Job:  map 42% reduce 0%
16/11/16 02:46:23 INFO mapreduce.Job:  map 43% reduce 0%
16/11/16 02:46:24 INFO mapreduce.Job:  map 44% reduce 0%
16/11/16 02:46:30 INFO mapreduce.Job:  map 45% reduce 0%
16/11/16 02:46:33 INFO mapreduce.Job:  map 46% reduce 0%
16/11/16 02:46:35 INFO mapreduce.Job:  map 47% reduce 0%
16/11/16 02:46:40 INFO mapreduce.Job:  map 48% reduce 0%
16/11/16 02:46:42 INFO mapreduce.Job:  map 49% reduce 0%
16/11/16 02:46:46 INFO mapreduce.Job:  map 50% reduce 0%
16/11/16 02:46:49 INFO mapreduce.Job:  map 51% reduce 0%
16/11/16 02:46:51 INFO mapreduce.Job:  map 52% reduce 0%
16/11/16 02:46:54 INFO mapreduce.Job:  map 53% reduce 0%
16/11/16 02:46:59 INFO mapreduce.Job:  map 54% reduce 0%
16/11/16 02:47:00 INFO mapreduce.Job:  map 55% reduce 0%
16/11/16 02:47:01 INFO mapreduce.Job:  map 56% reduce 0%
16/11/16 02:47:07 INFO mapreduce.Job:  map 57% reduce 0%
16/11/16 02:47:10 INFO mapreduce.Job:  map 58% reduce 0%
16/11/16 02:47:11 INFO mapreduce.Job:  map 59% reduce 0%
16/11/16 02:47:14 INFO mapreduce.Job:  map 60% reduce 0%
16/11/16 02:47:20 INFO mapreduce.Job:  map 61% reduce 0%
16/11/16 02:47:21 INFO mapreduce.Job:  map 62% reduce 0%
16/11/16 02:47:23 INFO mapreduce.Job:  map 63% reduce 0%
16/11/16 02:47:29 INFO mapreduce.Job:  map 64% reduce 0%
16/11/16 02:47:31 INFO mapreduce.Job:  map 65% reduce 0%
16/11/16 02:47:32 INFO mapreduce.Job:  map 66% reduce 0%
16/11/16 02:47:35 INFO mapreduce.Job:  map 67% reduce 0%
16/11/16 02:47:39 INFO mapreduce.Job:  map 68% reduce 0%
16/11/16 02:47:42 INFO mapreduce.Job:  map 69% reduce 0%
16/11/16 02:47:45 INFO mapreduce.Job:  map 70% reduce 0%
16/11/16 02:47:48 INFO mapreduce.Job:  map 71% reduce 0%
16/11/16 02:47:51 INFO mapreduce.Job:  map 72% reduce 0%
16/11/16 02:47:55 INFO mapreduce.Job:  map 73% reduce 0%
16/11/16 02:47:57 INFO mapreduce.Job:  map 74% reduce 0%
16/11/16 02:47:59 INFO mapreduce.Job:  map 75% reduce 0%
16/11/16 02:48:03 INFO mapreduce.Job:  map 76% reduce 0%
16/11/16 02:48:07 INFO mapreduce.Job:  map 77% reduce 0%
16/11/16 02:48:08 INFO mapreduce.Job:  map 78% reduce 0%
16/11/16 02:48:10 INFO mapreduce.Job:  map 79% reduce 0%
16/11/16 02:48:15 INFO mapreduce.Job:  map 80% reduce 0%
16/11/16 02:48:18 INFO mapreduce.Job:  map 81% reduce 0%
16/11/16 02:48:20 INFO mapreduce.Job:  map 82% reduce 0%
16/11/16 02:48:24 INFO mapreduce.Job:  map 83% reduce 0%
16/11/16 02:48:27 INFO mapreduce.Job:  map 84% reduce 0%
16/11/16 02:48:31 INFO mapreduce.Job:  map 84% reduce 2%
16/11/16 02:48:33 INFO mapreduce.Job:  map 84% reduce 3%
16/11/16 02:48:34 INFO mapreduce.Job:  map 84% reduce 5%
16/11/16 02:48:35 INFO mapreduce.Job:  map 84% reduce 10%
16/11/16 02:48:36 INFO mapreduce.Job:  map 85% reduce 10%
16/11/16 02:48:39 INFO mapreduce.Job:  map 85% reduce 11%
16/11/16 02:48:40 INFO mapreduce.Job:  map 86% reduce 12%
16/11/16 02:48:41 INFO mapreduce.Job:  map 86% reduce 14%
16/11/16 02:48:42 INFO mapreduce.Job:  map 86% reduce 15%
16/11/16 02:48:45 INFO mapreduce.Job:  map 87% reduce 17%
16/11/16 02:48:47 INFO mapreduce.Job:  map 87% reduce 19%
16/11/16 02:48:48 INFO mapreduce.Job:  map 87% reduce 21%
16/11/16 02:48:50 INFO mapreduce.Job:  map 88% reduce 21%
16/11/16 02:48:51 INFO mapreduce.Job:  map 88% reduce 22%
16/11/16 02:48:53 INFO mapreduce.Job:  map 89% reduce 23%
16/11/16 02:48:54 INFO mapreduce.Job:  map 89% reduce 24%
16/11/16 02:48:56 INFO mapreduce.Job:  map 89% reduce 25%
16/11/16 02:49:01 INFO mapreduce.Job:  map 90% reduce 25%
16/11/16 02:49:03 INFO mapreduce.Job:  map 91% reduce 25%
16/11/16 02:49:09 INFO mapreduce.Job:  map 92% reduce 25%
16/11/16 02:49:12 INFO mapreduce.Job:  map 93% reduce 26%
16/11/16 02:49:15 INFO mapreduce.Job:  map 94% reduce 26%
16/11/16 02:49:22 INFO mapreduce.Job:  map 95% reduce 26%
16/11/16 02:49:23 INFO mapreduce.Job:  map 96% reduce 26%
16/11/16 02:49:25 INFO mapreduce.Job:  map 96% reduce 27%
16/11/16 02:49:29 INFO mapreduce.Job:  map 97% reduce 27%
16/11/16 02:49:31 INFO mapreduce.Job:  map 98% reduce 27%
16/11/16 02:49:35 INFO mapreduce.Job:  map 99% reduce 27%
16/11/16 02:49:39 INFO mapreduce.Job:  map 100% reduce 28%
16/11/16 02:49:42 INFO mapreduce.Job:  map 100% reduce 31%
16/11/16 02:49:43 INFO mapreduce.Job:  map 100% reduce 39%
16/11/16 02:49:44 INFO mapreduce.Job:  map 100% reduce 44%
16/11/16 02:49:45 INFO mapreduce.Job:  map 100% reduce 53%
16/11/16 02:49:46 INFO mapreduce.Job:  map 100% reduce 56%
16/11/16 02:49:47 INFO mapreduce.Job:  map 100% reduce 59%
16/11/16 02:49:48 INFO mapreduce.Job:  map 100% reduce 61%
16/11/16 02:49:49 INFO mapreduce.Job:  map 100% reduce 62%
16/11/16 02:49:50 INFO mapreduce.Job:  map 100% reduce 63%
16/11/16 02:49:51 INFO mapreduce.Job:  map 100% reduce 65%
16/11/16 02:49:52 INFO mapreduce.Job:  map 100% reduce 66%
16/11/16 02:49:53 INFO mapreduce.Job:  map 100% reduce 67%
16/11/16 02:49:54 INFO mapreduce.Job:  map 100% reduce 68%
16/11/16 02:49:55 INFO mapreduce.Job:  map 100% reduce 69%
16/11/16 02:49:56 INFO mapreduce.Job:  map 100% reduce 70%
16/11/16 02:49:57 INFO mapreduce.Job:  map 100% reduce 73%
16/11/16 02:49:58 INFO mapreduce.Job:  map 100% reduce 74%
16/11/16 02:49:59 INFO mapreduce.Job:  map 100% reduce 75%
16/11/16 02:50:00 INFO mapreduce.Job:  map 100% reduce 78%
16/11/16 02:50:01 INFO mapreduce.Job:  map 100% reduce 79%
16/11/16 02:50:02 INFO mapreduce.Job:  map 100% reduce 80%
16/11/16 02:50:03 INFO mapreduce.Job:  map 100% reduce 85%
16/11/16 02:50:04 INFO mapreduce.Job:  map 100% reduce 86%
16/11/16 02:50:05 INFO mapreduce.Job:  map 100% reduce 87%
16/11/16 02:50:06 INFO mapreduce.Job:  map 100% reduce 88%
16/11/16 02:50:07 INFO mapreduce.Job:  map 100% reduce 89%
16/11/16 02:50:09 INFO mapreduce.Job:  map 100% reduce 91%
16/11/16 02:50:10 INFO mapreduce.Job:  map 100% reduce 92%
16/11/16 02:50:12 INFO mapreduce.Job:  map 100% reduce 94%
16/11/16 02:50:14 INFO mapreduce.Job:  map 100% reduce 95%
16/11/16 02:50:15 INFO mapreduce.Job:  map 100% reduce 96%
16/11/16 02:50:16 INFO mapreduce.Job:  map 100% reduce 97%
16/11/16 02:50:18 INFO mapreduce.Job:  map 100% reduce 99%
16/11/16 02:50:20 INFO mapreduce.Job:  map 100% reduce 100%
16/11/16 02:50:21 INFO mapreduce.Job: Job job_1479251868188_0006 completed successfully
16/11/16 02:50:21 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=4477406020
		FILE: Number of bytes written=8890429103
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10000049800
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=918
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=12
	Job Counters 
		Launched map tasks=300
		Launched reduce tasks=6
		Data-local map tasks=300
		Total time spent by all maps in occupied slots (ms)=2922919
		Total time spent by all reduces in occupied slots (ms)=591249
		Total time spent by all map tasks (ms)=2922919
		Total time spent by all reduce tasks (ms)=591249
		Total vcore-seconds taken by all map tasks=2922919
		Total vcore-seconds taken by all reduce tasks=591249
		Total megabyte-seconds taken by all map tasks=2993069056
		Total megabyte-seconds taken by all reduce tasks=605438976
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Map output bytes=10200000000
		Map output materialized bytes=4375170195
		Input split bytes=49800
		Combine input records=0
		Combine output records=0
		Reduce input groups=100000000
		Reduce shuffle bytes=4375170195
		Reduce input records=100000000
		Reduce output records=100000000
		Spilled Records=200000000
		Shuffled Maps =1800
		Failed Shuffles=0
		Merged Map outputs=1800
		GC time elapsed (ms)=36723
		CPU time spent (ms)=1424620
		Physical memory (bytes) snapshot=145930158080
		Virtual memory (bytes) snapshot=479085039616
		Total committed heap usage (bytes)=173116751872
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=10000000000
	File Output Format Counters 
		Bytes Written=10000000000
16/11/16 02:50:21 INFO terasort.TeraSort: done

real	6m25.328s
user	0m9.396s
sys	0m0.459s
```