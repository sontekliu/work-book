# Vim coc 智能代码补全插件

`coc.nvim` 是最智能的代码补全插件，[官方地址](https://github.com/neoclide/coc.nvim)

### 1. 安装条件

* 先安装 `nodejs`
* `Vim >= 8.0` 
* `neovim >= 0.3.1` 

### 2. 安装

* 首先安装 nodejs
```vim
curl -sL install-node.now.sh/lts | bash
```

或者访问 [nodejs](https://nodejs.org/) 官方网站查看安装指南

* 使用插件管理器 `vim-plug` 安装

```vim
" 安装发行版
Plug 'neoclide/coc.nvim', {'branch': 'release'}
" 安装最新的 tag 版本
Plug 'neoclide/coc.nvim', {'tag': '*', 'branch': 'release'}
" 从源码编译，需要 yarn: https://yarnpkg.com
Plug 'neoclide/coc.nvim', {'do': 'yarn install --frozen-lockfile'} (recommand)
```

配置完成，然后重启 `vim` 然后执行 `PlugInstall`


### 3. 配置

默认情况下，`coc.nvim` 默认情况下是没有配置文件的，`:CocConfig` 可以打开创建文件，第一次是新建，
`coc.nvim` 配置文件的格式是 `json`。

在 `~/.vim/vimrc` 或者 `~/.config/nvim/init.vim` 下添加如下内容：

```vim
function! SetupCommandAbbrs(from, to)
  exec 'cnoreabbrev <expr> '.a:from
        \ .' ((getcmdtype() ==# ":" && getcmdline() ==# "'.a:from.'")'
        \ .'? ("'.a:to.'") : ("'.a:from.'"))'
endfunction

" Use C to open coc config
call SetupCommandAbbrs('C', 'CocConfig')
```

这样直接使用 `:C` 即可打开配置文件。

---

```vim
" use <tab> for trigger completion and navigate to the next complete item
function! s:check_back_space() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1]  =~ '\s'
endfunction

inoremap <silent><expr> <Tab>
      \ pumvisible() ? "\<C-n>" :
      \ <SID>check_back_space() ? "\<Tab>" :
      \ coc#refresh()

" use <c-space>for trigger completion
inoremap <silent><expr> <c-space> coc#refresh()
```

使用 `TAB` 键，触发代码补全。
注意：使用如下检查 TAB 键是否有映射 `:verbose imap <tab>`
