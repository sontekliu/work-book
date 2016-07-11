### CentOS YUM源的配置

**YUM简介** 
yum（全称为 Yellow dog Updater, Modified）是一个在Fedora和RedHat以及SUSE中的Shell前端软件包管理器。基於RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软体包，无须繁琐地一次次下载、安装。yum提供了查找、安装、删除某一个、一组甚至全部软件包的命令，而且命令简洁而又好记。

**本地YUM源的配置**

1、挂载系统安装光盘，命令如下：

# mount /dev/cdrom /mnt/cdrom/ 或者 # mount /dev/hdc   /media/cdrom

2、找到/etc/yum.repo.d/目录

3、下面有 CentOS-Base.repo和CentOS-Media.repo两个文件，分别对其备份为.bak文件

4、删除CentOS-Base.repo，否则先在网络源中寻找适合的包，改名之后直接从本地源读取。

5、修改CentOS-Media.repo 为：

[CentOS-Media]

name=CentOS-Media   #名称随便起

baseurl=file:///media/cdrom/   #mount 镜像文件的路径

gpgcheck=0  # 1表示启用，0表示不启用

enabled=1  # 1表示启用，0表示不启用

gpgkey=file:///usr/share/doc/centos-release-4/RPM-GPG-KEY-centos4

6、执行 yum clean all / yum makecache 启用当前的yum源

网络YUM源的配置

默认情况下，执行yum install命令时，先在网络资源中寻找合适的包，但是因为版本为CentOS4.X的镜像已关闭，所以导致安装CentOS4.X版本的系统时YUM报错，安装CentOS5.X和CentOS6.X则无此问题。难道CentOS4.X永远无镜像了？手工访问：http://mirror.centos.org/centos/4/发现里面没有任何软件包，只有一个readme。点开来一看：

This directory (and version of CentOS) is depreciated.
CentOS-4 is now past EOL
You can get the last released version of centos 4.9 here:
http://vault.centos.org/4.9/ 

大意是说，此目录已经没有任何价值了，因为CentOS-4已经停止发布了… 但是最后提供一个centos 4.9的下载链接：http://vault.centos.org/4.9/ 打开了一看，发现里面有个CentOS-Base.repo，正好CentOS的YUM源，执行：wget http://vault.centos.org/4.9/CentOS-Base.repo 将此YUM源下载到/etc/yum.repos.d目录CentOS5.x和CentOS6.x不需要做任何修改即可。

国内YUM源：

http://mirrors.163.com/.help/CentOS-Base-163.repo/ #网易YUM源

http://mirrors.sohu.com/help/CentOS-Base-sohu.repo #搜狐YUM源

执行 yum clean all / yum makecache 启用当前的yum源

