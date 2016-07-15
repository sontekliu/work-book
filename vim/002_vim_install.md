### 安装Vim

1. MS-Windows安装    

&nbsp;&nbsp;&nbsp;&nbsp; 首先登录 http://www.vim.org 下载vim的exe版本，即:gvim.exe      
&nbsp;&nbsp;&nbsp;&nbsp; 按照windows安装其他软件的方式，Next，Next，直到Finish

2. Unix 安装     

&nbsp;&nbsp;&nbsp;&nbsp; 1) 首先从官网下载想要安装的版本    
&nbsp;&nbsp;&nbsp;&nbsp; 2) 执行tar -jxvf vim-7.4.tar.bz2解压缩         
&nbsp;&nbsp;&nbsp;&nbsp; 3) 执行yum install ncurses*,否则执行编译时报错(CentOS)      
&nbsp;&nbsp;&nbsp;&nbsp; 4) 执行sudo apt-get install libncurses5-dev(Ubuntu)    
&nbsp;&nbsp;&nbsp;&nbsp; 5) cd vim74      
&nbsp;&nbsp;&nbsp;&nbsp; 6) ./configure         
&nbsp;&nbsp;&nbsp;&nbsp; 7) make        
&nbsp;&nbsp;&nbsp;&nbsp; 8) 测试编译是否成功，make test ,如果测试成功，则会显示如下结果 test result ALL DOWN       
&nbsp;&nbsp;&nbsp;&nbsp; 9) 如果测试失败，得到的信息是 “TEST FAILURE” 如果失败的较少，Vim可能还会工作，不过不太完美      
&nbsp;&nbsp;&nbsp;&nbsp; 10) make install      
&nbsp;&nbsp;&nbsp;&nbsp; 11) vim -version 查看其版本     
