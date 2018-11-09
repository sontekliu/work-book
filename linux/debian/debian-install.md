# Debian 安装

首先从 Debian 官网下载 Debian 操作系统。本文安装的操作系统是 debian-9.5.0，本文是基于 VirtualBox VM 进行安装的，具体安装步骤如下：

1. 启动虚拟机时的首个界面，选择使用图形界面安装的方式  
![开始安装](./images/debian-install/1.png)  

2. 选择语言，最好选择 English，也可以选择简体中文
![选择语言](./images/debian-install/2.png)  

3. 选择所在的地区，按实际情况选择即可，此处选择 China
![选择地区](./images/debian-install/3.png)  
![选择亚洲](./images/debian-install/4.png)  
![选择中国](./images/debian-install/5.png)  

4. 配置 Locale 
![配置Locale](./images/debian-install/6.png)  

5. 配置键盘键映射
![配置键盘](./images/debian-install/6.png)  

6. 配置键盘键映射
![配置键盘](./images/debian-install/7.png)  
![配置中](./images/debian-install/8.png)  

7. 配置主机名称
![配置hostname](./images/debian-install/9.png)  

8. 设置 root 的密码
![设置密码](./images/debian-install/11.png)  

9. 新建用户以及设置密码
![创建用户全名](./images/debian-install/12.png)  
![新用户的用户名](./images/debian-install/13.png)  
![设置密码](./images/debian-install/14.png)  

10. 磁盘分区
![选择手动分区](./images/debian-install/15.png)  
![选择手动分区](./images/debian-install/16.png)  
![选择手动分区](./images/debian-install/17.png)  
![选择手动分区](./images/debian-install/18.png)  

11. 创建 /boot 分区，一般设置 1G 大小
![创建boot分区](./images/debian-install/19.png)  
![设置1G](./images/debian-install/20.png)  
![选择主分区](./images/debian-install/21.png)  
![开始](./images/debian-install/22.png)  
![选择文件类型](./images/debian-install/23.png)  
![选择boot](./images/debian-install/24.png)  
![选择boot](./images/debian-install/25.png)  
![完成](./images/debian-install/26.png)  
![返回](./images/debian-install/27.png)  

12. 创建根分区，大小设置 25G 左右，可根据实际情况设置
![创建新分区](./images/debian-install/28.png)  
![设置25G](./images/debian-install/29.png)  
![选择主分区](./images/debian-install/30.png)  
![开始](./images/debian-install/31.png)  
![完成](./images/debian-install/32.png)  
![返回](./images/debian-install/33.png)  

13. 创建 swap 分区 一般设置实际内存的 2 倍，但是最大不要超过 8G 
![创建新分区](./images/debian-install/34.png)  
![设置8G](./images/debian-install/35.png)  
![选择主分区](./images/debian-install/36.png)  
![开始](./images/debian-install/37.png)  
![选择文件类型](./images/debian-install/38.png)  
![选择swap类型](./images/debian-install/39.png)  
![选择完成](./images/debian-install/40.png)  
![完成](./images/debian-install/41.png)  
![返回](./images/debian-install/42.png)  

14. 创建 /home 分区，剩下的空间可全部分给 /home 分区
![创建新分区](./images/debian-install/43.png)  
![设置大小](./images/debian-install/44.png)  
![选择主分区](./images/debian-install/45.png)  
![选择完成](./images/debian-install/46.png)  
![完成分区](./images/debian-install/47.png)  
![写入磁盘](./images/debian-install/48.png)  

15. 安装系统  
![安装](./images/debian-install/49.png)  

16. 配置包管理，是否启用网络镜像  
![是否启用镜像](./images/debian-install/50.png)  
![选择镜像地区](./images/debian-install/51.png)  
![选择163镜像](./images/debian-install/52.png)  
![配置代理](./images/debian-install/53.png)  
![完成镜像设置](./images/debian-install/54.png)  

17. 安装 GRUB 到磁盘
![安装 GRUB](./images/debian-install/55.png)  
![安装 GRUB](./images/debian-install/56.png)  

18. 安装完成并重启
![安装完成](./images/debian-install/57.png)  

19. 大功告成，看到登录界面
![登录界面](./images/debian-install/58.png)  
