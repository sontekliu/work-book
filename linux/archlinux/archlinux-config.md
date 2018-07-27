# ArchLinux Config

### Install Yaourt

```
$ sudo vim /etc/pacman.conf

[archlinuxcn]
# the Chinese Arch Linux communities packages
# SigLevel = Optional TrustAll
SigLevel = Never
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch

$ sudo pacman -Syy
$ sudo pacman -Syu yaourt
```

### Install fcitx

[reference](http://echoyun.com/2017/10/02/installing-fcitx-chinese-ime-arch-linux/)

https://fcitx-im.org/wiki/Input_method_related_environment_variables/zh-hans

```
$ sudo pacman -Syu fcitx fcitx-googlepinyin fcitx-im  fcitx-configtool

```

### Install google-chrome

```
$ sudo pacman -S google-chrome
```
