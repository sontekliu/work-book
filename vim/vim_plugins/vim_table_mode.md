# Vim Table Mode

### 1. 安装
[官方地址](https://github.com/dhruvasagar/vim-table-mode)

```vim
call plug#begin('~/.vim/plugged')
Plug 'dhruvasagar/vim-table-mode'
call plug#end()
```
安装完成插件之后，在 `～/.vim/vimrc` 中添加如下内容：

```vim
function! s:isAtStartOfLine(mapping)
  let text_before_cursor = getline('.')[0 : col('.')-1]
  let mapping_pattern = '\V' . escape(a:mapping, '\')
  let comment_pattern = '\V' . escape(substitute(&l:commentstring, '%s.*$', '', ''), '\')
  return (text_before_cursor =~? '^' . ('\v(' . comment_pattern . '\v)?') . '\s*\v' . mapping_pattern . '\v$')
endfunction

inoreabbrev <expr> <bar><bar>
          \ <SID>isAtStartOfLine('\|\|') ?
          \ '<c-o>:TableModeEnable<cr><bar><space><bar><left><left>' : '<bar><bar>'
inoreabbrev <expr> __
          \ <SID>isAtStartOfLine('__') ?
          \ '<c-o>:silent! TableModeDisable<cr>' : '__'
```
默认情况下，启用/关闭表格模式是 `<leader>tm` 添加如上代码之后，使用 `||` 启用表格，`__` 关闭表格模
式。

### 2. 使用方式
在第一行输入用 `|` 隔开的字符，回车到第二行（注意还是插入模式），连续输入两个 `|` 按下 `ESC` 此时进
入表格模式，输入相应的内容即可，每次输入一个 `|` 表格会自动格式化。如果想结束表格输入，在行首输入
`__` 再按下 `ESC` 即可。


