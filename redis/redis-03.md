### Redis配置

redis.conf 记录了配置文件的信息，可以通过修改该文件修改其配置信息
也可以通过config命令查看和设置配置项。

```
	# 查看配置项
	redis 127.0.0.1:6379> config get loglevel
	# 查看所有配置项
	redis 127.0.0.1:6379> config get *
	# 设置配置项
	redis 127.0.0.1:6379> config set loglevel "notice"
	OK
```

**Redis.conf 配置参数说明**   

参数名称         |  值                         |     说明
-----------------|-----------------------------|-----------------------------------------------------
daemonize        |  yes/no                     | 是否是守候线程启动，默认是no
pidfile          | /var/run/redis.pid          | redis以守候线程启动时，会把pid写入到pidfile文件中
port             |  6379                       | redis默认端口号
bind             | 127.0.0.1                   | 绑定的主机地址
timeout          | 300                         | 客户端闲置多久后关闭链接，0:表示关闭该功能
loglevel         | debug/verbose/notice/warning| 日志级别
logfile          | stdout                      | 日志记录方式，默认stdout，redis守候启动，日志输出到 /dev/null
database         | 10                          | 数据库数量
save             | <seconds> <changes>         | save 900 10 表示指定多久内有多少次更新就将数据同步到数据文件
rdbcompression   | yes                         | 存储本地数据库时，是否压缩
dbfilename       | dump.rdb                    | 指定本地数据库文件名，默认dump.rdb
dir              | ./                          | 指定本地数据库的存放目录
slaveof          | <masterip> <masterport>     | 当本机为slaveof时，设置master的ip和port，redis启动时，自动从master上数据同步
masterauth       | <master-password>           | 如果master设置了密码，slav链接master的密码





