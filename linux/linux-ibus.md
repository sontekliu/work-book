### Linux中使用拼音输入法

**1. Linux中设置ibus**      

System -> Perferences -> Input Method -> input method preferences 设置相应的输入法即可

**2. 重新安装python后，输入法失效**   
```
	找到如下文件:
	/usr/libexec/ibus-ui-gtk
	/usr/libexec/ibus-engine-table
	/usr/bin/ibus-setup
	并把其中的 "exec python" 改为 "exec python2.6"
	然后安装
	yum install ibus-table
	yum install ibus-pinyin
	重启 reboot
```





