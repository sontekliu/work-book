## Linux 使用 ssh 公钥实现免密码登陆

场景: A 机器(192.168.1.100)，B 机器(192.168.1.200)，实现 A 通过 `ssh` 免密码登陆 B

1. 在 A 机器下生成公钥／私钥对  
```
[root@A~]# ssh-keygen -t rsa 
```
回车三次，此时将在 `/root/.ssh` 目录下产生一对秘钥 `id_rsa` 和 `id_rsa.pub`

2. 将 A 机器下的 `/root/.ssh/id_rsa.pub` 复制到 B 机器的 `/root/.ssh/authorized_keys` 文件里，需先在 B 机器创建 `/root/.ssh` 目录  
```
[root@A~]# scp /root/.ssh/id_rsa.pub root@192.168.1.200:/root/.ssh/authorized_keys
```
此时需要输入 B 机器的密码，因为此时还未免密码。

3. 修改 authorized_keys 的权限为 600  
```
[root@B~]# chmod 600 /root/.ssh/authorized_keys
```

4. A 机器登陆 B 机器  
```
[root@A~] ssh root@192.168.1.200
```
现在 A 机器登陆 B 机器不需要密码即可登陆。


