---
layout: post
title: Python爬虫案例4：猫眼电影top100榜单数据抓取-xpath实现
date: 2020-09-11
tags: 
      - Spider
      - Python
      - xpath
---

# <font face="楷体"  color='blue'> Python爬虫案例4：猫眼电影top100榜单数据抓取-xpath实现</font>

<p><font face="楷体" color='blue'>作者：Barranzi_</font></p>
<p><font face="楷体" color='blue'>个人github主页：[github](https://github.com/La0bALanG)</font></p>
<p><font face="楷体" color='blue'>个人邮箱：awc19930818@outlook.com</font></p>
<p><font face="楷体" color='blue'>新时代的铁饭碗：一辈子不管走到哪里都有饭吃(还能吃上热乎的)。——佚名</font></p>
<p><font face="楷体" color='red'> 免责声明：</font></p>
<p><font face='楷体' color='red'>		本系列笔记撰写初衷就是为了分享个人知识以及个人学习历程中的感悟及思考，所涉及到的内容`仅供学习与交流`，请勿用作`非法或商业用途`！由此引发的任何法律纠纷`后果自负`，与作者本人无关！</font></p>
<p><font face="楷体"  color='red'>版权声明：</font></p>
<p><font face='楷体' color='red'>		未经作者本人授权，禁止转载！请尊重原创！</font></p>
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200926112825777.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

<p><font face="楷体" color='blue'>注：本文所有代码、案例测试环境：1.Linux -- 系统版本：Ubuntu20.04 LTS   2.windows -- 系统版本：WIN10 64位家庭版</font></p>
----------------------------------------------------------------------------

# 请求URL及页面数据分析

- 目标URL

  猫眼电影网：https://maoyan.com/

  选择榜单-top100:https://maoyan.com/board/4

- 目标数据

  抓取每一条电影信息的`电影名称`、`主演`、`上映时间`

- URL分析

  进入猫眼电影-榜单-top100，随意查看几页信息，观察其URL规律：

  ```python
  https://maoyan.com/board/4?offset=20
  https://maoyan.com/board/4?offset=30
  ...
  https://maoyan.com/board/4?offset=(页数 - 1) * 10
  ```

- 页面及所需数据分析

  浏览器F12-打开控制台-抓手工具-抓到对应电影内容-查看html信息，如下：

  ```html
  <div class="movie-item-info">        
      <p class="name"><a href="/films/4883" title="钢琴家" data-act="boarditem-click" data-val="{movieId:4883}">钢琴家</a></p>        
      <p class="star">                主演：艾德里安·布洛迪,艾米莉娅·福克斯,米哈乌·热布罗夫斯基        </p>        
      <p class="releasetime">上映时间：2002-05-24(法国)</p>    
  </div>
  ```

  所需数据存在于上述html内容中，且该部分html内容存在于response中。

  依据上述内容，确定使用xpath进行匹配。

  匹配思路：

  - 基准xpath: 匹配所有电影信息的节点对象列表;

        ```python
    //dl[@class="board-wrapper"]/dd
        ```

  - 遍历对象列表，依次获取每个电影信息;

    ```python
    for dd in dd_list:
        电影名称 ：.//p[@class="name"]/a/@title
        电影主演 ：.//p[@class="star"]/text()
        上映时间 ：.//p[@class="releasetime"]/text()
    ```

# 编码分析

- 第一步:构造基本URL格式，伪造headers

  ```python
      def __init__(self):
          self.__url = 'https://maoyan.com/board/4?offset={}'
          
      def __get_html(self,url):
          #伪造headers
          headers = {
              'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.83 Safari/537.36'
          }
  ```

- 第二步:发送请求，获得响应数据，转为文本格式，等待re正则解析

  ```python
          reqs = request.Request(url=url, headers=headers)
          # 2.发起正式请求，获得页面响应数据
          reps = request.urlopen(reqs).read().decode()
          self.__parse_html(reps)
  ```

- 第三步：xpath匹配解析数据，结果保存至字典

  ```python
      def __parse_html(self,html):
          dict = {}
          dom = etree.HTML(html)
          dd_list = dom.xpath('//dl[@class="board-wrapper"]/dd')
          for item in dd_list:
              dict['name'] = item.xpath('.//p[@class="name"]/a/@title')
              dict['star'] = item.xpath('.//p[@class="star"]/text()')
              dict['time'] = item.xpath('.//p[@class="releasetime"]/text()')
              print(dict)
  ```

# 编码实现

```python
# -*- coding:utf-8 _*-
"""
@version:
author:安伟超
@time: 2020/09/09
@file: demo05_MaoYanMovie_xpath_OOP.py.py
@environment:virtualenv
@email:awc19930818@outlook.com
@github:https://github.com/La0bALanG
@requirement:
"""

import threading
import requests
from lxml import etree
from fake_useragent import UserAgent


"""

分析
1、基准xpath: 匹配所有电影信息的节点对象列表
    //dl[@class="board-wrapper"]/dd
    
2、遍历对象列表，依次获取每个电影信息
   for dd in dd_list:
	   电影名称 ：.//p[@class="name"]/a/@title
	   电影主演 ：.//p[@class="star"]/text()
	   上映时间 ：.//p[@class="releasetime"]/text()

"""


class MaoYanMovieXpathSpider(object):
    '''

    面向对象思路：
    1.拆分功能细节。整体程序可拆分为:
        1.发请求获得页面
        2.解析页面
        3.持久化存储(写入文件保存)
    2.结合开闭原则，封装功能方法为私有方法，对外提供统一公共接口
    3.采用单例模式：假设本爬虫程序在多个时间、不同情况下多次使用，单例模式实现只创建一个对象，提升性能避免内存占用过高。



    '''
    _instance_lock = threading.Lock()

    # 单例模式实现：__new__方法
    def __new__(cls, *args, **kwargs):
        if not hasattr(MaoYanMovieXpathSpider, '_instance'):
            with MaoYanMovieXpathSpider._instance_lock:
                if not hasattr(MaoYanMovieXpathSpider, '_instance'):
                    MaoYanMovieXpathSpider._instance = object.__new__(cls)
        return MaoYanMovieXpathSpider._instance

    def __init__(self):
        self.__url = 'https://maoyan.com/board/4?offset={}'
        self.__headers = {
            'User-Agent':UserAgent().random
        }

    #设置只读属性
    @property
    def url(self):
        return self.__url

    @property
    def headers(self):
        return self.__headers

    def __get_html(self,url):
        return requests.get(url=url,headers=self.__headers).text

    def __parse_html(self,html):
        dict = {}
        dom = etree.HTML(html)
        dd_list = dom.xpath('//dl[@class="board-wrapper"]/dd')
        for item in dd_list:
            dict['name'] = item.xpath('.//p[@class="name"]/a/@title')
            dict['star'] = item.xpath('.//p[@class="star"]/text()')
            dict['time'] = item.xpath('.//p[@class="releasetime"]/text()')
            print(dict)

    def display(self):
        for offset in range(0,91,10):
            url = self.__url.format(offset)
            self.__parse_html(self.__get_html(url))

def test():
    MaoYanMovieXpathSpider().display()

if __name__ == '__main__':
    test()
```

