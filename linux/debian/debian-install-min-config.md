# Debian 安装完成之后的简单配置

#### 1. 配置静态IP （root 用户操作）

编辑如下文件：/etc/network/interfaces

```shell
auto enp0s3
iface enp0s3 inet static
address 192.168.1.160
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 114.114.114.114 8.8.8.8
```

重启网络

```shell
# systemctl enable networking
# systemctl restart networking	#重启网络
# systemctl status networking	#查看状态
# ip addr			#查看IP地址
# ping www.baidu.com
```

#### 2. 更换阿里云镜像或者 163 的也可以 (root用户操作)

备份原来的镜像  

```shell
# cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

编辑 `/etc/apt/sources.list` 输入如下内容

```shell
deb http://mirrors.aliyun.com/debian stretch main contrib non-free
deb-src http://mirrors.aliyun.com/debian stretch main contrib non-free
deb http://mirrors.aliyun.com/debian stretch-updates main contrib non-free
deb-src http://mirrors.aliyun.com/debian stretch-updates main contrib non-free
deb http://mirrors.aliyun.com/debian-security stretch/updates main contrib non-free
deb-src http://mirrors.aliyun.com/debian-security stretch/updates main contrib non-free
```

执行如下命令

```shell
# apt update
# apt list --upgradable
# apt upgrade
```

#### 3. 添加 sudo 权限 （root用户操作）

```shell
# apt install sudo
# vi /etc/sudoers
```

找到如下内容

```shell
# User privilege specification
root 	ALL=(ALL:ALL) ALL
```

在 `root  ALL=(ALL:ALL) ALL` 添加如下内容

```shell
sontek  ALL=(ALL:ALL) ALL
:wq!    # 保存退出
```

#### 4. 安装 vim, zsh, git, curl, wget, net-tools, on-my-zsh

```shell
$ sudo apt install vim zsh git curl wget net-tools
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

若更换 oh-my-zsh 主题，可编辑 `~/.vimrc` 将 `ZSH_THEME="robbyrussell"` 替换为 `ZSH_THEME="ys"` 即可。