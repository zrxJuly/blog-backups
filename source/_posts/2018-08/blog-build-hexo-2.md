---
title: 基于windows平台Git+GitHub+Hexo搭建个人博客（二）
date: 2017-09-21 14:55:03
tags: [Hexo]
categories: Hexo
---
## 博客主题设置
&emsp;&emsp;上一篇中我们已经成功搭建了自己的博客并deploy到远程GitHub上，也有很多炫酷的[Hexo主题](https://hexo.io/themes/)，我们可以将我们自己的博客设置成自己喜欢的主题。
在我们本地博客文件夹下，有个名为themes的文件夹，该文件夹就是用来存放各种主题的。Hexo默认的主题是landscape。
### 修改主题的步骤
1. 从网上把我们喜欢的主题下载下来，放到themes文件夹下;
2.  打开博客根目录下的_config.yml文件，找到theme的配置项，
<!-- more -->
```
theme: landscape
```
&emsp;&emsp;将landscape改为自己所换的主题名称，就OK了。
本地测试一下是否修改成功，再deploy到远程。
## 常用的Hexo命令
from [http://www.cnblogs.com/liuxianan/p/build-blog-website-by-hexo-github.html](http://www.cnblogs.com/liuxianan/p/build-blog-website-by-hexo-github.html)
```
hexo new "postName"       #新建文章
hexo new page "pageName"  #新建页面
hexo generate             #生成静态页面至public目录
hexo server               #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy               #部署到GitHub
hexo help                 # 查看帮助
hexo version              #查看Hexo的版本
```