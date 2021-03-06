# Linux 使用 ssh 公钥实现免密码登陆

场景: A 机器(192.168.1.100)，B 机器(192.168.1.200)，实现 A 通过 `ssh` 免密码登陆 B

1. 在 A 机器下生成公钥／私钥对  

    ```
    [root@A~]# ssh-keygen -t rsa 
    ```
    回车三次，此时将在 `/root/.ssh` 目录下产生一对秘钥 `id_rsa` 和 `id_rsa.pub`

2. 将 A 机器下的 `/root/.ssh/id_rsa.pub` 复制到 B 机器的 `/root/.ssh/authorized_keys` 文件里，需先在 B 机器创建 `/root/.ssh` 目录  

    ```
    [root@A~]# scp -p /root/.ssh/id_rsa.pub root@192.168.1.200:/root/.ssh/authorized_keys  # 覆盖原来的
    或者
    [root@A~]# ssh-copy-id -i /root/.ssh/id_rsa.pub root@192.168.1.200 # 不会覆盖原来的
    ```
    此时需要输入 B 机器的密码，因为此时还未免密码。
    `ssh-copy-id` 可以把本地主机的公钥复制到远程主机的 `authorized_keys` 文件中，同时也会给远程主机的用户主目录下的 `~/.ssh` 和 `~/.ssh/authorized_keys` 设置合适的权限。复制主机，不需要指定到 `~/.ssh/authorized_keys` 文件。

3. 修改 authorized_keys 的权限为 600  

    ```
    [root@B~]# chmod 700 /root/.ssh
    [root@B~]# chmod 600 /root/.ssh/authorized_keys
    ```

4. A 机器登陆 B 机器  

    ```
    [root@A~] ssh root@192.168.1.200
    ```
    现在 A 机器登陆 B 机器不需要密码即可登陆。

5. 当 C 机器也要免密登陆 B 的时候，一定要将 C 的 `id_rsa.pub` 追加到 B 机器 `authorized_keys` 里面，不要对其覆盖。



