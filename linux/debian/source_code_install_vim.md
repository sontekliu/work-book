# 从源码编译安装 Vim

由于系统默认安装的 `Vim` 缺少一些特性,比如不支持共享剪贴板等,可使用 `vim --version` 查看默认支持的特性,
如果前面有 `+` 则表示支持该特性,`-` 则表示不支持该特性.

> 注意,本文是基于 Debian 的发行版进行安装,其他发行版应该类似

### 1. 首先下载 Vim 源码(默认你已经安装了 git)
```
$ git clone https://github.com/vim/vim.git
$ cd vim
$ ./configure -h  # 查看编译配置选项
```

### 2. 安装必要的软件包
```
$ sudo apt-get install \
    build-essential \
    libncurses5-dev \
    python-dev \
    python3-dev \
    ruby-dev \
    lua5.2  \
    liblua5.2-dev \
    libperl-dev \
    libtcl8.6 \
    libgnomeui-dev \
    libx11-dev \
    libxt-dev \
    libxpm-dev
```

configure                    | feature             | dependency
-----------------------------|---------------------|----------------------
--enable-pythoninterp        | python              | python-dev
--enable-python3interp       | python3             | python3-dev
--enable-rubyinterp          | ruby                | ruby-dev
--enable-luainterp           | lua                 | liblua5.2-dev
--enable-perlinterp          | perl                | libperl-dev
--enable-tclinterp           | tcl                 | libtcl8.6
--enable-gui                 | gVim                | libgonmenui-dev
                             | clipboard           | libx11-dev libxt-dev
                             | xpm                 | libxpm-dev

### 3 配置编译选项
由于编译选项太多,操作比较麻烦,一开始肯定会反复编译,所以将其配置写到一个文件中,反复编译时,
只是简单的修改此文件即可,文件内容如下:

```
#!/bin/bash

cd vim
make clean 
git clean -fdx

./configure \
    --prefix=/usr/local/ \  # 安装目录
    --with-features=huge \  # 启用最多的 feature
    --enable-multibyte \    # 多字节语言支持
    --enable-cscope=yes \   
    --enable-perlinterp=yes \
    --enable-rubyinterp=yes \
    --with-ruby-command=/usr/bin/ruby \
    --enable-luainterp=yes \
    --enable-pythoninterp=yes \
    --enable-python3interp=yes \
    --enable-tclinterp=yes \
    --enable-gui=auto \
    # --enable-gnome-check \
    --enable-sniff \
    --enable-xim \
    --enable-fontset \
    --with-x \
    --with-compiledby=$USER  # 可有可无

make && src/vim --version

```

### 4. 大功告成

执行安装

```
$ cd vim
$ sudo make install 
```
至此, `Vim` 源码安装结束






