> hbase ServerNotRunningYetException: Server is not runn
关闭hadoop安全模式 `./bin/hdfs dfsadmin -safemode leave`,重启Hbase
若不行 停止hbase、hadoop、zk集群；删除datanode节点中的临时文件，删除zk下dataDir中的version-2文件；重新格式化namenode，和zkcf；重启zk、hadoop、hbase集群；（删除每个节点中的hadoopdata，然后格式化namenode：hdfs namenode -format）
