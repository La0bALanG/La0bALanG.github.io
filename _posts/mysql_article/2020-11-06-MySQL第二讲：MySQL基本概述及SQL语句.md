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
> ​																						———援引自：百度百科

# 数据库的主要应用范围

> 一切B/S及C/S类应用，诸如网站，软件，小程序等，包括各大其他行业也需要数据库支持。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201106140501700.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

# 数据库相关基础概念

- 数据：能够输入到计算机中并被识别处理的信息集合
- 数据结构：研究一个数据集合中数据之间的关系
- 数据库：按照数据结构，存储管理数据的仓库。数据库是再数据库管理系统管理和控制下，在一定介质上的数据集合
- 数据库管理系统：管理数据库的软件，用于建立和维护数据库
- 数据库系统：由数据库和数据库管理系统，开发工具等组成的集合

# 数据库分类和常见数据库

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

# 关系型数据库和MySQL

## 数据库结构

> 数据元素 --> 记录 --> 数据表 --> 数据库





