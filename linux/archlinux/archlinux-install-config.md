# Archlinux 安装完成之后的配置

### 1. 连接网络
默认情况下，安装完 `archlinux` 之后，默认是连上网络的。使用如下命令测试：

```shell
# ping www.baidu.com
```
如果连接不成功，则需要配置网络.

### 2. 创建普通用户

```shell
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

```shell
$ sudo pacman -S xorg-server xterm xorg-xeyes xorg-xclock
$ sudo pacman -S xorg-xinit
$ sudo pacman -S xf86-video-vesa xf86-video-intel nvidia nvidia-utils nvidia-settings
```
执行 `startx` 可以看一下效果，可以看到会显示一个特别简陋的图形界面

除了手动启动 X 的方法外，还可以使用登录管理器（显示管理器）进行图形界面登录。以 sddm 为例:

```shell
# sudo pacman -S sddm
# sudp systemctl enable sddm.service
# reboot
```
重启之后，显示登录界面.

> Ctrl + Alt + F2  # tty login

### 4. 安装 yay

编辑 /etc/pacman.conf 文件，在最下面添加如下：

```shell
Color # 将 Color 前面的注释去掉

[archlinuxcn]
#The Chinese Arch Linux communities packages.
# SigLevel = Optional TrustAll  
SigLevel = Never 
Server   = https://mirrors.ustc.edu.cn/archlinuxcn/$arch  
```

然后执行安装

```shell
$ sudo pacman -S yay
```

### 5. 安装一些必要软件

```shell
# terminal 终端
$ sudo pacman -S gnome-terminal       # Gnome 终端
$ sudo pacman -S alacritty            # 基于GPU渲染的终端
$ sudo pacman -S xfce4-terminal

$ sudo pacman -S firefox			  # 浏览器
$ sudo pacman -S google-chrome

$ sudo pacman -S openssh			  # 安装 zsh
$ sudo pacman -S zsh

$ sudo pacman -S scrot                 # 截屏软件
$ sudo pacman -S picom                 # 透明

$ sudo pacman -S rofi				   # 软件启动器
$ sudo pacman -S dmenu                 # 软件启动器

$ sudo pacman -S evince				   # PDF 阅读器
$ sudo pacman -S okular                # PDF 阅读器
$ sudo pacman -S thunar                # 文件管理器
$ sudo pacman -S ranger                # 终端文件管理器
$ sudo pacman -S netease-cloud-music   # 网易云音乐

$ sudo pacman -S vlc mplayer           # 视频播放器

$ sudo pacman -S lxappearance          # 图形的方式更换主题
$ sudo pacman -S variety               # 更换桌面
# 安装声音控制器
$ sudo pacman -S pulseaudio pulseaudio-bluetooth pulseaudio-alsa alsa-utils
$ sudo pacman -S pavucontrol playerctl

$ sudo pacman -S feh gimp              # 图片浏览和编辑软件

$ sudo pacman -S typora                # Markdown 编辑软件

# 以下软件根据自己的情况选择安装
$ sudo pacman -S simplescreenrecorder # record
$ sudo pacman -S obs-studio # record and stream
$ sudo pacman -S peek # gif
$ sudo pacman -S guvcview cheese # camera
$ sudo pacman -S screenkey # print the keys on the screen you entered 
$ sudo pacman -S flameshot # screenshot
$ sudo pacman -S hardinfo     # 以图形的方式显示硬件信息
$ sudo pacman -S baobab       # 以图形化的方式显示磁盘使用情况
$ sudo pacman -S screenfetch  # 不再使用
$ sudo pacman -S neofetch
$ sudo pacman -S thunderbird  # 邮件客户端
$ sudo pacman -S filezilla    # 安装 FTP 工具
$ sudo pacman -S nodejs npm   # 安装 nodejs
$ yay -S wps-office           # 启动 work，excel，ppt 命令分别是 `wps`，`et`，`wpp`
$ ysy -S xunlei-bin
```

### 5. 安装窗口管理器
```shell
$ sudo pacman -S i3
```
复制文件到家目录
$ cp /etc/X11/xinit/xinitrc .xinitrc
编辑此文件，将启动 xterm 的行注释掉,添加启动 i3 项,
此文件只能存在一个未注释掉的 exec 行

```shell
#twm &
#xclock -geometry 50x50-1+1 &
#xterm -geometry 80x50+494+51 &
#xterm -geometry 80x20+494-0 &
#exec xterm -geometry 80x66+0+0 -name login

