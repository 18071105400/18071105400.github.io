---
layout: post
title: "Python-8-copy"
categories: Python
tags: Python 深拷贝浅拷贝
author: worren li &emsp;

---

* centent
{:toc}

# Python-copy
## 深拷贝和浅拷贝
深拷贝 deep copy 和 浅拷贝 shallow copy  

### 浅拷贝
   浅拷贝是指在复制过程中,只复制一层变量,不会复制深层变量绑定的对象的复制过程  
```
  如:
    L = [3.1, 3.2]
    L1 = [1, 2, L]
    L2 = L1.copy()  # 浅拷贝
    print(L1)  # [1, 2, [3.1, 3.2]]
    print(L2)  # [1, 2, [3.1, 3.2]]
    L2[2][0] = 3.14
    print(L1)  # [1, 2, [3.14, 3.2]]
    print(L2)  # [1, 2, [3.14, 3.2]]
```

### 深拷贝 deep copy
```
  如:
    import copy  # 导入复制模块
    L = [3.1, 3.2]
    L1 = [1, 2, L]
    L2 = copy.deepcopy(L1)  # 深拷贝
    print(L1)  # [1, 2, [3.1, 3.2]]
    print(L2)  # [1, 2, [3.1, 3.2]]
    L2[2][0] = 3.14
    print(L1)  # [1, 2, [3.1, 3.2]]
    print(L2)  # [1, 2, [3.14, 3.2]]
```