### nginx 的安装
Nginx 是一个高性能的HTTP和反向代理服务器。   
Nginx 官方网址是：http://nginx.org         
Nginx 安装时需要依赖以下几个模块，请提前安装  

1. 依赖模块   
    gzip 模块需要zlib库   
    rewrite 模块需要pcre库    
    ssl 功能需要openssl库   
    
2. PCRE库的安装   
    官网：http://www.pcre.org 下载最新版本后，进行如下操作：
    ```
        $ tar -zxvf pcre2-10.21.tar.gz
        $ cd pcre2-10.21
        $ sudo ./configure --prefix=/usr/local/pcre
        $ sudo make
        $ sudo make install
    
        注意：如果在make时报错，可能需要先安装 build-essential
        $ sudo apt install build-essential
    ```
    
3. zlib库的安装   
    官网：http://www.zlib.net  
    ```
        $ tar -zxvf zlib-1.2.11.tar.gz
        $ cd zlib-1.2.11
        $ sudo ./configure
        $ sudo make
        $ sudo make install
    ```
    
4. Nginx的安装   
    ```
        $ tar -zxvf nginx-1.10.3.tar.gz
        $ cd nginx-1.10.3
        $ sudo ./configure --prefix=/usr/local/nginx
        $ sudo make
        $ sudo make install
    ```
    
5. Nginx 配置文件    
    `$ vim /usr/local/nginx/conf/nginx.conf`
    
6. 检测Nginx的配置文件是否正确，建议每次修改配置文件后均需检测一下   
    `$ /usr/local/nginx/sbin/nginx -t`        
    出现如下信息，代表成功：     
    ```
        nginx: the configuration file /usr/local/nginx/conf/nginx.conf syntax is ok
        nginx: configuration file /usr/local/nginx/conf/nginx.conf test is successful
    ```
    
7. 启动、停止、重启Nginx   
    ```
        $ sudo /usr/local/nginx/sbin/nginx              # 启动
        $ sudo /usr/local/nginx/sbin/nginx -s stop      # 停止
        $ sudo /usr/local/nginx/sbin/nginx -s reload    # 重启
    ```
    
8. 设置开机启动   
    编辑/etc下面的rc.local    
    `$ sudo vim /etc/rc.local`   
    添加：   
    `/usr/local/nginx/sbin/nginx`


