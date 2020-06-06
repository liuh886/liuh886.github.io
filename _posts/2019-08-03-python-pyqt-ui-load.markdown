---
layout:     post
title:      matplotlib分割画布的几种方法
subtitle:   
date:       2019-08-03
author:     ZOZN
tags:
    - matplotlib
---



简单的成图外，有时需要实现多图合一的效果，我们可以利用subplot函数或者GridSpec函数来实现。

### subplots

使用`plt.subplots`建立一个2行2列的图像窗口，`sharex=True`表示共享x轴坐标, `sharey=True`表示共享y轴坐标. `((ax11, ax12), (ax13, ax14))`表示第1行从左至右依次放`ax11`和`ax12`, 第2行从左至右依次放`ax13`和`ax14`.

```
f, ((ax11, ax12), (ax13, ax14)) = plt.subplots(2, 2, sharex=True, sharey=True)
```

使用`ax11.scatter`创建一个散点图.

```
ax11.scatter([1,2], [1,2])
```

`plt.tight_layout()`表示紧凑显示图像, `plt.show()`表示显示图像.

```
plt.tight_layout()
plt.show()
```

[![Subplot 分格显示](https://morvanzhou.github.io/static/results/plt/4_2_3.png)](https://morvanzhou.github.io/static/results/plt/4_2_3.png)

### gridspec

 

使用`import`导入`matplotlib.pyplot`模块, 并简写成`plt`. 使用`plt.figure()`创建一个图像窗口

```
import matplotlib.pyplot as plt

plt.figure()
```

使用`plt.subplot2grid`来创建第1个小图, `(3,3)`表示将整个图像窗口分成3行3列, `(0,0)`表示从第0行第0列开始作图，`colspan=3`表示列的跨度为3, `rowspan=1`表示行的跨度为1. `colspan`和`rowspan`缺省, 默认跨度为1.

```
ax1 = plt.subplot2grid((3, 3), (0, 0), colspan=3)
ax1.plot([1, 2], [1, 2])    # 画小图
ax1.set_title('ax1_title')  # 设置小图的标题
```

使用`plt.subplot2grid`来创建第2个小图, `(3,3)`表示将整个图像窗口分成3行3列, `(1,0)`表示从第1行第0列开始作图，`colspan=2`表示列的跨度为2. 同上画出 `ax3`, `(1,2)`表示从第1行第2列开始作图，`rowspan=2`表示行的跨度为2. 再画一个 `ax4` 和 `ax5`, 使用默认 `colspan, rowspan`.

```
ax2 = plt.subplot2grid((3, 3), (1, 0), colspan=2)
ax3 = plt.subplot2grid((3, 3), (1, 2), rowspan=2)
ax4 = plt.subplot2grid((3, 3), (2, 0))
ax5 = plt.subplot2grid((3, 3), (2, 1))
```

使用`ax4.scatter`创建一个散点图, 使用`ax4.set_xlabel`和`ax4.set_ylabel`来对x轴和y轴命名.

```
ax4.scatter([1, 2], [2, 2])
ax4.set_xlabel('ax4_x')
ax4.set_ylabel('ax4_y')
```

[![Subplot 分格显示](https://morvanzhou.github.io/static/results/plt/4_2_1.png)](https://morvanzhou.github.io/static/results/plt/4_2_1.png)