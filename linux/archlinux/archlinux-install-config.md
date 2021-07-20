# Archlinux 安装完成之后的配置

### 1. 连接网络
默认情况下，安装完 `archlinux` 之后，默认是连上网络的。使用如下命令测试：

```
# ping www.baidu.com
```
如果连接不成功，则需要配置网络.

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
$ sudo pacman -S xorg-server xterm xorg-xeyes xorg-xclock
$ sudo pacman -S xorg-xinit
$ sudo pacman -S xf86-video-vesa
```
执行 `startx` 可以看一下效果，可以看到会显示一个特别简陋的图形界面

除了手动启动 X 的方法外，还可以使用登录管理器（显示管理器）进行图形界面登录。以 sddm 为例:

```
# sudo pacman -S sddm
# sudp systemctl enable sddm.service
# reboot
```
重启之后，显示登录界面.

> Ctrl + Alt + F2  # tty login

### 4. 安装终端模拟器
安装窗口管理器前要先安装终端模拟器，否则，窗口管理器没有默认启动项
```
$ sudo pacman -S gnome-terminal
$ sudo pacman -S alacritty
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

### 9. install ssh zsh oh-my-zsh

```
$ sudo pacman -S openssh
$ sudo pacman -S zsh
```
安装 oh-my-zsh

```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### 10 安装中文输入法

```
$ sudo pacman -S fcitx fcitx-im fcitx-googlepinyin fcitx-sogoupinyin fcitx-configtool
```
编辑 `~/.xinitrc` 文件，添加如下：
```
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=@im=fcitx
```

编辑 `i3` 配置文件 `~/.config/i3/config`，使其启动 `i3` 的时候启动 `fcitx`，在该文件最后添加如下：
```
exec fcitx
```
此时，启动 `i3` 的时候在屏幕又下角，可以看到小键盘图标了。   
鼠标右击小键盘图标，选择 `configure -> +` 选择相应的输入法即可
汉化：
使其切换中文输入法，编辑 `~/.xinitrc` 文件，添加如下：
```
export LANG=zh_CN.UTF-8
export LANGUAGE=zh_CN:en_US
export LC_TYPE=zh_CN.UTF-8
```

### 11.  安装 screenfetch
```
$ sudo pacman -S screenfetch
$ sudo pacman -S neofetch
$ screenfetch    #  显示当前系统图标
```

### 12 按装 wps-office
```
$ sudo pacman -S wps-office
```
启动 work，excel，ppt 命令分别是 `wps`，`et`，`wpp`

### 13 安装 FTP 工具

```
$ sudo pacman -S filezilla
```

### 14. 安装邮件客户端

```
$ sudo pacman -S thunderbird
```

### 15 安装 nodejs
```
$ sudo pacman -S nodejs npm
```

### 16 安装 shadowsocks(没有shadowsocks帐号的可忽略此步)
```
$ sudo pacman -S shadowsocks-qt5
$ ss-qt5	# 启动客户端
```

### 17 同步时间
查看当前时间
```
$ timedatectl status
```
设置时区
```
$ sudo timedatectl set-timezone <Zone>/<SubZone>
$ sudo timedatectl set-timezone Asia/Shanghai
```

### 17 安装桌面环境(gnome)
```
$ sudo pacman -S gnome 
$ sudo pacman -S gnome-tweak-tool
```
编辑 `~/.xinitrc` 文件,添加如下内容:`exec gnome-session`,将原来的 `exec i3` 注释掉. 重启电脑


### 18 安装 QQ
首先编辑 `/etc/pacman.conf` 将如下内容注释掉  

```
[multilib]
Include = /etc/pacman.d/mirrorlist
```
更新仓库
```
$ sudo pacman -Syu
```
安装 wine
```
$ sudo pacman -S wine
```

安装 QQ
```
$ sudo pacman -S deepin.com.qq.im
```
现在可以在应用里面找到 QQ 并进行启动。但是如果不安装桌面环境，仅仅使用窗口管理器的话，例如：i3,则不能启动QQ .

