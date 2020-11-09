---
layout: post
title: Python基础语法之——字符串str
date: 2020-11-09
tags: 
      - Python
---

# <font face="楷体"  color='blue'> Python基础语法之——字符串str</font>

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

# 字符串定义

- 由一系列字符组成的不可变序列，存储的是字符的编码值

# 字符编码

- 字节byte：计算机中的最小存储单位，包含8个bit，即八位二进制

- 字符：单个的数字，文字及符号

- 字符集（码表）：存储字符与二进制序列的关系

- 编码：将字符转换为对应的二进制序列的过程

- 解码：将二进制序列转换为对应的字符的过程

- 编码方式：

  > --ASCII编码：包含英文、数字等字符，每个字符1个字节。
  >
  > --GBK编码：兼容ASCII编码，包含21003个中文；英文1个字节，汉字2个字节。
  >
  > --Unicode字符集：国际统一编码，旧字符集每个字符2字节，新字符集4字节。
  >
  > --UTF-8编码：Unicode的存储与传输方式，英文1字节，中文3字节。

- 字符串编解码相关基本函数：

  > ord(字符串):返回该字符串的Unicode码。
  >
  > chr(整数):返回该整数对应的字符串。

# 字符串字面值

- 单引号、双引号的区别

  > 单引号内的双引号不算结束符
  >
  > 双引号内的单引号不算结束符

- 三引号的作用

  > 三引号分为：三单引和三双引

  - 换行会自动转换为换行符\n
  - 三引号可以包含单引号和双引号
  - 作为对象的文档字符串，存储于对象内部的__doc__内置属性

- 转义字符

  | 转义字符    | 描述                                         |
  | :---------- | :------------------------------------------- |
  | \(在行尾时) | 续行符                                       |
  | \\          | 反斜杠符号                                   |
  | \'          | 单引号                                       |
  | \"          | 双引号                                       |
  | \a          | 响铃                                         |
  | \b          | 退格(Backspace)                              |
  | \e          | 转义                                         |
  | \000        | 空                                           |
  | \n          | 换行                                         |
  | \v          | 纵向制表符                                   |
  | \t          | 横向制表符                                   |
  | \r          | 回车                                         |
  | \f          | 换页                                         |
  | \oyy        | 八进制数，yy代表的字符，例如：\o12代表换行   |
  | \xyy        | 十六进制数，yy代表的字符，例如：\x0a代表换行 |
  | \other      | 其它的字符以普通格式输出                     |

# 字符串运算符

| 操作符 | 描述                                                         | 实例                                 |
| :----- | :----------------------------------------------------------- | :----------------------------------- |
| +      | 字符串连接                                                   | >>>a + b 'HelloPython'               |
| *      | 重复输出字符串                                               | >>>a * 2 'HelloHello'                |
| []     | 通过索引获取字符串中字符                                     | >>>a[1] 'e'                          |
| [ : ]  | 截取字符串中的一部分                                         | >>>a[1:4] 'ell'                      |
| in     | 成员运算符 - 如果字符串中包含给定的字符返回 True             | >>>"H" in a True                     |
| not in | 成员运算符 - 如果字符串中不包含给定的字符返回 True           | >>>"M" not in a True                 |
| r/R    | 原始字符串 - 原始字符串：所有的字符串都是直接按照字面的意思来使用，没有转义特殊或不能打印的字符。 原始字符串除在字符串的第一个引号前加上字母"r"（可以大小写）以外，与普通字符串有着几乎完全相同的语法。 | >>>print r'\n' \n >>> print R'\n' \n |
| %      | 格式字符串                                                   | 请看下一章节                         |

# 字符串的格式化及其格式化占位符

- 定义：生成一定格式的字符串

- 语法：字符串%(变量)

  举个例子：

  ​	name = '张三'

  ​	age = 18

  ​	print('我叫%s,我今年%d岁了'%(name,age))

  注意：

  - 占位符只有一个时，传参时无需括号
  - 多个占位符传入时，采用括号标识
  - 多个占位符传参时，按照占位符顺序依次传入

