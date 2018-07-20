# Debian Install

1. 安装 Virtual-Box Tools
```
	# cp  -R /media/cdrom0 /tmp
	# cd /tmp/cdrom0/
	# ./autorun.sh  或者 ./VBoxLinuxAdditions.run
	# reboot
```

2. 添加 sudo 权限 （root用户操作）
```
	# vi /etc/sudoers
	找到 
	# User privilege specification
	root 	ALL=(ALL:ALL) ALL
	添加如下内容
	sontek  ALL=(ALL:ALL) ALL
	wq! 保存退出 vi
```

3. debian 网络配置 (root用户操作)
```
	# vim /etc/network/interfaces
	# 查看 设备名称 
	# ip addr 
	systemctl disable network-manager
	systemctl enable networking
```

4. 安装open-ssh，并配置
   # apt install ssh
   # vim /etc/ssh/sshd_config
   // 见阮一峰配置

3. 更换阿里云镜像或者 163 的也可以 (root用户操作)
	# cp /etc/apt/sources.list /etc/apt/sources.list.bak
	输入如下内容
	deb http://mirrors.aliyun.com/debian stretch main contrib non-free
	deb-src http://mirrors.aliyun.com/debian stretch main contrib non-free
	deb http://mirrors.aliyun.com/debian stretch-updates main contrib non-free
	deb-src http://mirrors.aliyun.com/debian stretch-updates main contrib non-free
	deb http://mirrors.aliyun.com/debian-security stretch/updates main contrib non-free
	deb-src http://mirrors.aliyun.com/debian-security stretch/updates main contrib non-free
	执行如下命令
	apt update
	apt list --upgradable
	apt upgrade

4. 安装 zsh, on-my-zsh, Vim, git 并配置（普通用户）
	vim
	$ sudo apt install vim
	zsh
	$ sudo apt install zsh
	git
	$ sudo apt install git
	oh-my-zsh
	$ sudo apt install curl wget
	$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
	可以更换主题
	vim .zshrc 
	将如下内容替换即可
	ZSH_THEME="robbyrussell"  --> ZSH_THEME="ys"
	$ source ./.zshrc   使修改生效
5. 安装搜狗输入法(安装前看看有啥输入法)
   到搜狗输入法官方网站，下载 linux 版搜狗拼音输入法
   $ sudo dpkg -i sogoupinyin_version_amd64.deb
   // 安装错误图片
   $ sudo apt install libqt4-declarative zip fcitx-libs
   继续安装搜狗拼音输入法
   $ sudo reboot
6. 安装 i3 窗口管理器
   $ sudo apt install i3
   https://www.devpy.me/your-guide-to-a-practical-linux-desktop-with-i3wm/
7. 安装JDK
	Oracle 官网下载 JDK
   tar -zxvf jdk-8u151-linux-x64.tar.gz
   $ mkdir -p ~/opt/mysoftware
   配置环境变量
   $ vim .zshrc  添加如下内容
   ```
    export JAVA_HOME=~/opt/mysoftware/jdk1.8.0_151
	export CLASSPATH=.:$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar
	export PATH=$JAVA_HOME/bin:$PATH
   ```
   $ source .zshrc
8. 安装 maven
	$ tar -zxvf apache-maven-3.5.4-bin.tar.gz -C opt/mysoftware
	配置环境变量
    $ vim .zshrc  添加如下内容
   ```
    export MVN_HOME=~/opt/mysoftware/maven3.5.4
	export PATH=$MVN_HOME/bin:$PATH
   ```
    $ source .zshrc
    $ mvn -v
	编辑
	$MVN_HOME/conf/settings.xml
	修改如下
	<localRepository>~/opt/repo<localRepository>
8. 安装IDEA
	从官网下载 Linux 版本的IDEA
   $ tar -zxvf ideaIU-2018.1.6.tar.gz -C opt/mysoftware
   激活IDEA 请参考 http://idea.liyang.io/
   https://blog.csdn.net/qq_35246620/article/details/79050895

   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   


