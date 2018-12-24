---
layout: post
title: "Python-18-File"
categories: Python
tags: Python File
author: worren li &emsp;

---

* centent
{:toc}

# Python-File  
## 1.文件 File  
   * 文件是用于存储数据的基本单位  
   * 文件通常用来长期存储数据  
   * 文件中数据是以字节为单位进行顺序存储的  

## 2.文件的操作流程  
1. 打开文件  
2. 读/写文件  
3. 关闭文件  
   * 注: 任何的操作系统,一个应用程序同时打开文件的数量有最大数限制  

### 1. 文件的打开函数  
   * open(filename, mode='rt') 用于打开一个文件,返回此用来操作此文件的文件流对象,如果打开失败,则会触发OSError错误通知  

### 2.文件流对象的关闭方法  
   F.close()  关闭文件.释放系统资源  

### 3.以十六进制方式显示文件内容的命令:  
   $ xxd  文件名  

## 3.python3的文本文件模式  
1. 模式字符: 't'
2. 说明:
    1. 对文本文件的读写操作需要用字符串(str)进行读写操作  
    2. 在读写过程中会自动进行编码(encode) 和 解码(decode)操作  
    3. 以行为单位分隔,在python内部统一用'\n'作用换行符进行分隔  

3. 各操作系统的换行符:  
   Linux换行符: '\n'  
   Windows换行符: '\r\n'  
   新的Mac OS换行符: '\n'  


### 1.文本文件的写操作:
```
方法:  
    F.write(x)  
    F.writelines(列表)  
模式字符串:
     'w'  
     'x'  
     'a' 
```
  详见文档: python_base_docs_html/文件.html

### 2.二进制文件操作  
* 二进制模式字符: 'b'
* 默认文件中存储的都是以字节(byte)为单位的数据,通常人人为的格式  
* 对二进制文件的读写需要用字符串(bytes) 或字节数组(bytearray)进行操作  

* 对于二进制文件读写方法都 需要用字节为单位进行操作
```
    F.read(n)
    F.readline()
    F.readlines()
    F.write(字节串)
    F.writelines(字节串组成的列表)
```

#### F.seek方法
* 作用:
   设置文件的读写位置,返回新的读写位置
* 格式:
```
    F.seek(偏移量, whence=相对位置)
      偏移量
        大于0代表向文件末尾方向移动
        小于0代表向文件头方向移动
      相对位置:
        0 代表从文件头开始偏移
        1 代表从当前读写位置开始偏移
        2. 代表从文件尾开始偏移
```

### 3.标准输入输出文件:
* 模块名:
```
sys
  sys.stdin  标准输入文件(默认为键盘)
  sys.stdout 标准输出文件(默认为屏幕终端)
  sys.stderr 标准错误输出文件(默认为屏幕终端)
  注: 标准文件不需要打开即可以使用,也不用手动关闭
```

## 3.十个汉字占多少个字节?

### 1.汉字编码(只有两种)
```
   * 国标系列:  
    GB18030(二字节或四字节编码, 27533个字)  
    GBK(二字节编码,20013个字)  
    GB2313(二字节编码,约7千多个字)  
    (Windows常用)  

   * 国际标准:
    UNICODE(UNCODE16/UNICODE32)  <-> UTF-8  
    (Linux/Mac OS X/ IOS/ Android 常用)  
    UTF-8中:
         英文ASCII (0x0 - 0x7F) 一字节
         (0x80 - 0x3FF)         二字节
         (0x400 - 0xFFFF)       三字节(中文在此区)
```

### 2.python 编码字符串:
```
  'gb2312'
  'gbk'
  'gb18030'
  'utf-8'
  'ascii'
  ...

  如:
    s = "你好"
    print(s.encode('gbk'))
    print(s.encode('utf-8'))
    print(s.encode('ascii'))#出错,"你好"不在ascii内
```


### 3.编码注释:
```
  在源文件中,第一行或第二行写入的如下内容是编码注释
  \# -*- coding:gbk -*- 
  或 
  \# -*- coding:utf-8 -*-
```