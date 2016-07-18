### Linux 用户、组、文件权限简单介绍

> 主要介绍如果修改目录或者文件的所有者，所属组以及权限等

首先添加几个群组以及用户            
groupadd sontek            
groupadd mygroup          
useradd -g sontek -G mygroup sontek               

1、改变所属群组 (chgrp --> change group)

chgrp [-R] groupName dirname/filename    
例如：chgrp sontek .vimrc      

2、改变所有者 (chown --> change owner)

chown [-R] userName dirname/filename     
chown [-R] userName:groupName dirname/filename    
例如：chown sontek:sontek .vimrc       

3、改变文件权限 (chmod)

chmod [-R] 权限 dirname/filename          
例如：chmod 777 .vimrc         

4、权限对目录和文件的影响

1) 权限对文件的影响
```
r(read)   :可读取文件的实际内容
w(write)  :可修改(编辑，新增)文件内容(不能删除文件)
x(execute):该文件具有可以被系统执行的权限
````

2) 限对目录的影响
```
r:(read contents in directory)
		表示具有读取目录结构列表的权限，即，可以查询该目录
		下文件名数据，例如:ls 命令
w:(modify contents of directory)
		具体改动该目录结构列表的权限，具体表现如下：
		(1) 建立新的文件或目录
		(2) 删除已存在的文件或者目录
		(3) 对文件或目录重命名
		(4) 移动文件或目录的位置
x:(access directory)
		表示用户是否能进入该目录
```


