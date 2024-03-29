# 目录

- MySQL介绍

- 数据类型

- 数据库与表的创建

- 数据库的备份与还原

---

## MySQL介绍
  
> Mysql是最流行的关系型数据库管理系统，在WEB应用方面MySQL是最好的RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

## 创建用户
- 使用root登录MySQL
```
  # 仅本地访问的用户
  create user 'username'@'localhost' identified by 'password';
  # 可以远程访问的用户
  create user 'username'@'%' identified by 'password';
  # 删除用户
  drop user 'username'@'localhost/%';
  # 重置密码
  use mysql;
  1. update user set authentication_string=pasword('new password') where user = 'user name';
  2. 使用 SET PASSWORD 修改密码命令格式为 set password for username @localhost = password(newpwd);
  3. 使用 mysqladmin 命令修改 MySQL 的 root 用户密码格式为 mysqladmin -u用户名 -p旧密码 password 新密码；
  注意：修改密码的命令中 -uroot 和 -proot 是整体，不要写成 -u root -p root，-u 和 root 间可以加空格，但是会有警告出现，所以就不要加空格了；
```
- 授权数据库
```
  grant all privileges on database_name.* to user_name;
```
- 撤销授权
```
  revoke all privileges on database_name.* from user_name;
```

## 数据类型

- MySQL中常见的数据类型有:varchar(n),float,int(n),bigint(n),date,datetime,text.

- 默认值:default 'value'.

- 非空:not null.

- 自动增长:auto_increment(使用在int类型数据,一般用于创建key).

- 主键:primary key.

- 列备注:comment 'comment'

- 数据唯一: unique,该列数据不能重复.

## 数据库与表的创建

- 创建数据库

    
    ```
      CREATE DATABASE [DATABASE-NAME];
    ```
    
- 创建表

  ```
    CREATE TABLE USERS(
      UID smallint(6) NOT NULL AUTO_INCREMENT PRIMARY KEY COMMENT 'ID',
      NAME varchar(50) NOT NULL COMMENT 'NAME',
      AGE smallint(6) NOT NULL COMMENT 'AGE'
    ) 
  ```
## 数据库的备份与还原

- 命令方式在`cmd`下执行备份数据命令(此方式只是备份数据库里的表)

```
  
  命令格式：
  mysqldump -h[主机所在IP] -u[用户名] -p [要导出的数据库]>[导出的路径//[文件名].sql]
  实例：
  Remote:
  > mysqldump -h 192.168.2.184 -u root -p dxq_oaxt > d:\dxq_oaxt.sql    
  Local:
  > mysqldump -uroot -p [DatabaseName] > D:/backfile.sql
```
- MySQL下还原数据

  - 首先进入MySQL`cmd`下执行: 
  ``` 
    mysql -uroot -p 
  ```
  
  
  - 执行`show databases;`查看数据库  
  
  - 创建数据库`create database fsdb;`
  
  - 切换数据库 `use fsdb;`  
  
  - 执行数据备份脚本 `source d:/fsdb_bak.sql`
