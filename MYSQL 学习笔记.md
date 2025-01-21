# MYSQL 学习笔记

## 01_数据库的准备工作

基本命令：

```sql
# 通过CMD连接mysql
> mysql -u root -p（密码） -h（地址） -P（端口）  ## -p 后无内容，则会在回车后，需要手动输入隐私密码
> ******

exit # 退出MySQL

select version(); # 查询版本  并以';'结尾。 否则命令会延续到下一行。
```

MySQL可视化工具：（比CMD好用，而且能识别SQL关键字，且免费。）

SQLyog

## 02_数据定义语言DDL

1. 数据定义语言概述
2. SQL命名规定喝规范
3. 数据定义语言之库管理
4. 数据定义语言之表管理

### 1. 数据定义语言概述

创建库——定字段——创建表——插数据

DDL Data definition Language

DDL不涉及对数据的操作，而是关注数据库的结构喝元数据（容器）

**DDL三个关键字：**

CREATE: 用于创建数据库、表、索引、视图等。

ALTER: 用于修改数据库对象的结构，如修改表结构、添加列、删除列等。

DROP: 用于删除数据库对象，如删除表、删除索引等。

### 2. SQL命名规定和规范

1. 注释清晰，简洁
2. 库、表、列名应该使用小写字幕，并使用下划线（__）或驼峰命名法
3. 库，表，字段简洁
4. 库名应该与对应程序名一致
5. 表名最好遵循“业务名称__表”
6. 列名遵循“表实体__属性” 

参见  阿里巴巴规范手册

### 3. 数据定义语言之库管理

#### 3.1 库管理：创建库

```sql
方式一： CREATE DATABASE 数据库名;
方式二： CREATE DATABASE IF NOT EXISTS 数据库名;  （推荐）
方式三： CREATE DATABASE 数据库名 CHARACTER SET 字符集;
	    CREATE DATABASE 数据库名 COLLATE 排序规则
方式四： CREATE DATABASE 数据库名 CHARACTER SET 字符集  COLLATE 排序规则
```

```sql
# 创建数据库
CREATE DATABASE 数据库名;
# 判断再创建数据库
CREATE DATABASE IF NOT EXISTS 数据库名;
# 创建数据库指定字符集
CREATE DATABASE 数据库名 CHARACTER SET 字符集;
# 创建数据库指定排序方式

# 创建数据库指定字符集和排序方式
# 查询数据库的字符集和排序方式
# 练习：
#	创建ddl_d1库，指定字符集为utf8，且排序方式为大小写敏感的utf8mb4_0900_as_cs模式

```





