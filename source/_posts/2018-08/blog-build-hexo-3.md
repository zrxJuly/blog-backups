---
title: 基于windows平台Git+GitHub+Hexo搭建个人博客（三）
date: 2018-08-15 16:58:12
tags: [Hexo]
categories: Hexo
---
![Hexo banner](blog-build-hexo-3/banner.jpg)
&emsp;&emsp;去年的时候使用Hexo搭建了一个博客，当时主题使用的是JackMan，虽说这个theme是挺好看的了，但是自己感觉还少点东西，所以自从搭建好后就一直没用，笔记还是放在CSDN上。前两天偶然发现了一位大神的博客，当时一眼就喜欢上了这个主题，浏览网站后知道大神的博客也是用Hexo搭建的，内心窃喜。于是乎就去NexT官网clone，又根据自己之前写的博客笔记重新美化了自己的博客，大功告成。  

&emsp;&emsp;下面说一下在美化自己博客的时候遇到的问题及解决方法：
<!-- more -->
## Q&A
### 遇到的问题
needmoreshare2 开启分享功能后使用微信分享无法生成二维码。
### 问题原因
生成二维码的链接失效
### 解决方法
找到资源目录下的needsharebutton.js文件（themes/next/source/lib/needsharebutton/），打开文件，找到该行代码并注释：
```js
var imgSrc = "https://api.qinco.me/api/qr?size=400&content=" + encodeURIComponent(myoptions.url);
```
复制下面的代码粘贴到刚注释的代码下方：
```js
var imgSrc = 'https://api.qrserver.com/v1/create-qr-code/?size=150x150&data='+encodeURIComponent(myoptions.url);
```
重新运行，就OK了。当然，我现在使用的并不是needmoreshare2，而是Addthis，它可以自定义样式，自我感觉要好看一些。
## 分享一些搭建博客相关link
> [hexo搭建个人博客详细教程](https://www.jianshu.com/p/1f8107a8778c) 
> [hexo生成博文插入图片](https://blog.csdn.net/sugar_rainbow/article/details/57415705)
> [hexo设置阅读全文](https://www.jianshu.com/p/78c218f9d1e7)
> [hexo网站统计](https://blog.csdn.net/qw8880000/article/details/80235391)
## 博文存储形式及位置修改
用`hexo new 文章名称` 命令创建新文件的时候，会默认存放于博客根目录的`source/_posts`文件夹下，这样博文少了还好，但是多了就不好维护了。我们可以修改博文存放方式，将博文存放在以`yyyy-MM` 也就是‘年-月’这种格式的文件夹下，以年-月分类，方便维护。下面具体来说配置方法：
### 修改博客根目录配置文件_config.yml
#### 修改*new_post_name* 参数
找到`new_post_name: :title.md` 这里配置新建文件的名称，我们将属性值`:title.md` 修改为`:year-:month/:title.md` 也就是在文件名称前面加了一个目录，该目录名称的格式是`年-月`。所以当我们在执行`hexo new 文章名称` 的时候，会自动在`_post`文件夹下再创建一个以`年-月`为格式的文件夹，新创建的markdown 文件在该文件夹下。
> 你的文件位置： `_post/2018-08/title.md`   

#### 修改*permalink* 参数
找到`permalink: :year/:month/:day/:title/` 这是默认的博文访问路径。我们将其属性值修改为`:year-:month/:title/`。

按照以上步骤更改完后，可以新建一个post试一下。
## 编辑器推荐
写博客当然少不了好用的编辑器啦。
### Sublime Text 3
快速、好用、高效！
### HexoEditor
GitHub上一款开源的MarkDown编辑器。可边编辑边预览。

至于具体哪个好用，自己试了才会知道。我倾向于st3，主要是因为它可以open folder，感觉更方便一些^.^。
