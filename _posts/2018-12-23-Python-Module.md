---
layout: post
title: "Python-16-module"
categories: Python-module
tags: Python Module
author: worren li &emsp;

---

* centent
{:toc}

# Python-Module
## 模块 Module
### 1. 什么是模块  
* 模块是一个包含有一系列数的数据,函数,类等组成的程序组  
* 模块是一个文件,模块文件通常以.py结尾  
2.  作用:   
    * 让一些相关的数据,函数,类等有逻辑的组织在一起,使  逻辑结束更加清查晰  
    * 模块中的数据,函数和类等可提供给其它模块或程序调用  

### 2.模块的分类:  
    1. 内置模块,在解析器的内部可以直接使用  
    2. 标准库模块,安装python时已安装,且可直接使用  
    3. 第三方模块(通常为开源), 需要自己安装  
        $ pip3 install 模块名
    4. 用户自己编写的模块(可以作为其它人的第三方模块)

### 3.模块的导入 import 语句  
1. import 语句  
```
  语法:
    import 模块名1 [as 模块新名1],模块名2 [as 新名2]
  作用:
    将某模块整体导入到当前模块
  示例:
    import math
    import sys, os
  用法:
    模块名.属性名
    math.factorial(5)
    print(math.pi)  
```

* dir(obj) 函数,返回模块的所有属性的字符串列表  
* help(obj) 函数,可以查看模块相关的文档字符串  

2. from import 语句  
```
  语法:
    from 模块名 import 模块属性名1 [as 属性新名1], \
          模块属性名2 [as 属性新名2], ....
  作用:
    将某模块内的一个或多个属性导入到当前模块的作用域
  示例:
    from math import sin,cos,tan
    from math import pi
    from math import factorial as fac
    print(sin(pi/2)*fac(5)
```

3. from import * 语句  
```
  语法:
    from 模块名 import *
  作用:
    将某模块的所有属性导入到当前模块
  示例:
    from math import *
    print(factorial(5))
    print(sin(pi / 2))
```

### 4.dir([对象])  返回一个字符串列表  
1. dir函数的作用:  
* 如果没有参数调用,则返回当前作用域内所有变量的列表  
* 如果给定一个对象作为参数,则返回这个对象所有变量的列表  
   * 对于一个模块,返回这个模块的全部变量(属性)  
   * 对于一个类对象,返回类对象的所有变量,并递归基类对象的所有变量  
   * 对于其它对象,返回所有变量,类变量和基类变量  

### 5.数学模块  
   模块名: math  
   文档参见:  
     python_base_docs_html/数学模块math.html  

### 6.时间模块 time
   此模块提供了时间相关的函数,  
   文档参见:  
    python_base_docs_html/时间模块time.html  

### 7.系统模块 sys  
   运行时系统相关的信息  
   文档参见:  
    python_base_docs_html/系统模块sys.html 

