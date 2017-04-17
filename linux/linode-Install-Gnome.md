Linode VPS 安装Gnome VNC (CentOS 6)

安装Gnome

1. 安装Gnome桌面环境，执行如下命令：
	# yum groupinstall "X Window System" "Desktop Platform" Desktop
2. 安装相应的字体以及管理工具
	# yum -y groupinstall "Graphical Administration Tools"
	# yum -y groupinstall "Internet Browser"
	# yum -y groupinstall "General Purpose Desktop"
	# yum -y groupinstall "Office Suite and Productivity"
	# yum -y groupinstall "Graphics Creation Tools"
3. 修改系统默认启动级别，默认是命令行，现改成桌面
	编辑 /etc/inittab，将 id:3:initdefault: 改为 id:5:initdefault:。
4. 重启系统
	# reboot

安装VNC

1. 软件安装
	# yum install tigervnc-server
	# yum install xorg-x11-fonts-Type1
	# yum install vnc(可选)
2. 设置开机启动
	# chkconfig vncserver on
3. 设置密码(VNC登录时的密码)
	# vncpasswd
	Password:
	Verify:
4. 编辑VNC配置文件
	# vim /etc/sysconfig/vncservers
	在文件末尾添加如下：
	VNCSERVERS="1:root"
	VNCSERVERARGS[1]="-geometry 1920x1080"
5. 启动VNC
	# service vncserver start
6. 编辑xstartup文件
	vim ~/.vnc/xstartup
	添加如下
	# twm &
	exec gnome-session &
7. 重新启动VNC
	# service vncserver restart
8. 下载VNC Viewer连接服务器
	IP地址:1
	密码

解决中文乱码问题

1. 安装中文语言包
	# yum -y groupinstall chinese-support
2. 设置相应的字符集编码
	2.1 临时生效
	# export LANG="zh_CN.UTF-8"    # 设置为中文
 
	2.2 永久生效
	编辑/etc/sysconfig/i18n（最好reboot一下）
	LANG="zh_CN.UTF-8"
	或者编辑 /etc/profile 配置文件，添加如下一行
	export LANG="zh_CN.UTF-8"
	重新载入
	# . /etc/profile
	查看当前的字符集
	# echo $LANG
	
	
	
[参考资料]
https://cnzhx.net/blog/centos-yum-install-desktop/
https://rbgeek.wordpress.com/2012/06/26/how-to-install-vnc-server-on-centos-6/
http://www.ha97.com/4634.html
http://www.centoscn.com/image-text/install/2015/0211/4687.html
http://skypegnu1.blog.51cto.com/8991766/1545449


























