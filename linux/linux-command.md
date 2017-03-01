### Linux 命令详解

命令类型：
    内部命令（shell内置）
    外部命令:在文件系统的某个路径下有一个与命令名称相应的可执行文件
type: 显示指定命令属于哪种命令

获得命令的使用帮助
内部命令:
    help COMMAND
外部命令:
    COMMAND --help
内、外部命令手册：manual
    man COMMAND
man 分章节，whatis COMMAND 显示命令所在章节
1: 用户命令（/bin, /usr/bin, /usr/local/bin）
2: 系统调用
3: 库调用
4: 特殊文件（设备文件） man tty
5: 文件格式（配置文件的语法）man passwd
6: 游戏
7: 杂项(Miscellaneous)
8: 管理命令（/sbin, /usr/sbin, /usr/local/sbin）

MAN:
    <> : 必选
    [] : 可选
    ... : 可以出现多次
    | : 多选一

在线手册
info COMMAND （man的补充，使用不多）

文档 : /usr/share/doc


1. pwd(print working dircetory) 显示当前目录

2. cd(change directory) 切换目录
    cd: 不加任何参数回到用户的home目录
    ~:  表示home目录
    cd -:  表示在当前目录和上一次所在目录来回切换

3. ls
    -l : 长格式
        文件类型：
            - : 普通文件
            d : 目录文件
            b : 块设备文件（block）
            c : 字符设备文件（character）
            l : 符号链接文件（symbolic link file）
            p : 命令管道文件（pipe）
            s : 套接字文件（socket）
        文件权限：9位，每3位一组，每一组：rwx（读、写、执行）
        文件硬链接次数
        文件的属主（owner）
        文件的属组（group）
        文件的大小（size）单位是字节
        时间戳（timestamp）最近一次被修改的时间
            访问:access
            修改:modify，文件内容发生的改变
            改变:change,metadata,元数据
    -h: 做单位换算（human readable）
    -a: 显示以.开头的隐藏文件
        . 表示当前目录
        .. 表示父目录
    -A: 显示以.开头的隐藏文件，但是.和..不显示
    -d: 显示目录自身属性
    -i: 显示文件的inode节点
    -r: 逆序显示文件
    -R: 递归显示

4. 时间管理（date）
    硬件时钟hwclock
    系统时钟date
    hwclock 显示硬件时钟
    hwclock -w 更改硬件时钟为系统时钟
    hwclock -s 更改系统时间为硬件时钟。

5. cal : calender 日历

6. mkdir 创建目录
    -p : 一次性创建多个目录，mkdir -p /root/x/y/z
    -v : verbose 显示详细信息
    mkdir -pv /mnt/test/{x/m,y}
    mkdir -pv /test2/{a,d}_{b,c}

7. rmdir 删除目录
    删除非空目录

8. 文件创建和删除
touch 改变文件时间戳
    -a : 修改文件的访问时间
    -m : 修改文件的修改时间
    -t : 修改文件的修改和访问时间
    -c : 不创建文件
stat  查看文件或者文件系统的状态

9. 查看各个文件夹的大小
du -h --max-depth=1


