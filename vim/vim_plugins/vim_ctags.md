# Vim Catgs Plugin

ctags程序其实是叫 `Exuberant Ctags`，是 Unix 上面 ctags 程序的替代品，并且比他功能强大，是大多数Linux发行版上默认的 ctags 程序。tags文件是由ctags程序生存的一个索引文件。那么 tags 文件是做什么用的呢？    

如果你在读程序的时候看到一个函数，一个变量或者一个宏，你想知道他们的定义在哪儿，怎么办呢？用 grep ? 那样会搜出很多不相关的东西，并且不能直接到我们期望的地方。现在流行的是 `<C-]>`(Ctrl+])，光标会自动跳转到其定义处，厉害吧，那就看看怎么用吧。

**Ctags Install**   
首先在[这里](http://ctags.sourceforge.net)下载源文件。
使用下面的命令进行解压安装：
```
$ tar -zxvf ctags-5.8.tar.gz
$ cd ctags-5.8
$ make
# make install //需要root权限
```












