```

{
  "timestamp" : "2016-11-16T14:09:16.914Z",
  "clusters" : [ {
    "name" : "rgaleanog Cluster",
    "version" : "CDH5",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "832569344"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "3105882112"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "4627575603"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "778"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ip-172-31-25-141.eu-central-1.compute.internal"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "metastore_pass"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-090ba5a774c8734049252f1f0dce5eb1",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-238e149e"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-35bb4749233f6d7bafca42d528c33097",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-228e149f"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-57c50a7618a9ea5cd85a54e34e2ac323",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-1c8e14a1"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-892b10ee928db920acbd491375778dbc",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-1d8e14a0"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-bf559074e806bdc0443cebe219727a84",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-1f8e14a2"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-090ba5a774c8734049252f1f0dce5eb1",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "i-238e149e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5zg1m50kfy9el2szn2gjv33lg"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-090ba5a774c8734049252f1f0dce5eb1",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "i-238e149e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4jrnots0e81qjbv850dxk4cyc"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-bf559074e806bdc0443cebe219727a84",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "i-1f8e14a2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "443slw07w9ngmfcdngmc36i92"
          } ]
        }
      } ],
      "displayName" : "Hive"
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-090ba5a774c8734049252f1f0dce5eb1",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-238e149e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8tg9yvbfeh1710byhls8xnzjc"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-57c50a7618a9ea5cd85a54e34e2ac323",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-1c8e14a1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6nx75xacfy9r9ig2b9zvrxved"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-bf559074e806bdc0443cebe219727a84",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-1f8e14a2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8hmy3bikt26chzbirkinsrq6z"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "ip-172-31-25-141.eu-central-1.compute.internal"
        }, {
          "name" : "database_password",
          "value" : "hue_pass"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-NAMENODE-090ba5a774c8734049252f1f0dce5eb1"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-090ba5a774c8734049252f1f0dce5eb1",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "i-238e149e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ddmam5g7z595h932r4yk8nubb"
          }, {
            "name" : "secret_key",
            "value" : "nwGp5LzBmIAONSacwh3jEbJcVuwXwy"
          } ]
        }
      }, {
        "name" : "hue-HUE_SERVER-bf559074e806bdc0443cebe219727a84",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "i-1f8e14a2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4gdwpj5wn3ki48nzlfy6p79k5"
          }, {
            "name" : "secret_key",
            "value" : "f50dRk17ofOf08ATFcTYRDJNfQ4OKn"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "ip-172-31-25-141.eu-central-1.compute.internal"
          }, {
            "name" : "oozie_database_password",
            "value" : "oozie"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          }, {
            "name" : "oozie_java_heapsize",
            "value" : "832569344"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-090ba5a774c8734049252f1f0dce5eb1",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "i-238e149e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bfjtvd1lklsex42g9yq3i1mwl"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "6"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "1"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1800"
          }, {
            "name" : "rm_io_weight",
            "value" : "900"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/data1/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/data1/yarn/container-logs,/opt/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "3861"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "5192"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "90"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "0UpRiNgMd6m6LB1z5x6HLXAQuY5kNg"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-bf559074e806bdc0443cebe219727a84",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "i-1f8e14a2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "93gataupcluw09rbjwyoodex5"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-35bb4749233f6d7bafca42d528c33097",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-228e149f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5ksec89dj7kkwx6l3cu45ifyp"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-57c50a7618a9ea5cd85a54e34e2ac323",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-1c8e14a1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dyyws3d21cdwktlpkyt5c44x7"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-892b10ee928db920acbd491375778dbc",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-1d8e14a0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "e95265f5mrmuaxj8u6qjhmovz"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-bf559074e806bdc0443cebe219727a84",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "i-1f8e14a2"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "134"
          }, {
            "name" : "role_jceks_password",
            "value" : "a6mifvr0aoyh8u3rm5kfbm4e3"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "BALANCER",
          "items" : [ {
            "name" : "balancer_java_heapsize",
            "value" : "832569344"
          } ]
        }, {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/data1/dfs/dn"
          }, {
            "name" : "dfs_datanode_bind_wildcard",
            "value" : "true"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "4214151577"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "200"
          }, {
            "name" : "rm_io_weight",
            "value" : "100"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/data1/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_bind_wildcard",
            "value" : "true"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/data1/dfs/snn"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "uYETWCOlTFrcBocnI0M0kfXX8VuyxL"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "QyRMnGYqW5qEmIPMqpM2IU48sJmeb2"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "tRKPfslmuzCEIFISAhyW2Ls3rshWmF"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "10"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-090ba5a774c8734049252f1f0dce5eb1",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "i-238e149e"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-35bb4749233f6d7bafca42d528c33097",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-228e149f"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "nv6n4mtyvv5vo36c2hel1bzq"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-57c50a7618a9ea5cd85a54e34e2ac323",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-1c8e14a1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5ulikk5lcme7ussxhs31tbr05"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-892b10ee928db920acbd491375778dbc",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-1d8e14a0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6ip7uvjp97t6y0b6qsmnfev2y"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-090ba5a774c8734049252f1f0dce5eb1",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "i-238e149e"
        },
        "config" : {
          "items" : [ {
            "name" : "namenode_id",
            "value" : "136"
          }, {
            "name" : "role_jceks_password",
            "value" : "41l6u0dqo9pas62z797xbnvwq"
          } ]
        }
      }, {
        "name" : "hdfs-SECONDARYNAMENODE-bf559074e806bdc0443cebe219727a84",
        "type" : "SECONDARYNAMENODE",
        "hostRef" : {
          "hostId" : "i-1f8e14a2"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5rcerx4vfctc8bu9k8mg16t2v"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "i-1f8e14a2",
    "ipAddress" : "172.31.25.137",
    "hostname" : "ip-172-31-25-137.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-1c8e14a1",
    "ipAddress" : "172.31.25.138",
    "hostname" : "ip-172-31-25-138.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-1d8e14a0",
    "ipAddress" : "172.31.25.139",
    "hostname" : "ip-172-31-25-139.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-228e149f",
    "ipAddress" : "172.31.25.140",
    "hostname" : "ip-172-31-25-140.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-238e149e",
    "ipAddress" : "172.31.25.141",
    "hostname" : "ip-172-31-25-141.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-090ba5a774c8734049252f1f0dce5eb1",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "2eb539cde29f253143b619b9d779d88a6f6c4fc78eff92772c1500c21ca0c12f",
    "pwSalt" : -3731700070572720341,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-090ba5a774c8734049252f1f0dce5eb1",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "54644a032473c19e391062d02cc01fcda5a0d20e69fed99d2b0f5641ebbaa5f4",
    "pwSalt" : -5286859312404281192,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-090ba5a774c8734049252f1f0dce5eb1",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "30b8bef6b68af1d9cf317bade0d42282b5af3175555b67496a6e99576c42f03a",
    "pwSalt" : 7912711190189703423,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-090ba5a774c8734049252f1f0dce5eb1",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "2926ad150f4eb457798f5fe1760de32a14d4da285acd757d6dd386e1ce5a7e3a",
    "pwSalt" : -1205364562744384588,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "1f35a67ef048b62ba27f71c7a4b166d7c400736ecf8133575d6c1b9ed81a7c94",
    "pwSalt" : -6856782722751409052,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "6f84981166b3dcc349a01a90b753dd2c923fd6c2387d4c4a8ce38cd2cba7ac57",
    "pwSalt" : -4262226229023535907,
    "pwLogin" : true
  }, {
    "name" : "rgaleanog",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "6be3e3e1a5c921b4d723ead301835aae4f73e22f7a33645938f715cc0bf97338",
    "pwSalt" : -4245813323896771792,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.8.2",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20160916-1426",
    "gitHash" : "d23c620f3a3bbd85d8511d6ebba49beaaab14b75",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "832569344"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "832569344"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1082130432"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-172-31-25-141.eu-central-1.compute.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "rman_pass"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        }, {
          "name" : "headlamp_heapsize",
          "value" : "832569344"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "832569344"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1082130432"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ALERTPUBLISHER-090ba5a774c8734049252f1f0dce5eb1",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "i-238e149e"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "d4gwtj0wflvzbsaadvx48s2ox"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-090ba5a774c8734049252f1f0dce5eb1",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "i-238e149e"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "2clm18jqsc2k0y9q6ncjdjy6t"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-090ba5a774c8734049252f1f0dce5eb1",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "i-238e149e"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "b2f9be7ay8lya5a8x4311oz8n"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-090ba5a774c8734049252f1f0dce5eb1",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "i-238e149e"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "2j2hfi2gsmi45lfhro5iuo8vv"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-090ba5a774c8734049252f1f0dce5eb1",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "i-238e149e"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "40zawi5d4f37mid4n85j2a0nt"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/22/2012 21:50"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    } ]
  }
}
```