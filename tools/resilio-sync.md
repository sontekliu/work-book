### Resilio-sync Install 

#### For Debian-based Linux (Debian, Ubuntu, Zorin, Elementary)

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


#### For RPM-based Linux (Red Hat, Fedora, CentOS, OpenSUSE)

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

#### Resilio Sync 的使用

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



















