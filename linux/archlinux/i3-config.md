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
* $mod + Enter 开启终端，默认占满整个屏幕。再次按下将再启动一个终端，并且平分两个屏幕
* $mod + j 可以切换到左边的终端
* $mod + ; 可以切换到右边的终端
* $mod + k 可以切换到下边的终端
* $mod + l 可以切换到上边的终端

* $mod + v 水平平分屏幕，即，再次启动终端时,将水平切分屏幕
* $mod + h 垂直平分屏幕，即，再次启动终端时,将垂直切分屏幕

* $mod + w 按标签的形式显示窗口
* $mod + s 按堆积的形式显示窗口
* $mod + e 按水平或者垂直的形式显示窗口
* $mod + f 全屏显示当前窗口

* $mod + num 切换到某个工作区，num的值是 1-9 还有 0.
* $mod + shift + num 将当前活动的窗口移动到对应的工作区
* $mod + d 显示应用的名称，你可以输入相应的应用并启动,$PATH 中的应用
* $mod + shift + q 关闭当前活动的窗口
* $mod + shift + e 注销
* $mod + shift + r 重新启动 i3, 修改配置文件后可以使其生效
* $mod + shift + Space 使窗口浮动在其他窗口上

以上是 i3 默认情况下的基本使用。

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

```
