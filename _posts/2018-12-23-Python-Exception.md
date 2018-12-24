---
layout: post
title: "Python-19-Exception"
categories: Python
tags: Python 
author: worren li &emsp;

---

* centent
{:toc}

# Python-Exception
## 异常 exception (基础)
1. 什么是错误  
   错误是指由于逻辑或语法等导致程序无法正常执行的问题  
2. 特点  
   无法预知  

3. 什么是异常  
   异常是程序出错时标识的一种状态.当导常发生时,程序不会再向下执行,而转去调用此函数的地方待处理此错误并恢复为正常状态  
4. 作用:  
   用作信号通知,通知上层调用者有错误产生需要处理  

5. 程序有两种状态:  
   正常状态/异常状态  

## try语句 的两种语法  
    try-except语句  
    try-finally语句  

### try-except语句的语法
```
    try:
        可能触发异常的语句
    except 错误类型1 [as 变量1]:
        异常处理语句1
    except 错误类型2 [as 变量2]:
        异常处理语句2
    except (错误类型3, 错误类型4) [as 变量3]:
        异常处理语句3
    ...
    except:
        异常处理语句other
    else:
        末发生异常的语句
    finally:
        最终语句
```

1. 作用:  
   偿试捕获错误,得到异常通知,将程序由异常状态转换为正常状态并继续执行  
2. 说明:   
   as 子句是用于绑定错误对象的变量,可以省略  
   except 子句可以有一个或多个,但至少要有一个  
   else 子句最多只能有一个.也可以省略  
   finally子句最多只能有一个.也可以省略  

3. python3 中全部的错误类型:  
   文档参见: 
    python_base_docs_html/python全部的异常类型.html  

### try-finally 语句  
1. 语法  
```
    try:
        可能触发异常的语句
    finally:
        最终语句
```
2. 说明:  
    finally子句不可以省略  
    一定不存在except子句  
3. 作用:  
    通常用try-finally语句来做触发异常时必须要处理的事情无论异常是否发生,finally子句都会被执行  
*  注:  
    try-finally语句不会改变程序的(正常/异常)状态  
    
```
  请问以下语句在做什么事情:
    def get_number():
        s = input("请输入整数:") or '0'
        i = int(s)
        return i

    print(get_number())
    改写上述程序,自己制定规则,让程序不会出崩溃的现象

   改写后:
    def get_number():
        s = input("请输入整数:")
        try:
            i = int(s)
        except:
            i = 0
        return i
```

### raise 语句  
1. 作用:  
   触发一个错误,让程序进入异常状态发送错误通知给调用者  
2. 语法:
```
      raise 异常类型
      或
      raise 异常对象
      或
      raise  # 重新触发上一次异常
```


### assert语句(断言语句)  
1. 语法:  
    assert 真值表达式, 错误数据(通常是字符串)  
2. 作用:  
    当真值表达式为False时,用错误数据创建一个AssertionError类型的错误,并进入异常状态通常用来故意制造一个错误   

3. 等同于:  
   if bool(真值表达式) == False:  
      raise AssertionError(错误数据)  

## 异常中的语句小结:
1. try-except 语句   
      用于捕获(接收)错误通知,把异常状态转为正常状态  
2. try-finally语句  
      用于执行在任何状态(正常/异常)都必须要执行的语句  
3. raise 语句  
      触发错误(发送错误通知),让程序进入异常状态  
4. assert 语句  
      根据条件触发AssertionError类型的错误通知  