exec i3
```
修改 i3 默认启动的终端模拟器，编辑 `~/.config/i3/config`
将如下内容修改如下：

```shell
$ i3-config-wizard    # 生成 I3 的默认配置
```

```shell
修改前
bindsym $mod+Return exec i3-sensible-terminal
修改为：
bindsym $mod+Return exec gnome-terminal
```
### 6. 安装字体
```shell
$ sudo pamcan -S wqy-microhei wqy-microhei-lite wqy-zenhei wqy-bitmapfont 
$ sudo pacman -S noto-fonts noto-fonts-cjk noto-fonts-emoji 
$ sudo pacman -S ttf-font-awesome ttf-dejavu ttf-liberation ttf-symbola ttf-arphic-ukai 
$ sudo pacman -S adobe-source-han-sans-otc-fonts adobe-source-han-serif-otc-fonts adobe-source-han-serif-cn-fonts adobe-source-han-sans-cn-fonts 
$ yay -S font-manager

$ sudo fc-cache -f -v  # 使用字体生效
```

### 7. 安装 oh-my-zsh

```shell
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### 8 安装中文输入法

```shell
$ sudo pacman -S fcitx fcitx-im fcitx-googlepinyin fcitx-sogoupinyin fcitx-configtool
```
编辑 `~/.xinitrc` 文件，添加如下：
```shell
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=@im=fcitx
```

编辑 `i3` 配置文件 `~/.config/i3/config`，使其启动 `i3` 的时候启动 `fcitx`，在该文件最后添加如下：
```shell
exec --no-startup-id fcitx
```
此时，启动 `i3` 的时候在屏幕又下角，可以看到小键盘图标了。   
鼠标右击小键盘图标，选择 `configure -> +` 选择相应的输入法即可
汉化：
使其切换中文输入法，编辑 `~/.xinitrc` 文件，添加如下：
```shell
export LANG=zh_CN.UTF-8
export LANGUAGE=zh_CN:en_US
export LC_TYPE=zh_CN.UTF-8
```

### 9. 安装蓝牙

```shell
$ sudo pacman -S bluez bluez-utils
$ sudo pacman -S pulseaudio-bluetooh

$ sudo pacman -S blueevil                  # 图形管理工具
$ sudo pacman -S blueman                   # 图形管理工具

$ sudo systemctl enable bluetooth
$ sudo systemctl start bluetooth
```



### 10 安装 qv2ray



### 10 安装桌面环境(gnome)

```shell
$ sudo pacman -S gnome 
$ sudo pacman -S gnome-tweak-tool
```
编辑 `~/.xinitrc` 文件,添加如下内容:`exec gnome-session`,将原来的 `exec i3` 注释掉. 重启电脑


### 11 安装 QQ
首先编辑 `/etc/pacman.conf` 将如下内容注释掉  

```shell
[multilib]
Include = /etc/pacman.d/mirrorlist
```
更新仓库
```shell
$ sudo pacman -Syu
```
安装 wine
```shell
$ sudo pacman -S wines
```

安装 QQ
```shell
$ sudo pacman -S deepin.com.qq.im
```
现在可以在应用里面找到 QQ 并进行启动。但是如果不安装桌面环境，仅仅使用窗口管理器的话，例如：i3,则不能启动QQ .

