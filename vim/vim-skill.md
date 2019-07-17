# Vim 小技巧

* 删除空行
    ```vim
    :g/^$/f
    ```
* 查找并删除行
    ```
    :g/bak/d    # 查找并删除包含 bak 的行
    ```
* 命令行下使用 vi
    ```
    set -o vi   # 适用于当前环境，想一直有效 .zshrc 中配置 set -o vi,并 source .zshrc 使其生效
    ```
* Vim 快速打开 URL

首先鼠标定位在 URL 所在的位置，`normal` 模式下，使用 `gx` 即可调用默认的浏览器打开 `URL` 连接

* Vim 快速输入序列
    - 使用 linux 的 seq 命令
    ```
    :r !seq 1 20        (多行) 
    :r !echo {1..20}    (单行) 
    ```

    - vim 宏的方式

    ```
    1 <ESC>
    qq
    yyp
    <C-a> (Ctrl+a)
    q
    20@q
    ```
