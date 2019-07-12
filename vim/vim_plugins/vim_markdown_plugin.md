# Vim 安装 Markdown 插件

### 1. 安装 markdown 高亮(需要 Python 支持)

在 `~/.vim/vimrc` 下面添加插件，如下：

```vim
call plug#begin('~/.vim/plugged')
Plug 'godlygeek/tabular'
Plug 'plasticboy/vim-markdown'
call plug#end()
```

### 2. markdown 插件配置

参考资料：[Vim Markdown配置](https://5xruby.tw/posts/markdown-extension-on-vim/)

### 3. 安装 markdown 预览插件
在 `~/.vim/vimrc` 下面添加插件，如下：

```vim
call plug#begin('~/.vim/plugged')
Plug 'suan/vim-instant-markdown'
call plug#end()
```

若想实时预览编辑内容，需先安装 `nodejs` 和 `npm`，默认情况下，安装完 `nodejs` 就自带了 `npm`

```shell
$ sudo pacman -S nodejs
$ sudo npm -g install instant-markdown-d
```

