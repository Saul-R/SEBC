


# YARN slow Jobs
```
 hadoop jar hadoop-examples.jar teragen  -Dmapreduce.job.maps=8 -Dmapreduce.map.memory.mb=512 -Dmapreduce.map.java.opts.max.heap=409 100000 results/tg-10GB-8-8-512 elapsed: 20
hadoop jar hadoop-examples.jar terasort -Dmapreduce.job.maps=8 -Dmapreduce.job.reduces=8 -Dmapreduce.map.memory.mb=512 -Dmapreduce.map.java.opts.max.heap=409 -Dmapreduce.reduce.memory.mb=512 results/tg-10GB-8-8-512 -Dmapreduce.reduce.java.opts.max.heap=409 elapsed: 33
 hadoop jar hadoop-examples.jar teragen  -Dmapreduce.job.maps=8 -Dmapreduce.map.memory.mb=1024 -Dmapreduce.map.java.opts.max.heap=819 100000 results/tg-10GB-8-8-1024 elapsed: 20
hadoop jar hadoop-examples.jar terasort -Dmapreduce.job.maps=8 -Dmapreduce.job.reduces=8 -Dmapreduce.map.memory.mb=1024 -Dmapreduce.map.java.opts.max.heap=819 -Dmapreduce.reduce.memory.mb=1024 results/tg-10GB-8-8-1024 -Dmapreduce.reduce.java.opts.max.heap=819 elapsed: 31
```

# YARN fast Jobs
```
 hadoop jar hadoop-examples.jar teragen  -Dmapreduce.job.maps=2 -Dmapreduce.map.memory.mb=512 -Dmapreduce.map.java.opts.max.heap=409 100000 results/tg-10GB-2-2-512 elapsed: 15
hadoop jar hadoop-examples.jar terasort -Dmapreduce.job.maps=2 -Dmapreduce.job.reduces=2 -Dmapreduce.map.memory.mb=512 -Dmapreduce.map.java.opts.max.heap=409 -Dmapreduce.reduce.memory.mb=512 results/tg-10GB-2-2-512 -Dmapreduce.reduce.java.opts.max.heap=409 elapsed: 22
 hadoop jar hadoop-examples.jar teragen  -Dmapreduce.job.maps=2 -Dmapreduce.map.memory.mb=1024 -Dmapreduce.map.java.opts.max.heap=819 100000 results/tg-10GB-2-2-1024 elapsed: 16
hadoop jar hadoop-examples.jar terasort -Dmapreduce.job.maps=2 -Dmapreduce.job.reduces=2 -Dmapreduce.map.memory.mb=1024 -Dmapreduce.map.java.opts.max.heap=819 -Dmapreduce.reduce.memory.mb=1024 results/tg-10GB-2-2-1024 -Dmapreduce.reduce.java.opts.max.heap=819 elapsed: 23
```