### nginx 的安装
Nginx 是一个高性能的HTTP和反向代理服务器。
Nginx 官方网址是：http://nginx.org
Nginx 安装时需要依赖以下几个模块，请提前安装

1. 依赖模块
gzip 模块需要zlib库
rewrite 模块需要pcre库
ssl 功能需要openssl库

2. PCRE库的安装   
官网：http://www.pcre.org
下载最新版本后，进行如下操作
```
    $ tar -zxvf pcre2-10.21.tar.gz
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
    $ sudo ./configure
    $ sudo make
    $ sudo make install
```
