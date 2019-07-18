# Vim 插件 vim-surround

`vim-surround` 插件是修改文本对象符号的利器，例如，给某个单词添加双引号，尤其是在写 `markdown` 的时候给
对应单词高亮显示时，特别实用。

### 1. vim-surround 安装

```vim
call plug#begin('~/.vim/plugged')
Plug 'tpope/vim-surround'
call plug#end()
```

### 2. 命令

> 正常模式

| 序号 | 命令 | 含义                                | 示例                      |
|------|------|-------------------------------------|---------------------------|
| 1    | cs   | 修改包围                            | cs"[,  "hello" -> [hello] |
| 2    | ds   | 删除包围                            | ds",  "hello"  -> hello   |
| 3    | yss  | 添加一行包围                        | yss",  hello   -> "hello" |
| 4    | ySS  | 添加一行包围,并且被包围内容单独一行 |                           |

> 可视模式

| 序号 | 命令 | 含义                 | 示例                             |
|------|------|----------------------|----------------------------------|
| 1    | S    | 给选中的内容添加包围 | S", hello world -> "hello world" |

可在 `vimrc` 中添加如下配置：
```vim
vmap " S"
vmap ' S'
vmap ` S`
vmap [ S[
vmap ( S(
vmap { S{
vmap } S}
vmap ] S]
vmap ) S)
vmap > S>
```

> 插入模式

| 序号 | 命令             | 含义                        | 示例 |
|------|------------------|-----------------------------|------|
| 1    | <CTRL-s>         | 添加一个包围                |      |
| 2    | <CTRL-s><CTRL-s> | 添加一个包围,内容单独成一行 |      |

### 3. 参考

[官方](https://github.com/tpope/vim-surround) : https://github.com/tpope/vim-surround
[木凡](https://mounui.com/355.html) : https://mounui.com/355.html



















