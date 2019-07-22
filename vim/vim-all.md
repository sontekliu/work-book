# vim 配置大全

### 1. 安装 neovim
### 1. 安装 Python3


### 2. 安装插件

主要插件，文件目录树(NERDTree), markdown, 文件查找(fzf,CtrlP)，
代码补全(ncm2, YouCompleteMe, coc):https://github.com/neoclide/coc.nvim

```
" 关闭 vi 兼容模式
set nocompatible
filetype off
call plug#begin('~/.vim/plugged')
" vim 中文文档
Plug 'vimcn/vimcdoc'
" 状态栏
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
" markdown 语法高亮
Plug 'godlygeek/tabular'
Plug 'plasticboy/vim-markdown'
" markdown 实时预览
Plug 'suan/vim-instant-markdown'
" markdown 表格插件
Plug 'dhruvasagar/vim-table-mode'
" 文件目录结构
Plug 'scrooloose/nerdtree'
Plug 'Xuyuanp/nerdtree-git-plugin'
Plug 'scrooloose/nerdcommenter'
" 文件查找
Plug 'junegunn/fzf', {'dir': '~/.fzf', 'do': './install --all'}
Plug 'junegunn/fzf.vim'

" 字符匹配，主要包括 ",',`,[,{,(等
Plug 'tpope/vim-surround'
" 代码补全
Plug 'roxma/nvim-yarp'
Plug 'ncm2/ncm2'
" 路径补全
Plug 'ncm2/ncm2-path'
" python 补全
Plug 'ncm2/ncm2-jedi'
" go 代码补全
Plug 'ncm2/ncm2-go'
```

### 3. Tmux

