# Arch Linux 网络配置

> 可以使用 systemd-networkd, dhcpcd, netctl, network-manager等配置 Archlinux 网络  
> dhcpcd 是 Arch Linux 默认提供的网络配置工具，功能比较强大，network-manager 默认没有安装 如果需要此配置网络，则还得需要安装。

`Arch Linux` 安装之后，默认获取动态 IP 地址为 `IPv6`，如果想动态获取 `IPv4` 需要修改配置文件，修改文件为：`/etc/dhcpcd.conf`
原内容如下：
```
# Generate SLAAC address using the Hardware Address of the interface
#slaac hwaddr
# OR generate Stable Private IPv6 Addresses based from the DUID
slaac private
noipv4ll
```
修改后内容如下：
```
# Generate SLAAC address using the Hardware Address of the interface
#slaac hwaddr
# OR generate Stable Private IPv6 Addresses based from the DUID
# slaac private
# noipv4ll
```

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
$ sudo cp /etc/netctl/ethernet-static  /etc/netctl/enp5s0
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
# 你的IP地址,注意中间是空格
Address=('192.168.3.76/24' '192.168.3.12/24')
# 路由配置
# Routes=('192.168.0.0/24 via 192.168.3.1')
# 网关
Gateway=('192.168.3.1')
# DNS 配置,注意中间是空格
DNS=('114.114.114.114' '8.8.8.8')

## For IPv6 autoconfiguration
#IP6=stateless

## For IPv6 static address configuration
#IP6=static
#Address6=('1234:5678:9abc:def::1/64' '1234:3456::123/96')
#Routes6=('abcd::1234')
#Gateway6='1234:0:123::abcd'
```
关闭 `dhcpcd` 的网络服务，开启 `netctl` 服务
```
$ sudo systemctl stop dhcpcd        # 停止服务
$ sudo systemctl disable dhcpcd     # 开机不启动

$ sudo netctl enable enp5s0         # 开机启动
$ sudo netctl start enp5s0          # 启动服务
```
重启测试是否生效
```
$ sudo reboot
```

### 2. netctl 配置动态IP
`netctl` 配置动态 IP 和 配置静态 IP  的方式差不多，有一些细节可参考上面的内容，下面只说一下差别。

首先，复制示例配置文件到 `/etc/netctl/` 目录中，命令如下：
```
$ sudo cp /etc/netctl/ethernet-dhcp  /etc/netctl/enp5s0
```
以网络接口的名称重命名示例配置文件。

编辑此文件，此文件默认内容为：
```
Description='A basic dhcp ethernet connection'
Interface=eth0
Connection=ethernet
IP=dhcp
#DHCPClient=dhcpcd
#DHCPReleaseOnStop=no
## for DHCPv6
#IP6=dhcp
#DHCP6Client=dhclient
## for IPv6 autoconfiguration
#IP6=stateless
```
修改后如下：
```
Description='A basic dhcp ethernet connection'
Interface=enp5s0
Connection=ethernet
IP=dhcp
#DHCPClient=dhcpcd
#DHCPReleaseOnStop=no
## for DHCPv6
#IP6=dhcp
#DHCP6Client=dhclient
## for IPv6 autoconfiguration
#IP6=stateless
```
关闭 `dhcpcd` 的网络服务，开启 `netctl` 服务
```
$ sudo systemctl enable dhcpcd    # 开机启动
$ sudo systemctl start dhcpcd     # 启动服务

$ sudo netctl stop enp5s0         # 停止服务
$ sudo netctl disable enp5s0      # 开机不启动
```
重启测试是否生效
```
$ sudo reboot
```

### 3. 使用 systemd-network 配置静态IP

首先，在 `/etc/systemd/network/` 目录下创建文件，默认此目录无任何文件，命令如下:
```
$ sudo touch /etc/systemd/network/enp5s0.network
```
添加如下内容：
```
[Match]
Name=enp5s0

[Network]
Address=192.168.3.12/24
Gateway=192.168.3.1
DNS=114.114.114.114
DNS=8.8.8.8
```
关闭之前的网络服,如果之前是 `dhcpcd` 或者 `netctl` 均关闭，以免造成干扰
```
$ sudo systemctl stop dhcpcd         # 停止服务
$ sudo systemctl disable dhcpcd      # 开机不启动

