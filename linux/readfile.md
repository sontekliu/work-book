### 文件查看命令

1. cat     
cat [-AnbvTE] filename         

> 选项与参数      

```
-A	: 相当于-vET的整合选项,可以列出一些特殊字符而不是空白而已      
-b	: 列出行号，仅针对非空白行，空白行不显示行号         
-n	: 列出行号，与 -b 选项不同，空白行也会列出行号     
-E	: 将结尾的断行字符以 $ 显示出来           
-v	: 列出一些看不出来的特殊字符              
-T	: 将[tab]按键以 ^I 显示出来            
```

2. tac         
tac与cat相反，cat是将文件从第一行到最后一行显示，而tac则是将文件从最后一行到第一行显示

3. nl [-bnw] filename         
> 选项与参数         
```
-b	: 指定行号显示的方式，主要有两种            
	  -b a	: 表示无论是否为空号，也要显示行号(类似 cat -n)          
	  -b t	: 如果有空行，空行不列出行号(类似 cat -b)      
-n	: 行号显示的方式           
	  -n ln	: 行号在行号栏位的最左侧显示        
	  -n rn	: 行号在行号栏位的最右方显示，且不加0补全          
	  -n rz : 行号在行号栏位的最右方显示，且加0补全           
-w	: 行号栏位的占用位数         
```

4. more	filename       
> 按页显示文件内容，到文件结尾时退出more命令       
```
[space]	: 向下翻页     
[Enter]	: 向下翻一行          
q		: 表示退出more不再显示文件内容           
:f		: 显示文档名称以及目前显示的行数          
/string	: 向下搜索字符串        
```	

5. less filename        
> 按页显示文件内容，到文件结束后不退出less命令       
```
[space]	: 向下翻页        
[Enter]	: 向下翻一行    
[pgDn]	: 向下翻一页       
[pgUp]	: 向上翻一页     
q		: 退出less命令           
```

6. head [-n number] filename        
> 选项与参数      
```
-n	: 后面跟数字，表示显示文档的前number行     
```

7. tail [-n number] filename         
> 选项与参数         
```
-n	: 后面跟数字，表示显示文档的后number行          
-f	: 表示动态的显示文档的内容，对于查看日志特别有用        
```

8. touch
> 修改文件时间，文件的时间有：访问时间、修改时间、改变时间，通过stat命令可查看这三个时间         
**modification time(mtime)**    
	当文档的内容数据变更时，就会升级这个时间，内容数据是指文件的内容，而不是文件的属性或权限       
**status time(ctime)**    
	当文档的状态改变时，就会升级此时间，例如，权限与属性的更改。      
**access time(atime)**      
	当文档的内容被取用时，就会升级此时间，例如，cat filename 就会升级此时间           
> 选项与参数        
```
-a	: 修改访问时间，例如，touch -a 02_readfile.txt           
-m	: 修改修改时间，例如，touch -m 02_readfile.txt             
-c	: 不创建任何文件，例如，touch -c xxx.txt ，当前目录下并不存在xxx.txt        
-t	: use [[CC]YY]MMDDhhmm[.ss] instead of current time          
```



