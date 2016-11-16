# Explain any adjustments you make in resources/labs/0_YARNCalcs.md


I have reduce the OS Memory to 4GB, and leave the other parameters as is.
If we need a cluster with Impala, HBase o Solr, we must to assing at least 1 vCore to each Service at least 12-16GB GB of memory. This values depends of the planned workload for the cluster. For example, if you need a cluster for real time, process, you will need HBase and Impala, probably, so this values must be fit to this workload .


##What criteria affects workload factor? What does a value of 1, 2, or 4 signify?
This parameter is very important because it must conform to the planned workload for the cluster.

For example, if your cluster make a lot of use of CPU, like happends  in HPC, this value must be 1, because the Hyper Threathing process does generate extra overload on servers. Physical cores are forced to perform more calculations per cycle.So you are not taking advantage of resources.

But when your workload fits certain types of executions, such as encoding, encryption/Decryption or multiple application, It makes better use of parallelism. In this case, adjust vCores to 4 or 8 is recommended.