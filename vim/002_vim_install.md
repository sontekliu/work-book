### 安装Vim

**MS-Windows安装**   

```
首先登录 http://www.vim.org 下载vim的exe版本，即:gvim.exe      
按照windows安装其他软件的方式，Next，Next，直到Finish
```

**Unix 安装**   

```
1) 首先从官网下载想要安装的版本    
2) 执行tar -jxvf vim-7.4.tar.bz2解压缩         
3) 执行yum install ncurses*,否则执行编译时报错(CentOS)      
4) 执行sudo apt-get install libncurses5-dev(Ubuntu)    
5) cd vim74      
6) ./configure         
7) make        
8) 测试编译是否成功，make test ,如果测试成功，则会显示如下结果 test result ALL DOWN       
9) 如果测试失败，得到的信息是 “TEST FAILURE” 如果失败的较少，Vim可能还会工作，不过不太完美      
10) make install      
11) vim -version 查看其版本     
```