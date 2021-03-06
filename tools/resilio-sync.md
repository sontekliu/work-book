# Resilio-sync Install 

> https://www.btsynckeys.com

### For Debian-based Linux (Debian, Ubuntu, Zorin, Elementary)

1. 创建文件 `/etc/apt/sources.list.d/resilio-sync.list`
2. 写入如下内容:   
    `deb http://linux-packages.resilio.com/resilio-sync/deb resilio-sync non-free`      
    或者执行如下命令：     
    `echo "deb http://linux-packages.resilio.com/resilio-sync/deb resilio-sync non-free" | sudo tee /etc/apt/sources.list.d/resilio-sync.list`
3. 执行如下命令，添加public key :    
    `wget -qO - https://linux-packages.resilio.com/resilio-sync/key.asc | sudo apt-key add -`
4. 安装 Resilio-sync   
    ```
        sudo apt-get update    
        sudo apt-get install resilio-sync   
    ```


### For RPM-based Linux (Red Hat, Fedora, CentOS, OpenSUSE)

1. 创建文件: `/etc/yum.repos.d/resilio-sync.repo`
2. 添加如下内容：     
    ```
        [resilio-sync]   
        name=Resilio Sync   
        baseurl=http://linux-packages.resilio.com/resilio-sync/rpm/$basearch   
        enabled=1   
        gpgcheck=1   
    ```
3. 添加Public Key：
    ```
        rpm --import https://linux-packages.resilio.com/resilio-sync/key.asc
    ```
4. 安装Resilio-sync
    ```
        yum update    
        yum install resilio-sync   
    ```

### Resilio Sync 的使用

1. 使用当前用户启用Resilio-sync 服务，编辑如下内容:   
    `edit file /usr/lib/systemd/user/resilio-sync.service and change "WantedBy=multi-user.target" to "WantedBy=default.target". Save. `
2. 启用Resilios-sync服务   
    `systemctl --user enable resilio-sync`
3. Systemctl 还可以运行如下命令:
    ```
        systemctl --user start resilio-sync  
        systemctl --user stop resilio-sync  
        systemctl --user enable resilio-sync  
        systemctl --user disable resilio-sync  
        systemctl --user status resilio-sync   
    ```
4. 在2.2版本之前不支持Linux Gui版，使用浏览器进行访问    
    `http://localhost:8888/gui`

### Resilio Sync 的使用(2)

1. 下载 resilio-sync 软件
```
    wget https://download-cdn.resilio.com/stable/linux-x64/resilio-sync_x64.tar.gz
```
2. 解压缩，生成配置文件
```
    $ tar -zxvf resilio-sync_x64.tar.gz
    $ ./rslsync --dump-sample-config > bitsync.conf
```
3. 修改配置文件，如图:

![resilio-sync-config](./image/resilio-sync-config.png)

4. 启动软件
```
    $ ./rslsync --config bitsync.conf
```
5. 打开浏览器，输入: `http://127.0.0.1:9999` 显示如下图表示启动成功

![resilio-sync-index](./image/resilio-sync-index.jpg)


### Resilio Sync 的卸载

1. For Debian-based Linux:     
    `sudo apt-get purge btsync`

2. For RPM-based Linux   
    `sudo yum remove btsync`

















