> 版本
hadoop 2.5.0
hbase 0.98.6-cdh5.3.0
zookeeper 3.4.5

1. 解压
- `tar -zxvf hbase-2.0.5-bin.tar.gz -C /opt/modules/`

2. 删除无用数据
- `rm -rf /opt/modules/hbase-2.0.5/docs/`

3. 配置
```
# hbase-env.sh
export JAVA_HOME=/usr/java/jdk-12.0.2
export HBASE_MANAGES_ZK=false
```
```
# habse-site.xml
<configuration>
  <property>
    <name>hbase.tmp.dir</name>
    <value>/opt/modules/hbase-2.0.5/data/tmp</value>
  </property>
  <property>
    <name>hbase.rootdir</name>
    # hdoop端口
    <value>hdfs://localhost:9000/hbase</value>
  </property>
  <property>
    <name>hbase.cluster.distributed</name>
    <value>true</value>
  </property>
  <property>
    <name>hbase.zookeeper.quorum</name>
    # zookeeper 端口
    <value>localhost:2181</value>
  </property>
  <property>
    <name>hbase.master.info.port</name>
    <value>60010</value>
  </property>
  <property>
     <name>zookeeper.znode.parent</name>
     <value>/hbase/master</value>
   </property>
</configuration>
```
```
# regionservers
localhost
```

4. 启动
- `yourPath/bin/start-hbase.sh`

5. web
- `localhost:60010`

6. 操作
- `yourPath/bin/hbase sheel`