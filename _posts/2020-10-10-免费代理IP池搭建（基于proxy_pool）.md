---
layout: post
title: 免费代理IP池搭建（基于proxy_pool）
date: 2020-10-10
tags: 
      - Spider
      - Python
      - xpath


---

# <font face="楷体"  color='blue'> 免费代理IP池搭建（基于proxy_pool）</font>

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

### 仓库地址：[proxy_pool](https://github.com/La0bALanG/proxy_pool)

### 搭建教程

1.将github仓库克隆至本地；

```python
git clone git@github.com:La0bALanG/proxy_pool.git
```

2.至本地仓库解压后进入目录，安装依赖：

```python
pip install -r requirements.txt -i https://pypi.douban.com/simple
```

注意：此过程会安装redis数据库。安装完毕后，至redis数据库安装路径内启动redis服务：

```python
redis-server.exe
```

随后链接redis服务：

```python
redis-cli.exe -h 127.0.0.1 -p 6379
```

因初次链接，无需密码。

进入redis安装目录，打开redis.conf配置文件，修改如下参数：

```python
# requirepass foobared
requirepass yourpassword  //此处注意，行前不能有空格
```

重新设置密码后，需重新链接才能获取操作权限：

```python
redis-cli.exe -h 127.0.0.1 -p 6379 -a 123456 //需添加密码参数
```

3.更改配置文件：

```python
# setting.py 为项目配置文件

# 配置API服务

HOST = "0.0.0.0"               # IP
PORT = 5000                    # 监听端口


# 配置数据库

DB_CONN = 'redis://:pwd@127.0.0.1:8888/0'


# 配置 ProxyFetcher

PROXY_FETCHER = [
    "freeProxy01",      # 这里是启用的代理抓取方法名，所有fetch方法位于fetcher/proxyFetcher.py
    "freeProxy02",
    # ....
]
```

4.启动项目：

```python
# 程序分为: schedule 调度程序 和 server Api服务

# 启动调度程序
python proxyPool.py schedule

# 启动webApi服务
python proxyPool.py server
```

### proxy_pool API

启动web服务后, 默认配置下会开启 [http://127.0.0.1:5010](http://127.0.0.1:5010/) 的api接口服务:

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020101016054313.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2F3YzE5OTMwODE4,size_16,color_FFFFFF,t_70#pic_center)

proxy_pool提供的可用API如下：

| api         | method | Description      | arg  |
| ----------- | ------ | ---------------- | ---- |
| /           | GET    | api介绍          | None |
| /get        | GET    | 随机获取一个代理 | None |
| /get_all    | GET    | 获取所有代理     | None |
| /get_status | GET    | 查看代理数量     | None |
| /delete     | GET    | 删除代理         |      |

### API使用

针对提供的若干API，使用时直接将其封装为函数或类内部的方法即可。

以下为代码举例：

```python
# -*- coding:utf-8 _*-
"""
@version:
author:weichao_an
@time: 2020/10/10
@file: test_proxy.py
@environment:virtualenv
@email:awc19930818@outlook.com
@github:https://github.com/La0bALanG
@requirement:测试proxy_pool相关API接口功能
"""

import requests


class ProxyPoolDemo(object):

    def __init__(self):
        self.retry_counts = 3

    def api_description(self):
        return requests.get('http://127.0.0.1:5010').text

    def get_proxy(self):
        return requests.get('http://127.0.0.1:5010/get').json()

    def delete_proxy(self,proxy):
        return requests.get('http://127.0.0.1:5010/delete/?proxy={}'.format(proxy))

    def get_all_proxy(self):
        return requests.get('http://127.0.0.1:5010/get_all').text

    def get_proxy_status(self):
        return requests.get('http://127.0.0.1:5010/get_status').text

    def test_one_proxy(self):
        proxy = self.get_proxy().get('proxy')
        while self.retry_counts > 0:
            try:
                html = requests.get('http://www.baidu.com', proxies={"http": "http://{}".format(proxy)})
                print(html.status_code)#查看状态码
            except Exception:
                self.retry_counts -= 1
        self.delete_proxy(proxy)



def test():
    proxys = ProxyPoolDemo()
    # desc = proxys.api_description()
    # print(desc)

    # proxys.test_one_proxy()

    # res = proxys.get_proxy_status()
    # print(res)

    res = proxys.get_all_proxy()
    print(res)

if __name__ == '__main__':
    test()
    
    
==============================================


api:/
测试结果：api介绍，内容如下：
{"delete?proxy=127.0.0.1:8080":"delete an unable proxy","get":"get an useful proxy","get_all":"get all proxy
from proxy pool","get_status":"proxy number","pop":"get and delete an useful proxy"}
----------------------------------------------
api:/get_status
测试结果：代理IP池IP数量：
{"count":21}
----------------------------------------------
api:/get_all
测试结果：返回当前代理池所有代理ip：
[{"check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 15:37:56","proxy":"61.135.185.69:80"
,"region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 1
5:36:26","proxy":"61.135.185.152:80","region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last
_status":1,"last_time":"2020-10-10 15:36:56","proxy":"61.135.185.38:80","region":"","source":"","type":""},{"
check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 15:37:19","proxy":"59.120.117.244:80","
region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 15:
37:35","proxy":"171.35.174.251:9999","region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last
_status":1,"last_time":"2020-10-10 15:38:22","proxy":"80.93.212.46:3128","region":"","source":"","type":""},{
"check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 15:37:12","proxy":"222.153.121.26:8080
","region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10
15:38:05","proxy":"61.135.186.80:80","region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last
_status":1,"last_time":"2020-10-10 15:36:27","proxy":"203.162.21.216:8000","region":"","source":"","type":""}
,{"check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 15:38:16","proxy":"61.135.185.68:80"
,"region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 1
5:37:50","proxy":"61.135.185.20:80","region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last_
status":1,"last_time":"2020-10-10 15:37:26","proxy":"61.135.186.243:80","region":"","source":"","type":""},{"
check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 15:37:34","proxy":"218.93.119.165:9002"
,"region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 1
5:37:17","proxy":"61.135.185.153:80","region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last
_status":1,"last_time":"2020-10-10 15:37:55","proxy":"61.135.185.31:80","region":"","source":"","type":""},{"
check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 15:37:26","proxy":"61.135.185.118:80","
region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 15:
38:05","proxy":"61.135.185.90:80","region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last_st
atus":1,"last_time":"2020-10-10 15:37:00","proxy":"45.71.114.134:999","region":"","source":"","type":""},{"ch
eck_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 15:37:32","proxy":"61.135.185.92:80","reg
ion":"","source":"","type":""},{"check_count":1,"fail_count":0,"last_status":1,"last_time":"2020-10-10 15:37:
51","proxy":"61.135.186.222:80","region":"","source":"","type":""},{"check_count":1,"fail_count":0,"last_stat
us":1,"last_time":"2020-10-10 15:37:54","proxy":"61.135.185.78:80","region":"","source":"","type":""}]
```

### 扩展代理及免费代理源介绍：详情参见仓库阅读文档。