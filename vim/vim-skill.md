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
