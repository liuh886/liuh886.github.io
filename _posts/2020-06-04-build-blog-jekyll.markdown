---
layout:     post
title:      基于Jekyll与GitHub Page的个人博客
subtitle:   不付费不敲代码，不香吗？
date:       2020-06-04
author:     ZOZN
header-img: img/post-bg-cook.jpg
tags: 
    - blog
---

## 流水线记录

### 一、Fork模板

这里是[黄玄大神的github仓库](https://github.com/Huxpro/huxblog-boilerplate)，直接Fork。

进入刚刚fork的项目，setting，将仓库名字改为： username.github.io，username就是你的github用户名（不可以自定义~），然后点击 Rename。

此时，打开 https://username.github.io 已经可以看到一个blog模板自动生成，且可以访问了。

如果无法打开，则先删掉CNAME文件内容。

### 二、修改配置文件

Jekyll是一个生成静态页面的博客工具，相关设置在_config.yml文件内，改为自己的就行了。

>title: ZOZN_109 Blog
>SEOTitle: ZOZN_109 Blog | OffshoreOrient | Geodata and Seismic QC
>header-img: img/post-bg-desk.jpg
>email: liuzhihao109@foxmail.com
>description: "ZOZN_109 Blog"
>keyword: "Blog, ZOZN_109的博客, Python, OOS, OffshoreOrient, Seismic, Geodata"
>url: "http://liuh886.github.io"          # your host, for absolute URL
>baseurl: ""      # for example, '/blog' if your blog hosted on 'host/blog'
>github_repo: "https://github.com/liuh886/liuh886.github.io.git" # you code repository

### 三、写博客

项目根目录下_post就是存放博客文章的地方。文件名使用***年-月-日-标题.md***格式，参考[Jekyll](http://jekyllcn.com/docs/posts/)文档：
>2011-12-31-new-years-eve-is-awesome.md
>2012-09-12-how-to-write-a-blog.textile

文件头里的规则与配置文件一样，参考博客模板里的文章修改即可。

### 四、自定义域名

- Ping username.github.io 获得ip地址。
- 购买域名。
- 在域名商那里设置DNS解析到如上ip。
- CNAME文件中加入自己的域名。

如此通过域名访问时，自动跳转到个人的GitHub Pages页面。

到这一步时，一个博客基本成型了。

### 五、一些效率工具

- GitHub Desktop。Clone项目文件到本地，每次修改后submit然后push到服务器，以后本地写博客更加方便。
- 本地安装Ruby、Jekyll环境。进入项目目录，使用命令 jekyll s 配置web服务器，然后访问127.0.0.1:4000即可在本地调试。

##### 本地调试的一点小经验

如果页面修改后无法刷新，可以删掉_site文件夹的内容，然后在目录下，执行重新生成静态页面。

```
jekyll build
```

### 六、优化完善

- Google Analysis。申请开通，添加个人域名，获得id，在_config.yml中写进去。
- GitTalk。需要注意申请client ID时，需要在Github开发者中申请OAuth App，在填写HomePage URL时，https://offshoreorient.xyz/，最后这个反斜杠不加会导致跳转错误。
- 添加页面。在项目目录下放置md或者html文件，会自动加载到顶部菜单栏，成为一个单独页面。具体从[Jekyll官方文档](https://jekyllrb.com/docs/pages/)了解。
