# i3 配置与使用

### 1. i3 的安装
```
$ sudo pacman -S i3
$ sudo pacman -S dmenu
```
i3是一个软件包组，默认会安装 `i3-gaps`、`i3-wm`、`i3blocks`、`i3lock`、`i3status`。
`dmenu` 是一个菜单管理工具，安装此软件之后，按下 `$mod+d` 可以启动相应的软件，例如 `firefox`

### 2. i3的使用
默认情况下，`$mod` 键是 `Alt` 键，可以修改成其他键，一般修改为 `win` 键，即 `Alt` 键和 `Ctrl` 键之间的键。
```
set $mod Mod1	# 设置 $mod 键为 Alt
set $mod Mod4   # 设置 $mod 键为 win

font pango:monospace 8  设置字体和字号
```

* $mod + Enter 开启终端，默认占满整个屏幕。再次按下将再启动一个终端，并且垂直平分两个屏幕
* $mod + shift + q 关闭当前活动的窗口
* $mod + d 显示应用的名称，你可以输入相应的应用并启动,$PATH 中的应用

* $mod + j 可以将焦点切换到左边
* $mod + ; 可以将焦点切换到右边
* $mod + k 可以将焦点切换到下边
* $mod + l 可以将焦点切换到上边

* $mod + Left 	可以将焦点切换到左边
* $mod + Right 	可以将焦点切换到右边
* $mod + Down 	可以将焦点切换到下边
* $mod + Up 	可以将焦点切换到上边

* $mod + Shift + j 可以将窗口移动到左边
* $mod + Shift + ; 可以将窗口移动到右边
* $mod + Shift + k 可以将窗口移动到下边
* $mod + Shift + l 可以将窗口移动到上边

* $mod + Shift + Left 	可以将窗口移动到左边
* $mod + Shift + Right 	可以将窗口移动到右边
* $mod + Shift + Down 	可以将窗口移动到下边
* $mod + Shift + Up 	可以将窗口移动到上边

* $mod + v 水平平分屏幕，即，再次启动终端时,将水平切分屏幕
* $mod + h 垂直平分屏幕，即，再次启动终端时,将垂直切分屏幕

* $mod + f 全屏显示当前窗口,多次按会来回切换

* $mod + w 按标签的形式显示窗口
* $mod + s 按堆积的形式显示窗口
* $mod + e 按水平或者垂直的形式显示窗口

* $mod + a		使焦点集中到父级窗口
* $mod + shift + Space 	使窗口浮动在其他窗口上
* $mod + Space 		浮动窗口与平铺窗口来回切换

* $mod + num 切换到某个工作区，num的值是 1-9 还有 0.
* $mod + shift + num 将当前活动的窗口移动到对应的工作区

* $mod + shift + e 注销 i3
* $mod + shift + c 重新加载 i3 配置文件
* $mod + shift + r 重新启动 i3, 修改配置文件后可以使其生效

以上均是在 i3 的默认模式下的操作，i3 还有其他模式，如 `resize`

* $mod + r 进入 resize 模式,按 回车， ESC，或者再次按 $mod + r 则恢复默认模式
`resize` 模式可以按上下左右键或者 `jkl;` 键调整窗口大小

以上是 i3 默认的配置

