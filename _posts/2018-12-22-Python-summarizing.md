---
layout: post
title: "Python-12-summarzing"
categories: Python
tags: Python 基础知识汇总
author: worren li &emsp;

---

* centent
{:toc}

#Python-Summary of basic knwledge

## 数据类型  
* 不可变的数据类型  
   bool, int, float, complex, str, tuple,frozenset, bytes(字节串,后面再学)    
* 可变的数据类型  
   list, dict, set, bytearray(字节数组,以后再讲)  
   值:
   None, False, True

## 运算符:
```
    + - * / // % **
    > >= < <= == !=
    in / not in
    is / is not
    not   and   or
    &  |  ^  
    +(正号)  -(负号)
    []  # 索引和切片
```

## 表达式  
```
    1
    True
    1 + 2 * 3
    print("hello")  # 函数调用
    L.pop(2)  # 方法调用也是表达式
    sum([1, 2, 5, 10])
    条件表达式:  x if x > y else y
    全部的推导式: 列表,字典,集合推导式(三种)
```

## 语句
   表达式语句(表达式单独在一行可以形成表达式语句)
```
    print("hello")
    "这是一段文字"
    赋值语句:
      a = 100
      a = b = c = 200
      x, y, z = 1, 2, 3
    del 语句
    if 语句
    while 语句
    for 语句
    break 语句
    continue 语句
    pass 语句
```

## 内建函数
```
  len(x)
  max(x)
  min(x)
  sum(x)
  any(x)
  all(x)
  --------- 构造函数 -------
  bool(x)
  int(x)
  float(x)
  complex(x)
  str(x)
  list(x)
  tuple(x)
  dict(x)
  set(x)
  frozenset(x)
  -------------------
  abs(x)
  round(x, y)
  pow(x, y, z=None)
  --------------------
  bin(x)
  oct(x)
  hex(x)
  chr(x)
  ord(x)
  --------------------
  range(start, stop, step)
  ----基本输入输出函数--
  input(x)
  print(....)
  --------------------
  id(x)    返回内存地址
  type(x)  返回类型
```





