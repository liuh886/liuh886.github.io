---
layout:     post
title:      QtDesigner加载ui的几个坑
subtitle:   
date:       2019-08-03
author:     ZOZN
tags:
    - pyqt
---



## 开发环境

Python3.6/PyCharm/PyQT5/QT Designer

## 遇到的问题

1 如何加载.ui

2 如何在ui中插入图片

### 解决1

加载有多种方式，推荐loadUI（）函数，能够在脚本中动态加载，无需转换格式再倒入，提高开发效率。

### 解决2

QT Designer内有多种方式加载图片，比如在label控件就支持pixlmap功能，设置图片大小适应，再调节label控件大小，就能取得满意效果。

加载前需要在资源管理器，生成一个.qrc文件，该文件实质上标记语言，记录了图片地址。

使用QT Designer完成上述步骤，能够在设计界面预览效果，但不能在程序执行中看到图片。

那是因为.qrc文件还需要经pyqrcc转换为py文件并import。

```javascript
pyrcc5 target.qrc -o target_new.py
```

然后将其导入到.py应用程序中，因为我们将它作为模块导入，所以无需在结尾添加.py。

```javascript
import target-new
```

现在，.py应用程序将显示图片

## 吐槽

首先是PyQT5生态糟糕，英文资料仍然偏少，由于QT系列版本众多，大量资料都是PyQT4, PySide, QT for c。

其次是QT Designer普及不足。大部分人仍然混杂逻辑代码与界面代码，这是另外一种流行的解决问题的方式，导致了网络上大量的资料没有参考加载。

简单如上述通过QT Designer插入图片，生成qrc，转换格式、导入的过程，就未有中文资料可以参考。

## 感慨

界面开发是比写代码更费心费力的活，因为美观是极细节且无止境的事情，需要大量的时间。

尽管如此，NavPy系列软件在UI设计、文件体积，及功能性上即将迎来大的升级。