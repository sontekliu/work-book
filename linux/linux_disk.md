### 磁盘查看，磁盘格式化，磁盘分区等

**1. df [-ahikHTm] filename/dirname**   

> 选项与参数

```
-a	: 列出所有的文件系统，包括系统特有的 /proc 等文件系统
-k	: 以 KBytes 的容量显示各文件系统
-m	: 以 MBytes 的容量显示各文件系统
-h	: 以人们较易阅读的 GBytes、MBytes、KBytes 等格式显示
-H	: 以 M=1000K 取代 M=1024K 的进位方式显示
-i	: 不显示磁盘容量，而是以 inode 的数量来显示
-T	: 把 partition 的 filesystem 名称(例如ext3)也显示出来
```

**2. du [-ahskm] filename/dirname**   

> 选项与参数

```
-a	: 列出所有的文件与目录容量，默认只统计目录底下的文件而已
-h	: 以人们易读的方式显示
-s	: 列出总量而已，而不列出每个个别目录占用容量
-S	: 不包括子目录下的统计
-k	: 以 KBytes 列出容量显示
-m	: 以 MBytes 列出容量显示
```

**3. fdisk [-l] devname(设备名称)**    

> 选项与参数

```
-l	: 输出设备所有的 partition 内容，若执行 fdisk -l 时，则系统将会把整个系统内能搜到的设备分区全部列出
创建新分区
fdisk /dev/sda (注意后面不要添加编号)
此时，输入m获取帮助信息，具体删除，添加分区可根据帮助操作
注意: 系统中最多能分4个主分区
```

**4. mkfs [-t 文件系统类型] devname**    

> 选项与参数

```
-t	: 可接文件系统类型，如，ext3、ext2、ext4等
例如: mkfs -t ext2 /dev/sda6 注意后面的标号
```

**5. mke2fs [-b block大小] [-i block大小] [-L 表头] [-cj] devname**    

> 选项与参数

```
-b	: 可以配置每个block的大小，目前支持 1024,2048,4096 bytes 三种
-i	: 多少容量给予一个 inode 
-c	: 检查磁盘错误，-c 时，会进行快速读取测试，如果 -c -c 会测试读写，很慢
-L	: 后面接表头名称，具体看 e2label
-j	: 本来 mke2fs 是ext2，加上 -j 后，会主动加入 journal 而成为ext3
例如: mke2fs -j -L "sontek_logical" -b 2048 -i 8192 /dev/sda6
mke2fs的各项参数均可用在 mkfs -t ext3 的后面。所以说在没有特殊说明的情况下
使用 mkfs -t ext3 ... 不但容易记忆并且还很好用
```



