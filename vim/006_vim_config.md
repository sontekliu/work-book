#### Vim vimrc config file
```
    " 关闭与Vi的兼容模式
    set nocompatible
    " 指明在插入模式下哪儿里允许<BS>删除光标前面的字符，三个值分别为：行首空白字符，
    " 换行符，插入模式开始处之前的字符
    set backspace=indent,eol,start
    " 显示所处在的模式
    set showmode
    " 显示执行的命令
    set showcmd
    " 显示行号
    set number
    " 取消显示行号
    set nonumber
    "显示标尺
    set ruler
    " 忽略大小写
    set ignorecase
    " 区分大小写
    set noignorecase
    " 高亮匹配
    set hlsearch
    " 取消高亮匹配
    set nohlsearch
    " 查找方式，在输入字符时就进行查找
    set incsearch
    " 查找到文件头部或者尾部之后停止查找，默认是折回继续查找
    set nowrapscan
    " 禁止长行自动回绕
    set nowarp
    " 一长行，右移动到不能显示的文字上，Vim会自动让你看到后面的10个字符
    set sidescroll=10
    " 智能缩进
    set autoindent
    " 开启文件类型检测，并使佣文件插件，文件缩进
    filetype plugin indent on
    " 简单键盘映射,定义F5 在一个单词上添加{},例如：amount --> F5 --> {amount}
    :map <F5> i{<Esc>ea}<Esc>
    " 移动命令换行，很多命令只能在行内移动，whichwarp可以改变这一规则。
    " whichwrap的默认值是 "b,s" <BS>键可以回到前一行的结尾，<Space>可以移动到下一行的行首
    set whichwrap=b,s
    " 显示TAB 键
    set list
    " iskeyword 指定哪儿些字母可以出现在一个单词中
    " @ 表示所有字母，48-57 表示0-9,192-255 是可显示的拉丁字符
    " 可以添加其他字符，set iskeyword+=-，表示把横线也当作关键字
    set iskeyword=@,48-57,_,192-255
    " 显示命令行的高度
    set cmdheight=3
```
