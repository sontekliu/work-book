## 本地与远程仓库的链接
> 本地与远程仓库的链接，一般是通过SSH进行链接

1. 首先在用户主目录下生成SSH-KEY
	ssh-keygen -t rsa -C "youremail@example.com"

2. 在当前目录下会生成.ssh文件
	将id_rsa.pub下的内容添加到github的SS keys中即可