$ sudo netctl stop enp5s0            # 停止服务
$ sudo netctl disable enp5s0         # 开机不启动
```
启动 `systemd-networkd` 和 `systemd-resolved` 服务
```
sudo systemctl enable systemd-networkd
sudo systemctl start systemd-networkd

sudo systemctl enable systemd-resolved
sudo systemctl start systemd-resolved
```
注意，`systemd-resolved` 服务是可选的，如果不启动服务，则需要在 `/etc/resolv.conf` 中配置 `DNS`。如果启动该服务则只需要在 `/etc/systemd/network/enp5s0.network` 中配置 `DNS` 即可。

重启测试是否生效
```
$ sudo reboot
```

### 4. 使用 systemd-networkd 配置动态 IP
使用 `systemd-networkd` 配置动态 IP 和配置静态 IP 类似，可参考以上内容，这里只是说一下差别。  
在 `/etc/systemd/network/` 目录下创建文件，命令如下：
```
$ sudo touch /etc/systemd/network/enp5s0.network
```

添加如下内容：
```
[Match]
Name=enp5s0

[Network]
DHCP=ipv4
```
重启测试是否生效
```
$ sudo reboot
```

### 5. 手动配置网络
```
# 查看服务状态
$ sudo systemctl status dhcpcd
# 重启服务
$ sudo systemctl restart dhcpcd

# 设置 IP 地址
$ sudo addr add 192.168.3.76/24 dev enp5s0
# 设置网关
$ sudo ip route add default via 192.168.3.1

# 配置 DNS
$ sudo vim /etc/resolv.conf
$ nameserver 114.114.114.114
$ nameserver 8.8.8.8
```


参考资料：https://www.ostechnix.com/configure-static-dynamic-ip-address-arch-linux/ [点击这里](https://www.ostechnix.com/configure-static-dynamic-ip-address-arch-linux/)



### 6. archlinux 无线网络配置

* 安装软件

```shell
sudo pacman -S iw
sudo pacman -S dialog
```

* 1. 首先获取接口名称：

```
# iw dev 
输出如下：
phy#0 
    Interface wlp0s19f2u1
            ifindex3
            wdev 0x1
            addr 12:34:56:78:9a:bc
            type managed
            channel 1 (2412 MHz), width: 40 MHz, center1: 2422 MHz
```
`wlp0s19f2u1` 是无线接口名称。

如果获取不到无线接口名称，那可能是无线网卡驱动没有安装好，具体检查无线网卡驱动安装，参看如下：

https://wiki.archlinux.org/index.php/Wireless_network_configuration_(简体中文)#安装_driver/firmware

我的无线网卡是博通系列，可参考如下：

http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/#Other_distributions_not_mentioned_above


* 2. 检查链接状态
```
# iw dev wlp0s19f2u1 link
Not connected.
```
表示未链接到无线网络

* 3. 激活网线网络接口
```
# ip link set wlp0s19f2u1 up
```
* 4. 查看无线网络接口启用状态
```
# ip link show wlp0s19f2u1
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 12:34:56:78:9a:bc brd ff:ff:ff:ff:ff:ff
```
`<BROADCAST,MULTICAST,UP,LOWER_UP>` 中的`UP` 显示接口已经打开。

* 5. 查看可接入的无线网
```
# iw dev wlp0s19f2u1 scan | less
```
其中 `SSID` 是无线网络名称

* 6. 链接到无线网络
    - 链接到无加密的无线网络
    ```
    # iw wlp0s19f2u1 connect SSID
    ```
    - 链接到 WPA/WPA2 加密类型的网络
    ```
    # wpa_supplicant -i wlp0s19f2u1 -c <(wpa_passphrase SSID PASSWORD)
    # iw dev wlp0s19f2u1 link  查看链接情况
    ```
* 7. 获取ip地址
    - DHCP
    ```
    # dhcpcd wlp0s19f2u1
    ```
    - 静态 IP
    ```
    # ip addr add 192.168.0.2/24 dev wlp0s19f2u1
    # ip route add default via 192.168.0.1
    ```

* 8. 遇到的问题

```
The interface of network profile 'wlan0-ssid' is already up
```

将接口 down 即可解决，再次重启即可

```shell
# ip link set wlan0 down
# netctl start wlan0-ssid
```



