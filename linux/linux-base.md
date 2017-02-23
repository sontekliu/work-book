## Linux 基本原则

1、由目的单一的小程序组成：组合小程序完成复杂任务
2、一切皆文件
3、尽量避免捕获用户接口
4、配置文件保存为纯文本格式

命令格式：
    命令  选项  参数
        选项：
            短选项：-
            长选项：--
        参数：命令的作用对象


## Linux 一些基础配置

#### 1. 配置IP
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
#### 2. 配置主机(该配置需重启)
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
##### 3. 关闭防火墙  
```
	查看防火墙状态
	service iptables status
	停用、启用、重启防火墙
	service iptables stop/start/restart
	开机不启用防火墙
	chkconfig iptables off
	查看防火墙开机启用状态
	chkconfig iptables --list
```

#### 4. 配置ssh免登陆         
```
	1)首先生成公钥和私钥，生成方式如下：    
	ssh-keygen -t rsa	# 默认在 ~/.ssh目录下生成id_rsa(私钥)、id_rsa.pub()   
	-t 表示指定加密方式  
	2)将公钥上传到要免登陆的服务器，并导入到认证文件中  
	scp ~/.ssh/id_rsa.pub xxx@host:/home/xxx/id_rsa.pub  
	cat ~/id_rsa.pub >> ~/.ssh/authorized_keys       
	或者直接         
	ssh-copy-id desc_host(目标主机)        
	3)测试  
	ssh des_host       
```
