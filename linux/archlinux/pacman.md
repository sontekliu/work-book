# pacman 的用法

### 1. 安装软件包,软件包组

```
$ sudo pacman -S package_name package_name2
$ sudo pacman -S zsh wget curl vim

$ sudo pacman -S package_group
$ sudo pacman -S gnome
```

### 2. 删除软件包

删除单个软件包，但是保留其依赖
```
$ sudo pacman -R package_name
```
删除指定的软件包，以及所有依赖的软件包，但是被其他的软件包依赖的除外

```
$ sudo pacman -Rs package_name
```

### 3. 升级软件包

升级整个系统
```
$ sudo pacman -Syu
```

### 4. 清理软件包缓存
`pacman` 下载的软件包存在 `/var/cache/pacman/pkg/` 不会移除旧的和未安装的软件包，需要手动清理

```
$ sudo pacman -Sc 
$ sudo pacman -Scc # 清理所有缓存
```

[参考资料 Archlinux](https://wiki.archlinux.org/index.php/Pacman_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#.E7.94.A8.E6.B3.95)
