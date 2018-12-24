---
layout: post
title: "Python-21- Iterator"
categories: Python
tags: Python 
author: worren li &emsp;

---

* centent
{:toc}

# Python- Iterator
## 迭代器 Iterator
1. 什么是迭代器  
   迭代器是访问可迭代对象的工具  
   迭代器是指iter(obj) 函数返回的对象(实例)  
   迭代器可以用next(it) 函数获取可迭代对象的数据  

2. 迭代器函数iter和next  
    * iter(iterable) 从可迭代对象中获取一个迭代器,iterable必须是能提供一个迭代器的可迭代对象  
    * next(Iterator)  从迭代器iterator中获取下一个记录,如果无法获取下一条记录,则触发StopIteration异常  

* 说明:
   迭代器只能往前取值,不会后退用iter函数可以返回一个可迭代对象的迭代器   
```
示例:
  L = [2, 3, 5, 7]
  it = iter(L)  # 从L对象中获取一个迭代器
  print(next(it))  # 2
  print(next(it))  # 3
  print(next(it))  # 5
  print(next(it))  # 7
  print(next(it))  # StopIteration 异常
  # 用迭代器访问 range() 函数返回的整数序列生成器
  it = iter(range(1, 10, 3))
  next(it)  # 1
  next(it)  # 4
  next(it)  # 7
  next(it)  # StopIteration
```
## 迭代工具函数
* 迭代工具函数的作用是生成一个符合条件的可迭代对象  

* zip(iter1[,iter2[, ...]])  返回一个zip生成器对象  
   此对象用于生成一个元组,此元组的数据分别来自于参数中的每个可迭代对象,生成元组的个数由最小的一个可迭代对象决定  

* enumerate(iterable, start=0)  返回一个enumerate生成器对象,此对象生成类型为(索引,值对) 的元组默认索引从零开始,也可以用start指定  

```
zip示例:
  numbers = [10086, 10000, 10010, 95588]
  names = ['中国移动', '中国电信', '中国联通']
  for t in zip(numbers, names):
      print(t)
             # 结果
             # (10086, '中国移动')
             # (10000, '中国电信')
             # (10010, '中国联通')
  for t in zip(numbers, names, range(1, 10000)):
      print(t)
```
```
enumerate 示例:
  names = ['中国移动', '中国电信', '中国联通']
  # for t in zip(range(100000000), names):
  #     print(t)
  for t in enumerate(names):
      print(t)
  # 打印 (0, '中国移动')  (1, '中国电信')  (2, '中国联通')
  for t in enumerate(names, 101):
      print(t)
  # 打印 (101, '中国移动')  (102, '中国电信')  (103, '中国联通')
```

## 生成器 Generator
1. 什么是生成器:  
   生成器是能够动态提供数据的可迭代对象,生成器在程序运行时生成数据,与容器类不同,它通常不会在  内存中保存大量的数据,而是现用现生成  

2. 好处:  
   不占用计算机的内存  

3. 生成器有两种:  
   生成器函数  
   生成器表达式  

3. 生成器函数的定义  
   含有yield语句的函数是生成器函数,此函数被调用将返回一个生成器对象  

4. yield 翻译为(产生或生成)   
    * yield 语句  
    * 语法:  
      `yield 表达式`
* 说明:
    yield 只能用于def 函数中,目地是将此函数作为生成器函数使用  
    yield 用来生成数据,供迭代器的next(it) 函数使用  

### 说明:
   1. 生成器函数的调用将返回一个生成器对象,生成器对象是一个可迭代对象  
   2. 生成器函数用return会触发一个StopIteration异常(即生成结束)  

### 生成器表达式
1. 语法:  
    (表达式 for 变量 in 可迭代对象 [if 真值表达式])  
2.作用:  
      用推导式形式创建一个新的生成器  
3.说明:   
      if 子句可以省略  
      生成器表达式也可以象列表推导式一样嵌套    
    
      
```
  示例:
    gen = (x**2 for x in range(1, 5))
    it = iter(gen)  # 拿到迭代器
    next(it)  # 1
    next(it)  # 4
    next(it)  # 9
    next(it)  # 16
    next(it)  # StopIteration
```

```
看懂下列函数的输出结果是什么?为什么?
    第1个程序
    L = [2, 3, 5, 7]
    a = [x*10 for x in L]
    it = iter(a)
    print(next(it))   # ???
    L[1] = 333
    print(next(it))   # ???
    第2个程序
    L = [2, 3, 5, 7]
    a = (x*10 for x in L)
    it = iter(a)
    print(next(it))   # ???
    L[1] = 333
    print(next(it))   # ???
```



