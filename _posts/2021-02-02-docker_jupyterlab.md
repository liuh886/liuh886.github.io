---
layout:     post
title:      Jupyterlab on Docker
subtitle:   快速配置指南
date:       2021-02-02
author:     ZOZN
header-img: img/post-bg-rwd.jpg
category:   Python
catalog:    true
tags:
    - docker
    - python
---



安装Jupyter最简单的方法是使用Docker。

#### 下载Jupyter官方镜像并运行

```
docker run -d --name jupyter -p 10000:8888 jupyter/scipy-notebook:17aba6048f44
```

> Copy/paste this URL into your browser when you connect for the first time,
>     to login with a token: http://(546219f9e925 or 127.0.0.1):8888/?token=8f2916bd5d3b3d0c953827b09e30bd7e5debbc4ba2251f35

- name 为 jupyter
- ID为546219f9e925 
- 外部端口10000，内部端口8888
- -d 保持jupyter 后台运行。如果忘记加了，可以手动运行，使用Ctrl+P+Q退出。
- jupyter/scipy-notebook:17aba6048f44 是某类某版镜像，更多类别可选 https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html，最新版本可选jupyter/scipy-notebook:latest，https://hub.docker.com/r/jupyter/scipy-notebook/tags/

#### 常见操作

##### 查看镜像ID

```
docker ps -a
```

##### 查看运行状态及日志

```
docker logs -tf ID_OR_name
```

##### 运行或移除Jupyter

```
docker start -a ID_OR_name
docker rm ID_OR_name
```

#### 浏览器打开并修改密码

http://XXX.XXX.XXX.XXX:10000/lab

### 参考资料

- docker退出但不关闭容器方法 https://www.jianshu.com/p/b1ce248d2a42



Published by [ZOZN_109 Blog](http://offshoreorient.xyz), [@ZYZN_109](http://github.com/liuh886)