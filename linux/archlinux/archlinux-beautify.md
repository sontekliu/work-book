# Archlinux 美化

> 注意，本系统没有使用桌面，仅仅使用的是 i3 窗口管理器

### 1. 安装VirtualBox 插件，使其支持最大化

```
# sudo pacman -S virtualbox-guest-utils virtualbox-guest-modules-arch
# sudo reboot
```
* 使宿主机器和客体机之间互通剪贴板，实现鼠标拖拽文件，
* 无缝窗口模式
* 宿主机的虚拟机窗口缩放之后，使客体机的显示分辨率与之自动匹配
* 检查宿主机的 VirtualBox 版本

上述功能的启用，需要执行如下命令，该命令需要设置启动 X 时候自动启动：
```
# VBoxClient-all
```
VirtualBox 默认情况下，剪贴板互通是禁用的，需要手动设置开启。
`Settings > General > Advanced > Shared Clipboard`

### 2. 配置 i3 窗口管理器

具体见[i3wm 配置](./archlinux-beautify-i3.md)
