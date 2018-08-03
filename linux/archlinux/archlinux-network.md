# Arch Linux 网络配置

> 可以使用 systemd-networkd, dhcpcd, netctl, network-manager等配置 Archlinux 网络
> dhcpcd 是 Arch Linux 默认提供的网络配置工具，功能比较强大，network-manager 默认没有安装 需要 安装

### 1. netctl 配置静态 IP
`netctl` 是 `base` 组的成员，所以系统中已默认安装了。`netctl` 是一个命令行应用程序
，使用配置文件来管理网络链接。在 `/etc/netctl/examples` 目录下面有一些网络配置的示例。  
```
$ ls /etc/netctl/examples/
```
输出如下：
```
bonding bridge ethernet-custom ethernet-dhcp ethernet-static macvlan-dhcp
macvlan-static mobile_ppp openvswitch pppoe tunnel tuntap vlan-dhcp vlan-static
wireless-open wireless-wep wireless-wpa wireless-wpa-config 
wireless-wpa-configsection wireless-wpa-static
```
如上，可以使用 `ethernet-static` 和 `ethernet-dhcp` 两个配置文件来配置网络。

首先，查看本机的网络接口名称，命令如下：
```
$ ip link
```
输出如下：
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether c8:5b:76:41:4e:1d brd ff:ff:ff:ff:ff:ff
```
本机网络接口名称为 `enp5s0`，你的机器可能不同。

复制示例配置文件到 `/etc/netctl/` 目录中，命令如下：
```
$ sudo cp /etc/netclt/ethernet-static  /etc/netctl/enp5s0
```
以网络接口的名称重命名示例配置文件。  

编辑此文件，此文件默认内容为：
```

Description='A basic static ethernet connection'
Interface=eth0
Connection=ethernet
IP=static
Address=('192.168.1.23/24' '192.168.1.87/24')
#Routes=('192.168.0.0/24 via 192.168.1.2')
Gateway='192.168.1.1'
DNS=('192.168.1.1')

## For IPv6 autoconfiguration
#IP6=stateless

## For IPv6 static address configuration
#IP6=static
#Address6=('1234:5678:9abc:def::1/64' '1234:3456::123/96')
#Routes6=('abcd::1234')
#Gateway6='1234:0:123::abcd'
```
修改后如下：
```

Description='A basic static ethernet connection'
# 你的网络接口
Interface=enp5s0
Connection=ethernet
IP=static
# 你的IP地址
Address=('192.168.3.76/24')
# 路由配置
Routes=('192.168.3.76/24 via 192.168.3.1')
# 网关
Gateway='192.168.3.1'
# DNS 配置
DNS=('114.114.114.114','8.8.8.8')
```


[参考资料](https://www.ostechnix.com/configure-static-dynamic-ip-address-arch-linux/)

















