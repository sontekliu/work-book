##1. 使用git前需做几点配置，具体配置如下
### 1)对终端显示的配置，给文字添加颜色，更易于阅读
	git config --global color.diff auto
	git config --global color.status auto
	git config --global color.branch auto
### 2)向服务器端提交代码时，需要有用户名和邮箱
	git config --global user.name "sontekliu"
	git config --global user.email "sontekliu@outlook.com"
### 3)git差异化比较工具设置
	git config --global core.editor vim
	git config --global merge.tool vimdiff

### 4)配置信息查看
	git config --list
	git config user.name
