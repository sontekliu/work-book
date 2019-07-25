# Archlinux 安装 mysql

### 1. 安装

```shell
# pacman -S mariadb mairadb-clients libmariadbclient
```
现在已创建完 `mysql` 用户，可以使用 `cat /etc/passwd` 检查。

### 2. 初始化数据

```shell
# mysql_install_db --user=mysql --basdir=/usr --datadir=/opt/mysql/data
```

此时创建了 `root` 账号，但是还没有设置密码

### 3. 启动 MySQL

如果你的 `datadir` 不是 `/var/lib/mysql` 的话，需要修改配置文件，`/etc/my.cnf.d/server.cnf`
在 `[mysqld]` 部分设置 `datadir=`，如:

```
[mysqld]
datadir=/opt/mysql/data
```

现在可以启动 `MySQL` 了。

```shell
# systemctl start mysqld
```

### 4. 设置 root 密码

```
# mysqladmin -u root password '123456'
```

### 5. 设置开机启动

```
# systemctl enable mysqld
Created symlink /etc/systemd/system/multi-user.target.wants/mariadb.service → /usr/lib/systemd/system/mariadb.service.
```

### 6. 添加用户，并赋权

```
# mysql -u root -p 

MariaDB [mysql]> CREATE USER 'snow'@'%' IDENTIFIED BY '123456';
MariaDB [mysql]> GRANT ALL PRIVILEGES ON *.* TO 'snow'@'%' WITH GRANT OPTION;
MariaDB [mysql]> FLUSH PRIVILEGES;
MariaDB [mysql]> quit;
```

添加了用户 `snon` 并赋予了所有权限，支持远程连接。

### 7. MySQL 读取配置文件的顺序

```
/etc/my.cnf -> /etc/my.cnf.d/ -> ~/.my.cnf
```

### 8. 为 MySQL 配置 utf8 编码

编辑 `/etc/my.cnf` 添加如下：
```
[client-server]
init_connect                = 'SET collation_connection = utf8_general_ci,NAMES utf8'
collation_server            = utf8_general_ci
character_set_client        = utf8
character_set_server        = utf8
```

或者 

```
[mysqld]
init_connect                = 'SET collation_connection = utf8_general_ci,NAMES utf8'
collation_server            = utf8_general_ci
character_set_client        = utf8
character_set_server        = utf8
```











