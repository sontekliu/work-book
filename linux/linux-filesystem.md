### Linux 文件系统

rootfs : 根文件系统

/boot : 系统启动相关的文件，如内核、initrd、grup(bootloader)
/dev  : 设备文件，块设备:随机访问，数据块;字符设备:线性访问，按字符为单位
        设备号:主设备号和次设备号
/etc  : 配置文件
/home : 用户的家目录，每一个用户的家目录通常默认为/home/USERNAME
/root : root用户的家目录
/lib  : 库文件
        静态库: .a
        动态库: .so (shared object)
        /lib/modules : 内核模块文件
/media: 挂载点目录，移动设备，U盘，光盘等
/mnt  : 挂载点目录，额外的临时文件系统
/misc : 杂项
/opt  : 可选目录
/proc : 伪文件系统，内核映射文件
/sys  : 伪文件系统，跟硬件设备相关的属性映射文件
/tmp  : 临时文件
/var  : 可变化的文件
/bin  : 可执行文件，用户命令
/sbin : 可执行文件，管理命令
/usr  : 全局的共享的只读文件(univisal shared read-only)
/usr/local : 第三方软件安装的位置


复制和移动文件

1. cp（copy）
cp SRC DEST
    -R(r)   递归复制目录及其文件
    -f      强行复制
    -i      提示是否覆盖
    -p      保留原来的属主、属组，权限，时间戳
    -a      归档复制，常用于备份

2. mv move
mv SRC DEST

3. install 复制文件
    -d DIRECTORY ... : 创建目录















