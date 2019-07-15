# Vim 插件 NERDTree

NERDTree 显示树形的目录结构

### 1. 安装

```vim
call plug#begin('~/.vim/plugged')
Plug 'scrooloose/nerdtree'
call plug#end()
```

### 2. 配置

在 vim 命令模式下可以执行 `:NERDTree` 回车，就可以启用目录窗口,可以配置快捷键。如下：
```vim
map <F3> :NERDTreeToggle<CR>
```
现在可以按 F3 进行显示和隐藏 NERDTree 了。

### 3. 使用

* 和编辑文件一样，在 NERDTree 窗口通过 h j k l 来进行光标移动
* `<C-w>` 进行窗口切换
* 回车打开和关闭目录，回车打开文件
* o 小写o, 打开文件，光标在文件中
* i 水平分割创建文件的窗口,光标在文件中
* s 垂直分割创建文件的窗口,光标在文件中
* gi,gs,go 水平/垂直分割,打开创建文件的窗口，光标在 NERDTree
* t 打开一个文件，创建的是 Tab，光标在文件中
* T 打开一个文件，创建的是 Tab，光标仍在 NERDTree
* K 大写K，到同一目录的第一个节点
* J 大写J，到同一目录的最后一个节点
* p 小写p，跳到光标所在目录的上一层目录
* P 大写P，跳到根目录
* r 刷新光标所在的目录
* R 刷新当前根路径
* x 小写x 收起当前打开的目录
* X 大写X 收起所有打开的目录
* gt 切换 Tab
* `<C-j>` 和 `<C-k>` 在同级目录或者文件中移动
* F 切换是否显示文件
* I 显示或者不显示隐藏文件
* A 全屏显示 NERDTree 或者关闭全屏
* m 显示文件系统菜单(添加，删除，移动操作)
* q 退出
* 

