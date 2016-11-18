[bavaria@ip-172-31-0-115 ~]$ time yarn jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Ddfs.block.size=16777216 -Dmapred.map.tasks=4 51200000 tgen512m
16/11/18 05:47:38 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-0-115.eu-central-1.compute.internal/172.31.0.115:8032
16/11/18 05:47:39 INFO terasort.TeraSort: Generating 51200000 using 4
16/11/18 05:47:39 INFO mapreduce.JobSubmitter: number of splits:4
16/11/18 05:47:39 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
16/11/18 05:47:39 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
16/11/18 05:47:39 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1479465617115_0001
16/11/18 05:47:39 INFO impl.YarnClientImpl: Submitted application application_1479465617115_0001
16/11/18 05:47:39 INFO mapreduce.Job: The url to track the job: http://ip-172-31-0-115.eu-central-1.compute.internal:8088/proxy/application_1479465617115_0001/
16/11/18 05:47:39 INFO mapreduce.Job: Running job: job_1479465617115_0001
16/11/18 05:47:46 INFO mapreduce.Job: Job job_1479465617115_0001 running in uber mode : false
16/11/18 05:47:46 INFO mapreduce.Job:  map 0% reduce 0%
16/11/18 05:47:57 INFO mapreduce.Job:  map 7% reduce 0%
16/11/18 05:47:58 INFO mapreduce.Job:  map 26% reduce 0%
16/11/18 05:48:00 INFO mapreduce.Job:  map 29% reduce 0%
16/11/18 05:48:01 INFO mapreduce.Job:  map 40% reduce 0%
16/11/18 05:48:03 INFO mapreduce.Job:  map 43% reduce 0%
16/11/18 05:48:04 INFO mapreduce.Job:  map 54% reduce 0%
16/11/18 05:48:06 INFO mapreduce.Job:  map 58% reduce 0%
16/11/18 05:48:07 INFO mapreduce.Job:  map 69% reduce 0%
16/11/18 05:48:09 INFO mapreduce.Job:  map 72% reduce 0%
16/11/18 05:48:10 INFO mapreduce.Job:  map 81% reduce 0%
16/11/18 05:48:12 INFO mapreduce.Job:  map 85% reduce 0%
16/11/18 05:48:13 INFO mapreduce.Job:  map 96% reduce 0%
16/11/18 05:48:15 INFO mapreduce.Job:  map 100% reduce 0%
16/11/18 05:48:16 INFO mapreduce.Job: Job job_1479465617115_0001 completed successfully
16/11/18 05:48:16 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=479056
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=339
		HDFS: Number of bytes written=5120000000
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=103624
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=103624
		Total vcore-seconds taken by all map tasks=103624
		Total megabyte-seconds taken by all map tasks=106110976
	Map-Reduce Framework
		Map input records=51200000
		Map output records=51200000
		Input split bytes=339
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=516
		CPU time spent (ms)=86740
		Physical memory (bytes) snapshot=1135730688
		Virtual memory (bytes) snapshot=6253158400
		Total committed heap usage (bytes)=1131937792
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=109963291816450258
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=5120000000

real	0m40.452s
user	0m6.156s
sys	0m0.296s