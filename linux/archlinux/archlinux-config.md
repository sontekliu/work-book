# Archlinux 安装之后的配置

### 1. 连接网络
默认情况下，安装完 `archlinux` 之后，默认是连上网络的。使用如下命令测试：

```
# ping www.baidu.com
```
如果连接不成功，则需要配置网络

### 2. 创建普通用户

```
# useradd -m -G wheel sontek
# passwd sontek

 安装 sudo
# pacman -S sudo 
# vim /etc/sudoers

添加如下内容：
root ALL=(ALL) ALL
sontek ALL=(ALL) ALL
```

### 3. 安装显示服务

```
$ sudo pacman -S xorg 
$ sudo pacman -S xorg-xinit
```

### 4. 安装终端模拟器
安装窗口管理器前要先安装终端模拟器，否则，窗口管理器没有默认启动项
```
$ sudo pacman -S gnome-terminal
```
### 5. 安装窗口管理器
```
$ sudo pacman -S i3
$ sudo pacman -S dmenu
```
启动 i3
copy 文件到家目录
$ cp /etc/X11/xinit/xinitrc .xinitrc
编辑此文件，将启动 xterm 的行注释掉,添加启动 i3 项,
此文件只能存在一个未注释掉的 exec 行
```
#twm &
#xclock -geometry 50x50-1+1 &
#xterm -geometry 80x50+494+51 &
#xterm -geometry 80x20+494-0 &
#exec xterm -geometry 80x66+0+0 -name login

exec i3
```
修改i3 默认启动的终端模拟器，编辑 `~/.config/i3/config`
将如下内容修改如下：
修改前：
```
bindsym $mod+Return exec i3-sensible-terminal
```
修改后：
```
bindsym $mod+Return exec gnome-terminal
```
### 6. 安装 Yaourt
编辑 /etc/pacman.conf 文件，在最下面添加如下：

```
[archlinuxcn]
#The Chinese Arch Linux communities packages.
SigLevel = Optional TrustAll  
Server   = https://mirrors.ustc.edu.cn/archlinuxcn/$arch  
```

然后执行安装
```
$ sudo pacman -Syu yaourt
```

### 7. 安装浏览器
```
$ sudo pacman -S firefox
$ sudo pacman -S google-chrome
```
 启动 firefox 按下 $mod+d 输入 `firefox` 回车
 启动 chrome 按下 $mod+d 输入 `google-chrome-stable` 回车

### 8. 安装字体
```
$ sudo pacman -S wqy-microhei
```

### 
