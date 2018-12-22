---
layout: post
title: "Python-14-variable"
categories: Python
tags: Python variable
author: worren li &emsp;

---

* centent
{:toc}

# Python-variable  
## 全局变量和局部变量

* 局部变量
1. 定义在函数内部的变量称为局部变量(函数的形参也是局部变量)
2. 局部变量只能在函数内部使用
3. 局部变量在函数调用时才能创建，在函数调用之后会自动销毁

* 全局变量
1. 定义在函数外部,模块内部的变量称为全局变量
2. 全局变量所有的函数都可以直接访问(但函数内部不能将其直接赋值)
* 说明:
   函数内部赋值语句不会对全局变量造成影响