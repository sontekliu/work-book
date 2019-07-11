# Vim 插件管理

### 1. 安装

[官方地址](https://github.com/junegunn/vim-plug) : https://github.com/junegunn/vim-plug

```shell
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

### 2. Plug 的使用

在 `~/.vim/vimrc` 中编辑如下内容：

```
call plug#begin('~/.vim/plugged')
"必须使用单引号

" Github 简化形式; fetches https://github.com/junegunn/vim-easy-align
Plug 'junegunn/vim-easy-align'

" 完整的 Github URL 地址
Plug 'https://github.com/junegunn/vim-github-dashboard.git'

" 多个插件写在一行，使用 `|` 分隔
Plug 'SirVer/ultisnips' | Plug 'honza/vim-snippets'

" On-demand loading (按需加载)
Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle' }
Plug 'tpope/vim-fireplace', { 'for': 'clojure' }

" 使用非主干分支
Plug 'rdnetto/YCM-Generator', { 'branch': 'stable' }

" 使用某个 tag 版本，允许使用通配符（要求 git 版本大于 1.9.2）
Plug 'fatih/vim-go', { 'tag': '*' }

" 插件选项
Plug 'nsf/gocode', { 'tag': 'v.20150303', 'rtp': 'vim' }

" Plugin outside ~/.vim/plugged with post-update hook
Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }

" 非托管插件，(手工安装和更新)
Plug '~/my-prototype-plugin'

call plug#end()
```

### 3. Commands


序号        | Command            | 描述
------------|--------------------|----------------
1           | PlugInstall        | 安装插件
2           | PlugUpdate         | 更新插件
3           | PlugUpgrade        | 升级插件
4           | PlugClean[!]       | 移出未列出的插件
5           | PlugStatus	 | 检查插件状态