### 3. i3 配置与美化
配置文件的位置，全局配置文件 `/etc/i3/config`,用户配置文件：`～/.config/i3/config`
也可以运行 `i3-config-wizard` 来生成配置文件。  
需要安装的软件包：
```
$ sudo pacman -S feh
$ sudo pacman -S ranger
```
配置如下：
```
# 字体配置，即，窗口所显示的字体的类型和大小
font pango:DejaVu Sans Mono 10

# 绑定快捷键
bindsym $mod + f    fullscreen toggle
bindsym $mod + Shift + r    restart
bindsym $mod + Shift + x    exec    i3lock

# 绑定鼠标（待完善）

# 绑定模式
# mod + o 进入 mode_launcher 模式，按 f 启动 firefox,按 t 启动 thunderbird
bindsyn $mod + o mode "mode_launcher"
mode "mode_launcher" {
    bindsym f exec firefox
    bindsym t exec thunderbird

    bindsym Escape mode "default"
    bindsym Return mode "default"
    bindsym $mod + o mode "default"
}

# 浮动修饰符
# 按下 mod 键和鼠标一块即可移动浮动的窗口
floating_modifier $mod

# 浮动窗口的大小
floating_minimum_size <width> x <height>
floating_maximum_size <width> x <height>

# 工作区间分屏方向  水平        垂直    自动
default_orientation horizontal|vertical|auto

# 默认的新容器的布局
workspace_layout default|stacking|tabbed

# 默认的新窗口的边框样式
default_border  normal|none|pixel
default_border  normal|pixel <px>
default_floating_border  normal|none|pixel
default_floating_border  normal|pixel <px>
# 例如
default_border none
default_border pixel 0
default_border pixel 3

# 靠近屏幕边缘时，隐藏边框
hide_edge_borders none|vertical|horizontal|both|smart

# 特殊应用对应的特殊窗口处理
for_window [class="urxvt"] border pixel 1
for_window [title="x200: ~/work"] floating enable

# 设置变量
set $<name> <value>
set $m Mod1
bindsym $m+Shift+r restart

# 自动将不同的客户端应用放到特殊的工作区间
assign <criteria> [->] [workspace] [number] <workspace>
assign <criteria> [->] output left|right|up|down|primary|<output>
# Examples
assign [class="URxvt"] 2
assign [class="^URxvt$"] 2  # 精确匹配
assign [class="^URxvt$"] -> 2  # 工作区名字 ->2 
assign [class="^URxvt$"] -> work # 指定到工作区名字
assign [class="^URxvt$"] -> number 2 # 指定到工作区，不管名字

# 在 i3 启动的时候,启动相应的应用
exec [--no-startup-id] <command>
exec_always [--no-startup-id] <command>
exec chromium
exec_always --no-startup-id urxvt

# 自动将工作区放到特殊的屏幕,主要用于多个显示器的情况
workspace <workspace> output <output>
workspace 1 output VGA1
workspace "2: Vim" output LVDS1


# 改变颜色
<colorclass> <border> <background> <text> <indicator> <child_border>
colorclass 可以是
client.focused  : 当前焦点的客户端
client.focused_inactive: 当前焦点容器的一个客户端,但是现在没有处在焦点中
client.unfocused: 一个容器中没有焦点的客户端
client.urgent:  激活其紧急的客户端
client.placeholder : 背景和文本颜色用于绘制占位符窗口内容(当恢复布局时),边界和指示符被忽略
client.background : 用于绘制客户端窗口的背景颜色,客户机窗口的背景将被渲染,只有不覆盖此窗口
整个区域的客户端才能显示颜色,请注意,此类只使用单个颜色.
# example
client.focused          #4c7899     #285577     #ffffff     #2e9ef4     #285577
client.focused_inactive #333333     #5f676a     #ffffff     #484e50     #5f676a
client.unfocuses        #333333     #222222     #888888     #292d2e     #222222
client.urgent           #2f343a     #900000     #ffffff     #900000     #900000
client.placeholder      #000000     #0c0c0c     #ffffff     #000000     #0c0c0c
client.backgrund        #ffffff





```

https://kntan.coding.me/2017/03/20/beautifull-i3/

https://void-shana.moe/linux/i3-conky-%E6%89%93%E9%80%A0%E5%AE%9E%E7%94%A8%E7%BE%8E%E8%A7%82%E7%9A%84%E6%A1%8C%E9%9D%A2%E7%8E%AF%E5%A2%83-w.html

http://www.cnblogs.com/vachester/p/5649813.html

http://blog.bantwor.com/2018/02/03/%E5%B1%9E%E4%BA%8E%E8%87%AA%E5%B7%B1%E7%9A%84-manjaro-i3/

https://github.com/ID1258/oh-my-i3/blob/master/README.md

https://fontawesome.com/cheatsheet
http://0x3f.org/

https://gist.github.com/hbpasti  
http://www.johnlozano.me/post/configuring-i3/  

https://blog.csdn.net/k_y_z_s/article/details/79363852   
https://www.jianshu.com/p/9717322753fc   
https://www.jianshu.com/p/f65bb6ab3e56   
h ttps://blog.csdn.net/github_37128837/article/details/78078526
https://github.com/FortAwesome/Font-Awesome
http://dotshare.it/
https://github.com/flumm/Themes
