# install

1. 包下载 [hadoop-2.9.2.tar.gz]
- http://archive.cloudera.com/cdh5/cdh/5/
- https://archive.apache.org/dist/

2. 解压
- `tar -zxvf hadoop-2.9.2.tar.gz -C /opt/modules/`

3. 删除无用数据
- `rm -rf /opt/modules/hadoop-2.9.2/share/doc/`
- `rm -rf /opt/modules/hadoop-2.9.2/etc/hadoop/*.cmd`

4. 配置
```
# /opt/modules/hadoop-2.9.2/etc/hadoop/hadoop-env.sh
# 将${JAVA_HOME} 修改为本地java路径
export JAVA_HOME=/usr/java/jdk-12.0.2
```
```
# /opt/modules/hadoop-2.9.2/etc/hadoop/core-site.xml
# 创建tmp目录后进行配置
<configuration>
    <property>
        <name>fs.defaultFS</name>
        <value>hdfs://localhost:9000</value>
    </property>

    <property>
        <name>hadoop.tmp.dir</name>
        <value>/opt/modules/hadoop-2.9.2/data/tmp</value>
    </property>
</configuration>
```
```
# /opt/modules/hadoop-2.9.2/etc/hadoop/hdfs-site.xml
<configuration>
    <property>
        <name>dfs.replication</name>
        <value>1</value>
    </property>

    <property>
        <name>dfs.permissions.enabled</name>
        <value>false</value>
    </property>
</configuration>
```
```
# /opt/modules/hadoop-2.9.2/etc/hadoop/slaves
localhost
```
5. 启动
- `/opt/modules/hadoop-2.9.2/bin/hdfs namenode -format`
- `/opt/modules/hadoop-2.9.2/sbin/hadoop-daemon.sh start namenode`
- `/opt/modules/hadoop-2.9.2/sbin/hadoop-daemon.sh start datanode`

6. 查看进程
- `jps`

7. 访问
- `http://localhost:50070/`