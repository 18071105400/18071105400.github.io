---
layout: post
title: "Python-5-while"
categories: Python
tags: Python while
author: worren li &emsp;

---

* centent
{:toc}

# Python-while

## while语句:
1. 作用:
    根据一定条件，重复执行一条语句或多条语句
2. 语法:
```
    while 真值表达式:
        语句块1(此部分语句可能会重复执行多次)
    else:
        语句块2
```
3. 说明:
    * 先执行真值表达式,得到布尔值为True或False
    * 如果真值表达式的值为True,则执行语句块1,然后再次返回到第1步，重复进行测试真值表达式的值
    * 如果真值表达式的值为False,则执行else子句部分的语句块2,然后结束此while语句的执行
* 注: else子句部分可以省略(同if语句类似)
      
4. while语句的注意事项:
    * 要控制循环的真值表达式的值来防止死循环
    * 通常用真值表达式内的循环变量来控制循环条件
    * 通常在语句内部改变循环变量
    
5. while 语句嵌套:
    while 语句本身就是语句,和其它语句一样，可以嵌套到任何的复合语句中
```
   示意:
    while 真值表达式:
        ....
        while 真值表达式2:
            ....
        else:
            ...
        ...
    else:
        ...
```

### 2.break 语句
1. 问题:
    如果在循环过程中不想再继续循环语句的执行了,怎么办?
2. 作用:
    用于循环语句(while,for语句)中,用来终止当前循环语句的执行  
3. 说明:
    * 当break语句执行后,此循环语句break之后的语句将不再执行
    * break 语句通常和if语句组合使用
    * break 语句终止循环时,循环语句的else子句的语句不会执行
    * break 语句只能终止当前循环语句的执行,如果有循环嵌套时,不会跳出嵌套的外重循环
    * break语句只能在循环语句(while,for语句)的内部使用

### 3.死循环
1. 注意事项：  
    * 死循环是指循环条件一直成立的循环  
    * 死循环能通常用break语句来终止循环  
    * 死循环的else子句永远不会执行  