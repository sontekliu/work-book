##Linux 一些基础配置

1.	配置IP
```
	DEVICE=eth0
	BOOTPROTO=static
	TYPE=Ethernet
	IPADDR=192.168.1.120
	NETMASK=255.255.255.0
	GATEWAY=192.168.1.1
	ONBOOT=yes
	DNS1=8.8.8.8
	DNS2=8.8.4.4
```
2.	配置主机(该配置需重启)
```
	vim /etc/sysconfig/network
	将HOSTNAME改成自己要设置的主机名称
	如：
		HOSTNAME=sontekliu

	vim /etc/hosts
	添加 对应IP和主机名
	如：
		192.168.1.120	sontekliu
```
4.	配置ssh免登陆
