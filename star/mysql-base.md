文件数据库缺陷：
	1、数据冗余和不一致性
	2、数据访问困难
	3、数据孤立
	4、完整性问题
	5、原子性问题
	6、并发访问问题
	7、安全性问题

关系模型：(结构化数据模型)
	关系模型
	实体-关系模型
	对象关系模型:基于对象的数据模型
	半结构化数据模型：XML(扩展标记语言)

关系：关系代数运算
	交集
	并集
	差集
	全集
	补集

DML:数据操作语言
	INSERT
	DELETE
	SELECT
	UPDATE
DDL:数据定义语言
	CREATE
	DROP
	ALTER
DCL:数据控制语言
	GRANT
	REVOKE


RDB对象：
	库、表、索引、视图、用户、存储过程、存储函数、触发器、事件调度器
	约束
		域约束：数据类型约束
		外键约束：引用完整性约束
		主键约束：某字段能唯一标识此字段所属的实体，并且不允许为空
			一张表中只能有一个主键
		唯一性约束：每一行的某个字段都不允许出现相同值，可以为空
			一张表中可以有多个
		检查性约束：例如年龄

数据查询和存储：
	存储管理器：
		权限及完整性管理器
		事物管理器
		文件管理器
		缓冲器管理器
	查询管理器：
		DML解释器
		DDL解释器
		DCL解释器
		查询执行引擎
单进程
	多线程
	
关系运算：
	投影：只输出指定属性
	选择：只输出符合条件的行
	自然连接：具有相同名字的属性值上所有取值相同的行
	笛卡尔积：
		(a + b) * (c + d) = ac + ad + bc + bd
	并：UNION，集合运算


SQL查询语句:
	SQL-86
	SQL-89
	SQL-92
	SQL-99
	SQL-03
	SQL-08

SQL语言的组成部分：
	DDL
	DML
	完整性定义语言：DDL的一部分功能
	视图定义
	事物控制
	嵌入式SQL和动态SQL
	授权:DCL

MySQL存储引擎
	MyISAM:
		不支持事物，特别适合数据仓库，
		适合查询较多，修改较少的场景
	InnoDB

MySQL的安装：
	专用软件包管理器安装
	deb,rpm
	rpm:
		RHEL(Oracle Linux),CentOS
		SUSE
	通用二进制格式包安装
		gcc:x86, x64
	源代码安装
		cmake编译

配置文件查找顺序：
	/etc/my.cnf
	/etc/mysql/my.cnf
	$MYSQL_HOME/my.cnf
	default-extra-file=/path/to/file
	~/.my.cnf

MySQL密码修改:
1. # mysqladmin -u root -h HOSTNAME password  'NEW_PASSWORD' -p 'OLD_PASSWORD'
2. # mysql> SET PASSWORD FOR 'USERNAME'@'HOST' = PASSWORD('NEW_PASSWORD')
3. # mysql> UPDATE mysql.user SET PASSWORD = PASSWORD('NEW_PASSWORD') WHERE
	FLSUH PRIVILEGES; 重读用户授权






