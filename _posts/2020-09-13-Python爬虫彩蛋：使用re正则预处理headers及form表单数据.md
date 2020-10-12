---
layout: post
title: Python爬虫彩蛋：使用re正则预处理headers及form表单数据
date: 2020-09-13
tags: 
      - Spider
      - Python
      - re



---

# <font face="楷体"  color='blue'> Python爬虫彩蛋：使用re正则预处理headers及form表单数据</font>

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
------

# 编码实现

```python
# -*- coding:utf-8 _*-
"""
@version:
author:安伟超
@time: 2020/09/11
@file: demo09_re_headers_and_formData.py.py
@environment:virtualenv
@email:awc19930818@outlook.com
@github:https://github.com/La0bALanG
@requirement:使用正则表达式预处理headers及form表单数据
"""

import re

class demoSpider(object):

    def __init__(self):
        self.__headers = """
Accept: application/json, text/javascript, */*; q=0.01
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: keep-alive
Content-Length: 248
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
Cookie: OUTFOX_SEARCH_USER_ID=1559141275@10.169.0.83; JSESSIONID=aaaUEr86rzfeo7xp8b7rx; OUTFOX_SEARCH_USER_ID_NCOO=1009771993.8014448; ___rl__test__cookies=1599804152408
Host: fanyi.youdao.com
Origin: http://fanyi.youdao.com
Referer: http://fanyi.youdao.com/
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.83 Safari/537.36
X-Requested-With: XMLHttpRequest
"""
        self.__formData = """
i: 朋友
from: zh-CHS
to: en
smartresult: dict
client: fanyideskweb
salt: 15998041524052
sign: bf3ecd8f4c8a282ed79468f49aeb69fd
lts: 1599804152405
bv: e915c77f633538e8cf44c657fe201ebb
doctype: json
version: 2.1
keyfrom: fanyi.web
action: lan-select
        """

    def re_parse(self,str_data):
        dict = {}
        for x,y in re.findall('(.*):(.*)',str_data):
            dict[x] = y.strip()
        return dict

    def display(self):
        headers = self.re_parse(self.__headers)
        form_data = self.re_parse(self.__formData)
        print(headers)
        print(form_data)

demoSpider().display()
```

