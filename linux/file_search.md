### 主要讲解文件查找命令

**1. which [-a] command (查找命令的完整路径)**   

> 选项与参数

```
-a	: 将所有由PATH目录中可以找到的命令全部列出来，而不仅仅是第一个被找到的
例如：which ifconfig  --> /sbin/ifconfig
如果切换到普通用户执行：which ifconfig 则查询不到，因为普通用户的PATH没有/sbin, which 仅仅是在PATH中查找
例如：which cd 也查不到，因为cd命令为bash的内建命令。内建命令使用type查找
```

**2. whereis [-bmsu] filenme/dirname**    

> 选项与参数

```
whereis 是基于数据库的查询，速度较快，但是经常找到一些已删除的文件，或者新建的文件找到不到。具体详情请看下面的locate命令
-b	: 只查找二进制文件
-m	: 只在说明文档的路径下寻找
-s	: 只找source来源文件
-u	: 搜寻不在上述三个项目中的其他特殊文件
```

**3. locate [-ir] keyword**   

> 选项与参数

```
locate搜寻的数据是由自己建立的 /var/lib/mlocate 的数据库查找的，所以新建的文档在数据库更新之前是查询不到的，
但是可以更新数据库，执行:updatedb 更新数据库,若无此命令应先安装mlocate数据库，安装如下:yum install mlocate
-i	: 忽略大小写
-r	: 后面可接正规表示法的显示方式
```

**4. find [PATH] [option] [action]**     

> 选项与参数

1) 与实践有关的选项：-atime,-mtime,-ctime,以-mtime说明

```
-mtime	n	: n为数字，意义为在n天之前(一天以内)被更动过内容的文件
-mtime	+n	: 列出n天之前(不包含n天本身)被修改过内容的文件名称
-mtime	-n	: 列出在n天之内(含n天本身)被修改过内容的文件名称
-newer	file: file为一个存在的文件，列出比file还要新的文件名称
例如:find /etc/ -mtime +4 表示列出大于等于5天前的文档
	 find /etc/ -mtime -4 表示列出小于等于4天内的文档
	 find /etc/ -mtime 4  表示列出4-5那一天的文档名称
```

2) 与用户或群组名称有关的参数

```
-uid n	: n为数字，表示用户ID，即UID，在/etc/passwd文件中
-gid n	: n为数字，表示群组ID，即GID，在/etc/group文件中
-user name	: name 为用户名称
-group name	: name 为群组名称
-nouser		: 寻找文件的拥有者不存在/etc/passwd的人
-nogroup	: 寻找文件的群组不存在/etc/group的人
```

3) 与文件权限以及名称有关的参数

```
-name filename	: 列出文件名称为filename的文件
-size [+-SIZE]	: 搜寻比SIZE还要大(+)或小(-)的文件，SIZE的规格有c:byte
				  k:1024byte。例如找比50KB还要大的文件 -size +50KB
-type TYPE		: 列出文件类型为TYPE的，TYPE有，f:一般文件，b、c:设备文件
				  d:目录文件，l:链接文件，s:socket文件，p:FIFO文件
-perm mode		: 列出文件权限恰好为mode的文件。例如，-rwsr-xr-x为4755
-perm -mode		: 列出文件权限“必须全部包括mode的权限”的文件，例如，
				  -rwxr--r--,0744使用 -perm 0744时，-rwsr-xr-x的文件也会列出
-perm +mode		: 列出文件权限“包含任一mode的权限”的文件，例如，-rwxr-xr-x
				  即 -perm +755时，一个文件属性为-rw-------也会被列出，因为
				  它有-rw...的属性存在
例如: find / -perm +7000，7000表示---s--s--t，那么只要含有s或t的就列出
要是使用 -7000时，表示要含有 ---s--s--t的所有三个权限
```

4) 额外可进行的动作

```
-exec command	: command 为其他命令，-exec 后面可接额外的命令来处理搜寻到
				  的结果，注意command不支持别名
-print			: 将结果打印到屏幕上，默认动作
例如：find / -perm +7000 -exec ls -l {} \;
{} 代表find找到的内容，find找到的结果会放置到{} 位置中。
-exec 一直到 \; 是关键字，代表find额外动作的开始(-exec)到结束(\;)
这中间就是find命令内的额外动作，本例中是:ls -l {}
;在bash中有特殊意义，所以使用\转义

find /etc/ -name '*httpd*'  模糊匹配
```





