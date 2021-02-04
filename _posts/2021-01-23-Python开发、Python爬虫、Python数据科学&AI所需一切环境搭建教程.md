---
layout: post
title: Python开发、Python爬虫、Python数据科学&AI所需一切环境搭建教程
date: 2021-01-23
tags: 
     - Python
     - Linux
     - Anaconda3
     - django 
---

# <font face="楷体"  color='blue'>Python开发、Python爬虫、Python数据科学&AI所需一切环境搭建教程</font>

<p><font face="楷体" color='blue'>作者：Barranzi_</font></p>
<p><font face="楷体" color='blue'>个人github主页：[github](https://github.com/La0bALanG)</font></p>
<p><font face="楷体" color='blue'>个人邮箱：awc19930818@outlook.com</font></p>
<p><font face="楷体" color='blue'>新时代的铁饭碗：一辈子不管走到哪里都有饭吃(还能吃上热乎的)。——佚名</font></p>
<p><font face="楷体" color='red'> 免责声明：</font></p>
<p><font face='楷体' color='red'>		本系列笔记撰写初衷就是为了分享个人知识以及个人学习历程中的感悟及思考，所涉及到的内容`仅供学习与交流`，请勿用作`非法或商业用途`！由此引发的任何法律纠纷`后果自负`，与作者本人无关！</font></p>
<p><font face="楷体"  color='red'>版权声明：</font></p>
<p><font face='楷体' color='red'>		未经作者本人授权，禁止转载！请尊重原创！</font></p><p><font face='楷体' color='red'>既然学的是Python，不知道祖师爷是谁可还好？无图言x，上祖师爷！</font></p>

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/tlYd2EOzWnss4a7r6nPRxicEFk3gvxdh0ORZdCkQrrKm5SQl3dh6XkVibqB2voyu1G8mHytiaa5D241u5vkwaic7YQ/640?wx_fmt=jpeg)



<p><font face="楷体" color='blue'>注：本文所有代码、案例测试环境：1.Linux -- 系统版本：Ubuntu20.04 LTS   2.windows -- 系统版本：WIN10 64位家庭版</font></p>

------

# 说明

> 本教程包含学习Python的任何技术方向、任何岗位所需的任何环境的安装教程，且包含三大操作系统：Windows、Linux（Ubuntu20.04 LTS桌面版）、macOS操作系统下的环境搭建，史上最全，最后一次整理，后期各博客中涉及的技术不再单独做环境搭建的赘述。

# Python相关环境搭建的特殊性

> 本文因面向人群的特殊性：既有小白会阅读，也有老鸟会阅读，所以本文讲解环境搭建时，大致分为：
>
> - 仅供学习使用的环境搭建
> - 生产环境下的环境搭建（当然也可用于学习）
>
> 读者自行选择即可。

# 常用虚拟机软件——VMWare WorkStation Pro的安装及配置 

## Windows系统

- 下载地址：https://www.vmware.com/cn/products/workstation-pro/workstation-pro-evaluation.html

- 安装步骤：一路傻瓜式下一步即可。

  注意：如果需要更改自定义路径，则手动自己选择，否则默认安装自C盘

- VMware许可证密钥：自行百度，以下附若干目前可用密钥：

  UG5J2-0ME12-M89WY-NPWXX-WQH88

  GA590-86Y05-4806Y-X4PEE-ZV8E0

  YA18K-0WY8P-H85DY-L4NZG-X7RAD

  UA5DR-2ZD4H-089FY-6YQ5T-YPRX6

  B806Y-86Y05-GA590-X4PEE-ZV8E0

  ZF582-0NW5N-H8D2P-0XZEE-Z22VA

# VMWare虚拟机内安装Ubuntu 20.04 LTS桌面版

- 新建虚拟机：

  ![image-20210202121158250](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202121158250.png)

- 默认，下一步：

  ![image-20210202121245945](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202121245945.png)

- 选择“稍后安装”，下一步：

  ![image-20210202121327585](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202121327585.png)

- 客户机操作系统选择：Linux，版本选择：Ubuntu 64位，下一步：

  ![image-20210202121506074](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202121506074.png)

- 名称自定义即可，路径如果想修改，自定义即可，下一步：

  ![image-20210202121615294](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202121615294.png)

- 处理器数量：1；内核数量：根据自己的电脑配置设置，一般不超过自己电脑CPU的核心数的一半，下一步：

  ![image-20210202121734590](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202121734590.png)

- 内存大小：根据自己电脑配置设置，一般不超过本机电脑内存数量的一半，下一步：

  ![image-20210202122007666](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202122007666.png)

- 网络类型：选择桥接网络，下一步：

  ![image-20210202122043059](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202122043059.png)

- 默认，下一步：

  ![image-20210202122109263](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202122109263.png)

- 默认，下一步：

  ![image-20210202122131708](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202122131708.png)

- 创建磁盘：选择创建新虚拟磁盘，下一步：

  ![image-20210202122210496](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202122210496.png)

- 磁盘大小：根据自身需求设定，下一步：

  ![image-20210202122241687](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202122241687.png)

- 总览页面，确认无误后，完成：

  ![image-20210202122313841](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202122313841.png)

