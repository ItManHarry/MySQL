# MySQL数据库

## 安装

- 方式一：yum/rpm方式安装MySQL 。 （使用场景并发不大，公司内部，企业内部的一些应用场景）

- 方式二：常规方式编译安装MySQL：./configure;make;make install

- 方式三：采用cmake/gmake方式编译安装MySQL：./cmake;make;make install

- 方式四：使用二进制方式编译安装MySQL

### 解压版MySQL安装 - Windows

```
	配置步骤：

	1. 下载MySQL Community Server 5.6.24-

	2. 解压MySQL压缩包
		将以下载的MySQL压缩包解压到自定义目录下,我的解压目录是:
		 "F:\Program Files\MySQL\mysql-5.6.24-win32"
		 将解压目录下默认文件 my-default.ini 拷贝一份，改名 my.ini
		 复制下面的配置信息到 my.ini 保存
		#如果没有my-default.ini,可自己新建my.ini或者从其他地方中获取，
		文件内容如下：
	#########################################################
	   [client]
		port=3306
		default-character-set=utf8
		[mysqld]
		port=3306
		character_set_server=utf8
		basedir=F:\Program Files\MySQL\mysql-5.6.24-win32
		#解压目录
		datadir=F:\Program Files\MySQL\mysql-5.6.24-win32\data
		#解压目录下data目录
		sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES 
		[WinMySQLAdmin]
		F:\Program Files\MySQL\mysql-5.6.24-win32\bin\mysqld.exe
		default-storage-engine=MyISAM
	 #########################################################

	3. 添加环境变量
		操作如下：
		1）右键单击我的电脑->属性->高级系统设置(高级)->环境变量
		  点击系统变量下的新建按钮
		  输入变量名：MYSQL_HOME
		   输入变量值：F:\Program Files\MySQL\mysql-5.6.24-win32
		   #即为mysql的自定义解压目录。
		2）选择系统变量中的Path
		   点击编辑按钮
		  在变量值中添加变量值：%MYSQL_HOME%\bin
		   注意是在原有变量值后面加上这个变量，用;隔开，不能删除原来的变量值，

	4. 将mysql注册为windows系统服务
		1）从控制台进入到MySQL解压目录下的 bin 目录下：
		2）输入服务安装命令：
		mysqld install MySQL --defaults-extra-file="F:\Program Files\MySQL\mysql-5.6.24-win32\my.ini"
		mysqld install MySQL --defaults-extra-file="C:\Program Files\mysql-5.6.24-win32\my.ini"
		 #解压目录下修改的my.ini文件
		安装成功后会提示服务安装成功。
		#注：my.ini文件放在MySQL解压后的根目录下
		#移除服务命令为：mysqld remove

	5. 启动MySQL服务
		方法一：
			启动服务命令为：net start mysql
		 方法二：
			打开管理工具 服务，找到MySQL服务。
			通过右键选择启动或者直接点击左边的启动来启动服务。

	6. 修改 root 账号的密码
		刚安装完成时root账号默认密码为空，此时可以将密码修改为指定的密码。如：123456
		 c:>mysql –uroot
		 mysql>show databases;
		 mysql>use mysql;
		 mysql>UPDATE user SET password=PASSWORD("123456") WHERE user='root';
		 mysql>FLUSH PRIVILEGES;
		 mysql>QUIT
```

### 解压版MySQL安装 - Linux

```

```