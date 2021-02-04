---
layout: post
title: MySQL第二讲：MySQL基本概述及SQL语句
date: 2020-11-06
tags: 
      - mysql
---

# <font face="楷体"  color='blue'> MySQL第二讲：MySQL基本概述及SQL语句</font>

<p><font face="楷体" color='blue'>作者：Barranzi_</font></p>
<p><font face="楷体" color='blue'>个人github主页：[github](https://github.com/La0bALanG)</font></p>
<p><font face="楷体" color='blue'>个人邮箱：awc19930818@outlook.com</font></p>
<p><font face="楷体" color='blue'>新时代的铁饭碗：一辈子不管走到哪里都有饭吃(还能吃上热乎的)。——佚名</font></p>
<p><font face="楷体" color='red'> 免责声明：</font></p>
<p><font face='楷体' color='red'>		本系列笔记撰写初衷就是为了分享个人知识以及个人学习历程中的感悟及思考，所涉及到的内容`仅供学习与交流`，请勿用作`非法或商业用途`！由此引发的任何法律纠纷`后果自负`，与作者本人无关！</font></p>
<p><font face="楷体"  color='red'>版权声明：</font></p>
<p><font face='楷体' color='red'>		未经作者本人授权，禁止转载！请尊重原创！</font></p>
<p><font face="楷体" color='blue'>注：本文所有代码、案例测试环境：1.Linux -- 系统版本：Ubuntu20.04 LTS   2.windows -- 系统版本：WIN10 64位家庭版</font></p>
------

# 数据存储发展历程

- 早期：人工管理阶段

  显著劣势：存储的数据无法共享，不能单独保存，且数据存储量有限

- 逐步发展：文件管理阶段(文档，表格等)

  优点：数据可以长期保存，且能够存储大量数据，使用时也相对简单

  缺点：数据一致性较差，数据查找时不太方便，数据的冗余度可能较大

- 主流思想：数据库管理

  优点：数据组织结构化，降低数据冗余度，提高了增删改查效率，且容易扩展，方便程序进行调用，方便做自动化处理

  缺点：需要使用sql或其他特定的语句实现，相对比较复杂

# MySQL简介

> MySQL是一个**关系型数据库管理系统****，**由瑞典MySQL AB 公司开发，属于 [Oracle](https://baike.baidu.com/item/Oracle) 旗下产品。MySQL 是最流行的[关系型数据库管理系统](https://baike.baidu.com/item/关系型数据库管理系统/696511)之一，在 WEB 应用方面，MySQL是最好的 [RDBMS](https://baike.baidu.com/item/RDBMS/1048260) (Relational Database Management System，关系数据库管理系统) 应用软件之一。
>
> MySQL是一种关系型数据库管理系统，关系数据库将数据保存在不同的表中，而不是将所有数据放在一个大仓库内，这样就增加了速度并提高了灵活性。
>
> MySQL所使用的 SQL 语言是用于访问[数据库](https://baike.baidu.com/item/数据库/103728)的最常用标准化语言。MySQL 软件采用了双授权政策，分为社区版和商业版，由于其体积小、速度快、总体拥有成本低，尤其是[开放源码](https://baike.baidu.com/item/开放源码/7176422)这一特点，一般中小型网站的开发都选择 MySQL 作为网站数据库。
>
> ​																																	———援引自：百度百科

- 官网地址：[https://www.mysql.com/

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020111314320143.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

- MySQL特点
  1. 是开源数据库，使用C和C++编写 
  2. 能够工作在众多不同的平台上
  3. 提供了用于C、C++、Python、Java、Perl、PHP、Ruby众多语言的API
  4. 存储结构优良，运行速度快
  5. 功能全面丰富

## MySQL数据库的主要应用范围

> 数据库的应用领域几乎涉及到了需要数据管理的方方面面，融机构、游戏网站、购物网站、论坛网站 ... ...都需要数据库进行数据存储管理。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201113142842520.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

## MySQL数据库相关基础概念

- 数据：能够输入到计算机中并被识别处理的信息集合
- 数据结构：研究一个数据集合中数据之间的关系
- 数据库：按照数据结构，存储管理数据的仓库。数据库是再数据库管理系统管理和控制下，在一定介质上的数据集合
- 数据库管理系统：管理数据库的软件，用于建立和维护数据库
- 数据库系统：由数据库和数据库管理系统，开发工具等组成的集合

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201106140501700.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

## 数据库分类和常见数据库

- 关系型数据库和非关系型数据库

  > 关系型：采用关系模型（二维表）来组织数据结构的数据库
  >
  > 非关系型：不采用关系模型组织数据结构的数据库

- 开源数据库和非开源数据库

  > 开源：使用全程完全免费且支持扩展
  >
  > 非开源：使用需收取一定费用且扩展性不高

- 常见关系型数据库和非关系型数据库

  > 关系型：MySQL，Oracle，SQL server，DB2 SQLite...
  >
  > 非关系型：MongoDB，Redis...

- 开源数据库及非开源数据库

  > 开源：MySQL、SQLite、MongoDB...
  >
  > 非开源：Oracle、DB2、SQL_Server

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201113142950863.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

## MySQL常用基本命令及操作

注意：确保当前本机或服务器内已安装完毕MySQL服务。

- 开启MySQL服务：

  ```mysql
  net start mysql
  ```

- 启动MySQL数据库（链接MySQL服务）：

  ```mysql
  mysql -h主机地址 -u用户名 -p密码
  ```

  - 主机地址：

    ​	本地连接 -- localhost、127.0.0.1、0.0.0.0

    ​	远程连接 -- 具体的主机IP地址

  - 用户名：登陆当前MySQL的系统用户名称。默认为root

  - 密码：设置的当前MySQL登陆密码。初次登陆需要使用初始密码。如何获取初始密码参见上一篇文章：MySQL第一讲：环境搭建

  - 通常，在无需远程连接MySQL，且通过默认用户登陆时，该命令可简化为如下：

    ```mysql
    mysql -uroot -p密码;
    ```

- 关闭连接：

  ```mysql
  CTRL + D
  exit
  quit
  ```

## 数据库结构

> 数据元素 --> 记录 --> 数据表 --> 数据库

- 数据库(databases)：包含多个数据表

- 数据表(table)：包含所有记录行及字段的表结构。表结构的行称为一条记录，表结构的列称为字段

- 数据元素(elements)：每一条记录内某字段下的具体数据对象

- 记录(row)：表中一行代表一条记录，表示一组完整的数据

- 字段(column)：表中每一列，表述该列数据的含义

  如下图：

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201113091020827.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

# SQL语句

## 什么是SQL语句

> SQL语句：结构化查询语言(Structured Query Language)，一种特殊目的的编程语言，是一种数据库查询和程序设计语言，用于存取数据以及查询、更新和管理关系数据库系统。

## SQL语句使用特点

> - SQL语言基本上独立于数据库本身
> - 各种不同的数据库对SQL语言的支持于

## 数据库管理基本语句

- 查看已有（现有）数据库：

  ```mysql
  show databases;
  ```

- 创建库：

  ```mysql
  create database 库名 [charactor set utf8];
  ```

  举个例子：

  ```mysql
  #创建student库，设置编码方式为utf8；
  create database student charactor set utf8;
  create database student charactor=utf8;
  ```

  > 注意:库名的命名
  >
  > - 数字、字母、下划线,但不能使用纯数字
  > - 库名区分字母大小写
  > - 不要使用特殊字符和mysql关键字

- 切换库

  ```mysql
  use 库名;
  ```

  举个例子：

  ```mysql
  use student;
  ```

- 查看当前所在库

  ```mysql
  select database();
  ```

- 删除库

  ```mysql
  drop database 库名;
  ```

  举个例子：

  ```mysql
  drop database student;
  ```

## 数据表管理

- 基本思路：
  - 确定存储内容
  - 明确字段构成
  - 确定字段数据类型

### 基本数据类型

- 数字类型：

  - 整数类型：INT，SMALLINT，TINYINT，MEDIUMINT，BIGINT
  - 浮点类型：FLOAT，DOUBLE，DECIMAL
  - 比特值类型：BIT

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201113150545930.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

  > 注意：
  >
  > - 对于准确性要求比较高的东西，比如money，用decimal类型减少存储误差。声明语法是DECIMAL(M,D)。M是数字的最大数字位数，D是小数点右侧数字的位数。比如 DECIMAL(6,2)最多存6位数字，小数点后占2位,取值范围-9999.99到9999.99。
  > - 比特值类型指0，1值表达2种情况，如真，假

- 字符串类型：
  - 普通字符串： CHAR，VARCHAR
  - 存储文本： text
  - 存储二进制数据： BLOB
  - 存储选项型数据：ENUM，SET

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/2020111315075767.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

  > 注意：
  >
  > 1. char：定长，即指定存储字节数后，无论实际存储了多少字节数据，最终都占指定的字节大小。默认只能存1字节数据。存取效率高。
  > 2. varchar：不定长，效率偏低 ，但是节省空间，实际占用空间根据实际存储数据大小而定。必须要指定存储大小 varchar(50)
  > 3. enum用来存储给出的多个值中的一个值,即单选，enum('A','B','C')
  > 4. set用来存储给出的多个值中一个或多个值，即多选，set('A','B','C')

### 表管理基本操作

- 创建表

  ```mysql
  create table 表名(字段名 数据类型 约束,字段名 数据类型 约束,...,字段名 数据类型 约束);
  ```

  字段约束：

  - 如果你想设置数字为无符号则加上 unsigned
  - 如果你不想字段为 NULL 可以设置字段的属性为 NOT NULL， 在操作数据库时如果输入该字段的数据为NULL ，就会报错。
  - DEFAULT 表示设置一个字段的默认值
  - COMMENT  增加字段说明
  - AUTO_INCREMENT定义列为自增的属性，一般用于主键，数值会自动加1。
  - PRIMARY KEY 关键字用于定义列为主键。主键的值不能重复,且不能为空。

  举个例子：

  ```mysql
  #创建班级表
  create table class_1(
  	id int primary key auto_increment,
      name varchar(32) not null,
      age tinyint unsigned not null,
      sex enum('w','m'), 
      score float default 0.0
  );
  
  #创建兴趣班表
  create table interset (
  	id int primary key auto_increment,
      name varchar(32) not null,
      hobby set('sing','dance','draw'),
      level char not null,
      price decimal(6,2),
      remark text
  );
  ```

- 查看数据表

  ```mysql
  show tables;
  ```

- 查看表结构

  ```mysql
  desc 表名;
  ```

- 查看数据表创建信息

  ```mysql
  show create table 表名;
  ```

- 删除表

  ```mysql
  drop table 表名;
  ```

### 表数据基本操作

- 表数据插入一条记录（插入一行:insert）

  ```mysql
  insert into 表名 values (值1),(值2),...;
  insert into 表名 (字段1,...) values(值1),...;
  ```

  举个例子：

  ```mysql
  insert into class_1 values (2,'Baron',10,'m',91),(3,'Jame',9,'m',90);
  
  insert into class_1 (name,age,sex,score) values ('Lucy',17,'w',81);
  ```

- 表数据中查询（查询某值或某条记录:select）

  ```mysql
  select * from 表名 [where 条件];
  select 字段1,字段2 from 表名 [where 条件];
  ```

  举个例子：

  ```mysql
  select * from class_1;
  select name,age from class_1;
  ```

- where子句

  where子句在sql语句中扮演了重要角色，主要通过一定的运算条件进行数据的筛选，在查询，删除，修改中都有使用。

  - 算数运算符

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201113153940647.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

  ​	举个例子：

  ```mysql
  select * from class_1 where age % 2 = 0;
  ```

  - 比较运算符

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/2020111315413639.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

  ​	举个例子：

  ```mysql
  select * from class_1 where age > 8;
  select * from class_1 where age between 8 and 10;
  select * from class_1 where age in (8,9);
  ```

  - 逻辑运算符

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201113155341279.png#pic_center)

  ​	举个例子：

  ```mysql
  select * from class_1 where sex='m' and age>9;
  ```

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201113155428838.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

- 更新表记录(update)

  ```mysql
  update 表名 set 字段1=值1,字段2=值2,... where 条件;
  
  注意:update语句后如果不加where条件,所有记录全部更新
  ```

  举个例子：

  ```mysql
  update class_1 set age=11 where name='Abby';
  ```

- 删除表记录（delete）

  ```mysql
  delete from 表名 where 条件;
  
  注意:delete语句后如果不加where条件,所有记录全部清空
  ```

  举个例子：

  ```mysql
  delete from class_1 where name='Abby';
  ```

- 表字段的操作(alter)

  ```mysql
  语法 ：alter table 表名 执行动作;
  
  * 添加字段(add)
      alter table 表名 add 字段名 数据类型;
      alter table 表名 add 字段名 数据类型 first;
      alter table 表名 add 字段名 数据类型 after 字段名;
  * 删除字段(drop)
      alter table 表名 drop 字段名;
  * 修改数据类型(modify)
      alter table 表名 modify 字段名 新数据类型;
  * 修改字段名(change)
      alter table 表名 change 旧字段名 新字段名 新数据类型;
  * 表重命名(rename)
      alter table 表名 rename 新表名;
  ```

  举个例子：

  ```mysql
  alter table hobby add tel char(11) after name;
  alter table hobby modify tel char(16);
  alter table hobby change tel phone char(16);
  ```

- 时间类型数据
  - 日期 ： DATE
  - 日期时间： DATETIME，TIMESTAMP
  - 时间： TIME
  - 年份 ：YEAR

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201116135122839.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)
  - 时间格式

  ```sql
  date ："YYYY-MM-DD"
  time ："HH:MM:SS"
  datetime ："YYYY-MM-DD HH:MM:SS"
  timestamp ："YYYY-MM-DD HH:MM:SS"
  ```

  > 注意:
  >
  > 1. datetime ：以系统时间存储
  > 2. timestamp ：以标准时间存储但是查看时转换为系统时区，所以表现形式和datetime相同

  ```mysql
  create table marathon (
      id int primary key auto_increment,
      athlete varchar(32),birthday date,
      registration_time datetime,
      performance time
  );
  ```

  - 日期时间函数

    - now() 返回服务器当前日期时间，格式对应datetime类型

  - 时间操作

    时间类型数据可以进行比较和排序等操作，在写时间字符串时尽量按照标准格式书写。

  ```mysql
    select * from marathon where birthday>='2000-01-01';
    select * from marathon where birthday>="2000-07-01" and performance<="2:30:00";
  ```

  

