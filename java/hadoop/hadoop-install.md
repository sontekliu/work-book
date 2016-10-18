## Haddoop 的安装

#### 1. 下载hadoop软件包
```
	访问 http://archive.apache.org/dist/ 下载hadoop的安装包
```

#### 2. 解压到指定目录
```
	tar -zxvf hadoop-xxx.tar.gz -C /hadoop
```

#### 3. 添加环境变量
```
	vim /etc/profile
	export HADOOP_HOME=/hadoop/hadoop-xxxx
	export PATH=$PATH:$HADOOP_HOME/bin
```
#### 4. 修改配置文件$HADOOP_HOME/etc/hadoop/hadoop-env.sh
```
	vim $HADOOP_HOME/etc/hadoop/hadoop-env.sh
	找到如下行
	export JAVA_HOME=${JAVA_HOME}
	修改如下：
	export JAVA_HOME=你自己的JAVA_HOME目录
```
#### 5. 修改$HADOOP_HOME/etc/hadoop/core-site.xml
```
	<configuration>
		<!-- 指定HDFS的老大 (NameNode) 的地址 -->
		<property>
			<name>fs.defaultFS</name>
			<value>hdfs://${host}:9000</value>
		</property>
		<!-- 用来指定hadoop运行时产生文件的地址 -->
		<property>
			<name>hadoop.tmp.dir</name>
			<value>${HADOOP_HOME}/tmp</value>
		</property>
	<configuration
```
#### 6. 修改$HADOOP_HOME/etc/hadoop/hdfs-site.xml
```
    <configuration>
		<!-- 指定HDFS保存数据副本的数量,本搭建为伪分布式，此值设置为1，若为分布式一般设置为3 -->
		<property>
			<name>dfs.replication</name>
			<value>1</value>
		</property>
	</configuration>
```
#### 7. 修改$HADOOP_HOME/etc/hadoop/mapred-site.xml，此文件可能不存在，复制mapred-site.xml.template
```
	<configuration>
		<!-- 告诉hadoop 以后mapreduce运行在yarn上 -->
		<property>
			<name>mapreduce.framework.name</name>
			<value>yarn</value>
		</property>
	</configuration>
```
#### 8. 修改$HADOOPHOME/etc/hadoop/yarn-site.xml
```
	<configuration>
		<property>
			<name>yarn.nodemanager.aux-services</name>
			<value>mapreduce_shuffle</value>
		</property>
		<property>
			<name>yarn.resourcemanager.hostname</name>
			<value>${hosts}</value>
		<property>
	<configuration>
```
#### 9. 初始化HDFS，即格式化文件系统
```
	hdfs namenode -format
```


