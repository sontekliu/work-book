mysql
	--user -u
	--password -p
	--host     -h
	--port
	--protocol
	--database DATABASE -D

mysql的工作模式：
	1.交互式模式
	2.批处理模式(脚本模式)
		mysql> source file.sql
	或者
		mysql < file.sql
	
mysqladmin [options] command [arg] [command [arg]]
	mysqladmin create database DATABASE_NAME
	mysqladmin drop database DATABASE_NAME
	mysqladmin ping
	mysqladmin processlist
	mysqladmin status 
					--sleep N : 显示频率
					--count N : 显示多少次
	mysqladmin extended-status : 显示状态变量
	mysqladmin variables:		 显示服务器变量
	flush-privileges			 刷新授权表

	
