---
layout: post
title: Python基础语法之——集合(set)与固定集合(frozenset)
date: 2020-10-27
tags: 
      - Python
---

# <font face="楷体"  color='blue'> Python基础语法之——集合(set)与固定集合(frozenset)</font>

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

# 集合与固定集合定义

> 1.集合（set）是一个无序的不重复元素的可变散列容器。
>
> 2.固定集合(frozenset)是一个无序的不重复元素的不可变散列容器。

注意：

- 集合元素必须是可哈希对象，可哈希对象的hash码对应唯一值，所以集合中的元素只可以为不可变类型数据对象，例如数字类型，字符串，元组，固定集合，而列表，字典，集合等可变类型数据对象不能存在于集合内部。

- 何谓可哈希对象？可哈希对象是指地址定位值唯一的对象，地址定位值唯一是指：变量引用改变，则浮点数对象也发生变化。所以，变量引用改变但浮点数对象不会产生变化的对象就是不可哈希对象。如下代码：

  ```python
  C:\Users\anwc>ipython
  Python 3.7.0 (default, Jun 28 2018, 08:04:48) [MSC v.1912 64 bit (AMD64)]
  Type 'copyright', 'credits' or 'license' for more information
  IPython 6.5.0 -- An enhanced Interactive Python. Type '?' for help.
  
  In [1]: a = [1,2,3]
  
  In [2]: id(a)
  Out[2]: 1660781748808
  
  In [3]: a[1] = '123'
  
  In [4]: id(a)
  Out[4]: 1660781748808
  
  In [5]: b = 123
  
  In [6]: id(b)
  Out[6]: 140733552590400
  
  In [7]: b = 234
  
  In [8]: id(b)
  Out[8]: 140733552593952
  ```

# 基础操作

- 创建空集合

  ```python
  1.创建可变的空集合：set()
  2.创建不可变的空集合：frozenset()
  ```

  注意：不能使用{}创建空集合，因为此种方法创建的是空字典。

- 创建具有默认值的集合

  ```python
  集合名 = {可哈希对象1,可哈希对象2,...}
  集合名 = set(可迭代对象)
  ```

- 向集合中添加元素，注意：只针对可变集合

  ```python
  集合名.add(可哈希对象)
  ```

- 集合中删除元素，注意：只针对可变集合

  ```python
  集合名.discard(可哈希对象)
  ```

# 集合与固定集合的运算

- 交集&：返回共同元素。

  ```python
  In [1]: s1 = {1,2,3}
  
  In [2]: s2 = {2,3,4}
  
  In [3]: s1 & s2
  Out[3]: {2, 3}
  ```

- 并集 | ：返回不重复元素

  ```python
  In [1]: s1 = {1,2,3}
  
  In [2]: s2 = {2,3,4}
  
  In [4]: s1 | s2
  Out[4]: {1, 2, 3, 4} 
  ```

- 补集-：返回只属于其中之一的元素

  ```python
  In [1]: s1 = {1,2,3}
  
  In [2]: s2 = {2,3,4}
  
  In [5]: s1 - s2
  Out[5]: {1}#属于s1单不属于s2的
  
  In [6]: s2 -s1
  Out[6]: {4}#属于s2但不属于s1的 
  ```

- 补集^：返回不同的的元素

  ```python
  In [1]: s1 = {1,2,3}
  
  In [2]: s2 = {2,3,4}
  
  In [7]: s1 ^ s2
  Out[7]: {1, 4}#等同于(s1-s2 | s2-s1) 
  ```

- 子集<：判断一个集合的所有元素是否完全在另一个集合中

  ```python
  In [8]: s3 = {1,2,3,4,5}
  
  In [9]: s4 = {1,2,3}
  
  In [10]: s4 < s3
  Out[10]: True
  ```

- 超集>：判断一个集合是否具有另一个集合的所有元素

  ```python
  In [8]: s3 = {1,2,3,4,5}
  
  In [9]: s4 = {1,2,3}
  
  In [10]: s4 < s3
  Out[10]: True
  
  In [11]: s3 > s4
  Out[11]: True
  ```

- 相同或不同 ==  !=：判断集合中的所有元素是否和另一个集合相同。

  ```python
  In [12]: s5 = {1,2,3}
  
  In [13]: s6 = {3,2,1}
  
  In [14]: s5 == s6
  Out[14]: True
  
  In [15]: s5 != s6
  Out[15]: False
  ```

# 集合常用操作

- 集合长度：len()

  ```python
  In [16]: s7 = set(("Google", "Runoob", "Taobao"))
  
  In [17]: len(s7)
  Out[17]: 3
  ```

- 清空集合：clear()

  ```python
  In [16]: s7 = set(("Google", "Runoob", "Taobao"))
  
  In [18]: s7
  Out[18]: {'Google', 'Runoob', 'Taobao'}
  
  In [19]: s7.clear()
  
  In [20]: s7
  Out[20]: set()
  ```

- 判断元素是否在集合中，存在返回True，不存在返回False

  ```python
  In [22]: s7 = set(("Google", "Runoob", "Taobao"))
  
  In [23]: s7
  Out[23]: {'Google', 'Runoob', 'Taobao'}
  
  In [24]: 'Taobao' in s7
  Out[24]: True
  
  In [25]: 'taobao' in s7
  Out[25]: False
  ```

# 总结：集合内置方法

| 方法                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [add()](https://www.runoob.com/python3/ref-set-add.html)     | 为集合添加元素                                               |
| [clear()](https://www.runoob.com/python3/ref-set-clear.html) | 移除集合中的所有元素                                         |
| [copy()](https://www.runoob.com/python3/ref-set-copy.html)   | 拷贝一个集合                                                 |
| [difference()](https://www.runoob.com/python3/ref-set-difference.html) | 返回多个集合的差集                                           |
| [difference_update()](https://www.runoob.com/python3/ref-set-difference_update.html) | 移除集合中的元素，该元素在指定的集合也存在。                 |
| [discard()](https://www.runoob.com/python3/ref-set-discard.html) | 删除集合中指定的元素                                         |
| [intersection()](https://www.runoob.com/python3/ref-set-intersection.html) | 返回集合的交集                                               |
| [intersection_update()](https://www.runoob.com/python3/ref-set-intersection_update.html) | 返回集合的交集。                                             |
| [isdisjoint()](https://www.runoob.com/python3/ref-set-isdisjoint.html) | 判断两个集合是否包含相同的元素，如果没有返回 True，否则返回 False。 |
| [issubset()](https://www.runoob.com/python3/ref-set-issubset.html) | 判断指定集合是否为该方法参数集合的子集。                     |
| [issuperset()](https://www.runoob.com/python3/ref-set-issuperset.html) | 判断该方法的参数集合是否为指定集合的子集                     |
| [pop()](https://www.runoob.com/python3/ref-set-pop.html)     | 随机移除元素                                                 |
| [remove()](https://www.runoob.com/python3/ref-set-remove.html) | 移除指定元素                                                 |
| [symmetric_difference()](https://www.runoob.com/python3/ref-set-symmetric_difference.html) | 返回两个集合中不重复的元素集合。                             |
| [symmetric_difference_update()](https://www.runoob.com/python3/ref-set-symmetric_difference_update.html) | 移除当前集合中在另外一个指定集合相同的元素，并将另外一个指定集合中不同的元素插入到当前集合中。 |
| [union()](https://www.runoob.com/python3/ref-set-union.html) | 返回两个集合的并集                                           |
| [update()](https://www.runoob.com/python3/ref-set-update.html) | 给集合添加元素                                               |