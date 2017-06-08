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

**使用Ctags**

1. 使用 `$ ctags -R` 命令，会在当前目录下马生成 tags 文件。
2. 在 Vim 中运行命令：`:set tags=/path/to/tags` 该命令将 tags 文件加入到 Vim 中来，也可以将此命令添加到 `~/.vimrc` 中去。
3. `<C-]>` 跳转到指定函数的定义的地方。`<C-T>` 跳回刚才的位置。
```
注意：修改程序后，如添加了新的方法，删除了变量等，tags 文件不能自动 rebuild 需手动运行一下命令：$ ctags -R
```