此时，新的Ubuntu虚拟机已创建完毕，接下来就是在该虚拟机上安装Ubuntu系统。

- 点击CD/DVD：

  ![image-20210202122412613](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202122412613.png)

- 在弹出页选择使用ISO镜像文件，点击浏览，找到你自己下载好的Ubuntu镜像，点击确定，即可：

  ![image-20210202122650740](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202122650740.png)

  这一步的目的是选定需要安装哪个镜像。

- 确定镜像之后，直接点击开启此虚拟机，进入安装界面，语言选择中文，点击安装Ubuntu：

  ![image-20210202123514040](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202123514040.png)

- 选择默认，继续：

  ![image-20210202123559300](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202123559300.png)

- 选择正常安装，继续：

  ![image-20210202123628955](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202123628955.png)

- 默认即可，点击现在安装：

  ![image-20210202123713490](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202123713490.png)

- 时区：默认上海即可，继续：

  ![image-20210202123801783](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202123801783.png)

- 自己设置用户相关信息，设置完毕，继续：

  ![image-20210202123841149](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202123841149.png)

- 等待安装成功即可：

  ![image-20210202123917868](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202123917868.png)

- 安装成功，重启虚拟机即可：

  ![image-20210202151408738](C:/Users/anwc/AppData/Roaming/Typora/typora-user-images/image-20210202151408738.png)









# VMWare虚拟机内安装CentOS8(无GUI界面的服务器版)

- 创建CentOS虚拟机

  - 文件 -- 新建虚拟机：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150256729.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 选择自定义 -- 下一步：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150341738.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 硬件兼容性 -- workstation 16.x -- 下一步：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150400178.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 选择稍后安装操作系统 -- 下一步：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150421495.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 客户机操作系统选择Linux -- 版本选择CentOS 7 64位 -- 下一步：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150438772.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 虚拟机名称：自定义 -- 位置：自定义路径即可 -- 下一步：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150504712.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 处理器数量、内核数量、内核总数：自定义即可，如果不修改，默认全1 （建议根据PC配置合理设置） -- 下一步：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150525853.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 内存大小根据PC配置设置，建议最低4GB -- 下一步：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150543347.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 网络连接方式选择：桥接网络 -- 下一步：

  - 选择推荐，下一步：

  - 选择推荐，下一步：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150556148.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 选择创建新虚拟磁盘 -- 下一步：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150611823.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 磁盘大小默认20GB，无需给到太大 -- 下一步：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150626475.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 点击完成，创建完毕。 

  - 安装CentOS前的虚拟机设置：

    虚拟机 -- 设置 -- CD/DVD选项：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/2020113015065112.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

    选择使用ISO映像文件：文件路径自己选择，能定位到目标的ISO镜像文件即可。

- 安装CentOS系统

  - 开启虚拟机，进入安装界面，选择：install centos 7

  - 语言设置：中文 -- 简体

  - 安装位置：默认即可

  - 时区设置：上海/Asia

  - 网络设置：打开

  - 安装介质：默认即可

  - 点击开始安装

  - 设置root账户密码

  - 安装完毕 -- 重启系统 

  - 进入CentOS命令行界面：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201130150706765.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70)

  - 输入密码，登陆 -- 成功 -- 进入系统。

  - 至此，CentOS安装完毕。

  - 注意：这里我们无需GUI的Linux，为了提升系统的资源占用及稳定性，不使用带有GUI界面的Linux。

# VMWare虚拟机内安装WIN10

- 步骤与安装Ubuntu&CentOS类似，只是在选择操作系统时选择WIN10即可。

# Python解释器安装——供学习&生产环境使用皆可

## Windows系统

- 官网下载最新的Windows版Python解释器安装包：www.python.org

- 双击运行解释器安装程序：

  

# Virtualenvwarpper——第三方虚拟环境安装及配置

## Windows系统

## Linux系统

# Anaconda3虚拟环境安装及配置

## Windows系统

## Linux系统

# Python IDE——Pycharm的下载、安装、配置&在Pycharm中配置virtualenv虚拟环境及conda虚拟环境

## Windows系统

## Linux系统

# pip包管理工具的安装及配置

## Windows系统

## Linux系统

# 常用第三方库(非WEB框架及非爬虫库)的安装

## Windows系统

## Linux系统

# Python WEB开发框架——Flask安装及配置

## Windows系统

## Linux系统

# Python WEB开发框架——Django安装及配置

## Windows系统

## Linux系统

# Python WEB开发框架——Torando安装及配置

## Windows系统

## Linux系统

# Python爬虫常用第三方库安装

## Windows系统

## Linux系统

# Python爬虫框架——Scrapy的安装及配置

## Windows系统

## Linux系统

# 常用数据库——MySQL的安装及配置

## Windows系统

## Linux系统

# 常用数据库——Redis的安装及配置

## Windows系统

## Linux系统

# 常用数据库——MongoDB的安装及配置

## Windows系统

## Linux系统

# 常用数据库可视化IDE——DataGrip&Navicat for MySQL的安装及配置

## Windows系统

## Linux系统

# CentOS8配置SSH远程登陆

## Windows系统

## Linux系统

# Docker环境部署

## Windows系统

## Linux系统







