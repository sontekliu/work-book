# Ranger 简介

`Ranger` 是一个基于终端的文件管理器。类似于很多文件管理器，如 `thunar`, `pcmanfm` 等,
但是 `ranger` 是一个神器。

### 1. Ranger 安装

```shell
$ brew install ranger               # for Mac
$ sudo apt install ranger           # for Ubuntu
$ sudo pacman -S ranger             # for ArchLinux(my Linux)
```

* highlight                 高亮浏览代码
* atool                     预览压缩文件
* pdftotext                 预览PDF文件
* exiftool                  预览媒体文件信息

```shell
brew install highlight atool exiftool
brew cask install pdftotext
```

`imgcat` 是一个 `shell` 脚本，与 `iTerm2` 结合起来使用，可以直接使用终端查看远程 `Linux` 上的 图片。不过仅限于在 `iTerm2` 上使用

安装使用如下：

```shell
curl "https://iterm2.com/utilities/imgcat" > imgcat
chmod +x imgcat
mv imgcat /usr/bin
```

### 2. 生成配置文件

```shell
# ranger --copy-config=all

creating : /Users/sontek/.config/ranger/rifle.conf          # 指定不同类型的文件的默认打开程序
creating : /Users/sontek/.config/ranger/commands.py         # 能通过 : 执行的命令
creating : /Users/sontek/.config/ranger/commands_full.py
creating : /Users/sontek/.config/ranger/rc.conf             # 选项设置和快捷键
creating : /Users/sontek/.config/ranger/scope.sh            # 用于指定预览程序的文件

> Please note that configuration files may change as ranger evolves.
  It's completely up to you to keep them up to date.

> To stop ranger from loading both the default and your custom rc.conf,
  please set the environment variable RANGER_LOAD_DEFAULT_RC to FALSE.
```

然后到 `~/.config/ranger/` 目录下配置各种选项即可。

### 3. 配置 Ranger

- 默认情况下，在 `archlinux` 中是可以预览图片的，但是在 `MacOS` 中是不能预览图片的，需做如下修改

```
$ vim ~/.config/ranger/rc.conf

set preview_images  true
set preview_images_method iterm2
```

---

- 启动 `ranger` 时，使用边框环绕。

```
set draw_borders outline    # separators, outline, both, none
```

---

- 与版本管理器集成

```
set vcs_aware true
```



### 4. Ranger 快捷键

> 1. 浏览

 | 序号 | 快捷键 | 对应操作         |
 |------|--------|------------------|
 | 1    | h      | 后退             |
 | 2    | l      | 前进             |
 | 3    | gg     | 跳转顶端         |
 | 4    | G      | 跳转低端         |
 | 5    | gh     | 跳转到 home 目录 |
 | 6    | k      | 向上移动         |
 | 7    | j      | 向下移动         |
 | 8    | f      | 查找             |
 | 9    | /      | 搜索             |

> 编辑

 | 序号 | 快捷键  | 对应操作                 |
 |------|---------|--------------------------|
 | 1    | space   | 选择与取消选择           |
 | 2    | yy      | 复制                     |
 | 3    | dd      | 剪切                     |
 | 4    | pp      | 粘贴                     |
 | 5    | cw      | 重命名                   |
 | 6    | A       | 在当前名称的基础上重命名 |
 | 7    | I       | 类似A，光标在起始位置    |
 | 8    | :delete | 删除文件                 |

> TAB 标签

 | 序号 | 快捷键   | 对应操作 |
 |------|----------|----------|
 | 1    | gn / C-n | 新建标签 |
 | 2    | gt / TAB | 切换标签 |
 | 3    | gc / C-w | 关闭标签 |

> 书签

 | 序号 | 快捷键       | 对应操作                  |
 |------|--------------|---------------------------|
 | 1    | m 任一字符   | 新建标签                  |
 | 2    | `            | 显示标签列表(数字1左侧键) |
 | 3    | um  对应字符 | 取消标签                  |

> 排序

 | 序号 | 快捷键 | 对应操作                                                 |
 |------|--------|----------------------------------------------------------|
 | 1    | on/ob  | 根据文件名称进行排序（natural/basename）                 |
 | 2    | oc     | 根据改变时间进行排序（Change Time,包括权限组和文件自身） |
 | 3    | os     | 根据文件大小进行排序（Size）                             |
 | 4    | ot     | 根据后缀名进行排序（Type）                               |
 | 5    | oa     | 根据访问时间进行培训（Access Time）                      |
 | 6    | om     | 根据修改进行排序（Modify Time 文件自身被修改）                                     |

> 其他

 | 序号 | 快捷键  | 对应操作                                  |
 |------|---------|-------------------------------------------|
 | 1    | S(大写) | 在当前目录打开终端                        |
 | 2    | zf      | 过滤文件，zf 输入 pdf 回车，过滤 pdf 文件 |
 | 3    | :       | 使用 ranger 命令，（? 查看可用命令)       |
 | 4    | zh      | 显示或者不显示隐藏文件                    |
 | 5    | zp      | 打开或关闭文件预览功能                    |
 | 6    | zP      | 打开或关闭目录预览功能                    |

> 操作命令

 | 序号 | 快捷键 | 对应操作     |
 |------|--------|--------------|
 | 1    | d      | 对应删除操作 |
 | 2    | p      | 对应粘贴操作 |
 | 3    | u      | 对应撤销操作 |
 | 4    | c      | 对应修改操作 |
 | 5    | y      | 对应复制操作 |
 | 6    | o      | 对应排序操作 |

> 批量修改文件名称

 批量选择文件之后，键入命令`:bulkname` ,会打开编辑器，将文件名称编辑后保存退出即可。

> 任务管理

在执行某些操作(比如复制一个大文件)时不能立即完成, 这在 `ranger` 中就是一个任务. 
你可以停止, 启动某个任务, 也可以对某个任务设置优先级.

w: 打开/关闭任务视图. 在w打开的任务视图中:  

     dd: 终止一个任务
     J: 降低当前任务的优先级
     K: 提升当前任务的优先级







