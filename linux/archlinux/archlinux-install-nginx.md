# Archlinux 安装 Nginx

### 1. 安装 

```shell
# pacman -S nginx
```

安装完成之后， 配置 `Nginx` 在 `/etc/nginx` 目录，网页文件在 `/usr/share/nginx` 目录下。

### 2. 启动 nginx

```shell
# systemctl start nginx.service     # 启动
# systemctl restart nginx.service   # 重启
# systemctl status nginx.service    # 查看状态
# systemctl enable nginx.service    # 开机启动
```

### 3. 配置 Nginx

将不同的 `server` 模块放到不同的文件里，这样方便管理。

创建以下目录：

```shell
# mkdir /etc/nginx/sites-available
# mkdir /etc/nginx/sites-enabled
```

在 `sites-available` 目录下创建一个或者多个服务模块。

```
/etc/nginx/sites-available/example
------------------------------------
server {
    .....
}
```

把 `include sites-enabled/*;` 放到 `http` 模块的末尾。

```
/etc/nginx/nginx.conf
-------------------------------------
...
http {
    ...
    include sites-enabled/*;
}
...
```

启用一个 `server` 模块，只需要创建简单的符号连接。

```shell
# ln -s /etc/nginx/sites-available/example /etc/nginx/sites-enabled/example 
```

如果要移出一个模块：

```shell
# unlink /etc/nginx/sites-enabled/example
```

此过程需要重启 `Nginx` 。
