# Archlinux 美化 - feh

`feh` 是用来设置壁纸的.

### 1. 首先安装 feh

```
$ sudo pacman -S feh
```

### 2. i3 配置 feh

```
exec_always --no-startup-id feh --bg-scale "path/xxxx.jpg"
```

