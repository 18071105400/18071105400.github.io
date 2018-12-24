---
layout: post
title: "Python-15-Function programming"
categories: Python
tags: Python Function programiming
author: worren li &emsp;

---

* centent
{:toc}

# Python - Function programiming
## 函数式编程 Function programiming

1. 函数式编程是指用一系列函数解决问题
   * 好处:
      a. 用每个函数完成细小的功能,一系列函数的任意组合可以解决大问题
      b. 函数仅接收输入并产生输出,不包含任何能影响输出的内部状态

2. 函数的可重入性  
    * 当一个函数的输入实参一定.结果也必须一定的函数称为可重入函数
    * 说明:
       可重入函数在函数内部一定不访问除局部变量以外的变量
```
示例:
    # 可重入函数:
    def myadd(x, y):
       return x + y
    # 不可重入函数
    s = 0
    def myadd2(x, y):
        global s
        s += x + y
        return s
```

### 高阶函数 High Order Function
```
    map  filter  sorted
```

#### 什么是高阶函数
* 满足下列条件中一个的函数即为高阶函数
    1. 函数接受一个或多个函数作用参数传入
    2. 函数返回一个函数

##### 1.map 函数
* map(func, \*iterable)返回一个可迭代对象，此可迭代对象用函数 func对可迭代对象iterable中的每一个元素作用参数计算后得一结果，当最短的一个可迭代对象不再提供数据时可迭代对象生成数据结束
```
  示例:
    def power2(x):
        return x ** 2
    # 生成一个可迭代对象,此可迭代对象可以生成1~9的
    # 整数的平方
    for x in map(power2, range(1, 10)):
        print(x)
    # 生成一个可迭代对象, 此可迭代对象可以生成:
      1**4, 2**3, 3**2, 4**1
      
    def mypower2(x, y):
        return x ** y
    
    for x in map(mypower2,[1,2,3,4],[4,3,2,1]):
        print(x)
    # 看懂下面程序在做什么:
    for x in map(pow, [1,2,3,4], [4,3,2,1],
                 range(5, 10)):
        print(x)
```

##### 2. filter函数:
* filter(function, iterable)   返回一个可迭代对象，此可迭代对象将iterable提供的数据用函数function进行筛选，function将对iterable中的每个元素求值，返回False将此数据丢弃,返回True则保留
```
  示例:
    def isodd(x):
       return x % 2 == 1
    # 打印0~10之间所有的奇数:
    for x in filter(isodd, range(11)):
        print(x)
    for x in filter(lambda x:x%2, range(11)):
        print(x)
    
    L = [x for x in filter(isodd, range(11))]
```

##### 3.sorted函数
1. 作用:
    将原可迭代对象提供的数据进行排序, 生成排序后的列表
2. 格式说明
    sorted(iterable, key=None, reverse=False)
    返回一个新的包含所有可迭代对象中数据的列表,新的列表是排序过的列表
3. 参数说明:
    iterable  可迭代对象   
    key     函数是用来提供一个值,这个值将作用排序的依据  (只能等于函数如：max ,min )   
    reverse  标志用来设置是否降序排序(默认为升序))   
```
  示例:
    L = [5, -2, -4, 0, 3, 1]  
    L2 = sorted(L)  # L2=[-4, -2, 0, 1, 3, 5]
    L3 = sorted(L, reverse=True)  # 从大到小排序

    L4 = sorted(L, key=abs)  # L4=[0, 1, -2, 3, -4, 5]
                             # 依据 0, 1,  2, 3,  4, 5
    
    names = ['Tom', 'Jerry', 'Spike', 'Tyke']
    sorted(names)  # ['Jerry', 'Spike', 'Tom', 'Tyke']
    sorted(names, key=len)
    sorted(names, key=len, reverse=True)
```

### 递归函数  recursion
* 函数直接或间接的调用自身
```
示例:
    # 函数直接调用自身
    def f():
        f()  # 调用自己
    f()
    # 函数间接调用自身
    def fa():
        fb()
    
    def fb():
        fa()
    
    fa()
```
#### 递归说明:
* 递归一定要控制递归的层数,当符合某一条件时要终止递归调用，几乎所有的递归都能用while循环来代替

##### 递归的优缺点:
    * 优点:递归可以把问题简单化,让思路更为清晰,代码更简洁   
    * 缺点: 递归因系统环境影响大,当递归深度太大时,可能会得到不可预知的结果  

##### 递归函数的执行分为两个阶段:  
* 递推阶段: 调用进入函数内部  
* 回归阶段: 返回结果,得到最终结果  


### 闭包 closure
1. 什么是闭包
* 闭包是指引用了此函数外部变量的函数(外部变量指:外部嵌套函数作用域内的变量)

2. 闭包必须满足三个条件:  
   1. 必须有一个内嵌函数  
   2. 内嵌函数必须引用外部函数中的变量  
   3. 外部函数返回值必须是内嵌函数  

3. 注意点:  
* 由于闭包会使得函数中的变量都被保留在内存中,内存消耗比较大,所以不能滥用闭包  

4. 闭包测试题:  

```
  试看下列程序的执行结果是什么?
  def get_funs(n):
      L = []
      for i in range(n):
          L.append(lambda x: x * i)
      return L

  funs = get_funs(4)
  print(funs[0](10))  # 30
  print(funs[1](10))  # 30
  print(funs[2](10))  # 30
  print(funs[3](10))  # 30
```


## 装饰器 decorators(专业提高篇)
### 什么是装饰器
1. 装饰器是一个函数,主要作用是用来包装另一个函数或类(后面才讲)，包装的目的是在不改变原函数名(或类名) 的情况下改变或添加被包装对象的行为  

2. 函数装饰器  
* 是指装饰器是一个函数,传入的是一个函数,返回的也是一个函数  

*  语法:
```
    def 装饰器函数名(参数):
       语句块
       return 函数对象
    
    @装饰器函数名<换行>
    def 函数名(形参列表):
        语句块
```

3. 函数的文档字符串
* 函数内第一次末赋值给任何变量的字符串是此函数的文档字符串

* 语法:
```
    def 函数名(参数列表):
        '函数的文档字符串'
        语句块
```
```
  示例:
    def hello(name):
        '''这是一个向别人问好的函数
        name 绑定人的姓名
        '''
        pass
```

4. 说明:
* 文档字符串通常用来说明本函数的功能的使用方法，函数的文档字符串绑定在函数对象的 __doc__ 属性上  
  
* 函数的 __doc__ 属性  
   __doc__属性用于绑定函数的文档字符串  
   
```
函数定义语句的完整的语法:
 [@装饰器名1]
 [@装饰器名2]
 ...
 def 函数名([位置形参], [*元组形参], [命名关键字形参]
            ,[**字典形参]):
    '文档字符串'
    语句块
```