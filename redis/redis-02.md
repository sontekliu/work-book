### Redis 安装(Linux)

**1. 下载Redis安装包**   

	浏览器输入: http://redis.io Redis官方网址，下载stable version版本 

**2. 解压缩安装**  

```
	tar -zxvf redis-3.2.3.tar.gz 
	cd redis-3.2.3
	make      # 官网下载完成之后就已经configure了，所以直接make
	make test
	make install 
	cp redis.conf /etc/
	至此，安装完毕
	cd /usr/local/bin
	该目录下多了如下文件:
	redis-benchmark                 #redis性能测试工具,测试redis在当前系统的读写性能
	redis-check-aof                 #检查aof日志的工具
	redis-check-dump                #检查rdb日志的工具
	redis-cli                       #客户端链接工具
	redis-sentinel -> redis-server
	redis-server                    #redis启动服务工具
```

**3. 启动Redis服务**  

```
	$ cd /usr/local/bin
	$ ./redis-server /etc/redis.conf
	$ ps -ef | grep redis
```




