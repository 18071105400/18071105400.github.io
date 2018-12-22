---
layout: post
title: "Python总结第六篇"
categories: Python
tags: Python for
author: worren li &emsp;

---

* centent
{:toc}

# Python-for

## for语句
1. 作用:
    用来遍历可迭代对象的数据元素
    可迭代对象是指能依次获取数据元素的对象
    如:
    字符串,列表,元组,range函数返回的对象等
2. 语法:
```
    for 变量列表 in 可迭代对象:
        语句块1(此处是可能重复执行的语句块)
    else:
        语句块2
```
3. 说明:
    当在循环体内用break终止循环时,else子句部分的语句不会执行,else子句部分可以省略

### range() 函数:
1. range(stop)  用来生成0~stop区间内的整数,直到stop为止(不包含stop)
2. range(start, stop[,step])  用来生成start~stop区间内的整数,直到stop为止(不包含stop),每个整数间隔step.
3. 格式详见:
    >>> help(range)
5. 作用:
    用来创建一个生成一系列整数的可迭代对象(也叫整数序列生成器)
```
    示意:
      range(4)       生成 0, 1, 2, 3
      range(3, 6)     生成 3, 4, 5
      range(1, 10, 2) 生成 1, 3, 5, 7, 9
      range(5, 0, -1) 生成 5, 4, 3, 2, 1
      range(5, 0, -2) 生成 5, 3, 1
      range(4, 0)     生成 空
```


### for语句嵌套:
```
示例:
    for x in "ABC":
        for y in "123":
            print(x + y)
```

### continue 语句
1. 问题:
    如何让程序不再向下执行，重新开始一次新的循环?
2. 作用:
    用于循环语句(while，for)中，不再执行本次循环内
    continue之后的语句，重新开始一次新的循环
3. 说明:
    1. 在while语句中执行continue语句，将会直接跳转到while语句的真值表达式处，重新判断循环条件
    2. 在for语句中执行continue语句，将会从可迭代对象中取下一个数据绑定变量后再次进行循环

## 循环总结:
    while 语句
    for 语句
    字符串str
    range() 函数返回的对象
    break 语句
    continue 语句

