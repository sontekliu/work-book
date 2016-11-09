### Linux下网络对时

#### 1. 安装ntpdate

	yum install ntpdate

#### 2. 设置自己的时区

		# vim /etc/sysconfig/clock        
		ZONE = "Asia/Shanghai"

#### 3. 执行命令，同步时间

	ntpdate	us.pool.ntp.org
	ntpdate	time.nist.org