- python字符串格式化占位符

  | 符   号 | 描述                                 |
  | :------ | :----------------------------------- |
  | %c      | 格式化字符及其ASCII码                |
  | %s      | 格式化字符串                         |
  | %d      | 格式化整数                           |
  | %u      | 格式化无符号整型                     |
  | %o      | 格式化无符号八进制数                 |
  | %x      | 格式化无符号十六进制数               |
  | %X      | 格式化无符号十六进制数（大写）       |
  | %f      | 格式化浮点数字，可指定小数点后的精度 |
  | %e      | 用科学计数法格式化浮点数             |
  | %E      | 作用同%e，用科学计数法格式化浮点数   |
  | %g      | %f和%e的简写                         |
  | %G      | %F 和 %E 的简写                      |
  | %p      | 用十六进制数格式化变量的地址         |

- 字符串格式化方法：str.format()
  - 作用：强化格式化字符串的功能
  - 语法：'字符串{}'.format(对象)

# 字符串切片

- 定义：字符串的索引取值

  注意：因为字符串为不可变序列，所以字符串没有索引赋值

- 语法：str[起始位置:结束位置:步长]

# 字符串常用方法

| **方法**                                                     | **描述**                                                     |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [string.capitalize()](https://www.runoob.com/python/att-string-capitalize.html) | 把字符串的第一个字符大写                                     |
| [string.center(width)](https://www.runoob.com/python/att-string-center.html) | 返回一个原字符串居中,并使用空格填充至长度 width 的新字符串   |
| **string.count(str, beg=0, end=len(string))**                | 返回 str 在 string 里面出现的次数，如果 beg 或者 end 指定则返回指定范围内 str 出现的次数 |
| [string.decode(encoding='UTF-8', errors='strict')](https://www.runoob.com/python/att-string-decode.html) | 以 encoding 指定的编码格式解码 string，如果出错默认报一个 ValueError 的 异 常 ， 除非 errors 指 定 的 是 'ignore' 或 者'replace' |
| [string.encode(encoding='UTF-8', errors='strict')](https://www.runoob.com/python/att-string-encode.html) | 以 encoding 指定的编码格式编码 string，如果出错默认报一个ValueError 的异常，除非 errors 指定的是'ignore'或者'replace' |
| **string.endswith(obj, beg=0, end=len(string))**             | 检查字符串是否以 obj 结束，如果beg 或者 end 指定则检查指定的范围内是否以 obj 结束，如果是，返回 True,否则返回 False. |
| [string.expandtabs(tabsize=8)](https://www.runoob.com/python/att-string-expandtabs.html) | 把字符串 string 中的 tab 符号转为空格，tab 符号默认的空格数是 8。 |
| **string.find(str, beg=0, end=len(string))**                 | 检测 str 是否包含在 string 中，如果 beg 和 end 指定范围，则检查是否包含在指定范围内，如果是返回开始的索引值，否则返回-1 |
| **string.format()**                                          | 格式化字符串                                                 |
| **string.index(str, beg=0, end=len(string))**                | 跟find()方法一样，只不过如果str不在 string中会报一个异常.    |
| [string.isalnum()](https://www.runoob.com/python/att-string-isalnum.html) | 如果 string 至少有一个字符并且所有字符都是字母或数字则返回 True,否则返回 False |
| [string.isalpha()](https://www.runoob.com/python/att-string-isalpha.html) | 如果 string 至少有一个字符并且所有字符都是字母则返回 True,否则返回 False |
| [string.isdecimal()](https://www.runoob.com/python/att-string-isdecimal.html) | 如果 string 只包含十进制数字则返回 True 否则返回 False.      |
| [string.isdigit()](https://www.runoob.com/python/att-string-isdigit.html) | 如果 string 只包含数字则返回 True 否则返回 False.            |
| [string.islower()](https://www.runoob.com/python/att-string-islower.html) | 如果 string 中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是小写，则返回 True，否则返回 False |
| [string.isnumeric()](https://www.runoob.com/python/att-string-isnumeric.html) | 如果 string 中只包含数字字符，则返回 True，否则返回 False    |
| [string.isspace()](https://www.runoob.com/python/att-string-isspace.html) | 如果 string 中只包含空格，则返回 True，否则返回 False.       |
| [string.istitle()](https://www.runoob.com/python/att-string-istitle.html) | 如果 string 是标题化的(见 title())则返回 True，否则返回 False |
| [string.isupper()](https://www.runoob.com/python/att-string-isupper.html) | 如果 string 中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是大写，则返回 True，否则返回 False |
| **string.join(seq)**                                         | 以 string 作为分隔符，将 seq 中所有的元素(的字符串表示)合并为一个新的字符串 |
| [string.ljust(width)](https://www.runoob.com/python/att-string-ljust.html) | 返回一个原字符串左对齐,并使用空格填充至长度 width 的新字符串 |
| [string.lower()](https://www.runoob.com/python/att-string-lower.html) | 转换 string 中所有大写字符为小写.                            |
| [string.lstrip()](https://www.runoob.com/python/att-string-lstrip.html) | 截掉 string 左边的空格                                       |
| [string.maketrans(intab, outtab\])](https://www.runoob.com/python/att-string-maketrans.html) | maketrans() 方法用于创建字符映射的转换表，对于接受两个参数的最简单的调用方式，第一个参数是字符串，表示需要转换的字符，第二个参数也是字符串表示转换的目标。 |
| [max(str)](https://www.runoob.com/python/att-string-max.html) | 返回字符串 *str* 中最大的字母。                              |
| [min(str)](https://www.runoob.com/python/att-string-min.html) | 返回字符串 *str* 中最小的字母。                              |
| **string.partition(str)**                                    | 有点像 find()和 split()的结合体,从 str 出现的第一个位置起,把 字 符 串 string 分 成 一 个 3 元 素 的 元 组 (string_pre_str,str,string_post_str),如果 string 中不包含str 则 string_pre_str == string. |
| **string.replace(str1, str2,  num=string.count(str1))**      | 把 string 中的 str1 替换成 str2,如果 num 指定，则替换不超过 num 次. |
| [string.rfind(str, beg=0,end=len(string) )](https://www.runoob.com/python/att-string-rfind.html) | 类似于 find() 函数，返回字符串最后一次出现的位置，如果没有匹配项则返回 -1。 |
| [string.rindex( str, beg=0,end=len(string))](https://www.runoob.com/python/att-string-rindex.html) | 类似于 index()，不过是从右边开始.                            |
| [string.rjust(width)](https://www.runoob.com/python/att-string-rjust.html) | 返回一个原字符串右对齐,并使用空格填充至长度 width 的新字符串 |
| [string.rpartition(str)](https://www.runoob.com/python/att-string-rpartition.html) | 类似于 partition()函数,不过是从右边开始查找                  |
| [string.rstrip()](https://www.runoob.com/python/att-string-rstrip.html) | 删除 string 字符串末尾的空格.                                |
| **string.split(str="", num=string.count(str))**              | 以 str 为分隔符切片 string，如果 num 有指定值，则仅分隔 num+ 个子字符串 |
| [string.splitlines([keepends\])](https://www.runoob.com/python/att-string-splitlines.html) | 按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表，如果参数 keepends 为 False，不包含换行符，如果为 True，则保留换行符。 |
| [string.startswith(obj, beg=0,end=len(string))](https://www.runoob.com/python/att-string-startswith.html) | 检查字符串是否是以 obj 开头，是则返回 True，否则返回 False。如果beg 和 end 指定值，则在指定范围内检查. |
| **string.strip([obj])**                                      | 在 string 上执行 lstrip()和 rstrip()                         |
| [string.swapcase()](https://www.runoob.com/python/att-string-swapcase.html) | 翻转 string 中的大小写                                       |
| [string.title()](https://www.runoob.com/python/att-string-title.html) | 返回"标题化"的 string,就是说所有单词都是以大写开始，其余字母均为小写(见 istitle()) |
| **string.translate(str, del="")**                            | 根据 str 给出的表(包含 256 个字符)转换 string 的字符,要过滤掉的字符放到 del 参数中 |
| [string.upper()](https://www.runoob.com/python/att-string-upper.html) | 转换 string 中的小写字母为大写                               |
| [string.zfill(width)](https://www.runoob.com/python/att-string-zfill.html) | 返回长度为 width 的字符串，原字符串 string 右对齐，前面填充0 |