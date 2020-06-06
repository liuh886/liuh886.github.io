---
layout:     post
title:      动态语言赋值中的浅拷贝与深拷贝
subtitle:   
date:       2019-08-03
author:     ZOZN
tags:
    - python
---



在Python中，经常要对一个list进行赋值、元素删减操作。

a = [1，2，3]

b= a

b.remove（2）

print（a）

如果用=直接赋值，是非拷贝方法。这两个列表是等价的，修改其中任何一个列表都会影响到另一个列表。这也是Python作为动态语言与C这类静态语言在思想上的不同之处。

而使用

b = a.copy()

浅拷贝就能避免之前的问题。但对于list里的嵌套的list，仍然不行。内层的list保存的是地址，复制过去的时候是把地址复制过去了。嵌套的list在内存中指向的还是同一个。 

```
import copy
```

b = copy.deepcopy(a)

如果用deepcopy()方法，则无论多少层，无论怎样的形式，得到的新列表都是和原来无关的，这是最安全最清爽最有效的方法。

使用时，要导入copy。