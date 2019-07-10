# Archlinux 美化 - rofi

`rofi` 显示启动菜单.

### 1. 首先安装 rofi

```
$ sudo pacman -S rofi
```

### 2. 配置 rofi 启动，我的是 i3 

```
bindsym $mod + d exec rofi -show run
```

### 3. 配置样式

编辑 `~/.Xresources` 配置文件，添加如下内容：
```
rofi.color-enabled: true
rofi.color-window: #272827, #13bf9d, #13bf9d
rofi.color-normal: #272827, #657b83, #272827, #272827, #13bf9d
rofi.color-active: #272827, #657b83, #272827, #272827, #13bf9d
rofi.color-urgent: #272827, #657b83, #272827, #272827, #13bf9d

rofi.separator-style: solid
rofi.sidebar-mode: false
rofi.lines: 5
rofi.font: Monaco 12
rofi.bw: 1
rofi.columns: 2
rofi.padding: 5
rofi.fixed-num-lines: true
rofi.hide-scrollbar: true
```
