# 目录

- MySQL介绍

- 数据库与表的创建

- 数据库的备份与还原

- 简单查询

---

## MySQL介绍
  
> Mysql是最流行的关系型数据库管理系统，在WEB应用方面MySQL是最好的RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

## 数据库与表的创建

- 创建数据库

    
    ```
      CREATE DATABASE [DATABASE-NAME];
    ```
    
- 创建表

  ```
    CREATE TABLE USERS(
      UID smallint(6) NOT NULL AUTO_INCREMENT,
      NAMEchar(50) NOT NULL,
      AGE smallint(6) NOT NULL
    ) 
  ```
## 数据库的备份与还原

- 命令方式在`cmd`下执行备份数据命令(此方式只是备份数据库里的表)

```
  mysqldump -uroot -p [DatabaseName] > D:/backfile.sql
  
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
